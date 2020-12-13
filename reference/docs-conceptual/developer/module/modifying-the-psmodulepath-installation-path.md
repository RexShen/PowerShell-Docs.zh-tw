---
ms.date: 09/13/2016
ms.topic: reference
title: 修改 PSModulePath 安裝路徑
description: 修改 PSModulePath 安裝路徑
ms.openlocfilehash: b802492bf9b49e8165e296817e3f80b9ae8265a6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92661942"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="5d464-103">修改 PSModulePath 安裝路徑</span><span class="sxs-lookup"><span data-stu-id="5d464-103">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="5d464-104">`PSModulePath`環境變數會儲存安裝在磁片上的模組位置路徑。</span><span class="sxs-lookup"><span data-stu-id="5d464-104">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="5d464-105">當使用者未指定模組的完整路徑時，PowerShell 會使用此變數來尋找模組。</span><span class="sxs-lookup"><span data-stu-id="5d464-105">PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="5d464-106">此變數中的路徑會依照其出現的順序來搜尋。</span><span class="sxs-lookup"><span data-stu-id="5d464-106">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="5d464-107">當 PowerShell 啟動時， `PSModulePath` 會建立為具有下列預設值的系統內容變數： `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` 在 Windows、 `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` Linux 或 Mac 上，以及 `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` 用於 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="5d464-107">When PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` on Windows and `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` on Linux or Mac, and `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` for Windows PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="5d464-108">使用者專屬的 **CurrentUser** 位置是 `WindowsPowerShell\Modules` 位於您使用者設定檔中檔位置的資料夾。</span><span class="sxs-lookup"><span data-stu-id="5d464-108">The user-specific **CurrentUser** location is the `WindowsPowerShell\Modules` folder located in the **Documents** location in your user profile.</span></span> <span data-ttu-id="5d464-109">該位置的特定路徑會因 Windows 版本而異，以及您是否正在使用資料夾重新導向。</span><span class="sxs-lookup"><span data-stu-id="5d464-109">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="5d464-110">根據預設，在 Windows 10 上，該位置為 `$HOME\Documents\WindowsPowerShell\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="5d464-110">By default, on Windows 10, that location is `$HOME\Documents\WindowsPowerShell\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="5d464-111">若要查看 PSModulePath 變數</span><span class="sxs-lookup"><span data-stu-id="5d464-111">To view the PSModulePath variable</span></span>

<span data-ttu-id="5d464-112">若要查看變數中指定的路徑 `PSModulePath` ，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="5d464-112">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="5d464-113">若要將位置新增至 PSModulePath 變數</span><span class="sxs-lookup"><span data-stu-id="5d464-113">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="5d464-114">若要將路徑新增至此變數，請使用下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="5d464-114">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="5d464-115">若要新增僅適用于目前會話的暫時值，請在命令列執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="5d464-115">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- <span data-ttu-id="5d464-116">若要新增會話開啟時可用的持續值，請將上述命令新增至 PowerShell 設定檔檔 (`$PROFILE`) # A0</span><span class="sxs-lookup"><span data-stu-id="5d464-116">To add a persistent value that is available whenever a session is opened, add the above command to a PowerShell profile file (`$PROFILE`)></span></span>

  <span data-ttu-id="5d464-117">如需設定檔的詳細資訊，請參閱 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)。</span><span class="sxs-lookup"><span data-stu-id="5d464-117">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

- <span data-ttu-id="5d464-118">若要將持續性變數新增至登錄，請 `PSModulePath` 使用 [ **系統屬性** ] 對話方塊中的環境變數編輯器，建立名為的新使用者環境變數。</span><span class="sxs-lookup"><span data-stu-id="5d464-118">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="5d464-119">若要使用腳本新增持續性變數，請在[system.object](/dotnet/api/system.environment)類別上使用 .Net 方法[SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable) 。</span><span class="sxs-lookup"><span data-stu-id="5d464-119">To add a persistent variable by using a script, use the .Net method [SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable) on the [System.Environment](/dotnet/api/system.environment) class.</span></span> <span data-ttu-id="5d464-120">例如，下列腳本會將路徑新增 `C:\Program Files\Fabrikam\Module` 至 `PSModulePath` 電腦的環境變數值。</span><span class="sxs-lookup"><span data-stu-id="5d464-120">For example, the following script adds the `C:\Program Files\Fabrikam\Module` path to the value of the `PSModulePath` environment variable for the computer.</span></span> <span data-ttu-id="5d464-121">若要將路徑新增至使用者 `PSModulePath` 環境變數，請將目標設定為 "user"。</span><span class="sxs-lookup"><span data-stu-id="5d464-121">To add the path to the user `PSModulePath` environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="5d464-122">從 PSModulePath 中移除位置</span><span class="sxs-lookup"><span data-stu-id="5d464-122">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="5d464-123">您可以使用類似的方法，從變數移除路徑：例如， `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` 將會從目前的會話移除 **c:\ModulePath** 路徑。</span><span class="sxs-lookup"><span data-stu-id="5d464-123">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d464-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d464-124">See Also</span></span>

[<span data-ttu-id="5d464-125">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="5d464-125">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="5d464-126">about_Modules</span><span class="sxs-lookup"><span data-stu-id="5d464-126">about_Modules</span></span>](/powershell/module/microsoft.powershell.core/about/about_modules)
