---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 撰寫 DSC 設定的說明
ms.openlocfilehash: 498ec0f594ed3229e097903c4ea2ae34d3da03a2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400827"
---
# <a name="writing-help-for-dsc-configurations"></a><span data-ttu-id="eecbd-103">撰寫 DSC 設定的說明</span><span class="sxs-lookup"><span data-stu-id="eecbd-103">Writing help for DSC configurations</span></span>

><span data-ttu-id="eecbd-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="eecbd-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="eecbd-105">您可以在 DSC 設定中，以註解方式呈現說明。</span><span class="sxs-lookup"><span data-stu-id="eecbd-105">You can use comment-based help in DSC configurations.</span></span> <span data-ttu-id="eecbd-106">使用者可以存取說明，藉由呼叫**組態**具有`-?`，或使用[Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eecbd-106">Users can access the help by calling the **Configuration** with `-?`, or by using the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.</span></span> <span data-ttu-id="eecbd-107">放置您上方的註解型說明`Configuration`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="eecbd-107">Place your Comment-based help directly above the `Configuration` keyword.</span></span>
<span data-ttu-id="eecbd-108">您可以將參數說明內建與您的註解區塊，正上方參數宣告，或兩者如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="eecbd-108">You can place parameter help in-line with your comment block, directly above the parameter declaration, or both as in the example below.</span></span>

<span data-ttu-id="eecbd-109">如需如何在 PowerShell 中，以註解方式呈現說明的詳細資訊，請參閱 [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。</span><span class="sxs-lookup"><span data-stu-id="eecbd-109">For more information about PowerShell comment-based help, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

> [!NOTE]
> <span data-ttu-id="eecbd-110">PowerShell 開發環境，例如 VSCode 與 ISE 中，也會有程式碼片段可讓您自動插入註解區塊的範本。</span><span class="sxs-lookup"><span data-stu-id="eecbd-110">PowerShell development environments, like VSCode and the ISE, also have snippets to allow you to automatically insert comment block templates.</span></span>

<span data-ttu-id="eecbd-111">下列範例顯示了包含設定及其註解式說明的指令碼。</span><span class="sxs-lookup"><span data-stu-id="eecbd-111">The following example shows a script that contains a configuration and comment-based help for it.</span></span> <span data-ttu-id="eecbd-112">這個範例示範具有參數的組態。</span><span class="sxs-lookup"><span data-stu-id="eecbd-112">This example shows a Configuration with parameters.</span></span> <span data-ttu-id="eecbd-113">若要深入了解在您的組態中使用參數，請參閱[將參數加入至您的組態](add-parameters-to-a-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="eecbd-113">To learn more about using parameters in your Configurations, see [Add Parameters to your Configurations](add-parameters-to-a-configuration.md).</span></span>

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each configuration.


.PARAMETER ComputerName
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
(and their descriptions) appear in help topic. To change the order, change the syntax.

.EXAMPLE
HelpSample -ComputerName localhost

A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

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

## <a name="viewing-configuration-help"></a><span data-ttu-id="eecbd-114">檢視設定說明</span><span class="sxs-lookup"><span data-stu-id="eecbd-114">Viewing configuration help</span></span>

<span data-ttu-id="eecbd-115">若要檢視組態的說明，請使用`Get-Help`cmdlet 與函式或類型名稱的函式名稱後面加上`-?`。</span><span class="sxs-lookup"><span data-stu-id="eecbd-115">To view the help for a configuration, use the `Get-Help` cmdlet with the name of the function, or type the name of the function followed by `-?`.</span></span> <span data-ttu-id="eecbd-116">以下是先前的設定傳遞至輸出`Get-Help`。</span><span class="sxs-lookup"><span data-stu-id="eecbd-116">The following is the output of the previous Configuration passed to `Get-Help`.</span></span>

```powershell
Get-Help HelpSample1 -Detailed
```

```output
NAME
    HelpSample1

SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.


SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-PsDscRunAsCredential] <PSCredential>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName] <String>] [[-FilePath] <String>] [<CommonParameters>]


DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.


PARAMETERS
    -InstanceName <String>

    -DependsOn <String[]>

    -PsDscRunAsCredential <PSCredential>

    -OutputPath <String>

    -ConfigurationData <Hashtable>

    -ComputerName <String>
        The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

        Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
        Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
        The description can include paragraph breaks.

        The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
        (and their descriptions) appear in help topic. To change the order, change the syntax.

    -FilePath <String>
        Provide a PARAMETER section for each parameter that your script or function accepts.

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (https:/go.microsoft.com/fwlink/?LinkID=113216).

    -------------------------- EXAMPLE 1 --------------------------

    PS C:\>HelpSample -ComputerName localhost

    A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
    PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

    If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.




    -------------------------- EXAMPLE 2 --------------------------

    PS C:\>HelpSample -FilePath "C:\output.txt"

    This example will be labeled "EXAMPLE 2" when help is displayed to the user.




REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

> [!NOTE]
> <span data-ttu-id="eecbd-117">語法欄位和參數屬性會自動為您產生 powershell。</span><span class="sxs-lookup"><span data-stu-id="eecbd-117">Syntax fields and parameter attributes are automatically generated for you by PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="eecbd-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eecbd-118">See Also</span></span>

- [<span data-ttu-id="eecbd-119">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="eecbd-119">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="eecbd-120">撰寫、編譯及套用設定</span><span class="sxs-lookup"><span data-stu-id="eecbd-120">Write, Compile, and Apply a Configuration</span></span>](write-compile-apply-configuration.md)
- [<span data-ttu-id="eecbd-121">將參數新增至設定</span><span class="sxs-lookup"><span data-stu-id="eecbd-121">Add Parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
