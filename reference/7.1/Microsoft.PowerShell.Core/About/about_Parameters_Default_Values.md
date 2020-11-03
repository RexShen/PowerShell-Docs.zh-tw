---
description: 說明如何設定 Cmdlet 參數和 advanced 函數的自訂預設值。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 5/31/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters_default_values?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters_Default_Values
ms.openlocfilehash: c16af49308df26fc51f57c9bd176ad2fd5537e2c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207467"
---
# <a name="about-parameters-default-values"></a>關於參數的預設值

## <a name="short-description"></a>簡短描述

說明如何設定 Cmdlet 參數和 advanced 函數的自訂預設值。

## <a name="long-description"></a>完整描述

`$PSDefaultParameterValues`喜好設定變數可讓您指定任何 Cmdlet 或 advanced 函數的自訂預設值。 除非您在命令中指定另一個值，否則 Cmdlet 和 advanced 函數會使用自訂預設值。

Cmdlet 和 advanced 函式的作者會為其參數設定標準預設值。 一般而言，標準預設值很有用，但可能不適合所有環境。

當您在每次使用命令時，或是當特定的參數值很難記住（例如電子郵件伺服器名稱或專案 GUID）時，這項功能特別有用。

如果所需的預設值有不同的預期值，您可以指定腳本區塊，在不同的條件下為參數提供不同的預設值。

`$PSDefaultParameterValues` 已在 PowerShell 3.0 中引進。

## <a name="syntax"></a>Syntax

`$PSDefaultParameterValues`變數是一個雜湊表，可驗證索引鍵的格式是否為 **DefaultParameterDictionary** 的物件類型。 雜湊表包含索引 **鍵/值** 組。 索引 **鍵** 的格式為 `CmdletName:ParameterName` 。 **值** 是指派給索引鍵的 **DefaultValue** 或 **ScriptBlock** 。

喜好設定變數的語法如下所示 `$PSDefaultParameterValues` ：

```
$PSDefaultParameterValues=@{"CmdletName:ParameterName"="DefaultValue"}

$PSDefaultParameterValues=@{ "CmdletName:ParameterName"={{ScriptBlock}} }

$PSDefaultParameterValues["Disabled"]=$True | $False
```

**CmdletName** 和 **ParameterName** 值中允許使用萬用字元。

若要設定、變更、新增或移除中的特定索引 **鍵/值** 組 `$PSDefaultParameterValues` ，請使用方法來編輯標準雜湊表。 例如， **新增** 和 **移除** 方法。 這些方法不會覆寫雜湊表中的其他值。

還有另一個不會覆寫現有 `$PSDefaultParameterValues` 雜湊表的語法。 若要新增或變更特定的索引 **鍵/值** 組，請使用下列語法：

```
$PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

**CmdletName** 必須是 Cmdlet 的名稱或使用 **CmdletBinding** 屬性之 advanced 函數的名稱。 您無法使用 `$PSDefaultParameterValues` 來指定腳本或簡單函數的預設值。

**DefaultValue** 可以是物件或腳本區塊。 如果此值為腳本區塊，則 PowerShell 會評估腳本區塊，並使用結果做為參數值。 當指定的參數接受腳本區塊值時，請將腳本區塊值括在第二組大括弧中，例如：

```powershell
$PSDefaultParameterValues=@{ "Invoke-Command:ScriptBlock"={{Get-Process}} }
```

如需詳細資訊，請參閱下列文件：

- [about_Hash_Tables](about_Hash_Tables.md)
- [about_Script_Blocks](about_Script_Blocks.md)
- [about_Preference_Variables](about_Preference_Variables.md)

## <a name="examples"></a>範例

### <a name="how-to-set-psdefaultparametervalues"></a>如何設定 \$ PSDefaultParameterValues

`$PSDefaultParameterValues` 是喜好設定變數，所以它只存在於設定的會話中。 它沒有預設值。

若要設定 `$PSDefaultParameterValues` ，請輸入變數名稱和一或多個索引 **鍵/值** 組。 如果您執行另一個 `$PSDefaultParameterValues` 命令，則會覆寫現有的雜湊表。

如需有關如何在不覆寫現有雜湊表值的情況下變更索引 **鍵/值** 組的範例，請參閱 [如何將值加入至 \$ PSDefaultParameterValues](#how-to-add-values-to-psdefaultparametervalues) 或 [如何變更 \$ PSDefaultParameterValues 中的值](#how-to-change-values-in-psdefaultparametervalues)。

若要儲存 `$PSDefaultParameterValues` 未來的會話，請將 `$PSDefaultParameterValues` 命令新增至您的 PowerShell 設定檔。 如需詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。

#### <a name="set-a-custom-default-value"></a>設定自訂預設值

索引 **鍵/值** 組會將索引 `Send-MailMessage:SmtpServer` 鍵設定為自訂預設值 **Server123** 。

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
}
```

