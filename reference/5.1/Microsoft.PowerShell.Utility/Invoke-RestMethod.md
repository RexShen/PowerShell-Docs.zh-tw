---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/13/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-RestMethod
ms.openlocfilehash: c89f7351e9c874cea2cc0cd5e0912e3ca0d8b0bf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203208"
---
# Invoke-RestMethod

## 概要
傳送 HTTP 或 HTTPS 要求至 RESTful Web 服務。

## 語法

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-CertificateThumbprint <String>] [-Certificate <X509Certificate>]
 [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>] [-Headers <IDictionary>]
 [-MaximumRedirection <Int32>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials]
 [-Body <Object>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>]
 [-PassThru] [<CommonParameters>]
```

## 描述

`Invoke-RestMethod`指令程式會將 HTTP 和 HTTPS 要求傳送至具象狀態傳輸 (REST) web 服務，以傳回豐富的結構化資料。

Windows PowerShell 會根據資料類型設定回應格式。 對於 RSS 或 ATOM 摘要，Windows PowerShell 會傳回項目 XML 節點。 對於 JavaScript Object Notation (JSON) 或 XML，Windows PowerShell 會將內容轉換 (或還原序列化) 為物件。

此 Cmdlet 是在 Windows PowerShell 3.0 引進。

> [!NOTE]
> 根據預設，當剖析頁面以填入屬性時，可能會執行網頁中的腳本程式碼 `ParsedHtml` 。 使用 **UseBasicParsing** 參數來隱藏此。

## 範例

### 範例1：取得 PowerShell RSS 摘要

```powershell
Invoke-RestMethod -Uri https://devblogs.microsoft.com/powershell/feed/ |
  Format-Table -Property Title, pubDate
```

```Output
Title                                                                pubDate
-----                                                                -------
Join the PowerShell 10th Anniversary Celebration!                    Tue, 08 Nov 2016 23:00:04 +0000
DSC Resource Kit November 2016 Release                               Thu, 03 Nov 2016 00:19:07 +0000
PSScriptAnalyzer Community Call - Oct 18, 2016                       Thu, 13 Oct 2016 17:52:35 +0000
New Home for In-Box DSC Resources                                    Sat, 08 Oct 2016 07:13:10 +0000
New Social Features on Gallery                                       Fri, 30 Sep 2016 23:04:34 +0000
PowerShellGet and PackageManagement in PowerShell Gallery and GitHub Thu, 29 Sep 2016 22:21:42 +0000
PowerShell Security at DerbyCon                                      Wed, 28 Sep 2016 01:13:19 +0000
DSC Resource Kit September Release                                   Thu, 22 Sep 2016 00:25:37 +0000
PowerShell DSC and implicit remoting broken in KB3176934             Tue, 23 Aug 2016 15:07:50 +0000
PowerShell on Linux and Open Source!                                 Thu, 18 Aug 2016 15:32:02 +0000
```

此命令會使用 `Invoke-RestMethod` Cmdlet 來取得來自 PowerShell BLOG rss 摘要的資訊。 此命令會使用 `Format-Table` Cmdlet，在資料表中顯示每個 blog 的 **Title** 和 **pubDate** 屬性的值。

### 範例 2

在下列範例中，使用者會 `Invoke-RestMethod` 執行，以在使用者組織內部網路網站上執行 POST 要求。

```powershell
$Cred = Get-Credential

# Next, allow the use of self-signed SSL certificates.

[System.Net.ServicePointManager]::ServerCertificateValidationCallback = { $True }

# Create variables to store the values consumed by the Invoke-RestMethod command.
# The search variable contents are later embedded in the body variable.

$Server = 'server.contoso.com'
$Url = "https://${server}:8089/services/search/jobs/export"
$Search = "search index=_internal | reverse | table index,host,source,sourcetype,_raw"

# The cmdlet handles URL encoding. The body variable describes the search criteria, specifies CSV as
# the output mode, and specifies a time period for returned data that starts two days ago and ends
# one day ago. The body variable specifies values for parameters that apply to the particular REST
# API with which Invoke-RestMethod is communicating.

$Body = @{
    search = $Search
    output_mode = "csv"
    earliest_time = "-2d@d"
    latest_time = "-1d@d"
}

# Now, run the Invoke-RestMethod command with all variables in place, specifying a path and file
# name for the resulting CSV output file.

Invoke-RestMethod -Method Post -Uri $url -Credential $Cred -Body $body -OutFile output.csv

{"preview":true,"offset":0,"result":{"sourcetype":"contoso1","count":"9624"}}

{"preview":true,"offset":1,"result":{"sourcetype":"contoso2","count":"152"}}

{"preview":true,"offset":2,"result":{"sourcetype":"contoso3","count":"88494"}}

