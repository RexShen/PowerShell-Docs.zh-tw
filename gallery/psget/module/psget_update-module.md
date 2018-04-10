---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: 資源庫,powershell,cmdlet,psget
title: Update-Module
ms.openlocfilehash: 89b0111eda4421606843f108dca90519b2c9379e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="update-module"></a><span data-ttu-id="a825f-103">Update-Module</span><span class="sxs-lookup"><span data-stu-id="a825f-103">Update-Module</span></span>

<span data-ttu-id="a825f-104">將來自線上組件庫之指定模組的最新版本下載並安裝至本機電腦。</span><span class="sxs-lookup"><span data-stu-id="a825f-104">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <a name="description"></a><span data-ttu-id="a825f-105">描述</span><span class="sxs-lookup"><span data-stu-id="a825f-105">Description</span></span>

<span data-ttu-id="a825f-106">Update-Module Cmdlet 會在本機電腦上執行 Install-Module，以安裝已從線上組件庫安裝的較新 Windows PowerShell 模組版本。</span><span class="sxs-lookup"><span data-stu-id="a825f-106">The Update-Module cmdlet installs a newer version of a Windows PowerShell module that was installed from the online gallery by running Install-Module on the local computer.</span></span>

<span data-ttu-id="a825f-107">除非您指定所需的版本，否則預設會安裝線上組件庫中可用指定模組的最新版本。</span><span class="sxs-lookup"><span data-stu-id="a825f-107">By default, the newest version of the specified module available in online gallery is installed, unless you specify a required version.</span></span> <span data-ttu-id="a825f-108">您可以指定模組名稱來更新現有的已安裝模組；Update-Module 會搜尋 $env:PSModulePath 中是否有您要更新的模組。</span><span class="sxs-lookup"><span data-stu-id="a825f-108">You can update an existing, installed module by specifying the name of the module; Update-Module searches $env:PSModulePath for the module that you want to update.</span></span>

<span data-ttu-id="a825f-109">執行不含 Name 參數的 Update-Module 會更新可在本機電腦上更新的所有模組。</span><span class="sxs-lookup"><span data-stu-id="a825f-109">Running Update-Module without the Name parameter updates all modules that can be updated on the local computer.</span></span>

### <a name="notes"></a><span data-ttu-id="a825f-110">注意</span><span class="sxs-lookup"><span data-stu-id="a825f-110">Notes</span></span>

- <span data-ttu-id="a825f-111">這個 Cmdlet 會在 Windows PowerShell 3.0 或更新版本的 Windows PowerShell、Windows 7 或 Windows 2008 R2 和更新版本的 Windows 上執行。</span><span class="sxs-lookup"><span data-stu-id="a825f-111">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>
- <span data-ttu-id="a825f-112">如果未使用 Install-Module 來安裝利用 Name 參數所指定的模組，則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="a825f-112">If the module that you specify with the Name parameter was not installed by using Install-Module, an error occurs.</span></span> <span data-ttu-id="a825f-113">您只能在執行 Install-Module 以從線上組件庫所安裝的模組上執行 Update-Module。</span><span class="sxs-lookup"><span data-stu-id="a825f-113">You can only run Update-Module on modules that you installed from the online gallery by running Install-Module.</span></span>
- <span data-ttu-id="a825f-114">如果 Update-Module 嘗試更新使用中的二進位檔，Update-Module 會傳回錯誤以識別問題程序，以及通知使用者在停止程序之後重試 Update-Module。</span><span class="sxs-lookup"><span data-stu-id="a825f-114">If Update-Module attempts to update binaries that are in use, Update-Module returns an error that identifies the problem processes, and informs the user to retry Update-Module after stopping the processes.</span></span>
- <span data-ttu-id="a825f-115">在 PowerShell 5.0 或更新版本上，當 Update-Module 更新模組時，會新增最新 (或指定) 版本的模組，因此新舊版本現在會並存在相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="a825f-115">On PowerShell 5.0 or newer versions, when Update-Module updates a module, it adds the latest (or specified) version of the module, so the older and newer versions are now side-by-side in the same directory.</span></span> <span data-ttu-id="a825f-116">這十分有用，而且可用來顯示這些命令的輸出範例。</span><span class="sxs-lookup"><span data-stu-id="a825f-116">It would be useful to say so and to show an example of the output from these commands.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="a825f-117">Cmdlet 語法</span><span class="sxs-lookup"><span data-stu-id="a825f-117">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="a825f-118">Cmdlet 線上說明參考資料</span><span class="sxs-lookup"><span data-stu-id="a825f-118">Cmdlet online help reference</span></span>

[<span data-ttu-id="a825f-119">Update-Module</span><span class="sxs-lookup"><span data-stu-id="a825f-119">Update-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398576)


## <a name="example-commands"></a><span data-ttu-id="a825f-120">範例命令</span><span class="sxs-lookup"><span data-stu-id="a825f-120">Example commands</span></span>

```powershell
PS C:\windows\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\windows\system32> Update-Module -Name ContosoServer
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```

### <a name="update-the-module-with-a-prerelease-version-requires--allowprerelease-flag"></a><span data-ttu-id="a825f-121">以發行前版本更新模組，需要 -AllowPrerelease 旗標</span><span class="sxs-lookup"><span data-stu-id="a825f-121">Update the module with a prerelease version, requires -AllowPrerelease flag</span></span>
```powershell
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module

PS C:\windows\system32> Find-Module ContosoServer -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
3.0.0-alpha    ConstosoServer                      MSPSGallery          The PowerShell Contoso Server deployment tools...

PS C:\windows\system32> Update-Module -Name ContosoServer -AllowPrerelease
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
3.0.0-alpha ContosoServer MSPSGallery ContosoServer module

```


### <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a><span data-ttu-id="a825f-122">更新具相依性的 TestDepWithNestedRequiredModules1 模組。</span><span class="sxs-lookup"><span data-stu-id="a825f-122">Update the TestDepWithNestedRequiredModules1 module with dependencies.</span></span>
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module



```