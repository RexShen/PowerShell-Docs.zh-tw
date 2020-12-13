---
ms.date: 09/12/2016
ms.topic: reference
title: 註解型說明的範例
description: 註解型說明的範例
ms.openlocfilehash: 35fe9103a261483c56af629f620dbd6b3c642e68
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667635"
---
# <a name="examples-of-comment-based-help"></a><span data-ttu-id="5dc33-103">註解型說明的範例</span><span class="sxs-lookup"><span data-stu-id="5dc33-103">Examples of Comment-Based Help</span></span>

<span data-ttu-id="5dc33-104">本主題包含範例，示範如何針對腳本和函式使用以批註為基礎的說明。</span><span class="sxs-lookup"><span data-stu-id="5dc33-104">This topic includes example that demonstrate how to use comment-based help for scripts and functions.</span></span>

## <a name="example-1-comment-based-help-for-a-function"></a><span data-ttu-id="5dc33-105">範例1：函數的 Comment-Based 說明</span><span class="sxs-lookup"><span data-stu-id="5dc33-105">Example 1: Comment-Based Help for a Function</span></span>

 <span data-ttu-id="5dc33-106">下列範例函數包含以批註為基礎的說明。</span><span class="sxs-lookup"><span data-stu-id="5dc33-106">The following sample function includes comment-based Help.</span></span>

```powershell
function Add-Extension
{
    param ([string]$Name,[string]$Extension = "txt")
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.

        .DESCRIPTION
        Adds a file name extension to a supplied name.
        Takes any strings for the file name or extension.

        .PARAMETER Name
        Specifies the file name.

        .PARAMETER Extension
        Specifies the extension. "Txt" is the default.

        .INPUTS
        None. You cannot pipe objects to Add-Extension.

        .OUTPUTS
        System.String. Add-Extension returns a string with the extension or file name.

        .EXAMPLE
        C:\PS> extension -name "File"
        File.txt

        .EXAMPLE
        C:\PS> extension -name "File" -extension "doc"
        File.doc

        .EXAMPLE
        C:\PS> extension "File" "doc"
        File.doc

        .LINK
        Online version: http://www.fabrikam.com/extension.html

        .LINK
        Set-Item
    #>
}
```

<span data-ttu-id="5dc33-107">下列輸出會顯示命令的結果 `Get-Help` ，此命令會顯示函式的說明 `Add-Extension` 。</span><span class="sxs-lookup"><span data-stu-id="5dc33-107">The following output shows the results of a `Get-Help` command that displays the help for the `Add-Extension` function.</span></span>

```powershell
C:\PS> get-help add-extension -full
```

```Output
        NAME
            Add-Extension

        SYNOPSIS
            Adds a file name extension to a supplied name.

        SYNTAX
            Add-Extension [[-Name] <String>] [[-Extension] <String>] [<CommonParameters>]

        DESCRIPTION
            Adds a file name extension to a supplied name. Takes any strings for the file name or extension.

        PARAMETERS
           -Name
               Specifies the file name.

               Required?                    false
               Position?                    0
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

           -Extension
               Specifies the extension. "Txt" is the default.

               Required?                    false
               Position?                    1
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

            <CommonParameters>
               This cmdlet supports the common parameters: -Verbose, -Debug,
               -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
               -OutBuffer and -OutVariable. For more information, type
               "get-help about_commonparameters".

        INPUTS
            None. You cannot pipe objects to Add-Extension.

        OUTPUTS
            System.String. Add-Extension returns a string with the extension or file name.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> extension -name "File"
            File.txt

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> extension -name "File" -extension "doc"
            File.doc

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> extension "File" "doc"
            File.doc

        RELATED LINKS
            Online version: http://www.fabrikam.com/extension.html
            Set-Item
```

## <a name="example-2-comment-based-help-for-a-script"></a><span data-ttu-id="5dc33-108">範例2：腳本的 Comment-Based 說明</span><span class="sxs-lookup"><span data-stu-id="5dc33-108">Example 2: Comment-Based Help for a Script</span></span>

<span data-ttu-id="5dc33-109">下列範例函數包含以批註為基礎的說明。</span><span class="sxs-lookup"><span data-stu-id="5dc33-109">The following sample function includes comment-based Help.</span></span>

