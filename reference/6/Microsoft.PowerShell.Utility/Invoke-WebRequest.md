---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: 09270fd74fd256858faacaae399e05b40985ddb5
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93206003"
---
# Invoke-WebRequest

## 概要
從網際網路上的網頁取得內容。

## SYNTAX

### StandardMethod (預設) 

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Method <WebRequestMethod>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### StandardMethodNoProxy

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Method <WebRequestMethod>] -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### CustomMethod

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -CustomMethod <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### CustomMethodNoProxy

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -CustomMethod <String> -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

## DESCRIPTION

`Invoke-WebRequest`Cmdlet 會將 HTTP 和 HTTPS 要求傳送至網頁或 web 服務。 它會剖析回應並傳回連結、影像和其他重要 HTML 元素的集合。

此 Cmdlet 是在 PowerShell 3.0 中引進。

## 範例

### 範例1：傳送 web 要求

此範例會使用 `Invoke-WebRequest` Cmdlet 將 web 要求傳送至 Bing.com 網站。

```powershell
$Response = Invoke-WebRequest -URI https://www.bing.com/search?q=how+many+feet+in+a+mile
$Response.InputFields | Where-Object {
    $_.name -like "* Value*"
} | Select-Object Name, Value
```

```Output
name       value
----       -----
From Value 1
To Value   5280
```

第一個命令會發出要求，並將回應儲存在 `$Response` 變數中。

第二個命令會取得 **名稱** 屬性類似的任何 **InputField** `"* Value"` 。 篩選後的結果會以管道傳送至， `Select-Object` 以選取 [ **名稱** ] 和 [ **值** ] 屬性。

### 範例2：使用具狀態的 web 服務

這個範例會示範如何搭配可設定 `Invoke-WebRequest` 狀態的 web 服務使用 Cmdlet。

```powershell
$Body = @{
    User = 'jdoe'
    password = 'P@S$w0rd!'
}
$LoginResponse = Invoke-WebRequest 'https://www.contoso.com/login/' -SessionVariable 'Session' -Body $Body -Method 'POST'

$Session

$ProfileResponse = Invoke-WebRequest 'https://www.contoso.com/profile/' -WebSession $Session

$ProfileResponse
```

第一個傳送登 `Invoke-WebRequest` 入要求的呼叫。 此命令會針對 **-SessionVariable** 參數的值指定 "Session" 值，並將結果儲存在 `$LoginResponse` 變數中。 當命令完成時， `$LoginResponse` 變數會包含 `BasicHtmlWebResponseObject` ，而且 `$Session` 變數包含 `WebRequestSession` 物件。 這會將使用者登入網站。

的呼叫 `$Session` 本身會顯示 `WebRequestSession` 變數中的物件。

第二個呼叫 `Invoke-WebRequest` 會提取使用者的設定檔，要求使用者必須登入網站。 變數中所儲存的會話資料 `$Session` 會用來提供會話 cookie 給登入期間所建立的網站。 結果會儲存在變數中 `$ProfileResponse` 。

的呼叫 `$ProfileResponse` 本身會顯示 `BasicHtmlWebResponseObject` 變數中的。

### 範例3：取得網頁的連結

這個範例會取得網頁中的連結。 它會使用 `Invoke-WebRequest` Cmdlet 來取得網頁內容。 然後，它會使用傳回之的 **Links** 屬性 `BasicHtmlWebResponseObject` `Invoke-WebRequest` ，以及每個連結的 **Href** 屬性。

```powershell
(Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs").Links.Href
```

### 範例4：使用要求的頁面中定義的編碼，將回應內容寫入檔案。

此範例會使用 `Invoke-WebRequest` Cmdlet 來取得 PowerShell 檔頁面的網頁內容。

```powershell
$Response = Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs"
$Stream = [System.IO.StreamWriter]::new('.\docspage.html', $false, $Response.Encoding)
try {
    $Stream.Write($Response.Content)
}
finally {
    $Stream.Dispose()
}
```

第一個命令會抓取頁面，並將回應物件儲存在 `$Response` 變數中。

第二個命令會建立 `StreamWriter` 用來將回應內容寫入檔案的。 Response 物件的 **encoding** 屬性是用來設定檔案的編碼方式。

最後幾個命令會將 **Content** 屬性寫入檔案，然後處置 `StreamWriter` 。

請注意，如果 web 要求未傳回文字內容，則 [ **編碼** ] 屬性會是 null。

### 範例5：提交多部分/表單資料檔案

此範例會使用 `Invoke-WebRequest` Cmdlet 將檔案上傳為 `multipart/form-data` 提交。 檔案 `c:\document.txt` 會提交為的表單欄位，以及 `document` `Content-Type` 的 `text/plain` 。

