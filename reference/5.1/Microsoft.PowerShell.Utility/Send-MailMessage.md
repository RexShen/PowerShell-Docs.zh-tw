---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Send-MailMessage
ms.openlocfilehash: 6f98c95e6c0144f76393e9d28454833097894512
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203147"
---
# Send-MailMessage

## 概要
傳送電子郵件訊息。

## SYNTAX

### 全部

```
Send-MailMessage [-To] <string[]> [-Subject] <string> [[-Body] <string>] [[-SmtpServer] <string>]
 -From <string> [-Attachments <string[]>] [-Bcc <string[]>] [-BodyAsHtml] [-Encoding <Encoding>]
 [-Cc <string[]>] [-DeliveryNotificationOption <DeliveryNotificationOptions>]
 [-Priority <MailPriority>] [-Credential <pscredential>] [-UseSsl] [-Port <int>]
 [<CommonParameters>]
```

## DESCRIPTION

`Send-MailMessage`Cmdlet 會從 PowerShell 內傳送電子郵件訊息。

您必須指定 Simple Mail Transfer Protocol (SMTP) server，否則 `Send-MailMessage` 命令會失敗。 使用 **SmtpServer** 參數或將變數設定 `$PSEmailServer` 為有效的 SMTP 伺服器。
指派給的值 `$PSEmailServer` 是 PowerShell 的預設 SMTP 設定。 如需詳細資訊，請參閱 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。

