---
title: 以批註為基礎的說明範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 868194a2-17e9-4184-bc36-c04a33f26494
caps.latest.revision: 4
ms.openlocfilehash: 30e98bfcf06b1720005a73ee8294aeba7e1ae066
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367817"
---
# <a name="examples-of-comment-based-help"></a><span data-ttu-id="4a56d-102">註解型說明的範例</span><span class="sxs-lookup"><span data-stu-id="4a56d-102">Examples of Comment-Based Help</span></span>

<span data-ttu-id="4a56d-103">本主題包含的範例示範如何針對腳本和函式使用以批註為基礎的說明。</span><span class="sxs-lookup"><span data-stu-id="4a56d-103">This topic includes example that demonstrate how to use comment-based help for scripts and functions.</span></span>

## <a name="example-1-comment-based-help-for-a-function"></a><span data-ttu-id="4a56d-104">範例1：函式以批註為基礎的說明</span><span class="sxs-lookup"><span data-stu-id="4a56d-104">Example 1: Comment-Based Help for a Function</span></span>

 <span data-ttu-id="4a56d-105">下列範例函數包含以批註為基礎的說明。</span><span class="sxs-lookup"><span data-stu-id="4a56d-105">The following sample function includes comment-based Help.</span></span>

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

<span data-ttu-id="4a56d-106">下列輸出顯示 Get-help 命令的結果，可顯示新增擴充功能函式的說明。</span><span class="sxs-lookup"><span data-stu-id="4a56d-106">The following output shows the results of a Get-Help command that displays the help for the Add-Extension function.</span></span>

```powershell
C:\PS> get-help add-extension -full
```

```output
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

## <a name="example-2-comment-based-help-for-a-script"></a><span data-ttu-id="4a56d-107">範例2：腳本的批註式說明</span><span class="sxs-lookup"><span data-stu-id="4a56d-107">Example 2: Comment-Based Help for a Script</span></span>

<span data-ttu-id="4a56d-108">下列範例函數包含以批註為基礎的說明。</span><span class="sxs-lookup"><span data-stu-id="4a56d-108">The following sample function includes comment-based Help.</span></span>

<span data-ttu-id="4a56d-109">請注意，結尾 **#>** 和 `Param` 語句之間的空白行。</span><span class="sxs-lookup"><span data-stu-id="4a56d-109">Notice the blank lines between the closing **#>** and the `Param` statement.</span></span> <span data-ttu-id="4a56d-110">在沒有 `Param` 語句的腳本中，說明主題中的最後一個批註和第一個函式宣告之間必須至少有兩個空白行。</span><span class="sxs-lookup"><span data-stu-id="4a56d-110">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the Help topic and the first function declaration.</span></span> <span data-ttu-id="4a56d-111">如果沒有這些空白行，Get-help 會將說明主題與函式相關聯，而不是腳本。</span><span class="sxs-lookup"><span data-stu-id="4a56d-111">Without these blank lines, Get-Help associates the Help topic with the function, instead of the script.</span></span>

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

<span data-ttu-id="4a56d-112">下列命令會取得腳本說明。</span><span class="sxs-lookup"><span data-stu-id="4a56d-112">The following command gets the script Help.</span></span> <span data-ttu-id="4a56d-113">由於此腳本不是 Path 環境變數中所列的目錄，因此取得腳本說明的 Get-help 命令必須指定腳本路徑。</span><span class="sxs-lookup"><span data-stu-id="4a56d-113">Because the script is not n a directory that is listed in the Path environment variable, the Get-Help command that gets the script Help must specify the script path.</span></span>

```powershell
C:\PS> get-help c:\ps-test\update-month.ps1 -full
```

```output
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

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a><span data-ttu-id="4a56d-114">範例3： Param 語句中的參數描述</span><span class="sxs-lookup"><span data-stu-id="4a56d-114">Example 3: Parameter Descriptions in a Param Statement</span></span>

