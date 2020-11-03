---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/get-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-IseSnippet
ms.openlocfilehash: c43dae3f178ae778d78fe3718fa85fd2635eba86
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205339"
---
# <span data-ttu-id="26d23-103">Get-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="26d23-103">Get-IseSnippet</span></span>

## <span data-ttu-id="26d23-104">概要</span><span class="sxs-lookup"><span data-stu-id="26d23-104">SYNOPSIS</span></span>
<span data-ttu-id="26d23-105">取得使用者建立的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="26d23-105">Gets snippets that the user created.</span></span>

## <span data-ttu-id="26d23-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="26d23-106">SYNTAX</span></span>

```
Get-IseSnippet [<CommonParameters>]
```

## <span data-ttu-id="26d23-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="26d23-107">DESCRIPTION</span></span>

<span data-ttu-id="26d23-108">此 `Get-IseSnippet` Cmdlet 會取得包含使用者所建立之可重複使用文字程式碼片段的 .ps1xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="26d23-108">The `Get-IseSnippet` cmdlet gets the PS1XML files that contain reusable text snippets that the user created.</span></span> <span data-ttu-id="26d23-109">此 Cmdlet 僅適用於 Windows PowerShell 整合式指令碼環境 (ISE)。</span><span class="sxs-lookup"><span data-stu-id="26d23-109">It works only in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

<span data-ttu-id="26d23-110">當您使用 `New-IseSnippet` Cmdlet 建立程式碼片段時，會 `New-IseSnippet` `<SnippetTitle>.Snippets.ps1xml` 在目錄中建立檔案 `$home\Documents\WindowsPowerShell\Snippets` 。</span><span class="sxs-lookup"><span data-stu-id="26d23-110">When you use the `New-IseSnippet` cmdlet to create a snippet, `New-IseSnippet` creates a `<SnippetTitle>.Snippets.ps1xml` file in the `$home\Documents\WindowsPowerShell\Snippets` directory.</span></span>
<span data-ttu-id="26d23-111">`Get-IseSnippet` 取得程式碼片段目錄中的程式碼片段檔案。</span><span class="sxs-lookup"><span data-stu-id="26d23-111">`Get-IseSnippet` gets the snippet files in the Snippets directory.</span></span>

<span data-ttu-id="26d23-112">此 Cmdlet 不會取得透過 Cmdlet 從模組匯入的內建程式碼片段或程式碼片段 `Import-IseSnippet` 。</span><span class="sxs-lookup"><span data-stu-id="26d23-112">This cmdlet does not get built-in snippets or snippets that are imported from modules through the `Import-IseSnippet` cmdlet.</span></span>

<span data-ttu-id="26d23-113">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="26d23-113">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="26d23-114">範例</span><span class="sxs-lookup"><span data-stu-id="26d23-114">EXAMPLES</span></span>

### <span data-ttu-id="26d23-115">範例 1：取得所有使用者定義的程式碼片段</span><span class="sxs-lookup"><span data-stu-id="26d23-115">Example 1: Get all user-defined snippets</span></span>

<span data-ttu-id="26d23-116">這個範例會取得程式碼片段目錄中所有使用者定義的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="26d23-116">This example gets all user-define snippets in the Snippets directory.</span></span>

```powershell
Get-IseSnippet
```

### <span data-ttu-id="26d23-117">範例 2︰將所有使用者定義的程式碼片段從遠端電腦複製到共用目錄</span><span class="sxs-lookup"><span data-stu-id="26d23-117">Example 2: Copy all user-defined snippets from remote computers to a shared directory</span></span>

<span data-ttu-id="26d23-118">此範例會將遠端電腦群組中的所有使用者建立程式碼片段複製到共用程式碼片段目錄。</span><span class="sxs-lookup"><span data-stu-id="26d23-118">This example copies all of the user-created snippets from a group of remote computers to a shared Snippets directory.</span></span>

```powershell
Invoke-Command -Computer (Get-Content Servers.txt) {Get-IseSnippet | Copy-Item -Destination \\Server01\Share01\Snippets}
```