> [!WARNING]
> `Send-MailMessage`Cmdlet 已淘汰。 此 Cmdlet 不保證 SMTP 伺服器的安全連線。 雖然 PowerShell 沒有立即可用的取代功能，但我們建議您不要使用 `Send-MailMessage` 。 如需詳細資訊，請參閱 [平臺相容性注意事項 DE0005](https://aka.ms/SendMailMessage)。

## 範例

### 範例1：將電子郵件從一個人傳送給另一個人

此範例會將一則電子郵件訊息傳送給其他人。

需要 **From** 、 **To** 和 **Subject** 參數 `Send-MailMessage` 。 此範例 `$PSEmailServer` 會使用 SMTP 伺服器的預設變數，所以不需要 **SmtpServer** 參數。

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>' -Subject 'Test mail'
```

此 `Send-MailMessage` Cmdlet 會使用 **From** 參數來指定訊息的寄件者。 **To** 參數會指定訊息的收件者。 **Subject** 參數會使用文字字串 **測試郵件** 做為訊息，因為不包含選擇性的 **Body** 參數。

### 範例2：傳送附件

此範例會傳送含有附件的電子郵件訊息。

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>', 'User03 <user03@fabrikam.com>' -Subject 'Sending the Attachment' -Body "Forgot to send the attachment. Sending now." -Attachments .\data.csv -Priority High -DeliveryNotificationOption OnSuccess, OnFailure -SmtpServer 'smtp.fabrikam.com'
```

此 `Send-MailMessage` Cmdlet 會使用 **From** 參數來指定訊息的寄件者。 **To** 參數會指定訊息的收件者。 **Subject** 參數描述訊息的內容。 **Body** 參數是訊息的內容。

**附件** 參數會指定目前目錄中附加至電子郵件訊息的檔案。 **Priority** 參數會將訊息設定為 **高** 優先順序。 **-DeliveryNotificationOption** 參數會指定 **OnSuccess** 和 **OnFailure** 這兩個值。 寄件者將會收到電子郵件通知，以確認訊息傳遞成功或失敗。
**SmtpServer** 參數會將 SMTP 伺服器設定為 **smtp.fabrikam.com** 。

### 範例3：將電子郵件傳送至郵寄清單

此範例會將電子郵件訊息傳送至郵寄清單。

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'ITGroup <itdept@fabrikam.com>' -Cc 'User02 <user02@fabrikam.com>' -Bcc 'ITMgr <itmgr@fabrikam.com>' -Subject "Don't forget today's meeting!" -Credential domain01\admin01 -UseSsl
```

此 `Send-MailMessage` Cmdlet 會使用 **From** 參數來指定訊息的寄件者。 **To** 參數會指定訊息的收件者。 **Cc** 參數會將訊息的副本傳送給指定的收件者。 **密件副本** 參數會傳送訊息的密件副本。 密件複製是由其他收件者隱藏的電子郵件地址。 **Subject** 參數是訊息，因為不包含選用的 **Body** 參數。

**Credential** 參數會指定用來傳送訊息的網域系統管理員認證。 **UseSsl** 參數會指定安全通訊端層 (SSL) 建立安全連線。

## PARAMETERS

### -Attachments

指定要附加至電子郵件訊息之檔案的路徑和檔案名。 您可以使用此參數，或使用管線將路徑和檔案名傳送至 `Send-MailMessage` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PsPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Bcc

指定可接收郵件副本但未列為訊息收件者的電子郵件地址。 輸入 (選用) 和電子郵件地址的名稱，例如 `Name <someone@fabrikam.com>` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Body

指定電子郵件訊息的內容。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BodyAsHtml

指定 **Body** 參數的值包含 HTML。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: BAH

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Cc

指定傳送電子郵件訊息副本 (副本) 的電子郵件地址。 輸入 (選用) 和電子郵件地址的名稱，例如 `Name <someone@fabrikam.com>` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定具有執行此動作權限的使用者帳戶。 預設為目前使用者。

輸入使用者名稱，例如 **User01** 或 **Domain01\User01** 。 或者，輸入 **PSCredential** 物件，例如 Cmdlet 中的物件 `Get-Credential` 。

認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DeliveryNotificationOption

指定電子郵件訊息的傳遞通知選項。 您可以指定多個值。
None 是預設值。 這個參數的別名是 **DNO** 。

傳遞通知會傳送至 **From** 參數中的位址。

此參數可接受的值如下：

- `None`：沒有通知。
- `OnSuccess`：如果傳遞成功，便通知。
- `OnFailure`：如果傳遞失敗，請通知。
- `Delay`：通知是否延遲傳遞。
- `Never`：永不通知。

```yaml
Type: System.Net.Mail.DeliveryNotificationOptions
Parameter Sets: (All)
Aliases: DNO
Accepted values: None, OnSuccess, OnFailure, Delay, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

指定目標檔案的編碼類型。 預設值是 `Default`。

此參數可接受的值如下：

- `ASCII` 使用 ASCII (7 位) 字元集。
- `BigEndianUnicode` 以位元組由大到小的順序使用 UTF-16。
- `Default` 使用與系統的作用中字碼頁對應的編碼， (通常是 ANSI) 。
- `OEM` 使用對應至系統目前 OEM 字碼頁的編碼方式。
- `Unicode` 使用 UTF-16 和位元組由小到小的位元組順序。
- `UTF7` 使用 UTF-7。
- `UTF8` 使用 UTF-8。
- `UTF32` 以位元組由小到大的位元組順序使用 UTF-32。

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases: BE
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -From

需要 **From** 參數。 此參數會指定寄件者的電子郵件地址。 輸入 (選用) 和電子郵件地址的名稱，例如 `Name <someone@fabrikam.com>` 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

指定 SMTP 伺服器上的替代連接埠。 預設值為 25，這是預設的 SMTP 連接埠。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 25
Accept pipeline input: False
Accept wildcard characters: False
```

### -Priority

指定電子郵件訊息的優先順序。 預設值為 Normal。 此參數可接受的值為 Normal、High 及 Low。

```yaml
Type: System.Net.Mail.MailPriority
Parameter Sets: (All)
Aliases:
Accepted values: Normal, High, Low

Required: False
Position: Named
Default value: Normal
Accept pipeline input: False
Accept wildcard characters: False
```

### -SmtpServer

指定傳送電子郵件訊息的 SMTP 伺服器名稱。

預設值為喜好設定變數的值 `$PSEmailServer` 。 如果未設定喜好設定變數，且未使用此參數，則 `Send-MailMessage` 命令會失敗。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ComputerName

Required: False
Position: 3
Default value: $PSEmailServer
Accept pipeline input: False
Accept wildcard characters: False
```

### -Subject

需要 **Subject** 參數。 此參數會指定電子郵件訊息的主旨。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sub

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -To

需要 **參數。** 此參數會指定收件者的電子郵件地址。 如果有多個收件者，請以逗號分隔其位址 (`,`) 。 輸入 (選用) 和電子郵件地址的名稱，例如 `Name <someone@fabrikam.com>` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSsl

安全通訊端層 (SSL) 通訊協定是用來建立遠端電腦的安全連線，以傳送郵件。 預設不會使用 SSL。

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

### System.String

您可以透過管道將附件的路徑和檔案名傳送至 `Send-MailMessage` 。

## 輸出

### 無

此 Cmdlet 不會產生任何輸出。

## 注意

## 相關連結

[about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)