```powershell
$FilePath = 'c:\document.txt'
$FieldName = 'document'
$ContentType = 'text/plain'

$FileStream = [System.IO.FileStream]::new($filePath, [System.IO.FileMode]::Open)
$FileHeader = [System.Net.Http.Headers.ContentDispositionHeaderValue]::new('form-data')
$FileHeader.Name = $FieldName
$FileHeader.FileName = Split-Path -leaf $FilePath
$FileContent = [System.Net.Http.StreamContent]::new($FileStream)
$FileContent.Headers.ContentDisposition = $FileHeader
$FileContent.Headers.ContentType = [System.Net.Http.Headers.MediaTypeHeaderValue]::Parse($ContentType)

$MultipartContent = [System.Net.Http.MultipartFormDataContent]::new()
$MultipartContent.Add($FileContent)

$Response = Invoke-WebRequest -Body $MultipartContent -Method 'POST' -Uri 'https://api.contoso.com/upload'
```

### 範例6：簡化多部分/表單資料提交

某些 Api 需要 `multipart/form-data` 提交才能上傳檔案和混合的內容。 此範例示範如何更新使用者設定檔。

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
$Result = Invoke-WebRequest -Uri $Uri -Method Post -Form $Form
```

設定檔表單需要下欄欄位： `firstName` 、 `lastName` 、 `email` 、 `avatar` 、 `birthday` 和 `hobbies` 。 API 預期會在欄位中提供使用者設定檔 pic 的影像 `avatar` 。 此 API 也會接受 `hobbies` 以相同形式提交的多個專案。

建立 `$Form` 雜湊表時，索引鍵名稱會用來做為表單欄位名稱。 根據預設，雜湊表的值會轉換成字串。 如果有 **FileInfo** 值，則會提交檔案內容。 如果有集合（例如陣列或清單）存在，就會提交表單欄位多次。

藉由 `Get-Item` 在索引 `avatar` 鍵上使用， `FileInfo` 就會將物件設定為值。 結果是提交的影像資料 `jdoe.png` 。

藉由提供清單給 `hobbies` 金鑰， `hobbies` 每個清單專案的提交一次就會出現此欄位。

### 範例7：攔截 Invoke-WebRequest 的非成功訊息

當 `Invoke-WebRequest` (404、500等 ) 遇到非成功的 HTTP 訊息時，它不會傳回任何輸出並擲回終止錯誤。 若要攔截錯誤並查看 **StatusCode** ，您可以在區塊中包含執行 `try/catch` 。

```powershell
try
{
    $Response = Invoke-WebRequest -Uri "www.microsoft.com/unkownhost" -ErrorAction Stop
    # This will only execute if the Invoke-WebRequest is successful.
    $StatusCode = $Response.StatusCode
}
catch
{
    $StatusCode = $_.Exception.Response.StatusCode.value__
}
$StatusCode
```

```Output
404
```

命令會 `Invoke-WebRequest` 以 **Stop** 的 **ErrorAction** 呼叫，這會強制 `Invoke-WebRequest` 在任何失敗的要求上擲回終止錯誤。 `catch`從 **例外** 狀況物件抓取 **StatusCode** 的區塊攔截到終止錯誤。

## PARAMETERS

### -AllowUnencryptedAuthentication

允許透過未加密的連接傳送認證和密碼。 依預設，以不是開頭的 **Uri** **提供認證** 或任何 **驗證** 選項會 `https://` 導致錯誤，並中止要求以防止不慎以純文字方式透過未加密的連接來傳達秘密。 若要以您自己的風險覆寫此行為，請提供 **AllowUnencryptedAuthentication** 參數。

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

- **無** ：當未提供 **驗證** 時，這是預設選項;未使用明確驗證。
- **基本** ：需要 **認證** 。 認證會以的格式在 RFC 7617 基本驗證標頭中傳送 `base64(user:password)` 。
- **持有** 人：需要 **權杖** 。 傳送 `Authorization: Bearer` 具有所提供權杖的 RFC 6750 標頭。 這是 **OAuth** 的別名
- **OAuth** ：需要 **權杖** 。 傳送 `Authorization: Bearer` 具有所提供權杖的 RFC 6750 標頭。 這是 **持有** 人的別名

提供 **驗證** 會覆寫 `Authorization` 提供給 **標頭** 或包含在 **WebSession** 中的任何標頭。

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
您也可以使用管線將主體值傳送至 `Invoke-WebRequest` 。

**Body** 參數可用來指定查詢參數的清單，或指定回應的內容。

