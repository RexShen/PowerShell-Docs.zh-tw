---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertto-securestring?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-SecureString
ms.openlocfilehash: e3ee17ed9c309a02bf2032c039adacf12ccff04f
ms.sourcegitcommit: df80c558e9a4b89c9798f084bd04012ece15155c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2020
ms.locfileid: "93208848"
---
# ConvertTo-SecureString

## 概要
將純文字或加密字串轉換成安全字串。

## SYNTAX

### Secure (預設值)

```
ConvertTo-SecureString [-String] <String> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### PlainText

```
ConvertTo-SecureString [-String] <String> [-AsPlainText] [-Force] [<CommonParameters>]
```

### 開啟

```
ConvertTo-SecureString [-String] <String> [-Key <Byte[]>] [<CommonParameters>]
```

## DESCRIPTION

此 `ConvertTo-SecureString` Cmdlet 會將加密的標準字串轉換成安全字串。 它也可以將純文字轉換成安全字串。 它會搭配 `ConvertFrom-SecureString` 和使用 `Read-Host` 。 Cmdlet 所建立的安全字串可搭配需要 **SecureString** 類型之參數的 Cmdlet 或函式使用。 您可以使用 Cmdlet，將安全字串轉換回加密的標準字串 `ConvertFrom-SecureString` 。 這可讓它儲存在檔案中以供日後使用。

如果要轉換的標準字串使用 `ConvertFrom-SecureString` 指定的金鑰進行加密，則必須提供該相同的金鑰作為 Cmdlet 的 **Key** 或 **SecureKey** 參數值 `ConvertTo-SecureString` 。

> [!NOTE]
> 請注意，在非 Windows 系統上，每個 [DotNet](/dotnet/api/system.security.securestring#remarks)都不會加密 SecureString 的內容。

## 範例

### 範例1：將安全字串轉換成加密字串

此範例顯示如何從使用者輸入建立安全字串、將安全字串轉換成加密的標準字串，然後再將加密的標準字串轉換回安全字串。

```powershell
PS C:\> $Secure = Read-Host -AsSecureString
PS C:\> $Secure
System.Security.SecureString
PS C:\> $Encrypted = ConvertFrom-SecureString -SecureString $Secure
PS C:\> $Encrypted
01000000d08c9ddf0115d1118c7a00c04fc297eb010000001a114d45b8dd3f4aa11ad7c0abdae98000000000
02000000000003660000a8000000100000005df63cea84bfb7d70bd6842e7efa79820000000004800000a000
000010000000f10cd0f4a99a8d5814d94e0687d7430b100000008bf11f1960158405b2779613e9352c6d1400
0000e6b7bf46a9d485ff211b9b2a2df3bd6eb67aae41
PS C:\> $Secure2 = ConvertTo-SecureString -String $Encrypted
PS C:\> $Secure2
System.Security.SecureString
```

第一個命令會使用 Cmdlet 的 **AsSecureString** 參數 `Read-Host` 來建立安全字串。 輸入命令之後，您輸入的任何字元都會轉換成安全字串，然後儲存在 `$Secure` 變數中。

第二個命令會顯示變數的內容 `$Secure` 。 因為 `$Secure` 變數包含安全字串，所以 PowerShell 只會顯示 **SecureString** 類型。

第三個命令會使用 `ConvertFrom-SecureString` Cmdlet 將變數中的安全字串轉換 `$Secure` 成加密標準字串。 它會將結果儲存在 `$Encrypted` 變數中。

第四個命令會在變數的值中顯示加密字串 `$Encrypted` 。

第五個命令會使用 `ConvertTo-SecureString` Cmdlet 將變數中的加密標準字串轉換 `$Encrypted` 回安全字串。 它會將結果儲存在 `$Secure2` 變數中。
第六個命令會顯示變數的值 `$Secure2` 。 SecureString 類型表示命令已成功。

### 範例2：從檔案中的加密字串建立安全字串

此範例顯示如何從儲存在檔案中之加密標準字串建立安全字串。

```powershell
$Secure = Read-Host -AsSecureString
$Encrypted = ConvertFrom-SecureString -SecureString $Secure -Key (1..16)
$Encrypted | Set-Content Encrypted.txt
$Secure2 = Get-Content Encrypted.txt | ConvertTo-SecureString -Key (1..16)
```

第一個命令會使用 Cmdlet 的 **AsSecureString** 參數 `Read-Host` 來建立安全字串。 輸入命令之後，您輸入的任何字元都會轉換成安全字串，然後儲存在 `$Secure` 變數中。

第二個命令會使用 `ConvertFrom-SecureString` Cmdlet 將變數中的安全字串轉換 `$Secure` 成加密的標準字串，方法是使用指定的索引鍵。 內容會儲存在變數中 `$Encrypted` 。

第三個命令會使用管線運算子 (`|`) 將變數的值傳送 `$Encrypted` 至 `Set-Content` Cmdlet，以將值儲存在 Encrypted.txt 檔案中。

第四個命令會使用 `Get-Content` Cmdlet 取得 Encrypted.txt 檔案中的加密標準字串。 此命令會使用管線運算子將加密的字串傳送至 `ConvertTo-SecureString` Cmdlet，此 Cmdlet 會使用指定的金鑰將它轉換為安全字串。
結果會儲存在變數中 `$Secure2` 。

### 範例3：將純文字字串轉換成安全字串

此命令會將純文字字串轉換 `P@ssW0rD!` 成安全字串，並將結果儲存在 `$Secure_String_Pwd` 變數中。 若要使用 **AsPlainText** 參數， **Force** 參數也必須包含在命令中。

```powershell
$Secure_String_Pwd = ConvertTo-SecureString "P@ssW0rD!" -AsPlainText -Force
```

> [!CAUTION]
> 您應該避免在腳本中或從命令列使用純文字字串。 純文字可能會顯示在事件記錄檔和命令歷程記錄中。

## PARAMETERS

### -AsPlainText

指定要轉換成安全字串的純文字字串。 安全字串 Cmdlet 有助於保護機密文字。 為保有隱私，文字會加密，而且在使用後會從電腦記憶體中刪除。 如果您使用此參數提供純文字做為輸入，系統就無法以此種方式保護保護該輸入。 若要使用此參數，您也必須指定 **Force** 參數。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

確認您瞭解使用 **AsPlainText** 參數的含意，並仍想使用它。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Key

指定用來將原始安全字串轉換成加密標準字串的加密金鑰。 有效的金鑰長度為16、24和32個位元組。

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

指定用來將原始安全字串轉換成加密標準字串的加密金鑰。 金鑰需以安全字串的格式提供。 安全字串將會轉換成要當做金鑰使用的位元組陣列。 有效的安全金鑰長度為8、12和16個程式碼點。

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

### -String

指定要轉換成安全字串的字串。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將標準加密字串傳送至 `ConvertTo-SecureString` 。

## 輸出

### System.Security.SecureString

`ConvertTo-SecureString` 傳回 **SecureString** 物件。

## 注意

某些字元（例如圖釋）會對應至包含它們的字串中的數個程式碼點。 請避免使用這些字元，因為它們在密碼中使用時可能會造成問題和誤解。

## 相關連結

[ConvertFrom-SecureString](ConvertFrom-SecureString.md)

[Read-Host](../Microsoft.PowerShell.Utility/Read-Host.md)
