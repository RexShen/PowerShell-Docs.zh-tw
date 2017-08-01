---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "多電腦部署和維護"
ms.technology: powershell
ms.openlocfilehash: 8117d0d12c062b460cb7117b54c138c8db5a1d0c
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-TW
---
# <a name="multi-machine-deployment-and-maintenance"></a><span data-ttu-id="8b159-103">多電腦部署和維護</span><span class="sxs-lookup"><span data-stu-id="8b159-103">Multi-machine Deployment and Maintenance</span></span>
<span data-ttu-id="8b159-104">此時，您已多次將 JEA 部署到本機系統。</span><span class="sxs-lookup"><span data-stu-id="8b159-104">At this point, you have deployed JEA to local systems several times.</span></span>
<span data-ttu-id="8b159-105">因為您的生產環境可能是由多部電腦所組成，所以請務必逐步執行部署處理程序中必須在每部電腦上重複的重要步驟。</span><span class="sxs-lookup"><span data-stu-id="8b159-105">Because your production environment probably consists of more than one machine, it's important to walk through the critical steps in the deployment process that must be repeated on each machine.</span></span>

## <a name="high-level-steps"></a><span data-ttu-id="8b159-106">高階步驟︰</span><span class="sxs-lookup"><span data-stu-id="8b159-106">High Level Steps:</span></span>
1.  <span data-ttu-id="8b159-107">將您的模組 (及角色功能) 複製到每個節點。</span><span class="sxs-lookup"><span data-stu-id="8b159-107">Copy your modules (with Role Capabilities) to each node.</span></span>
2.  <span data-ttu-id="8b159-108">將您的工作階段設定檔複製到每個節點。</span><span class="sxs-lookup"><span data-stu-id="8b159-108">Copy your session configuration files to each node.</span></span>
3.  <span data-ttu-id="8b159-109">使用您的工作階段設定執行 `Register-PSSessionConfiguration`。</span><span class="sxs-lookup"><span data-stu-id="8b159-109">Run `Register-PSSessionConfiguration` with your session configuration.</span></span>
4.  <span data-ttu-id="8b159-110">將一份工作階段設定和工具組複本保留在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="8b159-110">Keep a copy of your session configuration and toolkits in a secure location.</span></span>
<span data-ttu-id="8b159-111">當您修改時，最好有一個「單一信任來源」。</span><span class="sxs-lookup"><span data-stu-id="8b159-111">As you make modifications, it's good to have a "single source of truth."</span></span>

## <a name="example-script"></a><span data-ttu-id="8b159-112">範例指令碼</span><span class="sxs-lookup"><span data-stu-id="8b159-112">Example Script</span></span>
<span data-ttu-id="8b159-113">以下是部署的範例指令碼。</span><span class="sxs-lookup"><span data-stu-id="8b159-113">Here's an example script for deployment.</span></span>
<span data-ttu-id="8b159-114">若要在您的環境中使用，您必須使用實際檔案共用和模組的名稱/路徑。</span><span class="sxs-lookup"><span data-stu-id="8b159-114">To use it in your environment, you'll have to use the names/paths of real file shares and modules.</span></span>
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
## <a name="modifying-capabilities"></a><span data-ttu-id="8b159-115">修改功能</span><span class="sxs-lookup"><span data-stu-id="8b159-115">Modifying Capabilities</span></span>
<span data-ttu-id="8b159-116">當處理多部電腦時，請務必以一致的方式公開修改。</span><span class="sxs-lookup"><span data-stu-id="8b159-116">When dealing with many machines, it's important that modifications are rolled out in a consistent manner.</span></span>
<span data-ttu-id="8b159-117">一旦 JEA 擁有 DSC 資源，這將有助於確保您的環境保持同步。</span><span class="sxs-lookup"><span data-stu-id="8b159-117">Once JEA has a DSC Resource, this will help ensure your environment is in sync.</span></span>
<span data-ttu-id="8b159-118">在這之前，強烈建議您保留工作階段設定的主要複本，並在每次修改時重新部署。</span><span class="sxs-lookup"><span data-stu-id="8b159-118">Until that time, we highly recommend you keep a master copy of your session configurations and re-deploy each time you make a modification.</span></span>

## <a name="removing-capabilities"></a><span data-ttu-id="8b159-119">移除功能</span><span class="sxs-lookup"><span data-stu-id="8b159-119">Removing Capabilities</span></span>
<span data-ttu-id="8b159-120">若要從您的系統中移除 JEA 設定，請在每部電腦上使用下列命令︰</span><span class="sxs-lookup"><span data-stu-id="8b159-120">To remove your JEA configuration from your systems, use the following command on each machine:</span></span>
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo
```