當輸入為 GET 要求且主體為 `IDictionary` (時，雜湊表) ，主體會新增至 URI 作為查詢參數。 針對其他要求類型 (例如 POST) ，主體會設定為標準格式的要求主體值 `name=value` 。

**Body** 參數也可以接受 `System.Net.Http.MultipartFormDataContent` 物件。 這可協助 `multipart/form-data` 要求。 提供 **主體** 的 **>multipartformdatacontent** 物件時，提供給 **ContentType** 、 **標頭** 或 **WebSession** 參數的任何內容相關標頭都會由 **>multipartformdatacontent** 物件的內容標頭覆寫。 這項功能已在 PowerShell 6.0.0 中新增。

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

指定用於安全 web 要求的用戶端憑證。 輸入包含憑證的變數，或可取得憑證的命令或運算式。

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

憑證將用於用戶端憑證式驗證。 這些帳戶只能對應至本機使用者帳戶;它們無法使用網域帳戶。

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

如果省略此參數且要求方法為 POST，則會 `Invoke-WebRequest` 將內容類型設定為 `application/x-www-form-urlencoded` 。 否則，呼叫中不會指定內容類型。

提供 **主體** 的 **>multipartformdatacontent** 物件時，會覆寫 **ContentType** 。

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

**認證可以** 單獨使用，也可以搭配特定的 **驗證** 參數選項使用。 單獨使用時，如果遠端伺服器傳送驗證挑戰要求，它只會提供遠端伺服器的認證。 與 **驗證** 選項搭配使用時，會明確地傳送認證。

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

指定用於 web 要求的自訂方法。 如果端點所要求的要求方法不是 **方法** 的可用選項，就可以使用這個方法。 **方法** 和 **CustomMethod** 無法一起使用。

此範例會對 `TEST` API 提出 HTTP 要求：

