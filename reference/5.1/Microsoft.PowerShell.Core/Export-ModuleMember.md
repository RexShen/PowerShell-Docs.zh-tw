---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-modulemember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ModuleMember
ms.openlocfilehash: a8f059a5f7ae36415054dd94f87a1224d64c2cbf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202319"
---
# <span data-ttu-id="94769-103">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="94769-103">Export-ModuleMember</span></span>

## <span data-ttu-id="94769-104">概要</span><span class="sxs-lookup"><span data-stu-id="94769-104">SYNOPSIS</span></span>
<span data-ttu-id="94769-105">指定要匯出的模組成員。</span><span class="sxs-lookup"><span data-stu-id="94769-105">Specifies the module members that are exported.</span></span>

## <span data-ttu-id="94769-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="94769-106">SYNTAX</span></span>

```
Export-ModuleMember [[-Function] <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="94769-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="94769-107">DESCRIPTION</span></span>

<span data-ttu-id="94769-108">**Export-modulemember 指令程式** 會指定從腳本模組匯出的模組成員 (. .psm1) 檔案，或從使用 New-Module Cmdlet 所建立的動態模組。</span><span class="sxs-lookup"><span data-stu-id="94769-108">The **Export-ModuleMember** cmdlet specifies the module members that are exported from a script module (.psm1) file, or from a dynamic module created by using the New-Module cmdlet.</span></span>
<span data-ttu-id="94769-109">模組成員包含 Cmdlet、函式、變數和別名。</span><span class="sxs-lookup"><span data-stu-id="94769-109">Module members include cmdlets, functions, variables, and aliases.</span></span>
<span data-ttu-id="94769-110">此 Cmdlet 只能用在指令碼模組檔案或動態模組中。</span><span class="sxs-lookup"><span data-stu-id="94769-110">This cmdlet can be used only in a script module file or a dynamic module.</span></span>

<span data-ttu-id="94769-111">如果腳本模組未包含 **export-modulemember** 命令，則會匯出腳本模組中的函式和別名，但變數不會。</span><span class="sxs-lookup"><span data-stu-id="94769-111">If a script module does not include an **Export-ModuleMember** command, the functions and aliases in the script module are exported, but the variables are not.</span></span>
<span data-ttu-id="94769-112">當腳本模組包含 **export-modulemember** 命令時，只會匯出 **匯出 export-modulemember** 命令中指定的成員。</span><span class="sxs-lookup"><span data-stu-id="94769-112">When a script module includes **Export-ModuleMember** commands, only the members specified in the **Export-ModuleMember** commands are exported.</span></span>
<span data-ttu-id="94769-113">您也可以使用 **export-modulemember** 來抑制或匯出腳本模組從其他模組匯入的成員。</span><span class="sxs-lookup"><span data-stu-id="94769-113">You can also use **Export-ModuleMember** to suppress or export members that the script module imports from other modules.</span></span>

<span data-ttu-id="94769-114">**Export-modulemember** 命令是選擇性的，但這是最佳作法。</span><span class="sxs-lookup"><span data-stu-id="94769-114">An **Export-ModuleMember** command is optional, but it is a best practice.</span></span>
<span data-ttu-id="94769-115">即使命令已確認預設值，它仍會示範模組作者的意圖。</span><span class="sxs-lookup"><span data-stu-id="94769-115">Even if the command confirms the default values, it demonstrates the intention of the module author.</span></span>

## <span data-ttu-id="94769-116">範例</span><span class="sxs-lookup"><span data-stu-id="94769-116">EXAMPLES</span></span>

### <span data-ttu-id="94769-117">範例1：匯出腳本模組中的函式和別名</span><span class="sxs-lookup"><span data-stu-id="94769-117">Example 1: Export functions and aliases in a script module</span></span>

```powershell
Export-ModuleMember -Function * -Alias *
```

<span data-ttu-id="94769-118">此命令會匯出腳本模組中定義的所有函式和別名。</span><span class="sxs-lookup"><span data-stu-id="94769-118">This command exports all the functions and aliases defined in the script module.</span></span>

### <span data-ttu-id="94769-119">範例2：匯出特定別名和函式</span><span class="sxs-lookup"><span data-stu-id="94769-119">Example 2: Export specific aliases and functions</span></span>

```powershell
Export-ModuleMember -Function Get-Test, New-Test, Start-Test -Alias gtt, ntt, stt
```

<span data-ttu-id="94769-120">此命令匯出指令碼模組中定義的三個別名與三個函式。</span><span class="sxs-lookup"><span data-stu-id="94769-120">This command exports three aliases and three functions defined in the script module.</span></span>

<span data-ttu-id="94769-121">您可以使用此命令格式來指定模組成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="94769-121">You can use this command format to specify the names of module members.</span></span>

### <span data-ttu-id="94769-122">範例3：不匯出成員</span><span class="sxs-lookup"><span data-stu-id="94769-122">Example 3: Export no members</span></span>

```powershell
Export-ModuleMember
```

<span data-ttu-id="94769-123">此命令指定不要匯出指令碼模組中定義的任何成員。</span><span class="sxs-lookup"><span data-stu-id="94769-123">This command specifies that no members defined in the script module are exported.</span></span>

<span data-ttu-id="94769-124">此命令可防止匯出模組成員，但是不會隱藏成員。</span><span class="sxs-lookup"><span data-stu-id="94769-124">This command prevents the module members from being exported, but it does not hide the members.</span></span>
<span data-ttu-id="94769-125">使用者可以讀取和複製模組成員，或使用呼叫運算子 (&) 來呼叫不會匯出的模組成員。</span><span class="sxs-lookup"><span data-stu-id="94769-125">Users can read and copy module members or use the call operator (&) to invoke module members that are not exported.</span></span>

### <span data-ttu-id="94769-126">範例4：匯出特定變數</span><span class="sxs-lookup"><span data-stu-id="94769-126">Example 4: Export a specific variable</span></span>

```powershell
Export-ModuleMember -Variable increment
```

<span data-ttu-id="94769-127">此命令只會從指令碼模組匯出 $increment 變數。</span><span class="sxs-lookup"><span data-stu-id="94769-127">This command exports only the $increment variable from the script module.</span></span>
<span data-ttu-id="94769-128">不會匯出其他成員。</span><span class="sxs-lookup"><span data-stu-id="94769-128">No other members are exported.</span></span>

<span data-ttu-id="94769-129">如果您想要匯出變數，除了匯出模組中的函式外，Export-modulemember 命令必須包含所有函 **式** 的名稱和變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="94769-129">If you want to export a variable, in addition to exporting the functions in a module, the **Export-ModuleMember** command must include the names of all of the functions and the name of the variable.</span></span>

### <span data-ttu-id="94769-130">範例5：多個匯出命令</span><span class="sxs-lookup"><span data-stu-id="94769-130">Example 5: Multiple export commands</span></span>

```powershell
# From TestModule.psm1
Function New-Test
{
    Write-Output 'I am New-Test function'
}
Export-ModuleMember -Function New-Test