<span data-ttu-id="5dc33-110">請注意結尾和語句之間的空白行 **#>** `Param` 。</span><span class="sxs-lookup"><span data-stu-id="5dc33-110">Notice the blank lines between the closing **#>** and the `Param` statement.</span></span> <span data-ttu-id="5dc33-111">在沒有語句的腳本中，[ `Param` 說明] 主題和第一個函式宣告中的最後一個批註之間必須至少有兩個空白行。</span><span class="sxs-lookup"><span data-stu-id="5dc33-111">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the Help topic and the first function declaration.</span></span> <span data-ttu-id="5dc33-112">如果沒有這些空白行，請 `Get-Help` 將說明主題與函式相關聯，而不是腳本。</span><span class="sxs-lookup"><span data-stu-id="5dc33-112">Without these blank lines, `Get-Help` associates the Help topic with the function, instead of the script.</span></span>

```powershell
<#
  .SYNOPSIS
  Performs monthly data updates.

  .DESCRIPTION
  The Update-Month.ps1 script updates the registry with new data generated
  during the past month and generates a report.

  .PARAMETER InputPath
  Specifies the path to the CSV-based input file.

  .PARAMETER OutputPath
  Specifies the name and path for the CSV-based output file. By default,
  MonthlyUpdates.ps1 generates a name from the date and time it runs, and
  saves the output in the local directory.

  .INPUTS
  None. You cannot pipe objects to Update-Month.ps1.

  .OUTPUTS
  None. Update-Month.ps1 does not generate any output.

  .EXAMPLE
  C:\PS> .\Update-Month.ps1

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
```

<span data-ttu-id="5dc33-113">下列命令會取得腳本說明。</span><span class="sxs-lookup"><span data-stu-id="5dc33-113">The following command gets the script Help.</span></span> <span data-ttu-id="5dc33-114">因為腳本不在 Path 環境變數中所列的目錄中，所以 `Get-Help` 取得腳本說明的命令必須指定腳本路徑。</span><span class="sxs-lookup"><span data-stu-id="5dc33-114">Because the script is not in a directory that is listed in the Path environment variable, the `Get-Help` command that gets the script Help must specify the script path.</span></span>

```powershell
C:\PS> get-help c:\ps-test\update-month.ps1 -full
```

```Output
            NAME
                C:\ps-test\Update-Month.ps1

            SYNOPSIS
                Performs monthly data updates.

            SYNTAX
                C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
                <String>] [<CommonParameters>]

            DESCRIPTION
                The Update-Month.ps1 script updates the registry with new data
                generated during the past month and generates a report.

            PARAMETERS
               -InputPath
                   Specifies the path to the CSV-based input file.

                   Required?                    true
                   Position?                    0
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               -OutputPath
                   Specifies the name and path for the CSV-based output file. By
                   default, MonthlyUpdates.ps1 generates a name from the date
                   and time it runs, and saves the output in the local directory.

                   Required?                    false
                   Position?                    1
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               <CommonParameters>
                   This cmdlet supports the common parameters: -Verbose, -Debug,
                   -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
                   -OutBuffer and -OutVariable. For more information, type,
                   "get-help about_commonparameters".

            INPUTS
                   None. You cannot pipe objects to Update-Month.ps1.

            OUTPUTS
                   None. Update-Month.ps1 does not generate any output.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> .\Update-Month.ps1

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
            C:\Reports\2009\January.csv

            RELATED LINKS
```

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a><span data-ttu-id="5dc33-115">範例3： Param 語句中的參數描述</span><span class="sxs-lookup"><span data-stu-id="5dc33-115">Example 3: Parameter Descriptions in a Param Statement</span></span>

<span data-ttu-id="5dc33-116">這個範例示範如何在函數或腳本的語句中插入參數描述 `Param` 。</span><span class="sxs-lookup"><span data-stu-id="5dc33-116">This example shows how to insert parameter descriptions in the `Param` statement of a function or script.</span></span> <span data-ttu-id="5dc33-117">當參數描述很簡單時，此格式最有用。</span><span class="sxs-lookup"><span data-stu-id="5dc33-117">This format is most useful when the parameter descriptions are brief.</span></span>

