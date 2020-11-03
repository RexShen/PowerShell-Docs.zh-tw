---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-PSSessionConfigurationFile
ms.openlocfilehash: e64565cbc567ca42b190e143e065f9eddba2f311
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201196"
---
# Test-PSSessionConfigurationFile

## 概要
驗證工作階段設定檔中的索引鍵和值。

## SYNTAX

```
Test-PSSessionConfigurationFile [-Path] <String> [<CommonParameters>]
```

## DESCRIPTION

此 Cmdlet 會驗證會話設定檔包含有效的金鑰，而且值的類型是正確的。 對於列舉的值，此 Cmdlet 會驗證指定的值是否有效。

`$True`如果檔案通過所有測試，則 Cmdlet 會傳回， `$False` 否則會傳回。 若要尋找任何錯誤，請使用 **Verbose** 參數。

`Test-PSSessionConfigurationFile` 驗證會話設定檔，例如 Cmdlet 所建立的設定檔 `New-PSSessionConfigurationFile` 。 如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。 如需會話設定檔的詳細資訊，請參閱 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。

此 Cmdlet 是在 PowerShell 3.0 中引進。

## 範例

### 範例 1：測試工作階段設定檔

```powershell
Test-PSSessionConfigurationFile -Path "FullLanguage.pssc"
```

```Output
True
```

### 範例 2：測試工作階段設定的工作階段設定檔

在此範例中，我們會測試 **受限制** 會話設定中使用的設定檔。
**Path** 參數的值是命令的結果 `Get-PSSessionConfiguration` ，此命令會取得 **受限制** 的會話設定。 工作階段設定檔的路徑儲存在工作階段設定之 **ConfigFilePath** 屬性的值中。

```powershell
Test-PSSessionConfigurationFile -Path (Get-PSSessionConfiguration -Name Restricted).ConfigFilePath
```

### 範例 3：測試所有工作階段設定檔

此範例中的函數會測試本機電腦上的所有會話設定檔。 函數會使用 `Get-PSSessionConfiguration` Cmdlet 來取得所有會話設定。 迴圈內的程式碼會 `ForEach-Object` 顯示檔案路徑，並測試每個會話設定。

```powershell
function Test-AllConfigFiles
{
    Get-PSSessionConfiguration | ForEach-Object {
        if ($_.ConfigFilePath) {
            $_.ConfigFilePath
            Test-PSSessionConfigurationFile -Verbose -Path $_.ConfigFilePath
        }
    }
}
Test-AllConfigFiles
```

```Output
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Empty_6fd77bf6-e084-4372-bd8a-af3e207354d3.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
VERBOSE: The member 'AliasDefinitions' must contain the required key 'Description'. Add the require key
to the fileC:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc.
False
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RestrictedLang_b6bd9474-0a6c-4e06-8722-c2c95bb10d3e.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RRS_3fb29420-2c87-46e5-a402-e21436331efc.pssc
True
```

工作階段設定的 **ConfigFilePath** 屬性包含在工作階段設定中使用之工作階段設定檔的路徑 (如果有的話)。

如果已填入 **ConfigFilePath** 屬性的值 (為 True)，此命令會取得 (印出) **ConfigFilePath** 屬性的值。 然後，它會使用 `Test-PSSessionConfigurationFile` Cmdlet 來測試 **ConfigFilePath** 值中的檔案。 當檔案無法通過測試時， **Verbose** 參數會傳回檔案錯誤。

## PARAMETERS

### -Path

指定會話設定檔的路徑和檔案名 (. .pssc) 。 若省略路徑，則預設為目前資料夾。 支援使用萬用字元，但它們必須解析為單一檔案。 您也可以使用管線將會話設定檔路徑傳送至 `Test-PSSessionConfigurationFile` 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將會話設定檔路徑傳送至 `Test-PSSessionConfigurationFile` 。

## 輸出

### System.Boolean

## 注意

## 相關連結

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 提供者](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
