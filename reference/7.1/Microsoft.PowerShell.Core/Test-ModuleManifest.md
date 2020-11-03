---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-modulemanifest?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ModuleManifest
ms.openlocfilehash: 36232f96f8d9e51b4151b971321b1b91a8a3fb00
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204767"
---
# <span data-ttu-id="661d5-103">Test-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="661d5-103">Test-ModuleManifest</span></span>

## <span data-ttu-id="661d5-104">概要</span><span class="sxs-lookup"><span data-stu-id="661d5-104">SYNOPSIS</span></span>
<span data-ttu-id="661d5-105">驗證模組資訊清單檔案可精確地說明模組的內容。</span><span class="sxs-lookup"><span data-stu-id="661d5-105">Verifies that a module manifest file accurately describes the contents of a module.</span></span>

## <span data-ttu-id="661d5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="661d5-106">SYNTAX</span></span>

```
Test-ModuleManifest [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="661d5-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="661d5-107">DESCRIPTION</span></span>

<span data-ttu-id="661d5-108">**Test-ModuleManifest** Cmdlet 會驗證模組資訊清單 (.psd1) 檔案中所列的檔案實際位於指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="661d5-108">The **Test-ModuleManifest** cmdlet verifies that the files that are listed in the module manifest (.psd1) file are actually in the specified paths.</span></span>

<span data-ttu-id="661d5-109">這個 Cmdlet 是設計來協助模組作者測試其資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="661d5-109">This cmdlet is designed to help module authors test their manifest files.</span></span>
<span data-ttu-id="661d5-110">模組使用者也可以在執行相依於模組的指令碼之前，於指令碼和命令中使用這個 Cmdlet 來偵測錯誤。</span><span class="sxs-lookup"><span data-stu-id="661d5-110">Module users can also use this cmdlet in scripts and commands to detect errors before they run scripts that depend on the module.</span></span>

<span data-ttu-id="661d5-111">**Test-ModuleManifest** 會傳回代表模組的物件。</span><span class="sxs-lookup"><span data-stu-id="661d5-111">**Test-ModuleManifest** returns an object that represents the module.</span></span>
<span data-ttu-id="661d5-112">這與 Get-Module 傳回的物件類型相同。</span><span class="sxs-lookup"><span data-stu-id="661d5-112">This is the same type of object that Get-Module returns.</span></span>
<span data-ttu-id="661d5-113">若有檔案不在資訊清單中指定的位置，此 Cmdlet 也會針對每個遺失的檔案產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="661d5-113">If any files are not in the locations specified in the manifest, the cmdlet also generates an error for each missing file.</span></span>

## <span data-ttu-id="661d5-114">範例</span><span class="sxs-lookup"><span data-stu-id="661d5-114">EXAMPLES</span></span>

### <span data-ttu-id="661d5-115">範例 1：測試資訊清單</span><span class="sxs-lookup"><span data-stu-id="661d5-115">Example 1: Test a manifest</span></span>

```powershell
test-ModuleManifest -Path "$pshome\Modules\TestModule.psd1"
```

<span data-ttu-id="661d5-116">此命令測試 TestModule.psd1 模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="661d5-116">This command tests the TestModule.psd1 module manifest.</span></span>

### <span data-ttu-id="661d5-117">範例 2︰使用管線測試資訊清單</span><span class="sxs-lookup"><span data-stu-id="661d5-117">Example 2: Test a manifest by using the pipeline</span></span>

```powershell
"$pshome\Modules\TestModule.psd1" | test-modulemanifest
```

```Output
Test-ModuleManifest : The specified type data file 'C:\Windows\System32\Wi
ndowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml' could not be processed because the file was not found. Please correct the path and try again.
At line:1 char:34
+ "$pshome\Modules\TestModule.psd1" | test-modulemanifest <<<<
+ CategoryInfo          : ResourceUnavailable: (C:\Windows\System32\WindowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml:String) [Test-ModuleManifest], FileNotFoundException
+ FullyQualifiedErrorId : Modules_TypeDataFileNotFound,Microsoft.PowerShell.Commands.TestModuleManifestCommandName