#### <a name="set-default-values-for-multiple-parameters"></a>設定多個參數的預設值

若要設定多個參數的預設值，請以分號分隔每個索引 **鍵/值** 組 (`;`) 。 `Send-MailMessage:SmtpServer`和索引 `Get-WinEvent:LogName` 鍵會設定為自訂的預設值。

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123";
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
}
```

#### <a name="use-wildcards-and-switch-parameters"></a>使用萬用字元和切換參數

Cmdlet 和參數名稱可以包含萬用字元。 使用 `$True` 和 `$False` 來設定切換參數的值，例如 **Verbose** 。 一般參數的 **Verbose** 參數會 `$True` 針對所有命令設定為。

```powershell
$PSDefaultParameterValues = @{"*:Verbose"=$True}
```

#### <a name="use-an-array-for-the-default-value"></a>使用預設值的陣列

如果參數可以接受多個值（陣列），您可以將多個值設定為預設值。 索引鍵的預設值 `Invoke-Command:ComputerName` 會設定為數組值 **Server01** 和 **Server02** 。

```powershell
$PSDefaultParameterValues = @{
  "Invoke-Command:ComputerName"="Server01","Server02"
}
```

#### <a name="use-a-script-block"></a>使用腳本區塊

您可以使用腳本區塊，在不同的條件下為參數指定不同的預設值。 PowerShell 會評估腳本區塊，並使用結果作為預設參數值。

將 `Format-Table:AutoSize` 參數切換為預設值 **True** 的索引鍵集。 `If`語句包含 `$host.Name` 必須是 PowerShell 主控台 **ConsoleHost** 的條件。

```powershell
$PSDefaultParameterValues=@{
  "Format-Table:AutoSize"={if ($host.Name -eq "ConsoleHost"){$True}}
}
```

如果參數接受腳本區塊值，請將腳本區塊括在一組額外的大括弧中。 當 PowerShell 評估外部腳本區塊時，結果會是內部腳本區塊，並且會設定為預設參數值。

`Invoke-Command:ScriptBlock`因為腳本區塊是以第二組大括弧括住，所以索引鍵會設定為 **系統事件記錄** 檔的預設值。 腳本區塊的結果會傳遞至 `Invoke-Command` Cmdlet。

```powershell
$PSDefaultParameterValues=@{
  "Invoke-Command:ScriptBlock"={{Get-EventLog -Log System}}
}
```

### <a name="how-to-get-psdefaultparametervalues"></a>如何取得 \$ PSDefaultParameterValues

在 PowerShell 提示字元中輸入，即可顯示雜湊資料表值 `$PSDefaultParameterValues` 。

`$PSDefaultParameterValues`雜湊表會以三個索引 **鍵/值** 組來設定。
下列範例會使用此雜湊表，說明如何從加入、變更和移除值 `$PSDefaultParameterValues` 。

```
PS> $PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
  "Get-*:Verbose"=$True
}

PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

若要取得特定索引鍵的值 `CmdletName:ParameterName` ，請使用下列語法：

```
$PSDefaultParameterValues["CmdletName:ParameterName"]
```

例如，取得索引鍵的值 `Send-MailMessage:SmtpServer` 。

```
PS> $PSDefaultParameterValues["Send-MailMessage:SmtpServer"]
Server123
```

### <a name="how-to-add-values-to-psdefaultparametervalues"></a>如何將值新增至 \$ PSDefaultParameterValues

若要將值加入至 `$PSDefaultParameterValues` ，請使用 **add** 方法。 加入值並不會影響雜湊表的現有值。

使用逗號 (`,`) ，將索引 **鍵** 與 **值** 分隔開來。 下列語法顯示如何使用的 **Add** 方法 `$PSDefaultParameterValues` 。