{"preview":true,"offset":3,"result":{"sourcetype":"contoso4","count":"15277"}}
```

### 範例3：傳遞多個標頭

此範例示範如何將中的多個標頭傳遞 `hash-table` 至 REST API。

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

Api 通常需要經過傳遞的標頭以進行驗證、驗證等等。

### 範例3：提交表單資料

當主體為表單，或它是另一個呼叫的輸出時 `Invoke-WebRequest` ，PowerShell 會將要求內容設定為表單欄位。

例如：

```powershell
$R = Invoke-WebRequest https://website.com/login.aspx
$R.Forms[0].Name = "MyName"
$R.Forms[0].Password = "MyPassword"
Invoke-RestMethod https://website.com/service.aspx -Body $R.Forms[0]
```

## 參數

### -Body

指定要求的主體。 主體為標頭之後的要求內容。
您也可以使用管線將主體值傳送至 `Invoke-RestMethod` 。

**Body** 參數可用來指定查詢參數的清單，或指定回應的內容。

當輸入為 GET 要求且主體為 IDictionary (通常為雜湊表) 時，主體會新增至 URI 成為查詢參數。 對於其他要求類型 (例如，POST)，會以標準「名稱=值」格式將主體設定為要求主體的值。

> [!WARNING]
> POST 主體的詳細資訊輸出會以結尾 `with -1-byte payload` ，即使主體的大小是已知的，也會在 `Content-Length` HTTP 標頭中傳送。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Certificate

指定用於安全 Web 要求的用戶端憑證。 輸入包含憑證的變數，或可取得憑證的命令或運算式。

若要尋找憑證，請使用 `Get-PfxCertificate` 或使用 `Get-ChildItem` 憑證 (`Cert:`) 磁片磁碟機中的 Cmdlet。 若憑證無效或權限不足，則命令會失敗。

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

指定具有傳送要求權限之使用者帳戶的數位公開金鑰憑證 (X509)。 請輸入憑證的憑證指紋。

憑證將用於用戶端憑證式驗證。 這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。

若要取得憑證指紋，請使用 `Get-Item` `Get-ChildItem` Windows PowerShell () 磁片磁碟機中的或命令 `Cert:` 。

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

### -ContentType

指定 Web 要求的內容類型。

如果省略此參數且要求方法為 POST，則會 `Invoke-RestMethod` 將內容類型設定為 "application/x-www-urlencoded"。 否則，呼叫中不會指定內容類型。

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

### -Credential

指定具有傳送要求權限的使用者帳戶。 預設為目前使用者。

輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。

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

### -DisableKeepAlive

將 HTTP 標頭中的 **KeepAlive** 值設為 False。 **KeepAlive** 預設為 True。
**KeepAlive** 會建立伺服器持續連線，有助於後續要求。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: KeepAlive
Accept pipeline input: False
Accept wildcard characters: False
```

### -Headers

指定 Web 要求的標頭。 輸入雜湊表或字典。

若要設定 UserAgent 標頭，請使用 **UserAgent** 參數。 您無法使用此參數指定 UserAgent 或 Cookie 標頭。

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InFile

從檔案取得 Web 要求的內容。

輸入路徑和檔案名稱。 若省略路徑，則預設為目前位置。

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

### -MaximumRedirection

決定連線失敗之前，Windows PowerShell 可將連線重新導向至替代「統一資源識別項 (URI)」的次數。 預設值為 5。 值為 0 (零) 將禁止所有重新導向。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -Method

指定用於 Web 要求的方法。 此參數可接受的值為：

- 預設
- 刪除
- Get
- Head
- 合併
- 選項
- Patch
- 郵寄
- Put
- 追蹤

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestMethod
Parameter Sets: (All)
Aliases:
Accepted values: Default, Get, Head, Post, Put, Delete, Trace, Options, Merge, Patch

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutFile

將回應主體儲存在指定的輸出檔中。 輸入路徑和檔案名稱。 若省略路徑，則預設為目前位置。

依預設，會將 `Invoke-RestMethod` 結果傳回至管線。 若要傳送結果至檔案與管線，請使用 **Passthru** 參數。

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

### -PassThru

