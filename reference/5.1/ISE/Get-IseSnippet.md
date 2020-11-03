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
# Get-IseSnippet

## 概要
取得使用者建立的程式碼片段。

## SYNTAX

```
Get-IseSnippet [<CommonParameters>]
```

## DESCRIPTION

此 `Get-IseSnippet` Cmdlet 會取得包含使用者所建立之可重複使用文字程式碼片段的 .ps1xml 檔案。 此 Cmdlet 僅適用於 Windows PowerShell 整合式指令碼環境 (ISE)。

當您使用 `New-IseSnippet` Cmdlet 建立程式碼片段時，會 `New-IseSnippet` `<SnippetTitle>.Snippets.ps1xml` 在目錄中建立檔案 `$home\Documents\WindowsPowerShell\Snippets` 。
`Get-IseSnippet` 取得程式碼片段目錄中的程式碼片段檔案。

此 Cmdlet 不會取得透過 Cmdlet 從模組匯入的內建程式碼片段或程式碼片段 `Import-IseSnippet` 。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例 1：取得所有使用者定義的程式碼片段

這個範例會取得程式碼片段目錄中所有使用者定義的程式碼片段。

```powershell
Get-IseSnippet
```

### 範例 2︰將所有使用者定義的程式碼片段從遠端電腦複製到共用目錄

此範例會將遠端電腦群組中的所有使用者建立程式碼片段複製到共用程式碼片段目錄。

```powershell
Invoke-Command -Computer (Get-Content Servers.txt) {Get-IseSnippet | Copy-Item -Destination \\Server01\Share01\Snippets}
```

`Invoke-Command` 會在檔案 `Get-IseSnippet` 中的電腦上執行 `Servers.txt` 。 管線運算子 (`|`) 會將程式碼片段檔案傳送至 `Copy-Item` Cmdlet，此 Cmdlet 會將程式碼片段檔案複製到 **目的地** 參數所指定的目錄。

### 範例 3：顯示本機電腦上每個程式碼片段的標題和文字

這個範例會使用 `Get-IseSnippet` 和 `Select-Xml` Cmdlet 來顯示本機電腦上每個程式碼片段的標題和文字。

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

### 範例 4︰顯示工作階段中所有程式碼片段的標題和描述

此範例會顯示會話中所有程式碼片段的標題和描述，包括內建的程式碼片段、使用者定義的程式碼片段，以及匯入的程式碼片段。

```powershell
$PSISE.CurrentPowerShellTab.Snippets | Format-Table DisplayTitle, Description
```

`$PSISE`變數代表 Windows PowerShell ISE 的主機程式。 變數的 **CurrentPowerShellTab** 屬性 `$PSISE` 代表目前的會話。 **Snippets** 屬性代表目前工作階段中的程式碼片段。

此 `$PSISE.CurrentPowerShellTab.Snippets` 命令會傳回代表程式碼片段的 **ISESnippet** 物件，而不像 `Get-IseSnippet` Cmdlet。 `Get-IseSnippet` 傳回代表程式碼片段檔案 (FileInfo) 的檔案物件。

`Format-Table`Cmdlet 會在資料表中顯示程式碼片段的 **DisplayTitle** 和 **Description** 屬性。

## PARAMETERS

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

## 輸出

### System.IO.FileInfo

此 Cmdlet 會傳回代表程式碼片段檔案的檔案物件。

## 注意

* 此 `New-IseSnippet` Cmdlet 會將使用者建立的新程式碼片段儲存在未簽署的 .ps1xml 檔案中。 因此，Windows PowerShell 無法將它們新增到執行原則為 **AllSigned** 或 **Restricted** 的工作階段中。 在 **Restricted** 或 **AllSigned** 工作階段中，您可以建立、取得和匯入使用者建立的未簽署程式碼片段，卻無法在工作階段中使用它們。

  若要使用 Cmdlet 所傳回的未簽署使用者建立程式碼片段 `Get-IseSnippet` ，請變更執行原則，然後重新開機 Windows PowerShell ISE。

  如需 Windows PowerShell 執行原則的詳細資訊，請參閱[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)。

## 相關連結

[New-IseSnippet](New-IseSnippet.md)

[Import-IseSnippet](Import-IseSnippet.md)
