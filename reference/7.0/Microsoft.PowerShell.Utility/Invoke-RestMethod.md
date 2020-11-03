---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-RestMethod
ms.openlocfilehash: aab7ae73d223f349fc0c103332331710a3eb2efe
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201296"
---
# Invoke-RestMethod

## 概要
傳送 HTTP 或 HTTPS 要求至 RESTful Web 服務。

## SYNTAX

### StandardMethod (預設) 

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### StandardMethodNoProxy

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -NoProxy [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### CustomMethodNoProxy

```
Invoke-RestMethod -CustomMethod <String> [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -NoProxy [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### CustomMethod

```
Invoke-RestMethod -CustomMethod <String> [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

## 描述

此 `Invoke-RestMethod` Cmdlet 會將 HTTP 和 HTTPS 要求傳送至具象狀態傳輸 (REST) web 服務，以傳回豐富的結構化資料。

PowerShell 會根據資料類型來格式化回應。 針對 RSS 或 ATOM 摘要，PowerShell 會傳回專案 XML 節點。 針對 JavaScript 物件標記法 (JSON) 或 XML，PowerShell 會將內容轉換或還原序列化為物件。

此 Cmdlet 是在 Windows PowerShell 3.0 引進。

從 PowerShell 7.0 開始，可 `Invoke-RestMethod` 支援環境變數所定義的 proxy 設定。 請參閱本文的「 [附注](#notes) 」一節。

## 範例

### 範例1：取得 PowerShell RSS 摘要

此範例會使用 `Invoke-RestMethod` Cmdlet 從 PowerShell Blog 的 rss 摘要中取得資訊。 此命令會使用 `Format-Table` Cmdlet，在資料表中顯示每個 blog 的 **Title** 和 **pubDate** 屬性的值。

```powershell
Invoke-RestMethod -Uri https://blogs.msdn.microsoft.com/powershell/feed/ |
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

### 範例2：執行 POST 要求

在此範例中，使用者會 `Invoke-RestMethod` 執行，以在使用者組織內部網路網站上執行 POST 要求。

```powershell
$Cred = Get-Credential
$Url = "https://server.contoso.com:8089/services/search/jobs/export"
$Body = @{
    search = "search index=_internal | reverse | table index,host,source,sourcetype,_raw"
    output_mode = "csv"
    earliest_time = "-2d@d"
    latest_time = "-1d@d"
}
Invoke-RestMethod -Method 'Post' -Uri $url -Credential $Cred -Body $body -OutFile output.csv
```

系統會提示您輸入認證，然後將其儲存在中 `$Cred` ，並在中定義將存取的 URL `$Url` 。

`$Body`變數描述搜尋準則、將 CSV 指定為輸出模式，並指定在兩天前開始並結束一天前的傳回資料的時間週期。 本文變數指定的參數值適用于 `Invoke-RestMethod` 正在進行通訊的特定 REST API。

此 `Invoke-RestMethod` 命令會使用所有變數來執行，並指定所產生 CSV 輸出檔的路徑和檔案名。

### 範例3：遵循關聯連結

某些 REST Api 支援每個 [RFC5988](https://tools.ietf.org/html/rfc5988#page-6)的關聯性連結的分頁。 您可以讓 Cmdlet 為您完成此動作，而不是剖析標頭來取得下一個頁面的 URL。 此範例會傳回來自 PowerShell GitHub 存放庫的前兩個問題頁面。

```powershell
$url = 'https://api.github.com/repos/powershell/powershell/issues'
Invoke-RestMethod $url -FollowRelLink -MaximumFollowRelLink 2
```

### 範例4：簡化的多部分/表單資料提交

某些 Api 需要 `multipart/form-data` 提交才能上傳檔案和混合的內容。 此範例示範如何更新使用者的設定檔。

```powershell
$Uri = 'https://api.contoso.com/v2/profile'
$Form = @{
    firstName  = 'John'
    lastName   = 'Doe'
    email      = 'john.doe@contoso.com'
    avatar     = Get-Item -Path 'c:\Pictures\jdoe.png'
    birthday   = '1980-10-15'
    hobbies    = 'Hiking','Fishing','Jogging'
}
$Result = Invoke-RestMethod -Uri $Uri -Method Post -Form $Form
```

設定檔表單需要下欄欄位： `firstName` 、 `lastName` 、 `email` 、 `avatar` 、 `birthday` 和 `hobbies` 。 API 預期會在欄位中提供使用者設定檔 pic 的影像 `avatar` 。 此 API 也會接受 `hobbies` 以相同形式提交的多個專案。

建立 `$Form` 雜湊表時，索引鍵名稱會用來做為表單欄位名稱。 根據預設，雜湊表的值會轉換成字串。 如果有某個 `System.IO.FileInfo` 值，則會提交檔案內容。 如果有集合（例如陣列或清單），則會提交表單欄位多次。

藉由 `Get-Item` 在索引 `avatar` 鍵上使用， `FileInfo` 物件將會設定為值。 結果是將會提交的影像資料 `jdoe.png` 。

藉由提供清單給 `hobbies` 金鑰， `hobbies` 每個清單專案的提交一次就會出現此欄位。

### 範例5：傳遞多個標頭

Api 通常需要經過傳遞的標頭以進行驗證或驗證。 此範例示範如何將多個標頭從傳遞 `hash-table` 至 REST API。

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

## 參數

### -AllowUnencryptedAuthentication

允許透過未加密的連接傳送認證和密碼。 根據預設，如果提供的認證 **或任何****驗證** 選項的 **Uri** 不是以開頭， `https://` 將會產生錯誤，而且要求將會中止，以防止不慎以純文字方式透過未加密的連接來傳達秘密。 若要以您自己的風險覆寫此行為，請提供 **AllowUnencryptedAuthentication** 參數。

> [!WARNING]
> 使用這個參數並不安全，因此不建議使用。 它僅提供給無法提供加密連接的舊版系統相容。 使用您自己的風險。

這項功能已在 PowerShell 6.0.0 中新增。

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

### -Authentication

指定要用於要求的明確驗證類型。 預設值為 [無]。
**驗證** 無法與 **UseDefaultCredentials** 搭配使用。

可用的驗證選項：

- **無** ：當未提供 **驗證** 時，這是預設選項。 不會使用任何明確驗證。
- **基本** ：需要 **認證** 。 認證將用來傳送的格式為 RFC 7617 基本驗證 `Authorization: Basic` 標頭 `base64(user:password)` 。
- **持有** 人：需要 **權杖** 。 將會傳送和 RFC 6750 `Authorization: Bearer` 標頭與提供的權杖。 這是 **OAuth** 的別名
- **OAuth** ：需要 **權杖** 。 將會傳送 `Authorization: Bearer` 具有所提供權杖的 RFC 6750 標頭。 這是 **持有** 人的別名

提供 **驗證** 將會覆寫 `Authorization` 提供給 **標頭** 或包含在 **WebSession** 中的任何標頭。

這項功能已在 PowerShell 6.0.0 中新增。

```yaml
Type: Microsoft.PowerShell.Commands.WebAuthenticationType
Parameter Sets: (All)
Aliases:
Accepted values: None, Basic, Bearer, OAuth

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Body

指定要求的主體。 主體為標頭之後的要求內容。
您也可以使用管線將主體值傳送至 `Invoke-RestMethod` 。

**Body** 參數可用來指定查詢參數的清單，或指定回應的內容。

當輸入為 GET 要求且主體為 `IDictionary` (通常會) 雜湊表時，主體會新增至統一資源識別項 (URI) 作為查詢參數。 對於其他要求類型 (例如，POST)，會以標準「名稱=值」格式將主體設定為要求主體的值。

當主體為表單，或它是另一個呼叫的輸出時 `Invoke-WebRequest` ，PowerShell 會將要求內容設定為表單欄位。

**Body** 參數也可以接受 **>multipartformdatacontent** 物件。 這將有助於 `multipart/form-data` 要求。 提供 **主體** 的 **>multipartformdatacontent** 物件時，提供給 **ContentType** 、 **標頭** 或 **WebSession** 參數的任何內容相關標頭都會被物件的內容標頭覆寫 `MultipartFormDataContent` 。 這項功能已在 PowerShell 6.0.0 中新增。

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

若要尋找憑證，請使用 `Get-PfxCertificate` 或使用 `Get-ChildItem` 憑證 (`Cert:`) 磁片磁碟機中的 Cmdlet。 若憑證無效或沒有足夠的許可權，則命令會失敗。

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

若要取得憑證指紋，請使用 `Get-Item` `Get-ChildItem` PowerShell 磁片磁碟機中的或命令 `Cert:` 。

> [!NOTE]
> 這項功能目前僅支援 Windows OS 平臺。

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

如果省略此參數且要求方法為 POST，則會 `Invoke-RestMethod` 將內容類型設定為 `application/x-www-form-urlencoded` 。 否則，呼叫中不會指定內容類型。

**ContentType** `MultipartFormDataContent` 提供 **主體** 的物件時，會覆寫 ContentType。

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

**認證可以** 單獨使用，也可以搭配特定的 **驗證** 參數選項使用。 單獨使用時，如果遠端伺服器傳送驗證挑戰要求，它只會提供遠端伺服器的認證。 與 **驗證** 選項搭配使用時，將會明確地傳送認證。

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

### -CustomMethod

指定用於 web 要求的自訂方法。 這可以與端點所要求的要求方法搭配使用，而不是 **方法** 上的可用選項。 **方法** 和 **CustomMethod** 無法一起使用。

範例：

`Invoke-RestMethod -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

這會對 `TEST` API 發出 HTTP 要求。

這項功能已在 PowerShell 6.0.0 中新增。

```yaml
Type: System.String
Parameter Sets: CustomMethodNoProxy, CustomMethod
Aliases: CM

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableKeepAlive

指出此 Cmdlet 會將 HTTP 標頭中的 **KeepAlive** 值設定為 False。 **KeepAlive** 預設為 True。 **KeepAlive** 會建立伺服器持續連線，有助於後續要求。

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

### -FollowRelLink

指出 Cmdlet 應遵循關聯連結。

某些 REST Api 支援每個 [RFC5988](https://tools.ietf.org/html/rfc5988#page-6)的關聯性連結的分頁。 您可以讓 Cmdlet 為您完成此動作，而不是剖析標頭來取得下一個頁面的 URL。 若要設定要遵循關聯連結的次數，請使用 **MaximumFollowRelLink** 參數。

使用這個參數時，此 Cmdlet 會傳回結果的頁面集合。 每一頁的結果可能包含多個結果專案。

這項功能已在 PowerShell 6.0.0 中新增。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: FL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Form

將字典轉換為 `multipart/form-data` 提交。 **表單****不得與內文一起使用** 。
如果將忽略 **ContentType** 。

字典的索引鍵將會用來做為表單功能變數名稱。 根據預設，表單值會轉換成字串值。

如果值是 **FileInfo** 物件，則會提交二進位檔案內容。
檔案的名稱將會提交為 `filename` 。 MIME 將設定為 `application/octet-stream` 。 `Get-Item` 可以用來簡化 **FileInfo** 物件的提供。

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

如果值是集合型別（例如陣列或清單），則會多次提交 for 欄位。 預設會將清單的值視為字串。 如果值是 **FileInfo** 物件，則會提交二進位檔案內容。 不支援嵌套集合。

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

在上述範例中， `tags` 欄位會在表單中提供三次，每一個、和都提供一次 `Vacation` `Italy` `2017` 。 此 `pictures` 欄位也會針對資料夾中的每個檔案提交一次 `2017-Italy` 。 該資料夾中檔案的二進位內容將會以值的形式提交。

這項功能已在 PowerShell 6.1.0 中新增。

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

### -Headers

指定 Web 要求的標頭。 輸入雜湊表或字典。

若要設定 UserAgent 標頭，請使用 **UserAgent** 參數。 您無法使用這個參數來指定 `User-Agent` 或 cookie 標頭。

`Content-Type`在 `MultipartFormDataContent` 提供 **主體** 的物件時，將會覆寫內容相關的標頭（例如）。

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

### -MaximumFollowRelLink

指定使用 **FollowRelLink** 時，要遵循關聯連結的次數。 如果 REST api 因為太多要求而進行節流，則可能需要較小的值。 預設值是 `[Int32]::MaxValue`。 值為 0 (零) 可防止下列關聯連結。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: ML

Required: False
Position: Named
Default value: Int32.MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumRedirection

指定在連接失敗之前，PowerShell 將連接重新導向至替代統一資源識別項 (URI) 的次數。 預設值為 5。 值為 0 (零) 將禁止所有重新導向。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumRetryCount

指定當收到400到599（含）或304之間的失敗代碼時，PowerShell 重試連接的次數。 另請參閱 **RetryIntervalSec** 參數，以指定重試次數。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
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

**CustomMethod** 參數可以用於上面未列出的要求方法。

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestMethod
Parameter Sets: StandardMethod, StandardMethodNoProxy
Aliases:
Accepted values: Default, Get, Head, Post, Put, Delete, Trace, Options, Merge, Patch

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoProxy

指出此 Cmdlet 將不會使用 proxy 來連線至目的地。

當您需要略過 Internet Explorer 中設定的 proxy 或環境中指定的 proxy 時，請使用此參數。

此參數是在 PowerShell 6.0 中引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StandardMethodNoProxy, CustomMethodNoProxy
Aliases:

Required: True
Position: Named
Default value: None
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

### -PreserveAuthorizationOnRedirect

指出 Cmdlet 應該在重新導向 `Authorization` 之間保留標頭（若有的話）。

根據預設，此 Cmdlet 會在重新導向 `Authorization` 之前先移除標頭。 指定此參數會在標頭必須傳送至重新導向位置的情況下，停用此邏輯。

這項功能已在 PowerShell 6.0.0 中新增。

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

### -Proxy

針對要求使用 proxy 伺服器，而不是直接連接到網際網路資源。 輸入網路 proxy 伺服器 (URI) 的統一資源識別項。

這項功能已在 PowerShell 6.0.0 中新增。

```yaml
Type: System.Uri
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。 預設為目前使用者。

輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ）， **User@Domain.Com** 或輸入一個 `PSCredential` 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。

只有當命令中也使用 **Proxy** 參數時，此參數才會有效。 您無法在同一個命令中使用 **ProxyCredential** 和 **ProxyUseDefaultCredentials** 參數。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyUseDefaultCredentials

指出此 Cmdlet 會使用目前使用者的認證來存取 **proxy** 參數所指定的 proxy 伺服器。

只有當命令中也使用 **Proxy** 參數時，此參數才會有效。 您無法在同一個命令中使用 **ProxyCredential** 和 **ProxyUseDefaultCredentials** 參數。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResponseHeadersVariable

建立回應標頭字典，並將它儲存在指定變數的值中。 字典的索引鍵會包含 web 伺服器所傳回之回應標頭的功能變數名稱，而這些值會是各自的域值。

這項功能已在 PowerShell 6.0.0 中新增。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: RHV

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Resume

盡力嘗試繼續下載部分檔案。 **Resume** 參數需要 **OutFile** 參數。

**Resume** 只會在本機檔案和遠端檔案的大小上運作，而且不會執行本機檔案和遠端檔案相同的其他驗證。

如果本機檔案大小小於遠端檔案大小，則 Cmdlet 會嘗試繼續下載檔案，並將剩餘的位元組附加至檔案結尾。

如果本機檔案大小與遠端檔案大小相同，則不會採取任何動作，而且 Cmdlet 會假設下載已完成。

如果本機檔案大小大於遠端檔案大小，則會覆寫本機檔案，而且整個遠端檔案將會完全重新下載。 這種行為與使用 **OutFile** 而不需要 **Resume** 的行為相同。

如果遠端伺服器不支援下載繼續，則會覆寫本機檔案，而且整個遠端檔案將會完全重新下載。 這種行為與使用 **OutFile** 而不需要 **Resume** 的行為相同。

如果本機檔案不存在，則會建立本機檔案，而且整個遠端檔案將會完整下載。 這種行為與使用 **OutFile** 而不需要 **Resume** 的行為相同。

這項功能已在 PowerShell 6.1.0 中新增。

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

### -RetryIntervalSec

指定當收到400和599（含或304）之間的失敗代碼時，連接重試之間的間隔。 另請參閱 **MaximumRetryCount** 參數，以指定重試次數。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionVariable

指定此 Cmdlet 會建立 web 要求會話，並將其儲存在值中的變數。
輸入不含貨幣符號 () 符號的變數名稱 `$` 。

當您指定會話變數時，會 `Invoke-RestMethod` 建立 web 要求會話物件，並將它指派給您的 PowerShell 會話中具有指定名稱的變數。 一旦命令完成，便可在工作階段中使用變數。

不同于遠端會話，web 要求會話不是持續性連接。 它是一個物件，其中包含連線和要求的相關資訊，包括 cookie、認證、最大重新導向值，以及使用者代理字串。 您可以使用它在 Web 要求之間共用狀態與資料。

若要在後續 Web 要求中使用 Web 要求工作階段，請在 **WebSession** 參數值指定工作階段變數。 建立新連接時，PowerShell 會使用 web 要求會話物件中的資料。 若要覆寫 Web 要求工作階段中的值，請使用 Cmdlet 參數，例如 **UserAgent** 或 **Credential** 。 參數值的優先順序高於 Web 要求工作階段中的值。

您無法在同一個命令中使用 **SessionVariable** 和 **WebSession** 參數。

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

### -SkipCertificateCheck

略過包含所有驗證的憑證驗證檢查，例如到期、撤銷、受信任的根授權單位等等。

> [!WARNING]
> 使用這個參數並不安全，因此不建議使用。 此參數僅適用于使用自我簽署憑證的已知主機，以供測試之用。 使用您自己的風險。

這項功能已在 PowerShell 6.0.0 中新增。

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

### -SkipHeaderValidation

指出 Cmdlet 應該在沒有驗證的情況下，將標頭新增至要求。

此參數應用於需要不符合標準之標頭值的網站。
指定此參數會停用驗證，以允許未核取值的傳遞。 若有指定，則會新增所有標頭，而不進行驗證。

這會針對傳遞給 **ContentType** 、 **標頭** 和 **UserAgent** 參數的值停用驗證。

這項功能已在 PowerShell 6.0.0 中新增。

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

### -SkipHttpErrorCheck

此參數會讓 Cmdlet 忽略 HTTP 錯誤狀態，並繼續處理回應。
錯誤回應會寫入管線中，就如同成功一樣。

此參數是在 PowerShell 7 中引進。

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

### -SslProtocol

設定 web 要求所允許的 SSL/TLS 通訊協定。 預設會允許系統支援的 SSL/TLS 通訊協定。 **SslProtocol** 可基於合規性目的限制特定的通訊協定。

**SslProtocol** 使用 `WebSslProtocol` 旗標列舉。 您可以使用旗標標記法或結合多個選項來提供多個通訊協定 `WebSslProtocol` `-bor` ，但在所有平臺上都不支援提供多個通訊協定。

> [!NOTE]
> 在非 Windows 平臺上，可能無法提供 `'Tls, Tls12'` 作為選項。

這項功能已在 PowerShell 6.0.0 中新增。

```yaml
Type: Microsoft.PowerShell.Commands.WebSslProtocol
Parameter Sets: (All)
Aliases:
Accepted values: Default, Tls, Tls11, Tls12

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StatusCodeVariable

此參數會指定已指派狀態碼整數值的變數。 參數可以在與 **SkipHttpErrorCheck** 參數搭配使用時，識別成功訊息或失敗訊息。

以字串形式輸入參數的變數名稱，例如 `-StatusCodeVariable "scv"` 。

此參數是在 PowerShell 7 中引進。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimeoutSec

指定要求可在一段時間之前暫止的時間長度。輸入以秒為單位的值。 預設值為 0，會指定無限逾時。

網域名稱系統 (DNS) 查詢最多可能需要15秒的時間才會傳回或超時。如果您的要求包含需要解析的主機名稱，而且您將 **TimeoutSec** 設定為大於零的值，但不超過15秒，則在擲回 WebException 之前，可能需要15秒或更長的時間，而且您的要求超時。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Token

要包含在要求中的 OAuth 或持有人權杖。 某些 **驗證** 選項需要 **權杖** 。 無法獨立使用。

**權杖** 會採用 `SecureString` 包含權杖的。 若要提供權杖，請手動使用下列各項：

`Invoke-RestMethod -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

此參數是在 PowerShell 6.0 中引進。

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
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

指定傳送 web 要求的網際網路資源 (URI) 的統一資源識別項。 此參數支援 HTTP、HTTPS、FTP 與 FILE 值。

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

此參數已被取代。 從 PowerShell 6.0.0 開始，所有 Web 要求都會使用基本剖析。 此參數是為了回溯相容性而包含，而且任何使用它都不會影響 Cmdlet 的操作。

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

指出此 Cmdlet 會使用目前使用者的認證來傳送 web 要求。 這不能與 **驗證****或認證** 搭配使用，而且在所有平臺上都可能不受支援。

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

預設使用者代理程式類似于 `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` 每個作業系統和平臺的些許變化。

若要使用大部分網際網路瀏覽器所使用的標準使用者代理程式字串來測試網站，請使用 [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) 類別的屬性，例如 Chrome、FireFox、Microsoft-windows-ie-internetexplorer、Opera 和 Safari。

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

若要覆寫 Web 要求工作階段中的值，請使用 Cmdlet 參數，例如 **UserAgent** 或 **Credential** 。 參數值的優先順序高於 Web 要求工作階段中的值。 `Content-Type`當提供 **主體** 的 **>multipartformdatacontent** 物件時，也會覆寫內容相關的標頭（例如）。

不同于遠端會話，web 要求會話不是持續性連接。 它是一個物件，其中包含連線和要求的相關資訊，包括 cookie、認證、最大重新導向值，以及使用者代理字串。 您可以使用它在 Web 要求之間共用狀態與資料。

若要建立 web 要求會話，請在命令的 **SessionVariable** 參數值中輸入不含貨幣符號的變數名稱 `Invoke-RestMethod` 。 `Invoke-RestMethod` 建立會話，並將它儲存在變數中。 在後續命令中，使用變數作為 **WebSession** 參數的值。

您無法在同一個命令中使用 **SessionVariable** 和 **WebSession** 參數。

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

### 系統 Int64、System.string、System.Xml.Xml檔

Cmdlet 的輸出取決於抓取內容的格式。

### PSObject

如果要求傳回 JSON 字串，則 `Invoke-RestMethod` 會傳回代表字串的 **PSObject** 。

## 注意

某些功能可能無法在所有平臺上使用。

由於 .NET Core 3.1 的變更，PowerShell 7.0 和更新版本會使用 [HttpClient. DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) 屬性來判斷 proxy 設定。

這個屬性的值取決於您的平臺：

- 若 **為 Windows** ：從環境變數讀取 proxy 設定。 如果未定義這些變數，則屬性會衍生自使用者的 proxy 設定。
- 若 **為 macOS** ：從環境變數讀取 proxy 設定。 如果未定義這些變數，則屬性會衍生自系統的 proxy 設定。
- 若 **為 Linux** ：從環境變數讀取 proxy 設定。 如果未定義這些變數，屬性會初始化一個未設定的實例，以略過所有位址。

`DefaultProxy`在 Windows 和 Unix 平臺上用於初始化的環境變數如下：

- ` HTTP_PROXY`：用於 HTTP 要求之 proxy 伺服器的主機名稱或 IP 位址。
- `HTTPS_PROXY`：用於 HTTPS 要求的 proxy 伺服器的主機名稱或 IP 位址。
- `ALL_PROXY`：用於 HTTP 和 HTTPS 要求的 proxy 伺服器的主機名稱或 IP 位址（若 `HTTP_PROXY` `HTTPS_PROXY` 未定義的話）。
- `NO_PROXY`：應從 proxy 排除的主機名稱（以逗號分隔）清單。

## 相關連結

[ConvertTo-Json](ConvertTo-Json.md)

[ConvertFrom-Json](ConvertFrom-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)