```powershell
function Add-Extension
{
    param
    (
        [string]
        # Specifies the file name.
        $name,

        [string]
        # Specifies the file name extension. "Txt" is the default.
        $extension = "txt"
    )
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.
...
    #>
```

<span data-ttu-id="5dc33-118">結果與範例1的結果相同。</span><span class="sxs-lookup"><span data-stu-id="5dc33-118">The results are the same as the results for Example 1.</span></span> <span data-ttu-id="5dc33-119">`Get-Help` 將參數描述視為伴隨關鍵字來解讀 `.Parameter` 。</span><span class="sxs-lookup"><span data-stu-id="5dc33-119">`Get-Help` interprets the parameter descriptions as though they were accompanied by the `.Parameter` keyword.</span></span>

## <a name="example-4--redirecting-to-an-xml-file"></a><span data-ttu-id="5dc33-120">範例4：重新導向至 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="5dc33-120">Example 4:  Redirecting to an XML File</span></span>

<span data-ttu-id="5dc33-121">您可以撰寫函數和腳本的 XML 型說明主題。</span><span class="sxs-lookup"><span data-stu-id="5dc33-121">You can write XML-based Help topics for functions and scripts.</span></span> <span data-ttu-id="5dc33-122">雖然以批註為基礎的說明比較容易執行，但如果您想要更精確地控制說明內容，或將說明主題翻譯成多種語言，則需要以 XML 為基礎的協助。下列範例會顯示腳本的前幾行 `Update-Month.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="5dc33-122">Although comment-based Help is easier to implement, XML-based Help is required if you want more precise control over Help content or if you are translating Help topics into multiple languages.The following example shows the first few lines of the `Update-Month.ps1` script.</span></span> <span data-ttu-id="5dc33-123">腳本會使用 `.ExternalHelp` 關鍵字來指定腳本的 XML 型說明主題的路徑。</span><span class="sxs-lookup"><span data-stu-id="5dc33-123">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based Help topic for the script.</span></span>

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

<span data-ttu-id="5dc33-124">下列範例示範如何在函式 `.ExternalHelp` 中使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="5dc33-124">The following example shows the use of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a><span data-ttu-id="5dc33-125">範例5：重新導向至不同的說明主題</span><span class="sxs-lookup"><span data-stu-id="5dc33-125">Example 5:  Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="5dc33-126">下列程式碼是 PowerShell 中內建函數開頭的摘要 `Help` ，它會一次顯示一屏解說文字。</span><span class="sxs-lookup"><span data-stu-id="5dc33-126">The following code is an excerpt from the beginning of the built-in `Help` function in PowerShell, which displays one screen of Help text at a time.</span></span> <span data-ttu-id="5dc33-127">由於 Get-Help Cmdlet 的說明主題會描述 Help 函式，因此 Help 函式會使用 `.ForwardHelpTargetName` 和 `.ForwardHelpCategory` 關鍵字將使用者重新導向至 Get-Help Cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="5dc33-127">Because the Help topic for the Get-Help cmdlet describes the Help function, the Help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the Get-Help cmdlet Help topic.</span></span>

```powershell
function help
{

    <#
      .FORWARDHELPTARGETNAME Get-Help
      .FORWARDHELPCATEGORY Cmdlet
    #>
    [CmdletBinding(DefaultParameterSetName='AllUsersView')]
    param(
            [Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
            [System.String]
            ${Name},
    ...
```

<span data-ttu-id="5dc33-128">下列命令會使用這項功能。</span><span class="sxs-lookup"><span data-stu-id="5dc33-128">The following command uses this feature.</span></span> <span data-ttu-id="5dc33-129">當使用者輸入函式的 `Get-Help` 命令時 `Help` ，會 `Get-Help` 顯示 Cmdlet 的說明主題 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="5dc33-129">When a user types a `Get-Help` command for the `Help` function, `Get-Help` displays the Help topic for the `Get-Help` cmdlet.</span></span>

```powershell
C:\PS> get-help help
```

```Output
            NAME
                Get-Help

            SYNOPSIS
                Displays information about Windows PowerShell cmdlets and concepts.
            ...
```
