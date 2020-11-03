---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 07/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SecureString
ms.openlocfilehash: 4bbdab62168a7306bb02d0ac47b5513d23920814
ms.sourcegitcommit: b7ff031a12afd04910aeb98345ebee92f5845b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "93205795"
---
# ConvertFrom-SecureString

## 概要
將安全字串轉換成加密標準字串。

## SYNTAX

### Secure (預設值)

```
ConvertFrom-SecureString [-SecureString] <SecureString> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### AsPlainText

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-AsPlainText] [<CommonParameters>]
```

### 開啟

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-Key <Byte[]>] [<CommonParameters>]
```

## DESCRIPTION

**Convertfrom-string-SecureString** 指令程式會將安全字串 ( **SecureString** ) 轉換成加密標準字串， ( **system.string** ) 。 與安全字串不同，加密標準字串可以儲存在檔案中供日後使用。 您可以使用 Cmdlet，將加密的標準字串轉換回其安全字串格式 `ConvertTo-SecureString` 。

如果是使用 **Key** 或 **SecureKey** 參數來指定加密金鑰，便會使用「進階加密標準」(AES) 加密演算法。 指定之金鑰的長度必須為 128、192 或 256 個位元，因為這些是 AES 加密演算法所支援的金鑰長度。 如果未指定任何金鑰，則會使用「Windows 資料保護 API」(DPAPI) 來加密標準字串表示法。

> [!NOTE]
> 請注意，在非 Windows 系統上，每個 [DotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks)都不會加密 SecureString 的內容。

## 範例

### 範例 1︰建立安全字串

```powershell
$SecureString = Read-Host -AsSecureString
```

這個命令會從您在命令提示字元中輸入的字元建立安全字串。 輸入命令之後，請輸入您想要儲存為安全字串的字串。 `*`會顯示星號 () ，以代表您輸入的每個字元。

### 範例 2︰將安全字串轉換成加密標準字串

```powershell
$StandardString = ConvertFrom-SecureString $SecureString
```

此命令會將變數中的安全字串轉換 `$SecureString` 成加密的標準字串。 產生的加密標準字串會儲存在 `$StandardString` 變數中。

### 範例 3︰將安全字串轉換成使用 192 位元金鑰的加密標準字串

```powershell
$Key = (3,4,2,3,56,34,254,222,1,1,2,23,42,54,33,233,1,34,2,7,6,5,35,43)
$StandardString = ConvertFrom-SecureString $SecureString -Key $Key
```

這些命令會使用進階加密標準 (AES) 演算法，將儲存在變數中的安全字串轉換成 `$SecureString` 具有192位金鑰的加密標準字串。 產生的加密標準字串會儲存在 `$StandardString` 變數中。

第一個命令會將金鑰儲存在 `$Key` 變數中。 金鑰是24個十進位數的陣列，每個數位都必須小於256，才能納入單一不帶正負號的位元組內。

因為每個十進位數都代表單一位元組 (8 個位) ，所以索引鍵有24位數，總共192位 (8 x 24) 。 這是 AES 演算法的有效金鑰長度。

第二個命令會使用變數中的索引鍵 `$Key` ，將安全字串轉換成加密標準字串。

### 範例4：將安全字串直接轉換為純文字字串

```powershell
$secureString = ConvertTo-SecureString -String 'Example' -AsPlainText
$secureString # 'System.Security.SecureString'
ConvertFrom-SecureString -SecureString $secureString -AsPlainText # 'Example'
```

## PARAMETERS

### -AsPlainText

設定時， `ConvertFrom-SecureString` 會將安全字串轉換成解密的純文字字串作為輸出。

此辨識已新增至 PowerShell 7.0。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsPlainText
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Key

將加密金鑰指定為位元組陣列。

```yaml
Type: System.Byte[]
Parameter Sets: Open
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecureKey

將加密金鑰指定為安全字串。 安全字串值在被當作金鑰使用之前，會先轉換成位元組陣列。

```yaml
Type: System.Security.SecureString
Parameter Sets: Secure
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecureString

指定要轉換成加密標準字串的安全字串。

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。
如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Security.SecureString

您可以使用管線將 **SecureString** 物件傳送至 Convertfrom-string-SecureString。

## 輸出

### System.String

ConvertFrom-SecureString 會傳回標準字串物件。

## 注意

- 若要從命令提示字元輸入的字元建立安全字串，請使用 Cmdlet 的 **AsSecureString** 參數 `Read-Host` 。
- 當您使用 **key** 或 **SecureKey** 參數來指定金鑰時，金鑰長度必須正確。 例如，可以將128位的索引鍵指定為16個小數位數的位元組陣列。
  同樣地，192位和256位的金鑰會分別對應至24和32十進位數的位元組陣列。
- 某些字元（例如圖釋）會對應至包含它們的字串中的數個程式碼點。 請避免使用這些字元，因為它們在密碼中使用時可能會造成問題和誤解。

## 相關連結

[ConvertTo-SecureString](ConvertTo-SecureString.md)

[Read-Host](../Microsoft.PowerShell.Utility/Read-Host.md)