`Invoke-WebRequest -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

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

指出此 Cmdlet 會將 HTTP 標頭中的 **KeepAlive** 值設定為 **False** 。 **KeepAlive** 預設為 **True** 。 **KeepAlive** 會建立伺服器持續連線，有助於後續要求。

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

### -Form

將字典轉換為 `multipart/form-data` 提交。 **表單****不得與內文一起使用** 。
如果使用 **ContentType** ，則會予以忽略。

字典的索引鍵會用來做為表單欄位名稱。 根據預設，表單值會轉換成字串值。

如果值是 **FileInfo** 物件，則會提交二進位檔案內容。 檔案的名稱會提交為 **filename** 屬性。 MIME 類型設定為 `application/octet-stream` 。 `Get-Item` 可以用來簡化 **FileInfo** 物件的提供。

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

如果值是集合型別（例如陣列或清單），則會多次提交 for 欄位。
依預設，系統會將清單的值視為字串。 如果值是 **FileInfo** 物件，則會提交二進位檔案內容。 不支援嵌套集合。

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

在上述範例中， `tags` 欄位會在表單中提供三次，每一個、和都提供一次 `Vacation` `Italy` `2017` 。 此 `pictures` 欄位也會針對資料夾中的每個檔案提交一次 `2017-Italy` 。 該資料夾中檔案的二進位內容會以值的形式提交。

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

若要設定 UserAgent 標頭，請使用 **UserAgent** 參數。 您無法使用這個參數來指定 **使用者代理程式** 或 cookie 標頭。

`Content-Type`當提供 **主體** 的 **>multipartformdatacontent** 物件時，會覆寫內容相關的標頭（例如）。

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

從檔案取得 Web 要求的內容。 輸入路徑和檔案名稱。 若省略路徑，則預設為目前位置。

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

指定在連接失敗之前，PowerShell 將連接重新導向至替代統一資源識別項 (URI) 的次數。 預設值為 5。 值為 0 (零) 將禁止所有重新導向。

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

指出 Cmdlet 不應使用 proxy 來連線至目的地。 當您需要略過環境中設定的 proxy 時，請使用此參數。 這項功能已在 PowerShell 6.0.0 中新增。

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

指定此 Cmdlet 儲存回應主體的輸出檔。 輸入路徑和檔案名稱。
若省略路徑，則預設為目前位置。

依預設，會將 `Invoke-WebRequest` 結果傳回至管線。 若要傳送結果至檔案與管線，請使用 **Passthru** 參數。

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

指出除了將結果寫入檔案之外，指令程式還會傳回結果。 只有當命令中也使用 **OutFile** 參數時，此參數才會有效。

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

指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。
輸入網路 Proxy 伺服器的 URI。

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
Default value: Current user
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

### -Resume

盡力嘗試繼續下載部分檔案。 **Resume** 需要 **OutFile** 。

**Resume** 只會在本機檔案和遠端檔案的大小上運作，而且不會執行本機檔案和遠端檔案相同的其他驗證。

如果本機檔案大小小於遠端檔案大小，則 Cmdlet 會嘗試繼續下載檔案，並將剩餘的位元組附加至檔案結尾。

如果本機檔案大小與遠端檔案大小相同，則不會採取任何動作，而且 Cmdlet 會假設下載已完成。

如果本機檔案大小大於遠端檔案大小，則會覆寫本機檔案，並重新下載整個遠端檔案。 這種行為與使用 **OutFile** 而不需要 **Resume** 的行為相同。

如果遠端伺服器不支援下載繼續，則會覆寫本機檔案，並重新下載整個遠端檔案。 這種行為與使用 **OutFile** 而不需要 **Resume** 的行為相同。

如果本機檔案不存在，則會建立本機檔案，並下載整個遠端檔案。 這種行為與使用 **OutFile** 而不需要 **Resume** 的行為相同。

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

當您指定會話變數時，會 `Invoke-WebRequest` 建立 web 要求會話物件，並將它指派給您的 PowerShell 會話中具有指定名稱的變數。 一旦命令完成，便可在工作階段中使用變數。

Web 要求工作階段不同於遠端工作階段，並非持續連線。 它是一個物件，其中包含連線和要求的相關資訊，包括 cookie、認證、最大重新導向值，以及使用者代理字串。 您可以使用它在 Web 要求之間共用狀態與資料。

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

略過憑證驗證檢查。 這包括所有驗證，例如到期、撤銷、受信任的根授權單位等等。

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

此參數會針對傳遞給 **ContentType** 、 **標頭** 和 **UserAgent** 參數的值停用驗證。

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

### -SslProtocol

設定 web 要求所允許的 SSL/TLS 通訊協定。 預設會允許系統支援的 SSL/TLS 通訊協定。 **SslProtocol** 可基於合規性目的限制特定的通訊協定。

**SslProtocol** 使用 **WebSslProtocol** 旗標列舉。 您可以使用旗標標記法來提供多個通訊協定，或結合多個 **WebSslProtocol** 選項與 **bor** ，但在所有平臺上都不支援提供多個通訊協定。

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

### -TimeoutSec

指定要求可在一段時間之前暫止的時間長度。輸入以秒為單位的值。 預設值為 0，會指定無限逾時。

網域名稱系統 (DNS) 查詢最多可能需要15秒的時間才會傳回或超時。如果您的要求包含需要解析的主機名稱，而且您將 **TimeoutSec** 設定為大於零的值，但不超過15秒，則在擲回 WebException 之前，可能需要15秒或更長的時間，而且您的要求超時。

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

### -Token

要包含在要求中的 OAuth 或持有人權杖。 某些 **驗證** 選項需要 **權杖** 。 無法獨立使用。

**權杖** 會採用 `SecureString` 包含權杖的。 若要以手動方式提供權杖，請使用下列各項：

`Invoke-WebRequest -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

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

指定傳送 web 要求的網際網路資源 (URI) 的統一資源識別項。 輸入 URI。 此參數僅支援 HTTP 或 HTTPS。

這是必要參數。 參數名稱 **Uri** 是選擇性的。

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

例如，下列命令會使用使用者代理字串進行 Internet Explorer：

```powershell
Invoke-WebRequest -Uri https://website.com/ -UserAgent ([Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer)
```

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

若要建立 web 要求會話，請在命令的 **SessionVariable** 參數值中輸入不含貨幣符號的變數名稱 `Invoke-WebRequest` 。 `Invoke-WebRequest` 建立會話，並將它儲存在變數中。 在後續命令中，使用變數作為 **WebSession** 參數的值。

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

您可以使用管線將 web 要求的主體傳送至 `Invoke-WebRequest` 。

## 輸出

### BasicHtmlWebResponseObject。

## 注意

從 PowerShell 6.0.0 開始 `Invoke-WebRequest` 僅支援基本剖析。

如需 **BasicHtmlWebResponseObject** 物件類型的詳細資訊，請參閱 [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject)。

如需 .NET 如何提供 proxy 服務給 PowerShell 的詳細資訊，請參閱 [透過 Proxy 存取網際網路](/dotnet/framework/network-programming/accessing-the-internet-through-a-proxy)。

## 相關連結

[Invoke-RestMethod](Invoke-RestMethod.md)

[ConvertFrom-Json](ConvertFrom-Json.md)

[ConvertTo-Json](ConvertTo-Json.md)