<span data-ttu-id="4a56d-115">這個範例示範如何在函數或腳本的 `Param` 語句中插入 parameterdescriptions。</span><span class="sxs-lookup"><span data-stu-id="4a56d-115">This example show how to insert parameterdescriptions in the `Param` statement of a function or script.</span></span> <span data-ttu-id="4a56d-116">當參數描述為 brief 時，此格式最有用。</span><span class="sxs-lookup"><span data-stu-id="4a56d-116">This format is most useful when the parameter descriptions are brief.</span></span>

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

<span data-ttu-id="4a56d-117">結果與範例1的結果相同。</span><span class="sxs-lookup"><span data-stu-id="4a56d-117">The results are the same as the results for Example 1.</span></span> <span data-ttu-id="4a56d-118">Get-help 會解讀參數描述，就好像它們是伴隨 `.Parameter` 關鍵字一樣。</span><span class="sxs-lookup"><span data-stu-id="4a56d-118">Get-Help interprets the parameter descriptions as though they were accompanied by the `.Parameter` keyword.</span></span>

## <a name="example-4--redirecting-to-an-xml-file"></a><span data-ttu-id="4a56d-119">範例4：重新導向至 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="4a56d-119">Example 4:  Redirecting to an XML File</span></span>

<span data-ttu-id="4a56d-120">您可以撰寫函數和腳本的 XML 型說明主題。</span><span class="sxs-lookup"><span data-stu-id="4a56d-120">You can write XML-based Help topics for functions and scripts.</span></span> <span data-ttu-id="4a56d-121">雖然以批註為基礎的說明比較容易執行，但如果您想要更精確地控制說明內容，或要將說明主題翻譯成多種語言，則需要以 XML 為基礎的協助。下列範例顯示 Update-Month 腳本的前幾行。</span><span class="sxs-lookup"><span data-stu-id="4a56d-121">Although comment-based Help is easier to implement, XML-based Help is required if you want more precise control over Help content or if you are translating Help topics into multiple languages.The following example shows the first few lines of the Update-Month.ps1 script.</span></span> <span data-ttu-id="4a56d-122">腳本會使用 `.ExternalHelp` 關鍵字來指定腳本之 XML 型說明主題的路徑。</span><span class="sxs-lookup"><span data-stu-id="4a56d-122">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based Help topic for the script.</span></span>

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

<span data-ttu-id="4a56d-123">下列範例示範如何在函式中使用 `.ExternalHelp` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4a56d-123">The following example shows the use of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a><span data-ttu-id="4a56d-124">範例5：重新導向至不同的說明主題</span><span class="sxs-lookup"><span data-stu-id="4a56d-124">Example 5:  Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="4a56d-125">下列程式碼是從 Windows PowerShell 內建 `Help` 函式的開頭摘錄，一次只會顯示一個解說文字畫面。</span><span class="sxs-lookup"><span data-stu-id="4a56d-125">The following code is an excerpt from the beginning of the built-in `Help` function in Windows PowerShell, which displays one screen of Help text at a time.</span></span> <span data-ttu-id="4a56d-126">由於 Get-help Cmdlet 的說明主題會描述 Help 函式，因此 Help 函式會使用 `.ForwardHelpTargetName` 和 `.ForwardHelpCategory` 關鍵字，將使用者重新導向至 Get-help Cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="4a56d-126">Because the Help topic for the Get-Help cmdlet describes the Help function, the Help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the Get-Help cmdlet Help topic.</span></span>

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

<span data-ttu-id="4a56d-127">下列命令會使用這項功能。</span><span class="sxs-lookup"><span data-stu-id="4a56d-127">The following command uses this feature.</span></span> <span data-ttu-id="4a56d-128">當使用者輸入 Help 函數的 Get-help 命令時，Get-help 會顯示 Get-help Cmdlet 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="4a56d-128">When a user types a Get-Help command for the Help function, Get-Help displays the Help topic for the Get-Help cmdlet.</span></span>

```powershell
C:\PS> get-help help
```

```output
            NAME
                Get-Help

            SYNOPSIS
                Displays information about Windows PowerShell cmdlets and concepts.
            ...
```