<span data-ttu-id="26d23-119">`Invoke-Command` 會在檔案 `Get-IseSnippet` 中的電腦上執行 `Servers.txt` 。</span><span class="sxs-lookup"><span data-stu-id="26d23-119">`Invoke-Command` runs `Get-IseSnippet` on the computers in the `Servers.txt` file.</span></span> <span data-ttu-id="26d23-120">管線運算子 (`|`) 會將程式碼片段檔案傳送至 `Copy-Item` Cmdlet，此 Cmdlet 會將程式碼片段檔案複製到 **目的地** 參數所指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="26d23-120">A pipeline operator (`|`) sends the snippet files to the `Copy-Item` cmdlet, which copies them to the directory that is specified by the **Destination** parameter.</span></span>

### <span data-ttu-id="26d23-121">範例 3：顯示本機電腦上每個程式碼片段的標題和文字</span><span class="sxs-lookup"><span data-stu-id="26d23-121">Example 3: Display the title and text of each snippet on a local computer</span></span>

<span data-ttu-id="26d23-122">這個範例會使用 `Get-IseSnippet` 和 `Select-Xml` Cmdlet 來顯示本機電腦上每個程式碼片段的標題和文字。</span><span class="sxs-lookup"><span data-stu-id="26d23-122">This example uses the `Get-IseSnippet` and `Select-Xml` cmdlets to display the title and text of each snippet on the local computer.</span></span>

```powershell
#Parse-Snippet Function
function Parse-Snippet {
  $SnippetFiles = Get-IseSnippet
  $SnippetNamespace = @{x="http://schemas.microsoft.com/PowerShell/Snippets"}
  foreach ($SnippetFile in $SnippetFiles) {
     Write-Host ""
     $Title = Select-Xml -Path $SnippetFile.FullName -Namespace $SnippetNamespace -XPath "//x:Title" |
       ForEach-Object {$_.Node.InnerXML}
     $Text = Select-Xml -Path $SnippetFile.FullName -Namespace $SnippetNamespace -XPath "//x:Script" |
       ForEach-Object {$_.Node.InnerText}
     Write-Host "Title: $Title"
     Write-Host "Text: $Text"
   }
}
```

```Output
Title: Mandatory
Text:
Param
(
  [parameter(Mandatory=True)]
  [String[]]
  $<ParameterName>
)

Title: Copyright
Text:  (c) Fabrikam, Inc. 2012
```

### <span data-ttu-id="26d23-123">範例 4︰顯示工作階段中所有程式碼片段的標題和描述</span><span class="sxs-lookup"><span data-stu-id="26d23-123">Example 4: Display the title and description of all snippets in the session</span></span>

<span data-ttu-id="26d23-124">此範例會顯示會話中所有程式碼片段的標題和描述，包括內建的程式碼片段、使用者定義的程式碼片段，以及匯入的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="26d23-124">This example displays the title and description of all snippets in the session, including built-in snippets, user-defined snippets, and imported snippets.</span></span>

```powershell
$PSISE.CurrentPowerShellTab.Snippets | Format-Table DisplayTitle, Description
```

<span data-ttu-id="26d23-125">`$PSISE`變數代表 Windows PowerShell ISE 的主機程式。</span><span class="sxs-lookup"><span data-stu-id="26d23-125">The `$PSISE` variable represents the Windows PowerShell ISE host program.</span></span> <span data-ttu-id="26d23-126">變數的 **CurrentPowerShellTab** 屬性 `$PSISE` 代表目前的會話。</span><span class="sxs-lookup"><span data-stu-id="26d23-126">The **CurrentPowerShellTab** property of the `$PSISE` variable represent the current session.</span></span> <span data-ttu-id="26d23-127">**Snippets** 屬性代表目前工作階段中的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="26d23-127">The **Snippets** property represents snippets in the current session.</span></span>

