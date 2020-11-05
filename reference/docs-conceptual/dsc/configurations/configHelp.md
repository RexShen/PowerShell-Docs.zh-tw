---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 撰寫 DSC 設定的說明
description: 您可以在 DSC 設定中，以註解方式呈現說明。 使用者可以搭配 `-?` 參數呼叫設定，或是使用 Get-Help Cmdlet 來存取說明。
ms.openlocfilehash: 01c4f43253f4d4d8421ea3e0dfca797776acd426
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658624"
---
# <a name="writing-help-for-dsc-configurations"></a><span data-ttu-id="a59fe-105">撰寫 DSC 設定的說明</span><span class="sxs-lookup"><span data-stu-id="a59fe-105">Writing help for DSC configurations</span></span>

> <span data-ttu-id="a59fe-106">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a59fe-106">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="a59fe-107">您可以在 DSC 設定中，以註解方式呈現說明。</span><span class="sxs-lookup"><span data-stu-id="a59fe-107">You can use comment-based help in DSC configurations.</span></span> <span data-ttu-id="a59fe-108">使用者可以呼叫 **設定** 加上 `-?`，或使用 [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet 存取說明。</span><span class="sxs-lookup"><span data-stu-id="a59fe-108">Users can access the help by calling the **Configuration** with `-?`, or by using the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.</span></span> <span data-ttu-id="a59fe-109">將註解型說明直接放在 `Configuration` 關鍵字上方。</span><span class="sxs-lookup"><span data-stu-id="a59fe-109">Place your Comment-based help directly above the `Configuration` keyword.</span></span> <span data-ttu-id="a59fe-110">您可以將參數說明與註解區塊一起放在參數宣告的正上方，或者兩者都放置，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="a59fe-110">You can place parameter help in-line with your comment block, directly above the parameter declaration, or both as in the example below.</span></span>

<span data-ttu-id="a59fe-111">如需如何在 PowerShell 中，以註解方式呈現說明的詳細資訊，請參閱 [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。</span><span class="sxs-lookup"><span data-stu-id="a59fe-111">For more information about PowerShell comment-based help, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

> [!NOTE]
> <span data-ttu-id="a59fe-112">PowerShell 開發環境 (例如 VS Code 與 ISE) 也具有可讓您自動插入註解區塊範本的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="a59fe-112">PowerShell development environments, like VS Code and the ISE, also have snippets to allow you to automatically insert comment block templates.</span></span>

<span data-ttu-id="a59fe-113">下列範例顯示了包含設定及其註解式說明的指令碼。</span><span class="sxs-lookup"><span data-stu-id="a59fe-113">The following example shows a script that contains a configuration and comment-based help for it.</span></span>
<span data-ttu-id="a59fe-114">此範例顯示具有參數的設定。</span><span class="sxs-lookup"><span data-stu-id="a59fe-114">This example shows a Configuration with parameters.</span></span> <span data-ttu-id="a59fe-115">若要深入了解在設定中使用參數的詳細資訊，請參閱[將參數加入至您的設定](add-parameters-to-a-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="a59fe-115">To learn more about using parameters in your Configurations, see [Add Parameters to your Configurations](add-parameters-to-a-configuration.md).</span></span>

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each
configuration.

.PARAMETER ComputerName
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or
script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description
on the lines following the .PARAMETER keyword. Windows PowerShell interprets all text between the
.PARAMETER line and the next keyword or the end of the comment block as part of the parameter
description. The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script
syntax determines the order in which the parameters (and their descriptions) appear in help topic.
To change the order, change the syntax.

.EXAMPLE
HelpSample -ComputerName localhost

A sample command that uses the function or script, optionally followed by sample output and a
description. Repeat this keyword for each example. PowerShell automatically prefaces the first line
with a PowerShell prompt. Additional lines are treated as output and description. The example can
contain spaces, newlines and PowerShell code.

If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.

.EXAMPLE
HelpSample -FilePath "C:\output.txt"

This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>
configuration HelpSample1
{
    param
    (
        [string]$ComputerName = 'localhost',
        # Provide a PARAMETER section for each parameter that your script or function accepts.
        [string]$FilePath = 'C:\Destination.txt'
    )

    Node $ComputerName
    {
        File HelloWorld
        {
            Contents="Hello World"
            DestinationPath = $FilePath
        }
    }
}
```

## <a name="viewing-configuration-help"></a><span data-ttu-id="a59fe-116">檢視設定說明</span><span class="sxs-lookup"><span data-stu-id="a59fe-116">Viewing configuration help</span></span>

<span data-ttu-id="a59fe-117">若要檢視設定的說明，請使用 `Get-Help` Cmdlet 加上函式名稱，或輸入函式名稱加上 `-?`。</span><span class="sxs-lookup"><span data-stu-id="a59fe-117">To view the help for a configuration, use the `Get-Help` cmdlet with the name of the function, or type the name of the function followed by `-?`.</span></span> <span data-ttu-id="a59fe-118">下列是將前一個設定傳遞給 `Get-Help` 後的輸出。</span><span class="sxs-lookup"><span data-stu-id="a59fe-118">The following is the output of the previous Configuration passed to `Get-Help`.</span></span>

```powershell
Get-Help HelpSample1 -Detailed
```

```Output
NAME
    HelpSample1

SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.


SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-PsDscRunAsCredential] <PSCredential>]
      [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName] <String>] [[-FilePath] <String>]
      [<CommonParameters>]


DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.


PARAMETERS
    -InstanceName <String>

    -DependsOn <String[]>

    -PsDscRunAsCredential <PSCredential>

    -OutputPath <String>

    -ConfigurationData <Hashtable>

    -ComputerName <String>
        The description of a parameter. Add a .PARAMETER keyword for each parameter in the function
        or script syntax.

        Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter
        description on the lines following the .PARAMETER keyword. Windows PowerShell interprets all
        text between the .PARAMETER line and the next keyword or the end of the comment block as
        part of the parameter description. The description can include paragraph breaks.

        The Parameter keywords can appear in any order in the comment block, but the function or
        script syntax determines the order in which the parameters (and their descriptions) appear
        in help topic. To change the order, change the syntax.

    -FilePath <String>
        Provide a PARAMETER section for each parameter that your script or function accepts.

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (https:/go.microsoft.com/fwlink/?LinkID=113216).

    -------------------------- EXAMPLE 1 --------------------------

    PS C:\>HelpSample -ComputerName localhost

    A sample command that uses the function or script, optionally followed by sample output and a
    description. Repeat this keyword for each example. PowerShell automatically prefaces the first
    line with a PowerShell prompt. Additional lines are treated as output and description. The
    example can contain spaces, newlines and PowerShell code.

    If you have multiple examples, there is no need to number them. PowerShell will number the
    examples in help text.


    -------------------------- EXAMPLE 2 --------------------------

    PS C:\>HelpSample -FilePath "C:\output.txt"

    This example will be labeled "EXAMPLE 2" when help is displayed to the user.


REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

> [!NOTE]
> <span data-ttu-id="a59fe-119">PowerShell 會自動為您產生語法欄位和參數屬性。</span><span class="sxs-lookup"><span data-stu-id="a59fe-119">Syntax fields and parameter attributes are automatically generated for you by PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="a59fe-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a59fe-120">See Also</span></span>

- [<span data-ttu-id="a59fe-121">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="a59fe-121">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="a59fe-122">撰寫、編譯及套用設定</span><span class="sxs-lookup"><span data-stu-id="a59fe-122">Write, Compile, and Apply a Configuration</span></span>](write-compile-apply-configuration.md)
- [<span data-ttu-id="a59fe-123">將參數新增至設定</span><span class="sxs-lookup"><span data-stu-id="a59fe-123">Add Parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