function Validate-Test
{
    Write-Output 'I am Validate-Test function'
}
function Start-Test
{
    Write-Output 'I am Start-Test function'
}
Set-Alias stt Start-Test
Export-ModuleMember -Function Start-Test -Alias stt
```

<span data-ttu-id="94769-131">這些命令會示範如何在腳本模組中解讀多個 **匯出 export-modulemember** 命令， (. .psm1) 檔。</span><span class="sxs-lookup"><span data-stu-id="94769-131">These commands show how multiple **Export-ModuleMember** commands are interpreted in a script module (.psm1) file.</span></span>

<span data-ttu-id="94769-132">這些命令建立三個函式和一個別名，接著它們會匯出兩個函式和別名。</span><span class="sxs-lookup"><span data-stu-id="94769-132">These commands create three functions and one alias, and then they export two of the functions and the alias.</span></span>

<span data-ttu-id="94769-133">如果沒有 **export-modulemember** 命令，則會匯出三個函式和別名。</span><span class="sxs-lookup"><span data-stu-id="94769-133">Without the **Export-ModuleMember** commands, all three of the functions and the alias would be exported.</span></span>
<span data-ttu-id="94769-134">使用 **export-modulemember** 命令時，只會匯出 **新的測試** 和 **開始測試** 函數和 STT 別名。</span><span class="sxs-lookup"><span data-stu-id="94769-134">With the **Export-ModuleMember** commands, only the **New-Test** and **Start-Test** functions and the STT alias are exported.</span></span>

### <span data-ttu-id="94769-135">範例6：匯出動態模組中的成員</span><span class="sxs-lookup"><span data-stu-id="94769-135">Example 6: Export members in a dynamic module</span></span>

```powershell
New-Module -Script {function SayHello {"Hello!"}; Set-Alias Hi SayHello; Export-ModuleMember -Alias Hi -Function SayHello}
```

<span data-ttu-id="94769-136">此命令示範如何在使用 **New module** Cmdlet 建立的動態模組中使用 Export-ModuleMember。</span><span class="sxs-lookup"><span data-stu-id="94769-136">This command shows how to use Export-ModuleMember in a dynamic module that is created by using the **New-Module** cmdlet.</span></span>

<span data-ttu-id="94769-137">在此範例中，Export-modulemember 用來匯出動態模組中的 Hi 別名和 **SayHello** 函 **式** 。</span><span class="sxs-lookup"><span data-stu-id="94769-137">In this example, **Export-ModuleMember** is used to export both the Hi alias and the **SayHello** function in the dynamic module.</span></span>

### <span data-ttu-id="94769-138">範例7：在單一命令中宣告和匯出函數</span><span class="sxs-lookup"><span data-stu-id="94769-138">Example 7: Declare and export a function in a single command</span></span>

```powershell
# From TestModule.psm1
function Export
{
  param (
    [Parameter(Mandatory=$true)]
    [ValidateSet("function","variable")]
    $Type,
    [Parameter(Mandatory=$true)]
    $Name,
    [Parameter(Mandatory=$true)]
    $Value
    )

    if ($Type -eq "function")
    {
        Set-item "function:script:$Name" $Value
        Export-ModuleMember $Name
    }
    else
    {
    Set-Variable -scope Script $Name $Value
    Export-ModuleMember -variable $Name
    }
}