```
PS> $PSDefaultParameterValues.Add("CmdletName:ParameterName", "DefaultValue")
```

先前範例中建立的雜湊表會以新的索引 **鍵/值** 組進行更新。 **Add** 方法會將 `Get-Process:Name` 金鑰設定為 **PowerShell** 的值。

```powershell
$PSDefaultParameterValues.Add("Get-Process:Name", "PowerShell")
```

下列語法會完成相同的結果。

```powershell
$PSDefaultParameterValues["Get-Process:Name"]="PowerShell"
```

`$PSDefaultParameterValues`變數會顯示更新的雜湊表。 `Get-Process:Name`已新增金鑰。

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-Process:Name               PowerShell
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-remove-values-from-psdefaultparametervalues"></a>如何從 PSDefaultParameterValues 中移除值 \$

若要從移除值 `$PSDefaultParameterValues` ，請使用雜湊表的 **移除** 方法。 移除值並不會影響雜湊表的現有值。

下列語法示範如何在上使用 **Remove** 方法 `$PSDefaultParameterValues` 。

```
PS> $PSDefaultParameterValues.Remove("CmdletName:ParameterName")
```

在此範例中，會更新在先前範例中建立的雜湊表，以移除索引 **鍵/值** 組。 **Remove** 方法會移除索引 `Get-Process:Name` 鍵。

```powershell
$PSDefaultParameterValues.Remove("Get-Process:Name")
```

`$PSDefaultParameterValues`變數會顯示更新的雜湊表。 已 `Get-Process:Name` 移除索引鍵。

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-change-values-in-psdefaultparametervalues"></a>如何變更 PSDefaultParameterValues 中的值 \$

對特定值所做的變更不會影響現有的雜湊資料表值。 若要變更中的特定索引 **鍵/值** 組 `$PSDefaultParameterValues` ，請使用下列語法：

```
PS> $PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

在此範例中，會更新在先前範例中建立的雜湊表來變更索引 **鍵/值** 組。 下列命令會將機 `Send-MailMessage:SmtpServer` 碼變更為 **ServerXYZ** 的新值。

```powershell
$PSDefaultParameterValues["Send-MailMessage:SmtpServer"]="ServerXYZ"
```

`$PSDefaultParameterValues`變數會顯示更新的雜湊表。 `Send-MailMessage:SmtpServer`金鑰已變更為新的值。

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

### <a name="how-to-disable-and-re-enable-psdefaultparametervalues"></a>如何停用和重新啟用 \$ PSDefaultParameterValues

您可以暫時停用再重新啟用 `$PSDefaultParameterValues` 。
`$PSDefaultParameterValues`如果您執行的腳本需要不同的預設參數值，則停用會很有用。

若要停 `$PSDefaultParameterValues` 用，請新增 `Disabled` 值為 **True** 的索引鍵。 中的值 `$PSDefaultParameterValues` 會保持不變，但無效。

```
PS> $PSDefaultParameterValues.Add("Disabled", $True)
```

下列語法會完成相同的結果。

```
PS> $PSDefaultParameterValues["Disabled"]=$True
```

`$PSDefaultParameterValues`變數會以索引鍵的值顯示已更新的雜湊資料表 `Disabled` 。

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       True
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

若要重新啟用 `$PSDefaultParameterValues` ，請移除 **已停用** 的金鑰，或將 **停用** 的索引鍵值變更為 `$False` 。 先前的值 `$PSDefaultParameterValues` 會再次生效。

```
PS> $PSDefaultParameterValues.Remove("Disabled")
```

下列語法會完成相同的結果。

```
PS> $PSDefaultParameterValues["Disabled"]=$False
```

`$PSDefaultParameterValues`變數會顯示更新的雜湊表。 使用 **Remove** 方法時， `Disabled` 會從輸出中移除索引鍵。
如果替代語法是用來重新啟用的 `$PSDefaultParameterValues` ，則索引 `Disabled` 鍵會顯示為 **False** 。

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       False
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

## <a name="see-also"></a>另請參閱

[about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Preference_Variables](about_Preference_Variables.md)

[about_Profiles](about_Profiles.md)

[about_Script_Blocks](about_Script_Blocks.md)

