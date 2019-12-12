---
title: 修改 PSModulePath 安裝路徑 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 5957ea4c15cd3778bd09b67c4b97de0ef0cfdd2a
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953835"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="3b742-102">修改 PSModulePath 安裝路徑</span><span class="sxs-lookup"><span data-stu-id="3b742-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="3b742-103">`PSModulePath` 環境變數會儲存安裝在磁片上之模組位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="3b742-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="3b742-104">當使用者未指定模組的完整路徑時，PowerShell 會使用此變數來尋找模組。</span><span class="sxs-lookup"><span data-stu-id="3b742-104">PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="3b742-105">此變數中的路徑會依照其出現的順序進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="3b742-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="3b742-106">當 PowerShell 啟動時，`PSModulePath` 會建立為具有下列預設值的系統內容變數： `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` 或 `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` 適用于 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3b742-106">When PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` or `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` for Windows PowerShell.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="3b742-107">若要查看 PSModulePath 變數</span><span class="sxs-lookup"><span data-stu-id="3b742-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="3b742-108">若要查看在 `PSModulePath` 變數中指定的路徑，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="3b742-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="3b742-109">若要將位置新增至 PSModulePath 變數</span><span class="sxs-lookup"><span data-stu-id="3b742-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="3b742-110">若要將路徑新增至此變數，請使用下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="3b742-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="3b742-111">若要新增僅適用于目前會話的暫時值，請在命令列中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="3b742-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- <span data-ttu-id="3b742-112">若要新增每次開啟會話時可用的持續性值，請將上述命令新增至 PowerShell 設定檔檔案（`$PROFILE`） ></span><span class="sxs-lookup"><span data-stu-id="3b742-112">To add a persistent value that is available whenever a session is opened, add the above command to a PowerShell profile file (`$PROFILE`)></span></span>

  <span data-ttu-id="3b742-113">如需設定檔的詳細資訊，請參閱 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)。</span><span class="sxs-lookup"><span data-stu-id="3b742-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

- <span data-ttu-id="3b742-114">若要將持續變數新增至登錄，請使用 [**系統屬性**] 對話方塊中的 [環境變數編輯器]，建立稱為 `PSModulePath` 的新使用者環境變數。</span><span class="sxs-lookup"><span data-stu-id="3b742-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="3b742-115">若要使用腳本來加入持續性變數，請使用[SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable)在[system.web](https://docs.microsoft.com/dotnet/api/system.environment)類別上的 .net 方法。</span><span class="sxs-lookup"><span data-stu-id="3b742-115">To add a persistent variable by using a script, use the .Net method [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) on the [System.Environment](https://docs.microsoft.com/dotnet/api/system.environment) class.</span></span> <span data-ttu-id="3b742-116">例如，下列腳本會將 `C:\Program Files\Fabrikam\Module` 路徑新增至電腦的 `PSModulePath` 環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="3b742-116">For example, the following script adds the `C:\Program Files\Fabrikam\Module` path to the value of the `PSModulePath` environment variable for the computer.</span></span> <span data-ttu-id="3b742-117">若要將路徑新增至使用者 `PSModulePath` 環境變數，請將目標設定為 "User"。</span><span class="sxs-lookup"><span data-stu-id="3b742-117">To add the path to the user `PSModulePath` environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="3b742-118">若要從 PSModulePath 中移除位置</span><span class="sxs-lookup"><span data-stu-id="3b742-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="3b742-119">您可以使用類似的方法來移除變數中的路徑：例如，`$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` 會從目前的會話移除**c:\ModulePath**路徑。</span><span class="sxs-lookup"><span data-stu-id="3b742-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b742-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b742-120">See Also</span></span>

[<span data-ttu-id="3b742-121">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="3b742-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
