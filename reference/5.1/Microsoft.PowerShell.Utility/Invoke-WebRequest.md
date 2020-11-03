---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: 25da6262e93be3e3749aabaf4950e2fbcd91ff5c
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205900"
---
# Invoke-WebRequest

## 概要
從網際網路上的網頁取得內容。

## SYNTAX

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>] [-SessionVariable <String>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-CertificateThumbprint <String>]
 [-Certificate <X509Certificate>] [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>]
 [-Headers <IDictionary>] [-MaximumRedirection <Int32>] [-Method <WebRequestMethod>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>] [-ContentType <String>]
 [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>] [-PassThru] [<CommonParameters>]
```

## DESCRIPTION

`Invoke-WebRequest`Cmdlet 會將 HTTP、HTTPS、FTP 和檔案要求傳送至網頁或 web 服務。
它會剖析回應並傳回表單、連結、影像及其他主要 HTML 元素的集合。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

> [!NOTE]
> 根據預設，當剖析頁面以填入屬性時，可能會執行網頁中的腳本程式碼 `ParsedHtml` 。
> 使用 `-UseBasicParsing` 參數來隱藏此。

## 範例

### 範例1：傳送 web 要求

此命令會使用 `Invoke-WebRequest` Cmdlet 將 web 要求傳送至 Bing.com 網站。

```powershell
$R = Invoke-WebRequest -URI https://www.bing.com?q=how+many+feet+in+a+mile
$R.AllElements | Where-Object {
    $_.name -like "* Value" -and $_.tagName -eq "INPUT"
} | Select-Object Name, Value
```

```Output
name       value
----       -----
From Value 1
To Value   5280
```

第一個命令會發出要求，並將回應儲存在 `$R` 變數中。

第二個命令會篩選 **AllElements** 屬性中的物件，其中 **name** 屬性類似于 "* Value"，而 **tagName** 為 "INPUT"。 篩選後的結果會以管道傳送至， `Select-Object` 以選取 [ **名稱** ] 和 [ **值** ] 屬性。

### 範例2：使用具狀態的 web 服務

此範例示範如何使用 Cmdlet 搭配可設定 `Invoke-WebRequest` 狀態的 web 服務，例如 Facebook。

```powershell
$R = Invoke-WebRequest https://www.facebook.com/login.php -SessionVariable fb
# This command stores the first form in the Forms property of the $R variable in the $Form variable.
$Form = $R.Forms[0]
# This command shows the fields available in the Form.
$Form.fields
```

```Output
Key                     Value
---                     -----
...
email
pass
...
```

```powershell
# These commands populate the username and password of the respective Form fields.
$Form.Fields["email"]="User01@Fabrikam.com"
$Form.Fields["pass"]="P@ssw0rd"
# This command creates the Uri that will be used to log in to facebook.
# The value of the Uri parameter is the value of the Action property of the form.
$Uri = "https://www.facebook.com" + $Form.Action
# Now the Invoke-WebRequest cmdlet is used to sign into the Facebook web service.
# The WebRequestSession object in the $FB variable is passed as the value of the WebSession parameter.
# The value of the Body parameter is the hash table in the Fields property of the form.
# The value of the *Method* parameter is POST. The command saves the output in the $R variable.
$R = Invoke-WebRequest -Uri $Uri -WebSession $FB -Method POST -Body $Form.Fields
$R.StatusDescription
```

第一個命令會使用 `Invoke-WebRequest` Cmdlet 來傳送登入要求。 此命令會為 **SessionVariable** 參數的值指定 "FB" 值，並將結果儲存在 `$R` 變數中。 當命令完成時， `$R` 變數會包含 **htmlwebresponseobject links** ，而且 `$FB` 變數包含 **WebRequestSession** 物件。

在 `Invoke-WebRequest` Cmdlet 登入 facebook 之後，變數中 web 回應物件的 **StatusDescription** 屬性 `$R` 會指出使用者已成功登入。

### 範例3：取得網頁的連結

此命令會取得網頁中的連結。

```powershell
(Invoke-WebRequest -Uri "https://devblogs.microsoft.com/powershell/").Links.Href
```

`Invoke-WebRequest`Cmdlet 會取得網頁內容。 然後，傳回之 **htmlwebresponseobject links** 的 **Links** 屬性會用來顯示每個連結的 **Href** 屬性。

### 範例4：攔截 Invoke-WebRequest 的非成功訊息

當 `Invoke-WebRequest` (404、500等 ) 遇到非成功的 HTTP 訊息時，它不會傳回任何輸出並擲回終止錯誤。 若要攔截錯誤並查看 **StatusCode** ，您可以在區塊中包含執行 `try/catch` 。 下列範例顯示如何完成這項工作。

```powershell
try
{
    $response = Invoke-WebRequest -Uri "www.microsoft.com/unkownhost" -ErrorAction Stop
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

第一個命令會 `Invoke-WebRequest` 以 **Stop** 的 **ErrorAction** 呼叫，這會 `Invoke-WebRequest` 在任何失敗的要求上強制擲回終止錯誤。 `catch`從 **例外** 狀況物件抓取 **StatusCode** 的區塊攔截到終止錯誤。

## PARAMETERS

### -Body

指定要求的主體。
主體為標頭之後的要求內容。
您也可以使用管線將主體值傳送至 `Invoke-WebRequest` 。

**Body** 參數可用來指定查詢參數的清單，或指定回應的內容。

當輸入為 GET 要求且主體為 **IDictionary** (通常會) 雜湊表，主體會新增至 URI 作為查詢參數。 針對其他 GET 要求，主體會設定為標準格式的要求主體值 `name=value` 。

當主體為表單，或其為呼叫的輸出時 `Invoke-WebRequest` ，PowerShell 會將要求內容設定為表單欄位。
例如：

`$r = Invoke-WebRequest https://website.com/login.aspx`
`$r.Forms\[0\].Name = "MyName"`
`$r.Forms\[0\].Password = "MyPassword"`
`Invoke-RestMethod https://website.com/service.aspx -Body $r`

- 或 -

`Invoke-RestMethod https://website.com/service.aspx -Body $r.Forms\[0\]`

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

若要尋找憑證，請使用 `Get-PfxCertificate` 或使用 `Get-ChildItem` **憑證** (`Cert:`) 磁片磁碟機中的 Cmdlet。 若憑證無效或權限不足，則命令會失敗。

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

指定具有傳送要求權限之使用者帳戶的數位公開金鑰憑證 (X509)。 請輸入憑證的憑證指紋。 憑證將用於用戶端憑證式驗證。 這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。

若要取得憑證指紋，請使用 `Get-Item` `Get-ChildItem` PowerShell 磁片磁碟機中的或命令 `Cert:` 。

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

如果省略此參數且要求方法為 POST，則會 `Invoke-WebRequest` 將內容類型設定為 application/x-www 表單-urlencoded。 否則，呼叫中不會指定內容類型。

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

### -Headers

指定 Web 要求的標頭。 輸入雜湊表或字典。

若要設定 **UserAgent** 標頭，請使用 **UserAgent** 參數。 您無法使用此參數指定 **UserAgent** 或 cookie 標頭。

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

### -Proxy

指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。
輸入網路 Proxy 伺服器的 URI。

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

輸入使用者名稱（例如 `User01` 或）， `Domain01\User01` 或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。

只有當命令中也使用 **Proxy** 參數時，此參數才會有效。 您無法在相同命令中使用 **ProxyCredential** 與 **ProxyUseDefaultCredentials** 參數。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyUseDefaultCredentials

指出此 Cmdlet 會使用目前使用者的認證來存取 **proxy** 參數所指定的 proxy 伺服器。

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

指定此 Cmdlet 會建立 web 要求會話，並將其儲存在值中的變數。
輸入不含貨幣符號 () 符號的變數名稱 `$` 。

當您指定會話變數時，會 `Invoke-WebRequest` 建立 web 要求會話物件，並將它指派給您的 PowerShell 會話中具有指定名稱的變數。 一旦命令完成，便可在工作階段中使用變數。

Web 要求工作階段不同於遠端工作階段，並非持續連線。 它是包含連線與要求相關資訊的物件，這些資訊包括 Cookie、認證、重新導向上限值，以及使用者代理字串。 您可以使用它在 Web 要求之間共用狀態與資料。

若要在後續 Web 要求中使用 Web 要求工作階段，請在 **WebSession** 參數值指定工作階段變數。 建立新連接時，PowerShell 會使用 web 要求會話物件中的資料。 若要覆寫 Web 要求工作階段中的值，請使用 Cmdlet 參數，例如 **UserAgent** 或 **Credential** 。 參數值的優先順序高於 Web 要求工作階段中的值。

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

網域名稱系統 (DNS) 查詢最多可能需要15秒的時間才會傳回或超時。如果您的要求包含需要解析的主機名稱，而且您將 **TimeoutSec** 設定為大於零的值，但不超過15秒，則在擲回 **WebException** 之前，可能需要15秒或更長的時間，而且您的要求超時。

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

指定 Web 要求傳送目的地的網際網路資源「統一資源識別項 (URI)」。 輸入 URI。 此參數支援 HTTP、HTTPS、FTP 與 FILE 值。

這是必要參數。

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

指出 Cmdlet 使用 HTML 內容的回應物件，而不檔物件模型 (DOM) 剖析。 當電腦上沒有安裝 Internet Explorer 時，此參數為必要參數，例如在 Windows Server 作業系統的 Server Core 安裝上。

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

表示 cmdet 會使用目前使用者的認證來傳送 web 要求。

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

指定 Web 要求的使用者代理字串。 預設使用者代理程式類似于 `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` 每個作業系統和平臺的些許變化。

若要使用大部分網際網路瀏覽器所使用的標準使用者代理程式字串來測試網站，請使用 [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) 類別的屬性，例如 Chrome、FireFox、Microsoft-windows-ie-internetexplorer、Opera 和 Safari。 例如，下列命令會使用使用者代理字串進行 Internet Explorer

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

若要建立 web 要求會話，請在命令的 **SessionVariable** 參數值中輸入不含貨幣正負號)  (變數名稱 `Invoke-WebRequest` 。 `Invoke-WebRequest` 建立會話，並將它儲存在變數中。 在後續命令中，使用變數作為 **WebSession** 參數的值。

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

這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Object

您可以使用管線將 web 要求的主體傳送至 `Invoke-WebRequest` 。

## 輸出

### Microsoft.PowerShell.Commands.HtmlWebResponseObject

## 注意

## 相關連結

[Invoke-RestMethod](Invoke-RestMethod.md)

[ConvertFrom-Json](ConvertFrom-Json.md)

[ConvertTo-Json](ConvertTo-Json.md)
