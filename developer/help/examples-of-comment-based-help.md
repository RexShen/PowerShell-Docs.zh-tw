---
title: 註解型說明的範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 868194a2-17e9-4184-bc36-c04a33f26494
caps.latest.revision: 4
ms.openlocfilehash: dbccaf5b8e48a1c4d924bc0ec4ea09b25e10adf0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857964"
---
# <a name="examples-of-comment-based-help"></a><span data-ttu-id="398dc-102">註解型說明的範例</span><span class="sxs-lookup"><span data-stu-id="398dc-102">Examples of Comment-Based Help</span></span>

<span data-ttu-id="398dc-103">本主題包含範例，示範如何使用指令碼和函式的註解型說明。</span><span class="sxs-lookup"><span data-stu-id="398dc-103">This topic includes example that demonstrate how to use comment-based help for scripts and functions.</span></span>

## <a name="example-1-comment-based-help-for-a-function"></a><span data-ttu-id="398dc-104">範例 1：函式的註解型說明</span><span class="sxs-lookup"><span data-stu-id="398dc-104">Example 1: Comment-Based Help for a Function</span></span>

 <span data-ttu-id="398dc-105">下列範例函數會包含註解型說明。</span><span class="sxs-lookup"><span data-stu-id="398dc-105">The following sample function includes comment-based Help.</span></span>

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

<span data-ttu-id="398dc-106">下列輸出顯示 Get-help 命令，以顯示該函數的說明加入延伸模組的結果。</span><span class="sxs-lookup"><span data-stu-id="398dc-106">The following output shows the results of a Get-Help command that displays the help for the Add-Extension function.</span></span>

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

## <a name="example-2-comment-based-help-for-a-script"></a><span data-ttu-id="398dc-107">範例 2：如需指令碼的註解型說明</span><span class="sxs-lookup"><span data-stu-id="398dc-107">Example 2: Comment-Based Help for a Script</span></span>

<span data-ttu-id="398dc-108">下列範例函數會包含註解型說明。</span><span class="sxs-lookup"><span data-stu-id="398dc-108">The following sample function includes comment-based Help.</span></span>

<span data-ttu-id="398dc-109">請注意結尾之間的空白行**#>** 而`Param`陳述式。</span><span class="sxs-lookup"><span data-stu-id="398dc-109">Notice the blank lines between the closing **#>** and the `Param` statement.</span></span> <span data-ttu-id="398dc-110">在指令碼中沒有`Param`陳述式，說明主題中的最後一個註解與第一個函式宣告之間必須有至少兩個空白的行。</span><span class="sxs-lookup"><span data-stu-id="398dc-110">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the Help topic and the first function declaration.</span></span> <span data-ttu-id="398dc-111">而不需要這些空白行 Get-help 會關聯函式，而不是指令碼的說明主題。</span><span class="sxs-lookup"><span data-stu-id="398dc-111">Without these blank lines, Get-Help associates the Help topic with the function, instead of the script.</span></span>

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

<span data-ttu-id="398dc-112">下列命令會取得說明的指令碼。</span><span class="sxs-lookup"><span data-stu-id="398dc-112">The following command gets the script Help.</span></span> <span data-ttu-id="398dc-113">因為指令碼不是 n 會列在 Path 環境變數，可取得指令碼說明 Get-help 命令的目錄必須指定指令碼路徑。</span><span class="sxs-lookup"><span data-stu-id="398dc-113">Because the script is not n a directory that is listed in the Path environment variable, the Get-Help command that gets the script Help must specify the script path.</span></span>

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

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a><span data-ttu-id="398dc-114">範例 3：Param 陳述式中的參數說明</span><span class="sxs-lookup"><span data-stu-id="398dc-114">Example 3: Parameter Descriptions in a Param Statement</span></span>

<span data-ttu-id="398dc-115">此範例示範如何插入在 parameterdescriptions`Param`函式或指令碼的陳述式。</span><span class="sxs-lookup"><span data-stu-id="398dc-115">This example show how to insert parameterdescriptions in the `Param` statement of a function or script.</span></span> <span data-ttu-id="398dc-116">簡短參數描述時，這種格式是最有用。</span><span class="sxs-lookup"><span data-stu-id="398dc-116">This format is most useful when the parameter descriptions are brief.</span></span>

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

<span data-ttu-id="398dc-117">結果是相同的結果，例如 1。</span><span class="sxs-lookup"><span data-stu-id="398dc-117">The results are the same as the results for Example 1.</span></span> <span data-ttu-id="398dc-118">取得協助解譯參數描述，如同它們所伴隨`.Parameter`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="398dc-118">Get-Help interprets the parameter descriptions as though they were accompanied by the `.Parameter` keyword.</span></span>

## <a name="example-4--redirecting-to-an-xml-file"></a><span data-ttu-id="398dc-119">範例 4︰將重新導向至 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="398dc-119">Example 4:  Redirecting to an XML File</span></span>

<span data-ttu-id="398dc-120">您可以撰寫以 XML 為基礎的函式和指令碼的說明主題。</span><span class="sxs-lookup"><span data-stu-id="398dc-120">You can write XML-based Help topics for functions and scripts.</span></span> <span data-ttu-id="398dc-121">雖然註解型說明會比較容易實作，以 XML 為基礎的說明需要。 如果您想要更精確地控制 [說明] 內容，或如果您將 [說明] 主題轉譯成多種語言下列範例顯示更新 Month.ps1 指令碼的前幾行。</span><span class="sxs-lookup"><span data-stu-id="398dc-121">Although comment-based Help is easier to implement, XML-based Help is required if you want more precise control over Help content or if you are translating Help topics into multiple languages.The following example shows the first few lines of the Update-Month.ps1 script.</span></span> <span data-ttu-id="398dc-122">指令碼會使用`.ExternalHelp`關鍵字來指定指令碼以 XML 為基礎說明主題的路徑。</span><span class="sxs-lookup"><span data-stu-id="398dc-122">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based Help topic for the script.</span></span>

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

<span data-ttu-id="398dc-123">下列範例示範使用`.ExternalHelp`函式中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="398dc-123">The following example shows the use of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a><span data-ttu-id="398dc-124">範例 5:將重新導向至不同的 [說明] 主題</span><span class="sxs-lookup"><span data-stu-id="398dc-124">Example 5:  Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="398dc-125">下列程式碼是摘錄自內建的開頭`Help`函式，在 Windows PowerShell 中，一次顯示一個螢幕的說明文字。</span><span class="sxs-lookup"><span data-stu-id="398dc-125">The following code is an excerpt from the beginning of the built-in `Help` function in Windows PowerShell, which displays one screen of Help text at a time.</span></span> <span data-ttu-id="398dc-126">Help 函式會使用 Get-help cmdlet 的說明 」 主題所述的 Help 函式，因為`.ForwardHelpTargetName`和`.ForwardHelpCategory`關鍵字，以將使用者重新導向的 Get-help cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="398dc-126">Because the Help topic for the Get-Help cmdlet describes the Help function, the Help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the Get-Help cmdlet Help topic.</span></span>

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

<span data-ttu-id="398dc-127">下列命令會使用這項功能。</span><span class="sxs-lookup"><span data-stu-id="398dc-127">The following command uses this feature.</span></span> <span data-ttu-id="398dc-128">當使用者輸入的 Help 函式的 Get-help 命令時，取得說明會顯示 Get-help cmdlet 的說明 」 主題。</span><span class="sxs-lookup"><span data-stu-id="398dc-128">When a user types a Get-Help command for the Help function, Get-Help displays the Help topic for the Get-Help cmdlet.</span></span>

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