<span data-ttu-id="26d23-128">此 `$PSISE.CurrentPowerShellTab.Snippets` 命令會傳回代表程式碼片段的 **ISESnippet** 物件，而不像 `Get-IseSnippet` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="26d23-128">The `$PSISE.CurrentPowerShellTab.Snippets` command returns a **Microsoft.PowerShell.Host.ISE.ISESnippet** object that represents a snippet, unlike the `Get-IseSnippet` cmdlet.</span></span> <span data-ttu-id="26d23-129">`Get-IseSnippet` 傳回代表程式碼片段檔案 (FileInfo) 的檔案物件。</span><span class="sxs-lookup"><span data-stu-id="26d23-129">`Get-IseSnippet` returns a file object (System.Io.FileInfo) that represents a snippet file.</span></span>

<span data-ttu-id="26d23-130">`Format-Table`Cmdlet 會在資料表中顯示程式碼片段的 **DisplayTitle** 和 **Description** 屬性。</span><span class="sxs-lookup"><span data-stu-id="26d23-130">The `Format-Table` cmdlet displays the **DisplayTitle** and **Description** properties of the snippets in a table.</span></span>

## <span data-ttu-id="26d23-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="26d23-131">PARAMETERS</span></span>

### <span data-ttu-id="26d23-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="26d23-132">CommonParameters</span></span>

<span data-ttu-id="26d23-133">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="26d23-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="26d23-134">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="26d23-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="26d23-135">輸入</span><span class="sxs-lookup"><span data-stu-id="26d23-135">INPUTS</span></span>

## <span data-ttu-id="26d23-136">輸出</span><span class="sxs-lookup"><span data-stu-id="26d23-136">OUTPUTS</span></span>

### <span data-ttu-id="26d23-137">System.IO.FileInfo</span><span class="sxs-lookup"><span data-stu-id="26d23-137">System.IO.FileInfo</span></span>

<span data-ttu-id="26d23-138">此 Cmdlet 會傳回代表程式碼片段檔案的檔案物件。</span><span class="sxs-lookup"><span data-stu-id="26d23-138">This cmdlet returns a file object that represents the snippet file.</span></span>

## <span data-ttu-id="26d23-139">注意</span><span class="sxs-lookup"><span data-stu-id="26d23-139">NOTES</span></span>

* <span data-ttu-id="26d23-140">此 `New-IseSnippet` Cmdlet 會將使用者建立的新程式碼片段儲存在未簽署的 .ps1xml 檔案中。</span><span class="sxs-lookup"><span data-stu-id="26d23-140">The `New-IseSnippet` cmdlet stores new user-created snippets in unsigned .ps1xml files.</span></span> <span data-ttu-id="26d23-141">因此，Windows PowerShell 無法將它們新增到執行原則為 **AllSigned** 或 **Restricted** 的工作階段中。</span><span class="sxs-lookup"><span data-stu-id="26d23-141">As such, Windows PowerShell cannot add them to a session in which the execution policy is **AllSigned** or **Restricted** .</span></span> <span data-ttu-id="26d23-142">在 **Restricted** 或 **AllSigned** 工作階段中，您可以建立、取得和匯入使用者建立的未簽署程式碼片段，卻無法在工作階段中使用它們。</span><span class="sxs-lookup"><span data-stu-id="26d23-142">In a **Restricted** or **AllSigned** session, you can create, get, and import unsigned user-created snippets, but you cannot use them in the session.</span></span>

  <span data-ttu-id="26d23-143">若要使用 Cmdlet 所傳回的未簽署使用者建立程式碼片段 `Get-IseSnippet` ，請變更執行原則，然後重新開機 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="26d23-143">To use unsigned user-created snippets that the `Get-IseSnippet` cmdlet returns, change the execution policy, and then restart Windows PowerShell ISE.</span></span>

  <span data-ttu-id="26d23-144">如需 Windows PowerShell 執行原則的詳細資訊，請參閱[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="26d23-144">For more information about Windows PowerShell execution policies, see [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="26d23-145">相關連結</span><span class="sxs-lookup"><span data-stu-id="26d23-145">RELATED LINKS</span></span>

[<span data-ttu-id="26d23-146">New-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="26d23-146">New-IseSnippet</span></span>](New-IseSnippet.md)

[<span data-ttu-id="26d23-147">Import-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="26d23-147">Import-IseSnippet</span></span>](Import-IseSnippet.md)
