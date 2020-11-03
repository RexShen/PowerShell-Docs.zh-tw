---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/new-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-IseSnippet
ms.openlocfilehash: 0ed1c2913fc7531574bfbdd435a002d60931d24a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202476"
---
# New-IseSnippet

## 概要
建立 Windows PowerShell ISE 程式碼片段。

## SYNTAX

```
New-IseSnippet [-Title] <String> [-Description] <String> [-Text] <String> [-Author <String>]
 [-CaretOffset <Int32>] [-Force] [<CommonParameters>]
```

## DESCRIPTION

`New-ISESnippet`Cmdlet 會為 Windows PowerShell ISE 建立可重複使用的文字「程式碼片段」。 您可以使用程式碼片段來將文字新增到 Windows PowerShell ISE 的 [程式碼片段] 窗格或 [命令] 窗格。 這個 Cmdlet 只在 Windows PowerShell ISE 中提供。

自 Windows PowerShell 3.0 開始，Windows PowerShell ISE 包含了內建程式碼片段的集合。 此 `New-ISESnippet` Cmdlet 可讓您建立自己的程式碼片段，以加入至內建集合。 您可以檢視、變更、新增、刪除和共用程式碼片段檔案，並將它們包含在 Windows PowerShell 模組中。 若要查看 Windows PowerShell ISE 中的程式碼片段，請從 [ **編輯** ] 功能表選取 [ **啟動程式碼片段** ]，或按 <kbd>CTRL</kbd> + <kbd>J</kbd>。

`New-ISESnippet`Cmdlet `<Title>.Snippets.ps1xml` 會以 `$home\Documents\WindowsPowerShell\Snippets` 您指定的標題，在目錄中建立檔案。 如果要在您撰寫的模組中包含程式碼片段檔案，請將程式碼片段檔案加到模組目錄的 Snippets 子目錄。

您無法在執行原則 **受限** 或 **AllSigned** 的會話中使用使用者建立的程式碼片段。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例1：建立 Comment-Based 的說明程式碼片段

```
New-IseSnippet -Title Comment-BasedHelp -Description "A template for comment-based help." -Text "<#
    .SYNOPSIS

    .DESCRIPTION
    .PARAMETER  <Parameter-Name>
    .INPUTS
    .OUTPUTS
    .EXAMPLE
    .LINK
#>"
```

此命令會為 Windows PowerShell ISE 建立 Comment-BasedHelp 程式碼片段。 它會 `Comment-BasedHelp.snippets.ps1xml` 在使用者的程式碼片段目錄中建立名為的檔案 `$home\Documents\WindowsPowerShell\Snippets` 。

### 範例2：建立必要的程式碼片段

```
$M = @'
Param
(
  [parameter(Mandatory=$true)]
  [String[]]
  $<ParameterName>
)
'@

New-ISESnippet -Text $M -Title Mandatory -Description "Adds a mandatory function parameter." -Author "Patti Fuller, Fabrikam Corp." -Force
```

此範例會針對 Windows PowerShell ISE 建立名為「 **強制** 」的程式碼片段。 第一個命令會將程式碼片段文字儲存在 `$M` 變數中。 第二個命令會使用 `New-ISESnippet` Cmdlet 建立程式碼片段。 此命令會使用 **Force** 參數覆寫先前同名的程式碼片段。

### 範例3：將必要的程式碼片段從資料夾複製到目的資料夾

```
Copy-Item "$Home\Documents\WindowsPowerShell\Snippets\Mandatory.Snippets.ps1xml" -Destination "\\Server\Share"
```

此命令會使用 `Copy-Item` Cmdlet 將 **必要** 的程式碼片段從放置於 Server\Share 檔案共用的資料夾中複製 `New-ISESnippet` 。

## PARAMETERS

### -作者

指定程式碼片段的作者。 作者欄位會顯示在程式碼片段檔案中，但是當您在 Windows PowerShell ISE 中按一下程式碼片段名稱時則不會顯示。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CaretOffset

指定此 Cmdlet 放置游標所在的程式碼片段文字字元。 輸入一個代表游標位置的整數，"1" 代表文字的第一個字元。 預設值 0 (零) 會將游標放在文字第一個字元的正前方。 這個參數不會縮排程式碼片段文字。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -Description

指定程式碼片段的描述。 當您在 Windows PowerShell ISE 中按一下程式碼片段名稱時，即會顯示描述值。 這是必要參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

指出此 Cmdlet 會覆寫相同位置中名稱相同的程式碼片段檔案。 依預設，不 `New-ISESnippet` 會覆寫檔案。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -文字

指定當您選取程式碼片段時新增的文字值。 當您在 Windows PowerShell ISE 中按一下程式碼片段名稱時，即會顯示程式碼片段文字。 這是必要參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Title

指定程式碼片段的標題或名稱。 標題也會用來命名程式碼片段檔案。 這是必要參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

此 Cmdlet 不接受來自管線的輸入。

## 輸出

### 無

此 Cmdlet 不會產生任何輸出。

## 注意

`New-IseSnippet` 將新使用者建立的程式碼片段儲存在未簽署的 .ps1xml 檔案中。 因此，Windows PowerShell 無法將它們新增到執行原則為 **AllSigned** 或 **Restricted** 的工作階段中。 在 **Restricted** 或 **AllSigned** 工作階段中，您可以建立、取得和匯入使用者建立的未簽署程式碼片段，卻無法在工作階段中使用它們。

如果您 `New-IseSnippet` 在 **受限** 或 **AllSigned** 會話中使用此 Cmdlet，則會建立程式碼片段，但是當 Windows PowerShell 嘗試將新建立的程式碼片段新增至會話時，會出現錯誤訊息。 如果要使用新的程式碼片段 (和其他使用者建立的未簽署程式碼片段)，請變更執行原則，然後重新啟動 Windows PowerShell ISE。

如需 Windows PowerShell 執行原則的詳細資訊，請參閱 about_Execution_Policies。

- 若要變更程式碼片段，請編輯程式碼片段檔案。 您可以在 Windows PowerShell ISE 的腳本窗格中編輯程式碼片段檔案。
- 若要刪除您新增的程式碼片段，請刪除程式碼片段檔案。
- 您無法刪除內建的程式碼片段，但您可以使用 "$psise 來隱藏所有內建程式碼片段。ShowDefaultSnippets = $false "命令。
- 您可以建立與內建程式碼片段同名的程式碼片段。 這兩種程式碼片段都會顯示在 Windows PowerShell ISE 的程式碼片段功能表中。

## 相關連結

[Get-IseSnippet](Get-IseSnippet.md)

[Import-IseSnippet](Import-IseSnippet.md)