除了將結果寫入檔案，也會傳回結果。 只有當命令中也使用 **OutFile** 參數時，此參數才會有效。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: No output
Accept pipeline input: False
Accept wildcard characters: False
```

### -Proxy

對於要求使用 Proxy 伺服器，而不是直接連線網際網路資源。 輸入網路 Proxy 伺服器的 URI。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。 預設為目前使用者。

輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。

只有當命令中也使用 **Proxy** 參數時，此參數才會有效。 您無法在相同命令中使用 **ProxyCredential** 與 **ProxyUseDefaultCredentials** 參數。

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

### -ProxyUseDefaultCredentials

使用目前使用者的認證，存取 **Proxy** 參數指定的 Proxy 伺服器。

只有當命令中也使用 **Proxy** 參數時，此參數才會有效。 您無法在相同命令中使用 **ProxyCredential** 與 **ProxyUseDefaultCredentials** 參數。

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

### -SessionVariable

建立 Web 要求工作階段，並將它儲存在指定變數的值。 輸入不含貨幣符號 () 符號的變數名稱 `$` 。

當您指定會話變數時，會 `Invoke-RestMethod` 建立 web 要求會話物件，並將它指派給您的 PowerShell 會話中具有指定名稱的變數。 一旦命令完成，便可在工作階段中使用變數。

Web 要求工作階段不同於遠端工作階段，並非持續連線。 它是包含連線與要求相關資訊的物件，這些資訊包括 Cookie、認證、重新導向上限值，以及使用者代理字串。 您可以使用它在 Web 要求之間共用狀態與資料。

若要在後續 Web 要求中使用 Web 要求工作階段，請在 **WebSession** 參數值指定工作階段變數。 建立新連線時，Windows PowerShell 會使用 Web 要求工作階段物件中的資料。 若要覆寫 Web 要求工作階段中的值，請使用 Cmdlet 參數，例如 **UserAgent** 或 **Credential** 。 參數值的優先順序高於 Web 要求工作階段中的值。

您不能在同一個命令中使用 **SessionVariable** 和 **WebSession** 參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: SV

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimeoutSec

指定要求可在一段時間之前暫止的時間長度。輸入以秒為單位的值。 預設值為 0，會指定無限逾時。

網域名稱系統 (DNS) 查詢最多可能需要15秒的時間才會傳回或超時。如果您的要求包含需要解析的主機名稱，而且您將 TimeoutSec 設定為大於零的值，但不超過15秒，則在擲回 WebException 之前，可能需要15秒或更長的時間，而且您的要求超時。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -TransferEncoding

指定傳輸編碼 HTTP 回應標頭的值。 此參數可接受的值為：

- 區塊
- 壓縮
- 上下凹陷
- GZip
- 身分識別

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: chunked, compress, deflate, gzip, identity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Uri

指定 Web 要求傳送目的地的網際網路資源「統一資源識別項 (URI)」。 此參數支援 HTTP、HTTPS、FTP 與 FILE 值。

這是必要參數。  ( **Uri** ) 的參數名稱是選擇性的。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseBasicParsing

指出此 Cmdlet 會使用基本剖析。 Cmdlet 會傳回 **字串** 物件中的原始 HTML。

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

### -UseDefaultCredentials

使用目前使用者的認證來傳送 Web 要求。

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

### -UserAgent

指定 Web 要求的使用者代理字串。

預設使用者代理程式類似於 "Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0"，但是每種作業系統與平台會有些微差異。

若要使用大部分網際網路瀏覽器所使用的標準使用者代理程式字串來測試網站，請使用 [PSUserAgent](/dotnet/api/microsoft.powershell.commands) 類別的屬性，例如 Chrome、FireFox、Internet Explorer、Opera 和 Safari。

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

### -WebSession

指定 Web 要求工作階段。 輸入變數名稱，包括貨幣符號 (`$`) 。

若要覆寫 Web 要求工作階段中的值，請使用 Cmdlet 參數，例如 **UserAgent** 或 **Credential** 。 參數值的優先順序高於 Web 要求工作階段中的值。

Web 要求工作階段不同於遠端工作階段，並非持續連線。 它是包含連線與要求相關資訊的物件，這些資訊包括 Cookie、認證、重新導向上限值，以及使用者代理字串。 您可以使用它在 Web 要求之間共用狀態與資料。

若要建立 web 要求會話，請在命令的 **SessionVariable** 參數值中輸入不含貨幣正負號)  (變數名稱 `Invoke-RestMethod` 。 `Invoke-RestMethod` 建立會話，並將它儲存在變數中。 在後續命令中，使用變數作為 **WebSession** 參數的值。

您不能在同一個命令中使用 **SessionVariable** 和 **WebSession** 參數。

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestSession
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

### System.Object

您可以使用管線將 web 要求的主體傳送至 `Invoke-RestMethod` 。

## 輸出

### System.Xml.Xml檔，Microsoft.PowerShell.Commands.HtmlWebResponseObject，System.string

Cmdlet 的輸出取決於抓取內容的格式。

### PSObject

如果要求傳回 JSON 字串，則 `Invoke-RestMethod` 會傳回代表字串的 PSObject。

## 備忘稿

## 相關連結

[ConvertTo-Json](ConvertTo-Json.md)

[ConvertFrom-Json](ConvertFrom-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)
