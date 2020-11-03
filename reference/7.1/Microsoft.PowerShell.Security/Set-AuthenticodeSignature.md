---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-authenticodesignature?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-AuthenticodeSignature
ms.openlocfilehash: d4bddfb506a86cb36e61f94cabf6e24fadaed527
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202447"
---
# Set-AuthenticodeSignature

## 概要
將 [Authenticode](/windows-hardware/drivers/install/authenticode) 簽章新增至 PowerShell 腳本或其他檔案。

## SYNTAX

### ByPath (預設值)

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] [-FilePath] <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -LiteralPath <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByContent

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -SourcePathOrExtension <String[]>
 -Content <Byte[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Set-AuthenticodeSignature`Cmdlet 會將 Authenticode 簽章新增至任何支援主體介面套件 (SIP) 的檔案。

在 PowerShell 腳本檔案中，簽章會採用文字區塊的形式，指出腳本中執行的指示結尾。 如果執行此 Cmdlet 時檔案中有簽章，會移除該簽章。

## 範例

### 範例 1-使用本機憑證存放區中的憑證簽署腳本

這些命令會從 PowerShell 憑證提供者取得程式碼簽署憑證，並使用它來簽署 PowerShell 腳本。

```powershell
$cert=Get-ChildItem -Path Cert:\CurrentUser\My -CodeSigningCert
Set-AuthenticodeSignature -FilePath PsTestInternet2.ps1 -Certificate $cert
```

第一個命令會使用 `Get-ChildItem` Cmdlet 和 PowerShell 憑證提供者取得 `Cert:\CurrentUser\My` 憑證存放區之子目錄中的憑證。 `Cert:`磁片磁碟機是憑證提供者所公開的磁片磁碟機。 只有憑證提供者支援的 **CodeSigningCert** 參數，會將抓取的憑證限制為具有程式碼簽署授權單位的憑證。 命令會將結果儲存在 `$cert` 變數中。

第二個命令會使用 `Set-AuthenticodeSignature` Cmdlet 來簽署 `PSTestInternet2.ps1` 腳本。 它會使用 **FilePath** 參數指定腳本的名稱，以及使用 **certificate** 參數指定憑證儲存在 `$cert` 變數中。

> [!NOTE]
> 使用 **CodeSigningCert** 參數 `Get-ChildItem` 只會傳回具有程式碼簽署授權單位且包含私密金鑰的憑證。 如果沒有私密金鑰，則憑證無法用於簽署。

### 範例 2-使用 PFX 檔案中的憑證簽署腳本

這些命令會使用 `Get-PfxCertificate` Cmdlet 載入程式碼簽署憑證。 然後，使用它來簽署 PowerShell 腳本。

```powershell
$cert = Get-PfxCertificate -FilePath C:\Test\Mysign.pfx
Set-AuthenticodeSignature -FilePath ServerProps.ps1 -Certificate $cert
```

第一個命令會使用 `Get-PfxCertificate` Cmdlet 將 C:\Test\MySign.pfx 憑證載入到變數中 `$cert` 。

第二個命令會使用 `Set-AuthenticodeSignature` 來簽署腳本。 的 **FilePath** 參數 `Set-AuthenticodeSignature` 指定要簽署的腳本檔案的路徑，而 **Cert** 參數則會將 `$cert` 包含憑證的變數傳遞給 `Set-AuthenticodeSignature` 。

如果憑證檔案有密碼保護，則 PowerShell 會提示您輸入密碼。

### 範例 3-新增包含根授權單位的簽章

此命令在信任鏈結中加入包含根授權單位的數位簽章，並由協力廠商的時間戳記伺服器進行簽署。

```powershell
Set-AuthenticodeSignature -FilePath c:\scripts\Remodel.ps1 -Certificate $cert -IncludeChain All -TimestampServer "http://timestamp.fabrikam.com/scripts/timstamper.dll"
```

此命令會使用 **FilePath** 參數指定要簽署的腳本，以及使用 **certificate** 參數指定儲存在變數中的憑證 `$cert` 。 它使用 **IncludeChain** 參數來包含信任鏈中的所有簽章，包括根授權單位。 它也會使用 **TimeStampServer** 參數將時間戳記加入簽章。
這可防止指令碼在憑證過期時失敗。

## PARAMETERS

### -Certificate

指定要用來簽署指令碼或檔案的憑證。 輸入儲存代表憑證之物件的變數，或取得憑證的運算式。

若要尋找憑證，請使用 `Get-PfxCertificate` 或使用 `Get-ChildItem` 憑證磁片磁碟機中的 Cmdlet `Cert:` 。 若憑證無效或沒有 `code-signing` 授權單位，則命令會失敗。

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定要簽署的檔案路徑。

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Force

可讓 Cmdlet 將簽章附加到唯讀檔案。 即使使用 **Force** 參數，Cmdlet 也無法覆寫安全性限制。

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

### -HashAlgorithm

指定 Windows 用來計算檔案數位簽章的雜湊演算法。

針對 PowerShell 3.0，預設值是 SHA256，這是 Windows 預設的雜湊演算法。 針對 PowerShell 2.0，預設值為 SHA1。 在其他系統上可能無法辨識以不同雜湊演算法所簽署的檔案。 支援哪些演算法取決於作業系統的版本。

如需可能值的清單，請參閱 [HashAlgorithmName 結構](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties)。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SHA256
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeChain

判斷數位簽章中包含憑證信任鏈結中的哪個憑證。
預設值為 **NotRoot** 。

有效值為：

- Signer：只包含簽署者的憑證。
- NotRoot：包含憑證鏈結中 (除了根授權單位) 的所有憑證。
- 全部：包含憑證鏈中的所有憑證。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: NotRoot
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimestampServer

使用指定的時間戳記伺服器將時間戳記加入簽章。 以字串方式輸入時間戳記伺服器的 URL。

時間戳記代表憑證加入檔案的確切時間。 如果憑證過期，時間戳記會防止指令碼失敗，因為使用者和程式可以驗證憑證在簽署時是有效的。

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

### -LiteralPath

指定要簽署的檔案路徑。 **LiteralPath** 參數值與 **FilePath** 不同，會完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourcePathOrExtension

加入數位簽章之內容的檔案或檔案類型路徑。 此參數會搭配將檔案內容當做位元組陣列傳遞的 **內容** 使用。

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Content

檔案的內容，做為加入數位簽章的位元組陣列。 此參數必須搭配 **SourcePathOrExtension** 參數使用。 檔案內容的格式必須是 Unicode (UTF-16LE) 格式。

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

在執行 Cmdlet 前提示您確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。 Cmdlet 並不會執行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

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

您可以使用管線將包含檔案路徑的字串傳送至 `Set-AuthenticodeSignature` 。

## 輸出

### System.Management.Automation.Signature

## 注意

## 相關連結

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Get-executionpolicy](Get-ExecutionPolicy.md)

[Get-PfxCertificate](Get-PfxCertificate.md)

[Set-ExecutionPolicy](Set-ExecutionPolicy.md)

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)

