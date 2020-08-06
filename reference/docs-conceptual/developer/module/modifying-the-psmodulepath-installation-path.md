---
title: 修改 PSModulePath 安裝路徑 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 795f2bd52aeceddd3c0ca092d0c0cf2ef44bcf23
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784838"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="88537-102">修改 PSModulePath 安裝路徑</span><span class="sxs-lookup"><span data-stu-id="88537-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="88537-103">`PSModulePath`環境變數會儲存安裝在磁片上之模組位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="88537-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="88537-104">當使用者未指定模組的完整路徑時，PowerShell 會使用此變數來尋找模組。</span><span class="sxs-lookup"><span data-stu-id="88537-104">PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="88537-105">此變數中的路徑會依照其出現的順序進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="88537-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="88537-106">當 PowerShell 啟動時， `PSModulePath` 會建立為具有下列預設值的系統內容變數： `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` 在 Windows 和 `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` Linux 或 Mac 上，以及 `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="88537-106">When PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` on Windows and `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` on Linux or Mac, and `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` for Windows PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="88537-107">使用者專屬的**CurrentUser**位置是 `WindowsPowerShell\Modules` 位於使用者設定檔中 [**檔**] 位置的資料夾。</span><span class="sxs-lookup"><span data-stu-id="88537-107">The user-specific **CurrentUser** location is the `WindowsPowerShell\Modules` folder located in the **Documents** location in your user profile.</span></span> <span data-ttu-id="88537-108">該位置的特定路徑會因 Windows 版本，以及您是否使用資料夾重新導向而有所不同。</span><span class="sxs-lookup"><span data-stu-id="88537-108">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="88537-109">根據預設，在 Windows 10 上，該位置是 `$HOME\Documents\WindowsPowerShell\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="88537-109">By default, on Windows 10, that location is `$HOME\Documents\WindowsPowerShell\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="88537-110">若要查看 PSModulePath 變數</span><span class="sxs-lookup"><span data-stu-id="88537-110">To view the PSModulePath variable</span></span>

<span data-ttu-id="88537-111">若要查看變數中指定的路徑 `PSModulePath` ，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="88537-111">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="88537-112">若要將位置新增至 PSModulePath 變數</span><span class="sxs-lookup"><span data-stu-id="88537-112">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="88537-113">若要將路徑新增至此變數，請使用下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="88537-113">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="88537-114">若要新增僅適用于目前會話的暫時值，請在命令列中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="88537-114">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- <span data-ttu-id="88537-115">若要新增每當會話開啟時可用的持續性值，請將上述命令新增至 PowerShell 設定檔檔案 (`$PROFILE`) # A0</span><span class="sxs-lookup"><span data-stu-id="88537-115">To add a persistent value that is available whenever a session is opened, add the above command to a PowerShell profile file (`$PROFILE`)></span></span>

  <span data-ttu-id="88537-116">如需設定檔的詳細資訊，請參閱 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)。</span><span class="sxs-lookup"><span data-stu-id="88537-116">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

- <span data-ttu-id="88537-117">若要將持續變數新增至登錄，請 `PSModulePath` 使用 [**系統屬性**] 對話方塊中的 [環境變數編輯器]，建立名為的新使用者環境變數。</span><span class="sxs-lookup"><span data-stu-id="88537-117">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="88537-118">若要使用腳本來加入持續性變數，請使用[SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable)在[system.web](/dotnet/api/system.environment)類別上的 .net 方法。</span><span class="sxs-lookup"><span data-stu-id="88537-118">To add a persistent variable by using a script, use the .Net method [SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable) on the [System.Environment](/dotnet/api/system.environment) class.</span></span> <span data-ttu-id="88537-119">例如，下列腳本會將電腦的 `C:\Program Files\Fabrikam\Module` 環境變數值的路徑新增至 `PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="88537-119">For example, the following script adds the `C:\Program Files\Fabrikam\Module` path to the value of the `PSModulePath` environment variable for the computer.</span></span> <span data-ttu-id="88537-120">若要將路徑新增至使用者 `PSModulePath` 環境變數，請將目標設為 "user"。</span><span class="sxs-lookup"><span data-stu-id="88537-120">To add the path to the user `PSModulePath` environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="88537-121">若要從 PSModulePath 中移除位置</span><span class="sxs-lookup"><span data-stu-id="88537-121">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="88537-122">您可以使用類似的方法來移除變數中的路徑：例如， `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` 會從目前的會話移除**c:\ModulePath**路徑。</span><span class="sxs-lookup"><span data-stu-id="88537-122">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="88537-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88537-123">See Also</span></span>

[<span data-ttu-id="88537-124">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="88537-124">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="88537-125">about_Modules</span><span class="sxs-lookup"><span data-stu-id="88537-125">about_Modules</span></span>](/powershell/module/microsoft.powershell.core/about/about_modules)