Export function New-Test {Write-Output 'I am New-Test function'}
function helper {Write-Output 'I am helper function'}

Export variable Interval 0
$Interval = 2
```

<span data-ttu-id="94769-139">此範例包含名為 **Export** 的函式，該函式會宣告函式或建立變數，然後寫入函式 `Export-ModuleMember` 或變數的命令。</span><span class="sxs-lookup"><span data-stu-id="94769-139">This example includes a function named **Export** that declares a function or creates a variable, and then writes an `Export-ModuleMember` command for the function or variable.</span></span>
<span data-ttu-id="94769-140">這可讓您宣告和匯出單一命令中的函式或變數。</span><span class="sxs-lookup"><span data-stu-id="94769-140">This lets you declare and export a function or variable in a single command.</span></span>

<span data-ttu-id="94769-141">若要使用 **Export** 函式，請將它包含在腳本模組中。</span><span class="sxs-lookup"><span data-stu-id="94769-141">To use the **Export** function, include it in your script module.</span></span>
<span data-ttu-id="94769-142">若要匯出函式，請在 `Export` **function** 關鍵字前面輸入。</span><span class="sxs-lookup"><span data-stu-id="94769-142">To export a function, type `Export` before the **Function** keyword.</span></span>

<span data-ttu-id="94769-143">如果要匯出變數，請使用下列格式來宣告變數並設定其值：</span><span class="sxs-lookup"><span data-stu-id="94769-143">To export a variable, use the following format to declare the variable and set its value:</span></span>

`Export variable <variable-name> <value>`

<span data-ttu-id="94769-144">此範例中的命令會顯示正確的格式。</span><span class="sxs-lookup"><span data-stu-id="94769-144">The commands in the example show the correct format.</span></span>
<span data-ttu-id="94769-145">在此範例中，只會匯出 **新的測試** 函數和 $Interval 變數。</span><span class="sxs-lookup"><span data-stu-id="94769-145">In this example, only the **New-Test** function and the $Interval variable are exported.</span></span>

## <span data-ttu-id="94769-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="94769-146">PARAMETERS</span></span>

### <span data-ttu-id="94769-147">-Alias</span><span class="sxs-lookup"><span data-stu-id="94769-147">-Alias</span></span>

<span data-ttu-id="94769-148">指定從指令碼模組檔案匯出的別名。</span><span class="sxs-lookup"><span data-stu-id="94769-148">Specifies the aliases that are exported from the script module file.</span></span>
<span data-ttu-id="94769-149">輸入別名名稱。</span><span class="sxs-lookup"><span data-stu-id="94769-149">Enter the alias names.</span></span>
<span data-ttu-id="94769-150">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="94769-150">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="94769-151">-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="94769-151">-Cmdlet</span></span>

<span data-ttu-id="94769-152">指定從指令碼模組檔案匯出的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="94769-152">Specifies the cmdlets that are exported from the script module file.</span></span>
<span data-ttu-id="94769-153">輸入 Cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="94769-153">Enter the cmdlet names.</span></span>
<span data-ttu-id="94769-154">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="94769-154">Wildcard characters are permitted.</span></span>

<span data-ttu-id="94769-155">您無法在指令碼模組檔案中建立 Cmdlet，但可將二進位模組中的 Cmdlet 匯入指令碼模組，然後從指令碼模組重新匯出它們。</span><span class="sxs-lookup"><span data-stu-id="94769-155">You cannot create cmdlets in a script module file, but you can import cmdlets from a binary module into a script module and re-export them from the script module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="94769-156">-Function</span><span class="sxs-lookup"><span data-stu-id="94769-156">-Function</span></span>

<span data-ttu-id="94769-157">指定從指令碼模組檔案匯出的函式。</span><span class="sxs-lookup"><span data-stu-id="94769-157">Specifies the functions that are exported from the script module file.</span></span>
<span data-ttu-id="94769-158">輸入函式名稱。</span><span class="sxs-lookup"><span data-stu-id="94769-158">Enter the function names.</span></span>
<span data-ttu-id="94769-159">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="94769-159">Wildcard characters are permitted.</span></span>
<span data-ttu-id="94769-160">您也可以透過管線將函式名稱字串傳送至 **export-modulemember** 。</span><span class="sxs-lookup"><span data-stu-id="94769-160">You can also pipe function name strings to **Export-ModuleMember** .</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="94769-161">-Variable</span><span class="sxs-lookup"><span data-stu-id="94769-161">-Variable</span></span>

<span data-ttu-id="94769-162">指定從指令碼模組檔案匯出的變數。</span><span class="sxs-lookup"><span data-stu-id="94769-162">Specifies the variables that are exported from the script module file.</span></span>
<span data-ttu-id="94769-163">輸入不含貨幣符號的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="94769-163">Enter the variable names, without a dollar sign.</span></span>
<span data-ttu-id="94769-164">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="94769-164">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="94769-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="94769-165">CommonParameters</span></span>

<span data-ttu-id="94769-166">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="94769-166">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="94769-167">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="94769-167">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="94769-168">輸入</span><span class="sxs-lookup"><span data-stu-id="94769-168">INPUTS</span></span>

### <span data-ttu-id="94769-169">System.String</span><span class="sxs-lookup"><span data-stu-id="94769-169">System.String</span></span>

<span data-ttu-id="94769-170">您可以透過管道將函式名稱字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="94769-170">You can pipe function name strings to this cmdlet.</span></span>

## <span data-ttu-id="94769-171">輸出</span><span class="sxs-lookup"><span data-stu-id="94769-171">OUTPUTS</span></span>

### <span data-ttu-id="94769-172">無</span><span class="sxs-lookup"><span data-stu-id="94769-172">None</span></span>

<span data-ttu-id="94769-173">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="94769-173">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="94769-174">注意</span><span class="sxs-lookup"><span data-stu-id="94769-174">NOTES</span></span>

* <span data-ttu-id="94769-175">若要從匯出的成員清單中排除成員，請新增 **export-modulemember** 命令來列出所有其他成員，但省略您要排除的成員。</span><span class="sxs-lookup"><span data-stu-id="94769-175">To exclude a member from the list of exported members, add an **Export-ModuleMember** command that lists all other members but omits the member that you want to exclude.</span></span>

## <span data-ttu-id="94769-176">相關連結</span><span class="sxs-lookup"><span data-stu-id="94769-176">RELATED LINKS</span></span>

[<span data-ttu-id="94769-177">Get-Module</span><span class="sxs-lookup"><span data-stu-id="94769-177">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="94769-178">Import-Module</span><span class="sxs-lookup"><span data-stu-id="94769-178">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="94769-179">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="94769-179">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="94769-180">about_Modules</span><span class="sxs-lookup"><span data-stu-id="94769-180">about_Modules</span></span>](About/about_Modules.md)
