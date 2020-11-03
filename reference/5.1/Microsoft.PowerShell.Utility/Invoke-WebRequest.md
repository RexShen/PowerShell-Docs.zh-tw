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
# <span data-ttu-id="1b386-103">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="1b386-103">Invoke-WebRequest</span></span>

## <span data-ttu-id="1b386-104">概要</span><span class="sxs-lookup"><span data-stu-id="1b386-104">SYNOPSIS</span></span>
<span data-ttu-id="1b386-105">從網際網路上的網頁取得內容。</span><span class="sxs-lookup"><span data-stu-id="1b386-105">Gets content from a web page on the Internet.</span></span>

## <span data-ttu-id="1b386-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1b386-106">SYNTAX</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>] [-SessionVariable <String>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-CertificateThumbprint <String>]
 [-Certificate <X509Certificate>] [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>]
 [-Headers <IDictionary>] [-MaximumRedirection <Int32>] [-Method <WebRequestMethod>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>] [-ContentType <String>]
 [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="1b386-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1b386-107">DESCRIPTION</span></span>

<span data-ttu-id="1b386-108">`Invoke-WebRequest`Cmdlet 會將 HTTP、HTTPS、FTP 和檔案要求傳送至網頁或 web 服務。</span><span class="sxs-lookup"><span data-stu-id="1b386-108">The `Invoke-WebRequest` cmdlet sends HTTP, HTTPS, FTP, and FILE requests to a web page or web service.</span></span>
<span data-ttu-id="1b386-109">它會剖析回應並傳回表單、連結、影像及其他主要 HTML 元素的集合。</span><span class="sxs-lookup"><span data-stu-id="1b386-109">It parses the response and returns collections of forms, links, images, and other significant HTML elements.</span></span>

<span data-ttu-id="1b386-110">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="1b386-110">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="1b386-111">根據預設，當剖析頁面以填入屬性時，可能會執行網頁中的腳本程式碼 `ParsedHtml` 。</span><span class="sxs-lookup"><span data-stu-id="1b386-111">By default, script code in the web page may be run when the page is being parsed to populate the `ParsedHtml` property.</span></span>
> <span data-ttu-id="1b386-112">使用 `-UseBasicParsing` 參數來隱藏此。</span><span class="sxs-lookup"><span data-stu-id="1b386-112">Use the `-UseBasicParsing` switch to suppress this.</span></span>

## <span data-ttu-id="1b386-113">範例</span><span class="sxs-lookup"><span data-stu-id="1b386-113">EXAMPLES</span></span>

### <span data-ttu-id="1b386-114">範例1：傳送 web 要求</span><span class="sxs-lookup"><span data-stu-id="1b386-114">Example 1: Send a web request</span></span>

<span data-ttu-id="1b386-115">此命令會使用 `Invoke-WebRequest` Cmdlet 將 web 要求傳送至 Bing.com 網站。</span><span class="sxs-lookup"><span data-stu-id="1b386-115">This command uses the `Invoke-WebRequest` cmdlet to send a web request to the Bing.com site.</span></span>

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

<span data-ttu-id="1b386-116">第一個命令會發出要求，並將回應儲存在 `$R` 變數中。</span><span class="sxs-lookup"><span data-stu-id="1b386-116">The first command issues the request and saves the response in the `$R` variable.</span></span>

<span data-ttu-id="1b386-117">第二個命令會篩選 **AllElements** 屬性中的物件，其中 **name** 屬性類似于 "\* Value"，而 **tagName** 為 "INPUT"。</span><span class="sxs-lookup"><span data-stu-id="1b386-117">The second command filters the objects in the **AllElements** property where the **name** property is like "\* Value" and the **tagName** is "INPUT".</span></span> <span data-ttu-id="1b386-118">篩選後的結果會以管道傳送至， `Select-Object` 以選取 [ **名稱** ] 和 [ **值** ] 屬性。</span><span class="sxs-lookup"><span data-stu-id="1b386-118">The filtered results are piped to `Select-Object` to select the **name** and **value** properties.</span></span>

### <span data-ttu-id="1b386-119">範例2：使用具狀態的 web 服務</span><span class="sxs-lookup"><span data-stu-id="1b386-119">Example 2: Use a stateful web service</span></span>

<span data-ttu-id="1b386-120">此範例示範如何使用 Cmdlet 搭配可設定 `Invoke-WebRequest` 狀態的 web 服務，例如 Facebook。</span><span class="sxs-lookup"><span data-stu-id="1b386-120">This example shows how to use the `Invoke-WebRequest` cmdlet with a stateful web service, such as Facebook.</span></span>

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

<span data-ttu-id="1b386-121">第一個命令會使用 `Invoke-WebRequest` Cmdlet 來傳送登入要求。</span><span class="sxs-lookup"><span data-stu-id="1b386-121">The first command uses the `Invoke-WebRequest` cmdlet to send a sign-in request.</span></span> <span data-ttu-id="1b386-122">此命令會為 **SessionVariable** 參數的值指定 "FB" 值，並將結果儲存在 `$R` 變數中。</span><span class="sxs-lookup"><span data-stu-id="1b386-122">The command specifies a value of "FB" for the value of the **SessionVariable** parameter, and saves the result in the `$R` variable.</span></span> <span data-ttu-id="1b386-123">當命令完成時， `$R` 變數會包含 **htmlwebresponseobject links** ，而且 `$FB` 變數包含 **WebRequestSession** 物件。</span><span class="sxs-lookup"><span data-stu-id="1b386-123">When the command completes, the `$R` variable contains an **HtmlWebResponseObject** and the `$FB` variable contains a **WebRequestSession** object.</span></span>

<span data-ttu-id="1b386-124">在 `Invoke-WebRequest` Cmdlet 登入 facebook 之後，變數中 web 回應物件的 **StatusDescription** 屬性 `$R` 會指出使用者已成功登入。</span><span class="sxs-lookup"><span data-stu-id="1b386-124">After the `Invoke-WebRequest` cmdlet signs in to facebook, the **StatusDescription** property of the web response object in the `$R` variable indicates that the user is signed in successfully.</span></span>

### <span data-ttu-id="1b386-125">範例3：取得網頁的連結</span><span class="sxs-lookup"><span data-stu-id="1b386-125">Example 3: Get links from a web page</span></span>

<span data-ttu-id="1b386-126">此命令會取得網頁中的連結。</span><span class="sxs-lookup"><span data-stu-id="1b386-126">This command gets the links in a web page.</span></span>

```powershell
(Invoke-WebRequest -Uri "https://devblogs.microsoft.com/powershell/").Links.Href
```

<span data-ttu-id="1b386-127">`Invoke-WebRequest`Cmdlet 會取得網頁內容。</span><span class="sxs-lookup"><span data-stu-id="1b386-127">The `Invoke-WebRequest` cmdlet gets the web page content.</span></span> <span data-ttu-id="1b386-128">然後，傳回之 **htmlwebresponseobject links** 的 **Links** 屬性會用來顯示每個連結的 **Href** 屬性。</span><span class="sxs-lookup"><span data-stu-id="1b386-128">Then the **Links** property of the returned **HtmlWebResponseObject** is used to display the **Href** property of each link.</span></span>

### <span data-ttu-id="1b386-129">範例4：攔截 Invoke-WebRequest 的非成功訊息</span><span class="sxs-lookup"><span data-stu-id="1b386-129">Example 4: Catch non success messages from Invoke-WebRequest</span></span>

<span data-ttu-id="1b386-130">當 `Invoke-WebRequest` (404、500等 ) 遇到非成功的 HTTP 訊息時，它不會傳回任何輸出並擲回終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="1b386-130">When `Invoke-WebRequest` encounters a non-success HTTP message (404, 500, etc.), it returns no output and throws a terminating error.</span></span> <span data-ttu-id="1b386-131">若要攔截錯誤並查看 **StatusCode** ，您可以在區塊中包含執行 `try/catch` 。</span><span class="sxs-lookup"><span data-stu-id="1b386-131">To catch the error and view the **StatusCode** you can enclose execution in a `try/catch` block.</span></span> <span data-ttu-id="1b386-132">下列範例顯示如何完成這項工作。</span><span class="sxs-lookup"><span data-stu-id="1b386-132">The following example shows how to accomplish this.</span></span>

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

<span data-ttu-id="1b386-133">第一個命令會 `Invoke-WebRequest` 以 **Stop** 的 **ErrorAction** 呼叫，這會 `Invoke-WebRequest` 在任何失敗的要求上強制擲回終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="1b386-133">The first command calls `Invoke-WebRequest` with an **ErrorAction** of **Stop** , which forces `Invoke-WebRequest` to throw a terminating error on any failed requests.</span></span> <span data-ttu-id="1b386-134">`catch`從 **例外** 狀況物件抓取 **StatusCode** 的區塊攔截到終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="1b386-134">The terminating error is caught by the `catch` block which retrieves the **StatusCode** from the **Exception** object.</span></span>

## <span data-ttu-id="1b386-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1b386-135">PARAMETERS</span></span>

### <span data-ttu-id="1b386-136">-Body</span><span class="sxs-lookup"><span data-stu-id="1b386-136">-Body</span></span>

<span data-ttu-id="1b386-137">指定要求的主體。</span><span class="sxs-lookup"><span data-stu-id="1b386-137">Specifies the body of the request.</span></span>
<span data-ttu-id="1b386-138">主體為標頭之後的要求內容。</span><span class="sxs-lookup"><span data-stu-id="1b386-138">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="1b386-139">您也可以使用管線將主體值傳送至 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="1b386-139">You can also pipe a body value to `Invoke-WebRequest`.</span></span>

<span data-ttu-id="1b386-140">**Body** 參數可用來指定查詢參數的清單，或指定回應的內容。</span><span class="sxs-lookup"><span data-stu-id="1b386-140">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="1b386-141">當輸入為 GET 要求且主體為 **IDictionary** (通常會) 雜湊表，主體會新增至 URI 作為查詢參數。</span><span class="sxs-lookup"><span data-stu-id="1b386-141">When the input is a GET request and the body is an **IDictionary** (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="1b386-142">針對其他 GET 要求，主體會設定為標準格式的要求主體值 `name=value` 。</span><span class="sxs-lookup"><span data-stu-id="1b386-142">For other GET requests, the body is set as the value of the request body in the standard `name=value` format.</span></span>

<span data-ttu-id="1b386-143">當主體為表單，或其為呼叫的輸出時 `Invoke-WebRequest` ，PowerShell 會將要求內容設定為表單欄位。</span><span class="sxs-lookup"><span data-stu-id="1b386-143">When the body is a form, or it is the output of an `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>
<span data-ttu-id="1b386-144">例如：</span><span class="sxs-lookup"><span data-stu-id="1b386-144">For example:</span></span>

`$r = Invoke-WebRequest https://website.com/login.aspx`
`$r.Forms\[0\].Name = "MyName"`
`$r.Forms\[0\].Password = "MyPassword"`
`Invoke-RestMethod https://website.com/service.aspx -Body $r`

- <span data-ttu-id="1b386-145">或 -</span><span class="sxs-lookup"><span data-stu-id="1b386-145">or -</span></span>

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

### <span data-ttu-id="1b386-146">-Certificate</span><span class="sxs-lookup"><span data-stu-id="1b386-146">-Certificate</span></span>

<span data-ttu-id="1b386-147">指定用於安全 Web 要求的用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="1b386-147">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="1b386-148">輸入包含憑證的變數，或可取得憑證的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="1b386-148">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="1b386-149">若要尋找憑證，請使用 `Get-PfxCertificate` 或使用 `Get-ChildItem` **憑證** (`Cert:`) 磁片磁碟機中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1b386-149">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the **Certificate** (`Cert:`) drive.</span></span> <span data-ttu-id="1b386-150">若憑證無效或權限不足，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="1b386-150">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="1b386-151">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="1b386-151">-CertificateThumbprint</span></span>

<span data-ttu-id="1b386-152">指定具有傳送要求權限之使用者帳戶的數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="1b386-152">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="1b386-153">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="1b386-153">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="1b386-154">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="1b386-154">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="1b386-155">這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="1b386-155">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="1b386-156">若要取得憑證指紋，請使用 `Get-Item` `Get-ChildItem` PowerShell 磁片磁碟機中的或命令 `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="1b386-156">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

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

### <span data-ttu-id="1b386-157">-ContentType</span><span class="sxs-lookup"><span data-stu-id="1b386-157">-ContentType</span></span>

<span data-ttu-id="1b386-158">指定 Web 要求的內容類型。</span><span class="sxs-lookup"><span data-stu-id="1b386-158">Specifies the content type of the web request.</span></span>

<span data-ttu-id="1b386-159">如果省略此參數且要求方法為 POST，則會 `Invoke-WebRequest` 將內容類型設定為 application/x-www 表單-urlencoded。</span><span class="sxs-lookup"><span data-stu-id="1b386-159">If this parameter is omitted and the request method is POST, `Invoke-WebRequest` sets the content type to application/x-www-form-urlencoded.</span></span> <span data-ttu-id="1b386-160">否則，呼叫中不會指定內容類型。</span><span class="sxs-lookup"><span data-stu-id="1b386-160">Otherwise, the content type is not specified in the call.</span></span>

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

### <span data-ttu-id="1b386-161">-Credential</span><span class="sxs-lookup"><span data-stu-id="1b386-161">-Credential</span></span>

<span data-ttu-id="1b386-162">指定具有傳送要求權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="1b386-162">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="1b386-163">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="1b386-163">The default is the current user.</span></span>

<span data-ttu-id="1b386-164">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="1b386-164">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="1b386-165">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="1b386-165">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="1b386-166">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="1b386-166">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="1b386-167">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="1b386-167">-DisableKeepAlive</span></span>

<span data-ttu-id="1b386-168">指出此 Cmdlet 會將 HTTP 標頭中的 **KeepAlive** 值設定為 **False** 。</span><span class="sxs-lookup"><span data-stu-id="1b386-168">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to **False** .</span></span> <span data-ttu-id="1b386-169">**KeepAlive** 預設為 **True** 。</span><span class="sxs-lookup"><span data-stu-id="1b386-169">By default, **KeepAlive** is **True** .</span></span> <span data-ttu-id="1b386-170">**KeepAlive** 會建立伺服器持續連線，有助於後續要求。</span><span class="sxs-lookup"><span data-stu-id="1b386-170">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="1b386-171">-Headers</span><span class="sxs-lookup"><span data-stu-id="1b386-171">-Headers</span></span>

<span data-ttu-id="1b386-172">指定 Web 要求的標頭。</span><span class="sxs-lookup"><span data-stu-id="1b386-172">Specifies the headers of the web request.</span></span> <span data-ttu-id="1b386-173">輸入雜湊表或字典。</span><span class="sxs-lookup"><span data-stu-id="1b386-173">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="1b386-174">若要設定 **UserAgent** 標頭，請使用 **UserAgent** 參數。</span><span class="sxs-lookup"><span data-stu-id="1b386-174">To set **UserAgent** headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="1b386-175">您無法使用此參數指定 **UserAgent** 或 cookie 標頭。</span><span class="sxs-lookup"><span data-stu-id="1b386-175">You cannot use this parameter to specify **UserAgent** or cookie headers.</span></span>

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

### <span data-ttu-id="1b386-176">-InFile</span><span class="sxs-lookup"><span data-stu-id="1b386-176">-InFile</span></span>

<span data-ttu-id="1b386-177">從檔案取得 Web 要求的內容。</span><span class="sxs-lookup"><span data-stu-id="1b386-177">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="1b386-178">輸入路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="1b386-178">Enter a path and file name.</span></span> <span data-ttu-id="1b386-179">若省略路徑，則預設為目前位置。</span><span class="sxs-lookup"><span data-stu-id="1b386-179">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="1b386-180">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="1b386-180">-MaximumRedirection</span></span>

<span data-ttu-id="1b386-181">指定在連接失敗之前，PowerShell 將連接重新導向至替代統一資源識別項 (URI) 的次數。</span><span class="sxs-lookup"><span data-stu-id="1b386-181">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="1b386-182">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="1b386-182">The default value is 5.</span></span> <span data-ttu-id="1b386-183">值為 0 (零) 將禁止所有重新導向。</span><span class="sxs-lookup"><span data-stu-id="1b386-183">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="1b386-184">-Method</span><span class="sxs-lookup"><span data-stu-id="1b386-184">-Method</span></span>

<span data-ttu-id="1b386-185">指定用於 Web 要求的方法。</span><span class="sxs-lookup"><span data-stu-id="1b386-185">Specifies the method used for the web request.</span></span> <span data-ttu-id="1b386-186">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="1b386-186">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1b386-187">預設</span><span class="sxs-lookup"><span data-stu-id="1b386-187">Default</span></span>
- <span data-ttu-id="1b386-188">刪除</span><span class="sxs-lookup"><span data-stu-id="1b386-188">Delete</span></span>
- <span data-ttu-id="1b386-189">Get</span><span class="sxs-lookup"><span data-stu-id="1b386-189">Get</span></span>
- <span data-ttu-id="1b386-190">Head</span><span class="sxs-lookup"><span data-stu-id="1b386-190">Head</span></span>
- <span data-ttu-id="1b386-191">合併</span><span class="sxs-lookup"><span data-stu-id="1b386-191">Merge</span></span>
- <span data-ttu-id="1b386-192">選項</span><span class="sxs-lookup"><span data-stu-id="1b386-192">Options</span></span>
- <span data-ttu-id="1b386-193">Patch</span><span class="sxs-lookup"><span data-stu-id="1b386-193">Patch</span></span>
- <span data-ttu-id="1b386-194">郵寄</span><span class="sxs-lookup"><span data-stu-id="1b386-194">Post</span></span>
- <span data-ttu-id="1b386-195">Put</span><span class="sxs-lookup"><span data-stu-id="1b386-195">Put</span></span>
- <span data-ttu-id="1b386-196">追蹤</span><span class="sxs-lookup"><span data-stu-id="1b386-196">Trace</span></span>

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

### <span data-ttu-id="1b386-197">-OutFile</span><span class="sxs-lookup"><span data-stu-id="1b386-197">-OutFile</span></span>

<span data-ttu-id="1b386-198">指定此 Cmdlet 儲存回應主體的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="1b386-198">Specifies the output file for which this cmdlet saves the response body.</span></span> <span data-ttu-id="1b386-199">輸入路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="1b386-199">Enter a path and file name.</span></span>
<span data-ttu-id="1b386-200">若省略路徑，則預設為目前位置。</span><span class="sxs-lookup"><span data-stu-id="1b386-200">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="1b386-201">依預設，會將 `Invoke-WebRequest` 結果傳回至管線。</span><span class="sxs-lookup"><span data-stu-id="1b386-201">By default, `Invoke-WebRequest` returns the results to the pipeline.</span></span> <span data-ttu-id="1b386-202">若要傳送結果至檔案與管線，請使用 **Passthru** 參數。</span><span class="sxs-lookup"><span data-stu-id="1b386-202">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="1b386-203">-PassThru</span><span class="sxs-lookup"><span data-stu-id="1b386-203">-PassThru</span></span>

<span data-ttu-id="1b386-204">指出除了將結果寫入檔案之外，指令程式還會傳回結果。</span><span class="sxs-lookup"><span data-stu-id="1b386-204">Indicates that the cmdlet returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="1b386-205">只有當命令中也使用 **OutFile** 參數時，此參數才會有效。</span><span class="sxs-lookup"><span data-stu-id="1b386-205">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="1b386-206">-Proxy</span><span class="sxs-lookup"><span data-stu-id="1b386-206">-Proxy</span></span>

<span data-ttu-id="1b386-207">指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="1b386-207">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>
<span data-ttu-id="1b386-208">輸入網路 Proxy 伺服器的 URI。</span><span class="sxs-lookup"><span data-stu-id="1b386-208">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="1b386-209">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="1b386-209">-ProxyCredential</span></span>

<span data-ttu-id="1b386-210">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="1b386-210">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="1b386-211">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="1b386-211">The default is the current user.</span></span>

<span data-ttu-id="1b386-212">輸入使用者名稱（例如 `User01` 或）， `Domain01\User01` 或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="1b386-212">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="1b386-213">只有當命令中也使用 **Proxy** 參數時，此參數才會有效。</span><span class="sxs-lookup"><span data-stu-id="1b386-213">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="1b386-214">您無法在相同命令中使用 **ProxyCredential** 與 **ProxyUseDefaultCredentials** 參數。</span><span class="sxs-lookup"><span data-stu-id="1b386-214">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="1b386-215">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="1b386-215">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="1b386-216">指出此 Cmdlet 會使用目前使用者的認證來存取 **proxy** 參數所指定的 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="1b386-216">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="1b386-217">只有當命令中也使用 **Proxy** 參數時，此參數才會有效。</span><span class="sxs-lookup"><span data-stu-id="1b386-217">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="1b386-218">您無法在相同命令中使用 **ProxyCredential** 與 **ProxyUseDefaultCredentials** 參數。</span><span class="sxs-lookup"><span data-stu-id="1b386-218">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="1b386-219">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="1b386-219">-SessionVariable</span></span>

<span data-ttu-id="1b386-220">指定此 Cmdlet 會建立 web 要求會話，並將其儲存在值中的變數。</span><span class="sxs-lookup"><span data-stu-id="1b386-220">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="1b386-221">輸入不含貨幣符號 () 符號的變數名稱 `$` 。</span><span class="sxs-lookup"><span data-stu-id="1b386-221">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="1b386-222">當您指定會話變數時，會 `Invoke-WebRequest` 建立 web 要求會話物件，並將它指派給您的 PowerShell 會話中具有指定名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="1b386-222">When you specify a session variable, `Invoke-WebRequest` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="1b386-223">一旦命令完成，便可在工作階段中使用變數。</span><span class="sxs-lookup"><span data-stu-id="1b386-223">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="1b386-224">Web 要求工作階段不同於遠端工作階段，並非持續連線。</span><span class="sxs-lookup"><span data-stu-id="1b386-224">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="1b386-225">它是包含連線與要求相關資訊的物件，這些資訊包括 Cookie、認證、重新導向上限值，以及使用者代理字串。</span><span class="sxs-lookup"><span data-stu-id="1b386-225">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="1b386-226">您可以使用它在 Web 要求之間共用狀態與資料。</span><span class="sxs-lookup"><span data-stu-id="1b386-226">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="1b386-227">若要在後續 Web 要求中使用 Web 要求工作階段，請在 **WebSession** 參數值指定工作階段變數。</span><span class="sxs-lookup"><span data-stu-id="1b386-227">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="1b386-228">建立新連接時，PowerShell 會使用 web 要求會話物件中的資料。</span><span class="sxs-lookup"><span data-stu-id="1b386-228">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="1b386-229">若要覆寫 Web 要求工作階段中的值，請使用 Cmdlet 參數，例如 **UserAgent** 或 **Credential** 。</span><span class="sxs-lookup"><span data-stu-id="1b386-229">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="1b386-230">參數值的優先順序高於 Web 要求工作階段中的值。</span><span class="sxs-lookup"><span data-stu-id="1b386-230">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="1b386-231">您不能在同一個命令中使用 **SessionVariable** 和 **WebSession** 參數。</span><span class="sxs-lookup"><span data-stu-id="1b386-231">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="1b386-232">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="1b386-232">-TimeoutSec</span></span>

<span data-ttu-id="1b386-233">指定要求可在一段時間之前暫止的時間長度。輸入以秒為單位的值。</span><span class="sxs-lookup"><span data-stu-id="1b386-233">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="1b386-234">預設值為 0，會指定無限逾時。</span><span class="sxs-lookup"><span data-stu-id="1b386-234">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="1b386-235">網域名稱系統 (DNS) 查詢最多可能需要15秒的時間才會傳回或超時。如果您的要求包含需要解析的主機名稱，而且您將 **TimeoutSec** 設定為大於零的值，但不超過15秒，則在擲回 **WebException** 之前，可能需要15秒或更長的時間，而且您的要求超時。</span><span class="sxs-lookup"><span data-stu-id="1b386-235">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a **WebException** is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="1b386-236">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="1b386-236">-TransferEncoding</span></span>

<span data-ttu-id="1b386-237">指定傳輸編碼 HTTP 回應標頭的值。</span><span class="sxs-lookup"><span data-stu-id="1b386-237">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="1b386-238">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="1b386-238">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1b386-239">區塊</span><span class="sxs-lookup"><span data-stu-id="1b386-239">Chunked</span></span>
- <span data-ttu-id="1b386-240">壓縮</span><span class="sxs-lookup"><span data-stu-id="1b386-240">Compress</span></span>
- <span data-ttu-id="1b386-241">上下凹陷</span><span class="sxs-lookup"><span data-stu-id="1b386-241">Deflate</span></span>
- <span data-ttu-id="1b386-242">GZip</span><span class="sxs-lookup"><span data-stu-id="1b386-242">GZip</span></span>
- <span data-ttu-id="1b386-243">身分識別</span><span class="sxs-lookup"><span data-stu-id="1b386-243">Identity</span></span>

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

### <span data-ttu-id="1b386-244">-Uri</span><span class="sxs-lookup"><span data-stu-id="1b386-244">-Uri</span></span>

<span data-ttu-id="1b386-245">指定 Web 要求傳送目的地的網際網路資源「統一資源識別項 (URI)」。</span><span class="sxs-lookup"><span data-stu-id="1b386-245">Specifies the Uniform Resource Identifier (URI) of the Internet resource to which the web request is sent.</span></span> <span data-ttu-id="1b386-246">輸入 URI。</span><span class="sxs-lookup"><span data-stu-id="1b386-246">Enter a URI.</span></span> <span data-ttu-id="1b386-247">此參數支援 HTTP、HTTPS、FTP 與 FILE 值。</span><span class="sxs-lookup"><span data-stu-id="1b386-247">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="1b386-248">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="1b386-248">This parameter is required.</span></span>

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

### <span data-ttu-id="1b386-249">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="1b386-249">-UseBasicParsing</span></span>

<span data-ttu-id="1b386-250">指出 Cmdlet 使用 HTML 內容的回應物件，而不檔物件模型 (DOM) 剖析。</span><span class="sxs-lookup"><span data-stu-id="1b386-250">Indicates that the cmdlet uses the response object for HTML content without Document Object Model (DOM) parsing.</span></span> <span data-ttu-id="1b386-251">當電腦上沒有安裝 Internet Explorer 時，此參數為必要參數，例如在 Windows Server 作業系統的 Server Core 安裝上。</span><span class="sxs-lookup"><span data-stu-id="1b386-251">This parameter is required when Internet Explorer is not installed on the computers, such as on a Server Core installation of a Windows Server operating system.</span></span>

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

### <span data-ttu-id="1b386-252">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="1b386-252">-UseDefaultCredentials</span></span>

<span data-ttu-id="1b386-253">表示 cmdet 會使用目前使用者的認證來傳送 web 要求。</span><span class="sxs-lookup"><span data-stu-id="1b386-253">Indicates that the cmdet uses the credentials of the current user to send the web request.</span></span>

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

### <span data-ttu-id="1b386-254">-UserAgent</span><span class="sxs-lookup"><span data-stu-id="1b386-254">-UserAgent</span></span>

<span data-ttu-id="1b386-255">指定 Web 要求的使用者代理字串。</span><span class="sxs-lookup"><span data-stu-id="1b386-255">Specifies a user agent string for the web request.</span></span> <span data-ttu-id="1b386-256">預設使用者代理程式類似于 `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` 每個作業系統和平臺的些許變化。</span><span class="sxs-lookup"><span data-stu-id="1b386-256">The default user agent is similar to `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="1b386-257">若要使用大部分網際網路瀏覽器所使用的標準使用者代理程式字串來測試網站，請使用 [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) 類別的屬性，例如 Chrome、FireFox、Microsoft-windows-ie-internetexplorer、Opera 和 Safari。</span><span class="sxs-lookup"><span data-stu-id="1b386-257">To test a website with the standard user agent string that is used by most Internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span> <span data-ttu-id="1b386-258">例如，下列命令會使用使用者代理字串進行 Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="1b386-258">For example, the following command uses the user agent string for Internet Explorer</span></span>

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

### <span data-ttu-id="1b386-259">-WebSession</span><span class="sxs-lookup"><span data-stu-id="1b386-259">-WebSession</span></span>

<span data-ttu-id="1b386-260">指定 Web 要求工作階段。</span><span class="sxs-lookup"><span data-stu-id="1b386-260">Specifies a web request session.</span></span> <span data-ttu-id="1b386-261">輸入變數名稱，包括貨幣符號 (`$`) 。</span><span class="sxs-lookup"><span data-stu-id="1b386-261">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="1b386-262">若要覆寫 Web 要求工作階段中的值，請使用 Cmdlet 參數，例如 **UserAgent** 或 **Credential** 。</span><span class="sxs-lookup"><span data-stu-id="1b386-262">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="1b386-263">參數值的優先順序高於 Web 要求工作階段中的值。</span><span class="sxs-lookup"><span data-stu-id="1b386-263">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="1b386-264">Web 要求工作階段不同於遠端工作階段，並非持續連線。</span><span class="sxs-lookup"><span data-stu-id="1b386-264">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="1b386-265">它是包含連線與要求相關資訊的物件，這些資訊包括 Cookie、認證、重新導向上限值，以及使用者代理字串。</span><span class="sxs-lookup"><span data-stu-id="1b386-265">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="1b386-266">您可以使用它在 Web 要求之間共用狀態與資料。</span><span class="sxs-lookup"><span data-stu-id="1b386-266">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="1b386-267">若要建立 web 要求會話，請在命令的 **SessionVariable** 參數值中輸入不含貨幣正負號)  (變數名稱 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="1b386-267">To create a web request session, enter a variable name (without a dollar sign) in the value of the **SessionVariable** parameter of an `Invoke-WebRequest` command.</span></span> <span data-ttu-id="1b386-268">`Invoke-WebRequest` 建立會話，並將它儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="1b386-268">`Invoke-WebRequest` creates the session and saves it in the variable.</span></span> <span data-ttu-id="1b386-269">在後續命令中，使用變數作為 **WebSession** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="1b386-269">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="1b386-270">您不能在同一個命令中使用 **SessionVariable** 和 **WebSession** 參數。</span><span class="sxs-lookup"><span data-stu-id="1b386-270">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="1b386-271">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1b386-271">CommonParameters</span></span>

<span data-ttu-id="1b386-272">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="1b386-272">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="1b386-273">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="1b386-273">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1b386-274">輸入</span><span class="sxs-lookup"><span data-stu-id="1b386-274">INPUTS</span></span>

### <span data-ttu-id="1b386-275">System.Object</span><span class="sxs-lookup"><span data-stu-id="1b386-275">System.Object</span></span>

<span data-ttu-id="1b386-276">您可以使用管線將 web 要求的主體傳送至 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="1b386-276">You can pipe the body of a web request to `Invoke-WebRequest`.</span></span>

## <span data-ttu-id="1b386-277">輸出</span><span class="sxs-lookup"><span data-stu-id="1b386-277">OUTPUTS</span></span>

### <span data-ttu-id="1b386-278">Microsoft.PowerShell.Commands.HtmlWebResponseObject</span><span class="sxs-lookup"><span data-stu-id="1b386-278">Microsoft.PowerShell.Commands.HtmlWebResponseObject</span></span>

## <span data-ttu-id="1b386-279">注意</span><span class="sxs-lookup"><span data-stu-id="1b386-279">NOTES</span></span>

## <span data-ttu-id="1b386-280">相關連結</span><span class="sxs-lookup"><span data-stu-id="1b386-280">RELATED LINKS</span></span>

[<span data-ttu-id="1b386-281">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="1b386-281">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="1b386-282">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="1b386-282">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="1b386-283">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="1b386-283">ConvertTo-Json</span></span>](ConvertTo-Json.md)
