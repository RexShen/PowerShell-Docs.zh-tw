---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/07/2018
Module Name: Microsoft.PowerShell.Core
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/functions/get-verb?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: 4474bb50c2bf3be10e72d2554190208e956f9040
ms.sourcegitcommit: 7d052985c20761fdf4c6d7ce4e04df4c551c36a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "93206035"
---
# Get-Verb

## 概要
取得核准的 PowerShell 動詞。

## SYNTAX

```
Get-Verb [[-verb] <String[]>] [<CommonParameters>]
```

## DESCRIPTION

函式 `Get-Verb` 會取得已核准在 PowerShell 命令中使用的動詞命令。

PowerShell 建議 Cmdlet 和函式名稱具有 Verb-Noun 格式，並包含已核准的動詞命令。 這種做法可讓命令名稱更一致、可預測且更容易使用。

使用未核准的動詞命令在 PowerShell 中執行的命令。 不過，當您匯入包含命令的模組（其名稱中包含未核准的動詞命令）時，此 `Import-Module` 命令會顯示一則警告訊息。

> [!NOTE]
> 傳回的動詞清單 `Get-Verb` 可能不完整。 如需已核准的 PowerShell 動詞指令動詞清單和描述，請參閱 Microsoft Docs 中的 [已核准動詞](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) 。

## 範例

### 範例 1-取得所有動詞的清單

```powershell
Get-Verb
```

### 範例 2-取得以 "un" 開頭的已核准動詞清單

```powershell
Get-Verb un*
```

```Output
Verb                 Group
----                 -----
Undo                 Common
Unlock               Common
Unpublish            Data
Uninstall            Lifecycle
Unregister           Lifecycle
Unblock              Security
Unprotect            Security
```

### 範例 3-取得安全性群組中所有已核准的動詞

```powershell
Get-Verb | Where-Object Group -EQ Security
```

```Output
Verb      Group
----      -----
Block     Security
Grant     Security
Protect   Security
Revoke    Security
Unblock   Security
Unprotect Security
```

### 範例 4-在具有未核准動詞的模組中尋找所有命令

```powershell
Get-Command -Module Microsoft.PowerShell.Utility | Where-Object Verb -NotIn (Get-Verb).Verb
```

```Output
CommandType     Name            Version    Source
-----------     ----            -------    ------
Cmdlet          Sort-Object     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Tee-Object      3.1.0.0    Microsoft.PowerShell.Utility
```

## PARAMETERS

### -動詞

只取得指定的動詞命令。
輸入動詞命令的名稱或名稱模式。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: All verbs
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

## 輸入

### 無

## 輸出

### Selected.Microsoft.PowerShell.Commands.MemberDefinition

## 注意

`Get-Verb` 傳回 MemberDefinition 物件的已修改版本。
此物件沒有 MemberDefinition 物件的標準屬性， 而是擁有 Verb 和 Group 屬性。 Verb 屬性包含具有動詞命令名稱的字串。 Group 屬性包含具有動詞命令群組的字串。

PowerShell 動詞命令會根據其最常見的用途，指派給群組。 這些群組的設計可讓您輕鬆地尋找並比較動詞命令，而不限制其用途。 您可以為任何類型的命令使用任何已核准的動詞命令。

每個 PowerShell 動詞命令都會指派給下列其中一個群組。

- Common：定義可以套用到幾乎任何 Cmdlet 的一般動作，例如 Add。
- 通訊：定義適用于通訊的動作，例如 Connect。
- 資料：定義適用于資料處理的動作，例如備份。
- 診斷：定義適用于診斷的動作，例如 Debug。
- 生命週期：定義適用于 Cmdlet 生命週期的動作，例如 [完成]。
- 安全性：定義適用于安全性的動作，例如 Revoke。
- 其他：定義其他類型的動作。

與 PowerShell 一起安裝的某些 Cmdlet （例如 `Tee-Object` 和 `Where-Object` ）會使用未核准的動詞命令。 這些 Cmdlet 是記錄例外狀況，而其動詞命令會分類為 **保留** 。

## 相關連結

[Import-Module](import-module.md)