Name              : TestModule
Path              : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule\TestModule.psd1
Description       :
Guid              : 6f0f1387-cd25-4902-b7b4-22cff6aefa7b
Version           : 1.0
ModuleBase        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule
ModuleType        : Manifest
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {}
ExportedVariables : {}
NestedModules     : {}
```

<span data-ttu-id="661d5-118">此命令會使用管線運算子 (|) 將路徑字串傳送至 **ModuleManifest** 。</span><span class="sxs-lookup"><span data-stu-id="661d5-118">This command uses a pipeline operator (|) to send a path string to **Test-ModuleManifest** .</span></span>

<span data-ttu-id="661d5-119">命令輸出顯示測試失敗，因為找不到資訊清單中所列的 TestTypes.ps1xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="661d5-119">The command output shows that the test failed, because the TestTypes.ps1xml file, which was listed in the manifest, was not found.</span></span>

### <span data-ttu-id="661d5-120">範例 3：撰寫函式以測試模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="661d5-120">Example 3: Write a function to test a module manifest</span></span>

```powershell
function Test-ManifestBool ($path)
```

```Output
{$a = dir $path | Test-ModuleManifest -ErrorAction SilentlyContinue; $?}
```

<span data-ttu-id="661d5-121">此函式和 **Test-ModuleManifest** 相同，但它會傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="661d5-121">This function is like **Test-ModuleManifest** , but it returns a Boolean value.</span></span>
<span data-ttu-id="661d5-122">如果資訊清單通過測試，函式會傳回 $True，否則會傳回 $False。</span><span class="sxs-lookup"><span data-stu-id="661d5-122">The function returns $True if the manifest passed the test and $False otherwise.</span></span>

<span data-ttu-id="661d5-123">此函式使用 Get-ChildItem Cmdlet (別名 = dir)，來取得 $path 變數所指定的模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="661d5-123">The function uses the Get-ChildItem cmdlet, alias = dir, to get the module manifest specified by the $path variable.</span></span>
<span data-ttu-id="661d5-124">命令使用管線運算子 (|)，將檔案物件傳送至 **Test-ModuleManifest** 。</span><span class="sxs-lookup"><span data-stu-id="661d5-124">The command uses a pipeline operator (|) to pass the file object to **Test-ModuleManifest** .</span></span>

<span data-ttu-id="661d5-125">**Test-ModuleManifest** 命令使用 *ErrorAction* 一般參數搭配 SilentlyContinue 的值，來抑制顯示命令所產生的任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="661d5-125">**Test-ModuleManifest** uses the *ErrorAction* common parameter with a value of SilentlyContinue to suppress the display of any errors that the command generates.</span></span>
<span data-ttu-id="661d5-126">它也會將 **Test-ModuleManifest** 傳回的 **PSModuleInfo** 物件儲存於 $a 變數中。</span><span class="sxs-lookup"><span data-stu-id="661d5-126">It also saves the **PSModuleInfo** object that **Test-ModuleManifest** returns in the $a variable.</span></span>
<span data-ttu-id="661d5-127">因此該物件不會顯示。</span><span class="sxs-lookup"><span data-stu-id="661d5-127">Therefore, the object is not displayed.</span></span>

<span data-ttu-id="661d5-128">然後，在個別命令中，函式會顯示 $?</span><span class="sxs-lookup"><span data-stu-id="661d5-128">Then, in a separate command, the function displays the value of the $?</span></span>
<span data-ttu-id="661d5-129">自動變數的值。</span><span class="sxs-lookup"><span data-stu-id="661d5-129">automatic variable.</span></span>
<span data-ttu-id="661d5-130">如果前一個命令未產生任何錯誤，此命令會顯示 $True，否則為 $False。</span><span class="sxs-lookup"><span data-stu-id="661d5-130">If the previous command generates no error, the command displays $True, and $False otherwise.</span></span>

<span data-ttu-id="661d5-131">您可以在條件陳述式中使用這個函式，例如，可能在 **import-module** 命令之前的函式或使用模組的命令。</span><span class="sxs-lookup"><span data-stu-id="661d5-131">You can use this function in conditional statements, such as those that might precede an **Import-Module** command or a command that uses the module.</span></span>

## <span data-ttu-id="661d5-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="661d5-132">PARAMETERS</span></span>

### <span data-ttu-id="661d5-133">-Path</span><span class="sxs-lookup"><span data-stu-id="661d5-133">-Path</span></span>

<span data-ttu-id="661d5-134">指定資訊清單檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="661d5-134">Specifies a path and file name for the manifest file.</span></span>
<span data-ttu-id="661d5-135">輸入具有 .psd1 副檔名之模組資訊清單檔案的選擇性路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="661d5-135">Enter an optional path and name of the module manifest file that has the .psd1 file name extension.</span></span>
<span data-ttu-id="661d5-136">預設位置是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="661d5-136">The default location is the current directory.</span></span>
<span data-ttu-id="661d5-137">支援使用萬用字元，但必須解析為單一模組資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="661d5-137">Wildcard characters are supported, but must resolve to a single module manifest file.</span></span>
<span data-ttu-id="661d5-138">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="661d5-138">This parameter is required.</span></span>
<span data-ttu-id="661d5-139">您也可以使用管線將路徑傳送至 **測試 ModuleManifest** 。</span><span class="sxs-lookup"><span data-stu-id="661d5-139">You can also pipe a path to **Test-ModuleManifest** .</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="661d5-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="661d5-140">CommonParameters</span></span>

<span data-ttu-id="661d5-141">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="661d5-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="661d5-142">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="661d5-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="661d5-143">輸入</span><span class="sxs-lookup"><span data-stu-id="661d5-143">INPUTS</span></span>

### <span data-ttu-id="661d5-144">System.String</span><span class="sxs-lookup"><span data-stu-id="661d5-144">System.String</span></span>

<span data-ttu-id="661d5-145">您可以使用管線將模組資訊清單的路徑傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="661d5-145">You can pipe the path to a module manifest to this cmdlet.</span></span>

## <span data-ttu-id="661d5-146">輸出</span><span class="sxs-lookup"><span data-stu-id="661d5-146">OUTPUTS</span></span>

### <span data-ttu-id="661d5-147">System.Management.Automation.PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="661d5-147">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="661d5-148">此 Cmdlet 會傳回代表模組的 **PSModuleInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="661d5-148">This cmdlet returns a **PSModuleInfo** object that represents the module.</span></span>
<span data-ttu-id="661d5-149">即使資訊清單發生錯誤，它還是會傳回這個物件。</span><span class="sxs-lookup"><span data-stu-id="661d5-149">It returns this object even if the manifest has errors.</span></span>

## <span data-ttu-id="661d5-150">注意</span><span class="sxs-lookup"><span data-stu-id="661d5-150">NOTES</span></span>

## <span data-ttu-id="661d5-151">相關連結</span><span class="sxs-lookup"><span data-stu-id="661d5-151">RELATED LINKS</span></span>

[<span data-ttu-id="661d5-152">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="661d5-152">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="661d5-153">Get-Module</span><span class="sxs-lookup"><span data-stu-id="661d5-153">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="661d5-154">Import-Module</span><span class="sxs-lookup"><span data-stu-id="661d5-154">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="661d5-155">New-Module</span><span class="sxs-lookup"><span data-stu-id="661d5-155">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="661d5-156">New-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="661d5-156">New-ModuleManifest</span></span>](New-ModuleManifest.md)

[<span data-ttu-id="661d5-157">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="661d5-157">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="661d5-158">about_Modules</span><span class="sxs-lookup"><span data-stu-id="661d5-158">about_Modules</span></span>](About/about_Modules.md)

