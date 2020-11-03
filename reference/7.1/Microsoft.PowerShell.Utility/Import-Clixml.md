---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-clixml?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Clixml
ms.openlocfilehash: d33b74101301ec5806f456ddd9cc73bd8b6bb3e1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202775"
---
# Import-Clixml

## 概要
匯入 CLIXML 檔案，並在 PowerShell 中建立對應的物件。

## SYNTAX

### ByPath (預設值)

```
Import-Clixml [-Path] <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

### ByLiteralPath

```
Import-Clixml -LiteralPath <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

## DESCRIPTION

指令 `Import-Clixml` 程式會 (CLI) XML 檔案匯入通用語言基礎結構，其中包含代表 Microsoft .NET Framework 物件的資料，並建立 PowerShell 物件。 如需 CLI 的詳細資訊，請參閱 [語言獨立性](/dotnet/standard/language-independence)。

`Import-Clixml`在 Windows 電腦上有一個很重要的用途，就是匯入使用來匯出為安全 XML 的認證與安全字串 `Export-Clixml` 。 如需範例，請參閱範例2。

`Import-Clixml` 使用位元組順序標記 (BOM) 來偵測檔案的編碼格式。 如果檔案沒有 BOM，則會假設編碼為 UTF8。

## 範例

### 範例 1：匯出序列化的檔案並重新建立物件

這個範例會使用 `Export-Clixml` Cmdlet 來儲存所傳回之處理常式資訊的序列化複本 `Get-Process` 。 `Import-Clixml` 抓取序列化檔案的內容，並重新建立儲存在變數中的物件 `$Processes` 。

```powershell
Get-Process | Export-Clixml -Path .\pi.xml
$Processes = Import-Clixml -Path .\pi.xml
```

### 範例 2：匯入安全認證物件

在此範例中，藉由執行 Cmdlet 來儲存在變數中的認證 `$Credential` `Get-Credential` ，您可以執行 `Export-Clixml` Cmdlet 以將認證儲存至磁片。

> [!IMPORTANT]
> `Export-Clixml` 只會在 Windows 上匯出加密的認證。 在非 Windows 作業系統（例如 macOS 和 Linux）上，認證會以純文字格式匯出。

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

此 `Export-Clixml` Cmdlet 會使用 Windows [資料保護 API](/previous-versions/windows/apps/hh464970(v=win.10))來加密認證物件。
加密可確保只有您的使用者帳戶可以解密 credential 物件的內容。 匯出的檔案 `CLIXML` 不能用於不同的電腦或不同的使用者。

在此範例中，用來儲存認證的檔案會以表示 `TestScript.ps1.credential` 。 將 **>testscript** 取代為您要用來載入認證的腳本名稱。

您會將管線下的認證物件傳送至 `Export-Clixml` ，並將它儲存到 `$Credxmlpath` 您在第一個命令中指定的路徑。

若要將認證自動匯入至您的指令碼，請執行最後兩個命令。 執行 `Import-Clixml` 以將安全的認證物件匯入您的腳本中。 這項匯入消除了在腳本中公開純文字密碼的風險。

## PARAMETERS

### -First

只取得指定數目的物件。 輸入要取得的物件數目。

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeTotalCount

報告資料集中的物件總數，後面接著選取的物件。 如果 Cmdlet 無法判斷總數，則會顯示不明的 **總計數** 。 整數具有 **精確度** 屬性，指出 total count 值的可靠性。 **精確度** 的值範圍從 `0.0` 到 `1.0` where `0.0` 表示 Cmdlet 無法計算物件數目， `1.0` 表示計數是精確的，而介於之間的值則 `0.0` `1.0` 表示逐漸可靠的估計值。

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

### -LiteralPath

指定 XML 檔案的路徑。 與 **Path** 不同， **LiteralPath** 參數的值會完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定 XML 檔案的路徑。

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Skip

略過指定的物件數目，並取得剩餘的物件。 輸入要略過的物件數目。

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將包含路徑的字串管線 `Import-Clixml` 。

## 輸出

### PSObject

`Import-Clixml` 傳回已從儲存的 XML 檔案還原序列化的物件。

## 注意

當指定參數的多個值時，請使用逗號分隔值。 例如： `<parameter-name> <value1>, <value2>` 。

## 相關連結

[Export-Clixml](Export-Clixml.md)

[XML 序列化簡介](/dotnet/standard/serialization/introducing-xml-serialization)

[Join-Path](../Microsoft.PowerShell.Management/Join-Path.md)

[將認證安全地儲存在磁碟上](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[使用 PowerShell 將認證傳遞給舊版系統](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

