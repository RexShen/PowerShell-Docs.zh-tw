---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/import-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-IseSnippet
ms.openlocfilehash: 810be675fc593f665ccc6f3d5b86ac2f6b633863
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202479"
---
# Import-IseSnippet

## 概要
將 ISE 程式碼片段匯入目前的工作階段

## SYNTAX

### FromFolder (預設值)

```
Import-IseSnippet [-Path] <String> [-Recurse] [<CommonParameters>]
```

### FromModule

```
Import-IseSnippet [-Recurse] -Module <String> [-ListAvailable] [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會將 `Import-IseSnippet` 可重複使用的文字「程式碼片段」從模組或目錄匯入至目前的會話。 Windows PowerShell ISE 中的程式碼片段可立即使用。 這個 Cmdlet 只適用于 (ISE) 的 Windows PowerShell 整合式腳本環境。

若要查看並使用匯入的程式碼片段，請在 Windows PowerShell ISE [ **編輯** ] 功能表中，按一下 [ **啟動程式碼片段** ]，或按 <kbd>Ctrl</kbd> + <kbd>J</kbd>。

匯入的程式碼片段僅適用於目前的工作階段。 若要將程式碼片段匯入所有 Windows PowerShell ISE 會話，請將 `Import-IseSnippet` 命令新增至您的 Windows PowerShell 設定檔，或將程式碼片段檔案複製到您的本機程式碼片段目錄 `$home\Documents\WindowsPowershell\Snippets` 。

若要匯入程式碼片段，您必須在程式碼片段 XML 中正確格式化 Windows PowerShell ISE 程式碼片段，並將其儲存在 Snippet.ps1XML 檔案中。 若要建立符合資格的程式碼片段，請使用 `New-IseSnippet` Cmdlet。 `New-IseSnippet``<SnippetTitle>.Snippets.ps1xml`在目錄中建立檔案 `$home\Documents\WindowsPowerShell\Snippets` 。 您可以將程式碼片段移動或複製到 Windows PowerShell 模組的 Snippets 目錄或任何其他目錄。

`Get-IseSnippet`Cmdlet 會在本機程式碼片段目錄中取得使用者建立的程式碼片段，而不會取得匯入的程式碼片段。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例 1：從目錄匯入程式碼片段

此範例會將目錄中的程式碼片段匯入 `\\Server01\Public\Snippets` 至目前的會話。 它使用 **遞迴** 參數從程式碼片段目錄的所有子目錄中取得程式碼片段。

```powershell
Import-IseSnippet -Path \\Server01\Public\Snippets -Recurse
```

### 範例 2：從模組匯入程式碼片段

此範例會從 **SnippetModule** 模組匯入程式碼片段。 此命令會使用 **ListAvailable** 參數匯入程式碼片段（即使命令執行時 **SnippetModule** 模組未匯入使用者的會話）。

```powershell
Import-IseSnippet -Module SnippetModule -ListAvailable
```

### 範例 3：在模組中尋找程式碼片段

此範例會取得 PSModulePath 環境變數中所有已安裝模組中的程式碼片段。

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$_.fullname}
```

### 範例 4：匯入所有模組程式碼片段

此範例會將所有已安裝模組中的所有程式碼片段匯入到目前的會話。 一般來說，您不需要像這樣執行命令，因為具有程式碼片段的模組會在匯 `Import-IseSnippet` 入模組時使用 Cmdlet 將它們匯入。

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$psise.CurrentPowerShellTab.Snippets.Load($_)}
```

### 範例 5：複製所有模組程式碼片段

此範例會將所有已安裝模組中的程式碼片段檔案複製到目前使用者的程式碼片段目錄。 不同於匯入的程式碼片段只會影響目前工作階段，複製的程式碼片段則是可用於每個 Windows PowerShell ISE 工作階段。

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    Copy-Item -Destination $home\Documents\WindowsPowerShell\Snippets
```

## PARAMETERS

### -ListAvailable

指出此 Cmdlet 會從安裝在電腦上的模組取得程式碼片段（即使模組並未匯入目前的會話）。 如果省略此參數，且 **模組** 參數指定的模組未匯入目前的會話，則嘗試從模組取得程式碼片段將會失敗。

只有當命令中使用 **Module** 參數時，此參數才有效。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromModule
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Module

將指定模組中的程式碼片段匯入目前的工作階段。 不支援萬用字元。

此參數會從模組路徑的程式碼片段子目錄中 Snippet.ps1xml 檔案匯入程式碼片段（例如） `$home\Documents\WindowsPowerShell\Modules\<ModuleName>\Snippets` 。

此參數是為了讓模組作者在啟動指令碼 (例如在模組資訊清單的 **ScriptsToProcess** 索引鍵中指定的指令碼) 中使用而設計的。 模組中的程式碼片段不會自動隨模組匯入，但您可以使用 `Import-IseSnippet` 命令將它們匯入。

```yaml
Type: System.String
Parameter Sets: FromModule
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定此 Cmdlet 匯入程式碼片段的程式碼片段目錄路徑。

```yaml
Type: System.String
Parameter Sets: FromFolder
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Recurse

指出此 Cmdlet 會從 **Path** 參數值的所有子目錄匯入程式碼片段。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
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

- 您無法使用 `Get-IseSnippet` Cmdlet 來取得匯入的程式碼片段。 `Get-IseSnippet` 只取得目錄中的程式碼片段 `$home\Documents\WindowsPowerShell\Snippets` 。
- `Import-IseSnippet`會使用 **ISESnippetCollection** 物件的 **Load** 靜態方法。 您也可以在 Windows PowerShell ISE 物件模型中使用程式碼片段的 **Load** 方法： `$psISE.CurrentPowerShellTab.Snippets.Load()`
- 此 `New-IseSnippet` Cmdlet 會將使用者建立的新程式碼片段儲存在未簽署的 .ps1xml 檔案中。 因此，Windows PowerShell 無法將它們載入執行原則為 **AllSigned** 或 **Restricted** 的工作階段中。 在 **Restricted** 或 **AllSigned** 工作階段中，您可以建立、取得和匯入使用者建立的未簽署程式碼片段，卻無法在工作階段中使用它們。

  若要使用 Cmdlet 所傳回的未簽署使用者建立程式碼片段 `Import-IseSnippet` ，請變更執行原則，然後重新開機 Windows PowerShell ISE。

  如需 Windows PowerShell 執行原則的詳細資訊，請參閱[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)。

## 相關連結

[Get-IseSnippet](Get-IseSnippet.md)

[New-IseSnippet](New-IseSnippet.md)
