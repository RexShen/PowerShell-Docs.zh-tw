---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-acl?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Acl
ms.openlocfilehash: d9adce420ff8904fa40c7689a8b2ab5a3b5e945f
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347205"
---
# Get-Acl

## 概要
取得資源 (例如檔案或登錄機碼) 的安全性描述元。

## SYNTAX

### ByPath (預設值)

```
Get-Acl [[-Path] <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [<CommonParameters>]
```

### ByInputObject

```
Get-Acl -InputObject <PSObject> [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### ByLiteralPath

```
Get-Acl [-LiteralPath <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`Get-Acl`Cmdlet 會取得代表檔案或資源安全描述項的物件。 安全性描述元包含資源的存取控制清單 (ACL)。 ACL 會指定使用者和使用者群組存取資源所需的權限。

從 Windows PowerShell 3.0 開始，您可以使用的 **InputObject** 參數 `Get-Acl` 來取得沒有路徑之物件的安全描述項。

## 範例

### 範例 1-取得資料夾的 ACL

這個範例會取得目錄的安全描述項 `C:\Windows` 。

```powershell
Get-Acl C:\Windows
```

### 範例 2-使用萬用字元取得資料夾的 ACL

此範例會取得名稱開頭為之目錄中所有檔案的 PowerShell 路徑和 SDDL `.log` `C:\Windows` `s` 。

```powershell
Get-Acl C:\Windows\s*.log | Format-List -Property PSPath, Sddl
```

此命令會使用 `Get-Acl` Cmdlet 取得代表每個記錄檔之安全描述項的物件。 它會使用管線運算子 (`|`) 將結果傳送至 `Format-List` Cmdlet。 命令使用的 **Property** 參數 `Format-List` ，只顯示每個安全描述項物件的 **PsPath** 和 **SDDL** 屬性。

清單通常會在 PowerShell 中使用，因為資料表中的長值會被截斷。

**SDDL** 值對系統管理員而言非常有用，因為它們是簡單的文字字串，其中包含安全性描述元中的所有資訊。 因此，可輕鬆地傳遞和儲存這些值，並在需要時加以剖析。

### 範例 3-取得 ACL 的 Audit 專案計數

這個範例會取得 `.log` 名稱開頭為之目錄中檔案的安全描述項 `C:\Windows` `s` 。

```powershell
Get-Acl C:\Windows\s*.log -Audit | ForEach-Object { $_.Audit.Count }
```

它使用 **Audit** 參數，取得安全性描述元中 SACL 的稽核記錄。
然後，它會使用 `ForEach-Object` Cmdlet 來計算與每個檔案相關聯的 audit 記錄數目。 結果是一個數字清單，代表每個記錄檔的稽核記錄數目。

### 範例 4-取得登錄機碼的 ACL

這個範例會使用 `Get-Acl` Cmdlet 來取得 (登錄) 的控制項子機碼的安全描述項 `HKLM:\SYSTEM\CurrentControlSet\Control` 。

```powershell
Get-Acl -Path HKLM:\System\CurrentControlSet\Control | Format-List
```

**Path** 參數會指定 Control 子機碼。 管線運算子 (`|`) 會將取得的安全描述項傳遞 `Get-Acl` 至 `Format-List` 命令，這會將安全描述項的屬性格式化為清單，使其易於讀取。

### 範例 5-使用 **InputObject** 取得 ACL

此範例使用的 **InputObject** 參數 `Get-Acl` 來取得儲存子系統物件的安全描述項。

```powershell
Get-Acl -InputObject (Get-StorageSubSystem -Name S087)
```

## PARAMETERS

### -Audit

從系統存取控制清單 (SACL) 取得安全性描述元的稽核資料。

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

### -Exclude

省略指定的項目。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 `*.txt`。 允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Filter

以提供者的格式或語言指定篩選。 此參數的值會限定 **Path** 參數。 篩選的語法 (包括是否使用萬用字元) 取決於提供者。 篩選比其他參數更有效率，因為提供者會在取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

只取得指定的項目。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 `*.txt`。 允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Path

指定資源的路徑。 `Get-Acl` 取得路徑所指示之資源的安全描述項。 允許使用萬用字元。 如果您省略 **Path** 參數，會 `Get-Acl` 取得目前目錄的安全描述項。

參數名稱 ("Path") 為選擇性。

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -InputObject

取得指定物件的安全性描述元。 輸入包含物件的變數，或輸入可取得物件的命令。

您無法使用管線將路徑以外的物件傳送至 `Get-Acl` 。 請改為在命令中明確地使用 **InputObject** 參數。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

指定資源的路徑。 與 **Path** 不同， **LiteralPath** 參數值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將包含路徑的字串傳送至 `Get-Acl` 。

## 輸出

### AccessControl. System.security.accesscontrol.filesecurity，AccessControl. System.security.accesscontrol.directorysecurity，AccessControl. RegistrySecurity.。

`Get-Acl` 傳回物件，代表它取得的 Acl。 物件類型取決於 ACL 類型。

## 注意

此 Cmdlet 僅適用于 Windows 平臺。

依預設，會 `Get-Acl` 顯示資源 (的 PowerShell 路徑 `<provider>::<resource-path>`) 、資源的擁有者，以及「存取」，這是在資源的任意存取控制清單中) 存取控制專案的清單 (陣列 (DACL) 。 DACL 清單是由資源擁有者所控制。

當您將結果格式化為清單時， `Get-Acl | Format-List` 除了路徑、擁有者及存取清單之外， () ，PowerShell 還會顯示下列屬性和屬性值：

- **Group** ：擁有者的安全性群組。
- **Audit** ：系統存取控制清單 (SACL) 中的項目清單 (陣列)。 SACL 會指定 Windows 為其產生稽核記錄的存取嘗試類型。
- **Sddl** ：在單一文字字串中，以 Security Descriptor Definition Language 格式顯示的資源安全性描述元。 PowerShell 會使用安全描述項的 **GetSddlForm** 方法來取得此資料。

因為 `Get-Acl` 檔案系統和登錄提供者支援，所以您可以使用 `Get-Acl` 來查看檔案系統物件（例如檔案和目錄）與登錄物件（例如登錄機碼和專案）的 ACL。

## 相關連結

[Set-Acl](Set-Acl.md)
