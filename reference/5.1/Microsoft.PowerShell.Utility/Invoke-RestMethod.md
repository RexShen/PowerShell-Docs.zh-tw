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
# <span data-ttu-id="520e7-103">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="520e7-103">Invoke-RestMethod</span></span>

## <span data-ttu-id="520e7-104">概要</span><span class="sxs-lookup"><span data-stu-id="520e7-104">Synopsis</span></span>
<span data-ttu-id="520e7-105">傳送 HTTP 或 HTTPS 要求至 RESTful Web 服務。</span><span class="sxs-lookup"><span data-stu-id="520e7-105">Sends an HTTP or HTTPS request to a RESTful web service.</span></span>

## <span data-ttu-id="520e7-106">語法</span><span class="sxs-lookup"><span data-stu-id="520e7-106">Syntax</span></span>

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-CertificateThumbprint <String>] [-Certificate <X509Certificate>]
 [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>] [-Headers <IDictionary>]
 [-MaximumRedirection <Int32>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials]
 [-Body <Object>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>]
 [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="520e7-107">描述</span><span class="sxs-lookup"><span data-stu-id="520e7-107">Description</span></span>

<span data-ttu-id="520e7-108">`Invoke-RestMethod`指令程式會將 HTTP 和 HTTPS 要求傳送至具象狀態傳輸 (REST) web 服務，以傳回豐富的結構化資料。</span><span class="sxs-lookup"><span data-stu-id="520e7-108">The `Invoke-RestMethod` cmdlet sends HTTP and HTTPS requests to Representational State Transfer (REST) web services that returns richly structured data.</span></span>

<span data-ttu-id="520e7-109">Windows PowerShell 會根據資料類型設定回應格式。</span><span class="sxs-lookup"><span data-stu-id="520e7-109">Windows PowerShell formats the response based to the data type.</span></span> <span data-ttu-id="520e7-110">對於 RSS 或 ATOM 摘要，Windows PowerShell 會傳回項目 XML 節點。</span><span class="sxs-lookup"><span data-stu-id="520e7-110">For an RSS or ATOM feed, Windows PowerShell returns the Item or Entry XML nodes.</span></span> <span data-ttu-id="520e7-111">對於 JavaScript Object Notation (JSON) 或 XML，Windows PowerShell 會將內容轉換 (或還原序列化) 為物件。</span><span class="sxs-lookup"><span data-stu-id="520e7-111">For JavaScript Object Notation (JSON) or XML, Windows PowerShell converts (or deserializes) the content into objects.</span></span>

<span data-ttu-id="520e7-112">此 Cmdlet 是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="520e7-112">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="520e7-113">根據預設，當剖析頁面以填入屬性時，可能會執行網頁中的腳本程式碼 `ParsedHtml` 。</span><span class="sxs-lookup"><span data-stu-id="520e7-113">By default, script code in the web page may be run when the page is being parsed to populate the `ParsedHtml` property.</span></span> <span data-ttu-id="520e7-114">使用 **UseBasicParsing** 參數來隱藏此。</span><span class="sxs-lookup"><span data-stu-id="520e7-114">Use the **UseBasicParsing** switch to suppress this.</span></span>

## <span data-ttu-id="520e7-115">範例</span><span class="sxs-lookup"><span data-stu-id="520e7-115">Examples</span></span>

### <span data-ttu-id="520e7-116">範例1：取得 PowerShell RSS 摘要</span><span class="sxs-lookup"><span data-stu-id="520e7-116">Example 1: Get the PowerShell RSS feed</span></span>

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

<span data-ttu-id="520e7-117">此命令會使用 `Invoke-RestMethod` Cmdlet 來取得來自 PowerShell BLOG rss 摘要的資訊。</span><span class="sxs-lookup"><span data-stu-id="520e7-117">This command uses the `Invoke-RestMethod` cmdlet to get information from the PowerShell Blog RSS feed.</span></span> <span data-ttu-id="520e7-118">此命令會使用 `Format-Table` Cmdlet，在資料表中顯示每個 blog 的 **Title** 和 **pubDate** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="520e7-118">The command uses the `Format-Table` cmdlet to display the values of the **Title** and **pubDate** properties of each blog in a table.</span></span>

### <span data-ttu-id="520e7-119">範例 2</span><span class="sxs-lookup"><span data-stu-id="520e7-119">Example 2</span></span>

<span data-ttu-id="520e7-120">在下列範例中，使用者會 `Invoke-RestMethod` 執行，以在使用者組織內部網路網站上執行 POST 要求。</span><span class="sxs-lookup"><span data-stu-id="520e7-120">In the following example, a user runs `Invoke-RestMethod` to perform a POST request on an intranet website in the user's organization.</span></span>

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

### <span data-ttu-id="520e7-121">範例3：傳遞多個標頭</span><span class="sxs-lookup"><span data-stu-id="520e7-121">Example 3: Pass multiple headers</span></span>

<span data-ttu-id="520e7-122">此範例示範如何將中的多個標頭傳遞 `hash-table` 至 REST API。</span><span class="sxs-lookup"><span data-stu-id="520e7-122">This example demonstrates, how to pass multiple headers in from a `hash-table` to a REST API.</span></span>

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

<span data-ttu-id="520e7-123">Api 通常需要經過傳遞的標頭以進行驗證、驗證等等。</span><span class="sxs-lookup"><span data-stu-id="520e7-123">APIs often require passed headers for authentication, validation etc.</span></span>

### <span data-ttu-id="520e7-124">範例3：提交表單資料</span><span class="sxs-lookup"><span data-stu-id="520e7-124">Example 3: Submitting form data</span></span>

<span data-ttu-id="520e7-125">當主體為表單，或它是另一個呼叫的輸出時 `Invoke-WebRequest` ，PowerShell 會將要求內容設定為表單欄位。</span><span class="sxs-lookup"><span data-stu-id="520e7-125">When the body is a form, or it is the output of another `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>

<span data-ttu-id="520e7-126">例如：</span><span class="sxs-lookup"><span data-stu-id="520e7-126">For example:</span></span>

```powershell
$R = Invoke-WebRequest https://website.com/login.aspx
$R.Forms[0].Name = "MyName"
$R.Forms[0].Password = "MyPassword"
Invoke-RestMethod https://website.com/service.aspx -Body $R.Forms[0]
```

## <span data-ttu-id="520e7-127">參數</span><span class="sxs-lookup"><span data-stu-id="520e7-127">Parameters</span></span>

### <span data-ttu-id="520e7-128">-Body</span><span class="sxs-lookup"><span data-stu-id="520e7-128">-Body</span></span>

<span data-ttu-id="520e7-129">指定要求的主體。</span><span class="sxs-lookup"><span data-stu-id="520e7-129">Specifies the body of the request.</span></span> <span data-ttu-id="520e7-130">主體為標頭之後的要求內容。</span><span class="sxs-lookup"><span data-stu-id="520e7-130">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="520e7-131">您也可以使用管線將主體值傳送至 `Invoke-RestMethod` 。</span><span class="sxs-lookup"><span data-stu-id="520e7-131">You can also pipe a body value to `Invoke-RestMethod`.</span></span>

<span data-ttu-id="520e7-132">**Body** 參數可用來指定查詢參數的清單，或指定回應的內容。</span><span class="sxs-lookup"><span data-stu-id="520e7-132">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="520e7-133">當輸入為 GET 要求且主體為 IDictionary (通常為雜湊表) 時，主體會新增至 URI 成為查詢參數。</span><span class="sxs-lookup"><span data-stu-id="520e7-133">When the input is a GET request, and the body is an IDictionary (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="520e7-134">對於其他要求類型 (例如，POST)，會以標準「名稱=值」格式將主體設定為要求主體的值。</span><span class="sxs-lookup"><span data-stu-id="520e7-134">For other request types (such as POST), the body is set as the value of the request body in the standard name=value format.</span></span>

> [!WARNING]
> <span data-ttu-id="520e7-135">POST 主體的詳細資訊輸出會以結尾 `with -1-byte payload` ，即使主體的大小是已知的，也會在 `Content-Length` HTTP 標頭中傳送。</span><span class="sxs-lookup"><span data-stu-id="520e7-135">The verbose output of a POST body will end with `with -1-byte payload`, even though the size of the body is both known and sent in the `Content-Length` HTTP header.</span></span>

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

### <span data-ttu-id="520e7-136">-Certificate</span><span class="sxs-lookup"><span data-stu-id="520e7-136">-Certificate</span></span>

<span data-ttu-id="520e7-137">指定用於安全 Web 要求的用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="520e7-137">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="520e7-138">輸入包含憑證的變數，或可取得憑證的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="520e7-138">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="520e7-139">若要尋找憑證，請使用 `Get-PfxCertificate` 或使用 `Get-ChildItem` 憑證 (`Cert:`) 磁片磁碟機中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="520e7-139">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="520e7-140">若憑證無效或權限不足，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="520e7-140">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="520e7-141">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="520e7-141">-CertificateThumbprint</span></span>

<span data-ttu-id="520e7-142">指定具有傳送要求權限之使用者帳戶的數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="520e7-142">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="520e7-143">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="520e7-143">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="520e7-144">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="520e7-144">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="520e7-145">這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="520e7-145">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="520e7-146">若要取得憑證指紋，請使用 `Get-Item` `Get-ChildItem` Windows PowerShell () 磁片磁碟機中的或命令 `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="520e7-146">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the Windows PowerShell (`Cert:`) drive.</span></span>

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

### <span data-ttu-id="520e7-147">-ContentType</span><span class="sxs-lookup"><span data-stu-id="520e7-147">-ContentType</span></span>

<span data-ttu-id="520e7-148">指定 Web 要求的內容類型。</span><span class="sxs-lookup"><span data-stu-id="520e7-148">Specifies the content type of the web request.</span></span>

<span data-ttu-id="520e7-149">如果省略此參數且要求方法為 POST，則會 `Invoke-RestMethod` 將內容類型設定為 "application/x-www-urlencoded"。</span><span class="sxs-lookup"><span data-stu-id="520e7-149">If this parameter is omitted and the request method is POST, `Invoke-RestMethod` sets the content type to "application/x-www-form-urlencoded".</span></span> <span data-ttu-id="520e7-150">否則，呼叫中不會指定內容類型。</span><span class="sxs-lookup"><span data-stu-id="520e7-150">Otherwise, the content type is not specified in the call.</span></span>

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

### <span data-ttu-id="520e7-151">-Credential</span><span class="sxs-lookup"><span data-stu-id="520e7-151">-Credential</span></span>

<span data-ttu-id="520e7-152">指定具有傳送要求權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="520e7-152">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="520e7-153">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="520e7-153">The default is the current user.</span></span>

<span data-ttu-id="520e7-154">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="520e7-154">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="520e7-155">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="520e7-155">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="520e7-156">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="520e7-156">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="520e7-157">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="520e7-157">-DisableKeepAlive</span></span>

<span data-ttu-id="520e7-158">將 HTTP 標頭中的 **KeepAlive** 值設為 False。</span><span class="sxs-lookup"><span data-stu-id="520e7-158">Sets the **KeepAlive** value in the HTTP header to False.</span></span> <span data-ttu-id="520e7-159">**KeepAlive** 預設為 True。</span><span class="sxs-lookup"><span data-stu-id="520e7-159">By default, **KeepAlive** is True.</span></span>
<span data-ttu-id="520e7-160">**KeepAlive** 會建立伺服器持續連線，有助於後續要求。</span><span class="sxs-lookup"><span data-stu-id="520e7-160">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="520e7-161">-Headers</span><span class="sxs-lookup"><span data-stu-id="520e7-161">-Headers</span></span>

<span data-ttu-id="520e7-162">指定 Web 要求的標頭。</span><span class="sxs-lookup"><span data-stu-id="520e7-162">Specifies the headers of the web request.</span></span> <span data-ttu-id="520e7-163">輸入雜湊表或字典。</span><span class="sxs-lookup"><span data-stu-id="520e7-163">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="520e7-164">若要設定 UserAgent 標頭，請使用 **UserAgent** 參數。</span><span class="sxs-lookup"><span data-stu-id="520e7-164">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="520e7-165">您無法使用此參數指定 UserAgent 或 Cookie 標頭。</span><span class="sxs-lookup"><span data-stu-id="520e7-165">You cannot use this parameter to specify UserAgent or cookie headers.</span></span>

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

### <span data-ttu-id="520e7-166">-InFile</span><span class="sxs-lookup"><span data-stu-id="520e7-166">-InFile</span></span>

<span data-ttu-id="520e7-167">從檔案取得 Web 要求的內容。</span><span class="sxs-lookup"><span data-stu-id="520e7-167">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="520e7-168">輸入路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="520e7-168">Enter a path and file name.</span></span> <span data-ttu-id="520e7-169">若省略路徑，則預設為目前位置。</span><span class="sxs-lookup"><span data-stu-id="520e7-169">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="520e7-170">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="520e7-170">-MaximumRedirection</span></span>

<span data-ttu-id="520e7-171">決定連線失敗之前，Windows PowerShell 可將連線重新導向至替代「統一資源識別項 (URI)」的次數。</span><span class="sxs-lookup"><span data-stu-id="520e7-171">Determines how many times Windows PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="520e7-172">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="520e7-172">The default value is 5.</span></span> <span data-ttu-id="520e7-173">值為 0 (零) 將禁止所有重新導向。</span><span class="sxs-lookup"><span data-stu-id="520e7-173">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="520e7-174">-Method</span><span class="sxs-lookup"><span data-stu-id="520e7-174">-Method</span></span>

<span data-ttu-id="520e7-175">指定用於 Web 要求的方法。</span><span class="sxs-lookup"><span data-stu-id="520e7-175">Specifies the method used for the web request.</span></span> <span data-ttu-id="520e7-176">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="520e7-176">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="520e7-177">預設</span><span class="sxs-lookup"><span data-stu-id="520e7-177">Default</span></span>
- <span data-ttu-id="520e7-178">刪除</span><span class="sxs-lookup"><span data-stu-id="520e7-178">Delete</span></span>
- <span data-ttu-id="520e7-179">Get</span><span class="sxs-lookup"><span data-stu-id="520e7-179">Get</span></span>
- <span data-ttu-id="520e7-180">Head</span><span class="sxs-lookup"><span data-stu-id="520e7-180">Head</span></span>
- <span data-ttu-id="520e7-181">合併</span><span class="sxs-lookup"><span data-stu-id="520e7-181">Merge</span></span>
- <span data-ttu-id="520e7-182">選項</span><span class="sxs-lookup"><span data-stu-id="520e7-182">Options</span></span>
- <span data-ttu-id="520e7-183">Patch</span><span class="sxs-lookup"><span data-stu-id="520e7-183">Patch</span></span>
- <span data-ttu-id="520e7-184">郵寄</span><span class="sxs-lookup"><span data-stu-id="520e7-184">Post</span></span>
- <span data-ttu-id="520e7-185">Put</span><span class="sxs-lookup"><span data-stu-id="520e7-185">Put</span></span>
- <span data-ttu-id="520e7-186">追蹤</span><span class="sxs-lookup"><span data-stu-id="520e7-186">Trace</span></span>

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

### <span data-ttu-id="520e7-187">-OutFile</span><span class="sxs-lookup"><span data-stu-id="520e7-187">-OutFile</span></span>

<span data-ttu-id="520e7-188">將回應主體儲存在指定的輸出檔中。</span><span class="sxs-lookup"><span data-stu-id="520e7-188">Saves the response body in the specified output file.</span></span> <span data-ttu-id="520e7-189">輸入路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="520e7-189">Enter a path and file name.</span></span> <span data-ttu-id="520e7-190">若省略路徑，則預設為目前位置。</span><span class="sxs-lookup"><span data-stu-id="520e7-190">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="520e7-191">依預設，會將 `Invoke-RestMethod` 結果傳回至管線。</span><span class="sxs-lookup"><span data-stu-id="520e7-191">By default, `Invoke-RestMethod` returns the results to the pipeline.</span></span> <span data-ttu-id="520e7-192">若要傳送結果至檔案與管線，請使用 **Passthru** 參數。</span><span class="sxs-lookup"><span data-stu-id="520e7-192">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="520e7-193">-PassThru</span><span class="sxs-lookup"><span data-stu-id="520e7-193">-PassThru</span></span>

<span data-ttu-id="520e7-194">除了將結果寫入檔案，也會傳回結果。</span><span class="sxs-lookup"><span data-stu-id="520e7-194">Returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="520e7-195">只有當命令中也使用 **OutFile** 參數時，此參數才會有效。</span><span class="sxs-lookup"><span data-stu-id="520e7-195">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="520e7-196">-Proxy</span><span class="sxs-lookup"><span data-stu-id="520e7-196">-Proxy</span></span>

<span data-ttu-id="520e7-197">對於要求使用 Proxy 伺服器，而不是直接連線網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="520e7-197">Uses a proxy server for the request, rather than connecting directly to the Internet resource.</span></span> <span data-ttu-id="520e7-198">輸入網路 Proxy 伺服器的 URI。</span><span class="sxs-lookup"><span data-stu-id="520e7-198">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="520e7-199">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="520e7-199">-ProxyCredential</span></span>

<span data-ttu-id="520e7-200">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="520e7-200">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="520e7-201">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="520e7-201">The default is the current user.</span></span>

<span data-ttu-id="520e7-202">輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="520e7-202">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="520e7-203">只有當命令中也使用 **Proxy** 參數時，此參數才會有效。</span><span class="sxs-lookup"><span data-stu-id="520e7-203">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="520e7-204">您無法在相同命令中使用 **ProxyCredential** 與 **ProxyUseDefaultCredentials** 參數。</span><span class="sxs-lookup"><span data-stu-id="520e7-204">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="520e7-205">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="520e7-205">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="520e7-206">使用目前使用者的認證，存取 **Proxy** 參數指定的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="520e7-206">Uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="520e7-207">只有當命令中也使用 **Proxy** 參數時，此參數才會有效。</span><span class="sxs-lookup"><span data-stu-id="520e7-207">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="520e7-208">您無法在相同命令中使用 **ProxyCredential** 與 **ProxyUseDefaultCredentials** 參數。</span><span class="sxs-lookup"><span data-stu-id="520e7-208">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="520e7-209">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="520e7-209">-SessionVariable</span></span>

<span data-ttu-id="520e7-210">建立 Web 要求工作階段，並將它儲存在指定變數的值。</span><span class="sxs-lookup"><span data-stu-id="520e7-210">Creates a web request session and saves it in the value of the specified variable.</span></span> <span data-ttu-id="520e7-211">輸入不含貨幣符號 () 符號的變數名稱 `$` 。</span><span class="sxs-lookup"><span data-stu-id="520e7-211">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="520e7-212">當您指定會話變數時，會 `Invoke-RestMethod` 建立 web 要求會話物件，並將它指派給您的 PowerShell 會話中具有指定名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="520e7-212">When you specify a session variable, `Invoke-RestMethod` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="520e7-213">一旦命令完成，便可在工作階段中使用變數。</span><span class="sxs-lookup"><span data-stu-id="520e7-213">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="520e7-214">Web 要求工作階段不同於遠端工作階段，並非持續連線。</span><span class="sxs-lookup"><span data-stu-id="520e7-214">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="520e7-215">它是包含連線與要求相關資訊的物件，這些資訊包括 Cookie、認證、重新導向上限值，以及使用者代理字串。</span><span class="sxs-lookup"><span data-stu-id="520e7-215">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="520e7-216">您可以使用它在 Web 要求之間共用狀態與資料。</span><span class="sxs-lookup"><span data-stu-id="520e7-216">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="520e7-217">若要在後續 Web 要求中使用 Web 要求工作階段，請在 **WebSession** 參數值指定工作階段變數。</span><span class="sxs-lookup"><span data-stu-id="520e7-217">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="520e7-218">建立新連線時，Windows PowerShell 會使用 Web 要求工作階段物件中的資料。</span><span class="sxs-lookup"><span data-stu-id="520e7-218">Windows PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="520e7-219">若要覆寫 Web 要求工作階段中的值，請使用 Cmdlet 參數，例如 **UserAgent** 或 **Credential** 。</span><span class="sxs-lookup"><span data-stu-id="520e7-219">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="520e7-220">參數值的優先順序高於 Web 要求工作階段中的值。</span><span class="sxs-lookup"><span data-stu-id="520e7-220">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="520e7-221">您不能在同一個命令中使用 **SessionVariable** 和 **WebSession** 參數。</span><span class="sxs-lookup"><span data-stu-id="520e7-221">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="520e7-222">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="520e7-222">-TimeoutSec</span></span>

<span data-ttu-id="520e7-223">指定要求可在一段時間之前暫止的時間長度。輸入以秒為單位的值。</span><span class="sxs-lookup"><span data-stu-id="520e7-223">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="520e7-224">預設值為 0，會指定無限逾時。</span><span class="sxs-lookup"><span data-stu-id="520e7-224">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="520e7-225">網域名稱系統 (DNS) 查詢最多可能需要15秒的時間才會傳回或超時。如果您的要求包含需要解析的主機名稱，而且您將 TimeoutSec 設定為大於零的值，但不超過15秒，則在擲回 WebException 之前，可能需要15秒或更長的時間，而且您的要求超時。</span><span class="sxs-lookup"><span data-stu-id="520e7-225">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set TimeoutSec to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="520e7-226">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="520e7-226">-TransferEncoding</span></span>

<span data-ttu-id="520e7-227">指定傳輸編碼 HTTP 回應標頭的值。</span><span class="sxs-lookup"><span data-stu-id="520e7-227">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="520e7-228">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="520e7-228">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="520e7-229">區塊</span><span class="sxs-lookup"><span data-stu-id="520e7-229">Chunked</span></span>
- <span data-ttu-id="520e7-230">壓縮</span><span class="sxs-lookup"><span data-stu-id="520e7-230">Compress</span></span>
- <span data-ttu-id="520e7-231">上下凹陷</span><span class="sxs-lookup"><span data-stu-id="520e7-231">Deflate</span></span>
- <span data-ttu-id="520e7-232">GZip</span><span class="sxs-lookup"><span data-stu-id="520e7-232">GZip</span></span>
- <span data-ttu-id="520e7-233">身分識別</span><span class="sxs-lookup"><span data-stu-id="520e7-233">Identity</span></span>

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

### <span data-ttu-id="520e7-234">-Uri</span><span class="sxs-lookup"><span data-stu-id="520e7-234">-Uri</span></span>

<span data-ttu-id="520e7-235">指定 Web 要求傳送目的地的網際網路資源「統一資源識別項 (URI)」。</span><span class="sxs-lookup"><span data-stu-id="520e7-235">Specifies the Uniform Resource Identifier (URI) of the Internet resource to which the web request is sent.</span></span> <span data-ttu-id="520e7-236">此參數支援 HTTP、HTTPS、FTP 與 FILE 值。</span><span class="sxs-lookup"><span data-stu-id="520e7-236">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="520e7-237">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="520e7-237">This parameter is required.</span></span> <span data-ttu-id="520e7-238"> ( **Uri** ) 的參數名稱是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="520e7-238">The parameter name ( **Uri** ) is optional.</span></span>

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

### <span data-ttu-id="520e7-239">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="520e7-239">-UseBasicParsing</span></span>

<span data-ttu-id="520e7-240">指出此 Cmdlet 會使用基本剖析。</span><span class="sxs-lookup"><span data-stu-id="520e7-240">Indicates that the cmdlet uses basic parsing.</span></span> <span data-ttu-id="520e7-241">Cmdlet 會傳回 **字串** 物件中的原始 HTML。</span><span class="sxs-lookup"><span data-stu-id="520e7-241">The cmdlet returns the raw HTML in a **String** object.</span></span>

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

### <span data-ttu-id="520e7-242">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="520e7-242">-UseDefaultCredentials</span></span>

<span data-ttu-id="520e7-243">使用目前使用者的認證來傳送 Web 要求。</span><span class="sxs-lookup"><span data-stu-id="520e7-243">Uses the credentials of the current user to send the web request.</span></span>

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

### <span data-ttu-id="520e7-244">-UserAgent</span><span class="sxs-lookup"><span data-stu-id="520e7-244">-UserAgent</span></span>

<span data-ttu-id="520e7-245">指定 Web 要求的使用者代理字串。</span><span class="sxs-lookup"><span data-stu-id="520e7-245">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="520e7-246">預設使用者代理程式類似於 "Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0"，但是每種作業系統與平台會有些微差異。</span><span class="sxs-lookup"><span data-stu-id="520e7-246">The default user agent is similar to "Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0" with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="520e7-247">若要使用大部分網際網路瀏覽器所使用的標準使用者代理程式字串來測試網站，請使用 [PSUserAgent](/dotnet/api/microsoft.powershell.commands) 類別的屬性，例如 Chrome、FireFox、Internet Explorer、Opera 和 Safari。</span><span class="sxs-lookup"><span data-stu-id="520e7-247">To test a website with the standard user agent string that is used by most Internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands) class, such as Chrome, FireFox, Internet Explorer, Opera, and Safari.</span></span>

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

### <span data-ttu-id="520e7-248">-WebSession</span><span class="sxs-lookup"><span data-stu-id="520e7-248">-WebSession</span></span>

<span data-ttu-id="520e7-249">指定 Web 要求工作階段。</span><span class="sxs-lookup"><span data-stu-id="520e7-249">Specifies a web request session.</span></span> <span data-ttu-id="520e7-250">輸入變數名稱，包括貨幣符號 (`$`) 。</span><span class="sxs-lookup"><span data-stu-id="520e7-250">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="520e7-251">若要覆寫 Web 要求工作階段中的值，請使用 Cmdlet 參數，例如 **UserAgent** 或 **Credential** 。</span><span class="sxs-lookup"><span data-stu-id="520e7-251">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="520e7-252">參數值的優先順序高於 Web 要求工作階段中的值。</span><span class="sxs-lookup"><span data-stu-id="520e7-252">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="520e7-253">Web 要求工作階段不同於遠端工作階段，並非持續連線。</span><span class="sxs-lookup"><span data-stu-id="520e7-253">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="520e7-254">它是包含連線與要求相關資訊的物件，這些資訊包括 Cookie、認證、重新導向上限值，以及使用者代理字串。</span><span class="sxs-lookup"><span data-stu-id="520e7-254">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="520e7-255">您可以使用它在 Web 要求之間共用狀態與資料。</span><span class="sxs-lookup"><span data-stu-id="520e7-255">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="520e7-256">若要建立 web 要求會話，請在命令的 **SessionVariable** 參數值中輸入不含貨幣正負號)  (變數名稱 `Invoke-RestMethod` 。</span><span class="sxs-lookup"><span data-stu-id="520e7-256">To create a web request session, enter a variable name (without a dollar sign) in the value of the **SessionVariable** parameter of an `Invoke-RestMethod` command.</span></span> <span data-ttu-id="520e7-257">`Invoke-RestMethod` 建立會話，並將它儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="520e7-257">`Invoke-RestMethod` creates the session and saves it in the variable.</span></span> <span data-ttu-id="520e7-258">在後續命令中，使用變數作為 **WebSession** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="520e7-258">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="520e7-259">您不能在同一個命令中使用 **SessionVariable** 和 **WebSession** 參數。</span><span class="sxs-lookup"><span data-stu-id="520e7-259">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="520e7-260">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="520e7-260">CommonParameters</span></span>

<span data-ttu-id="520e7-261">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="520e7-261">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="520e7-262">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="520e7-262">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="520e7-263">輸入</span><span class="sxs-lookup"><span data-stu-id="520e7-263">Inputs</span></span>

### <span data-ttu-id="520e7-264">System.Object</span><span class="sxs-lookup"><span data-stu-id="520e7-264">System.Object</span></span>

<span data-ttu-id="520e7-265">您可以使用管線將 web 要求的主體傳送至 `Invoke-RestMethod` 。</span><span class="sxs-lookup"><span data-stu-id="520e7-265">You can pipe the body of a web request to `Invoke-RestMethod`.</span></span>

## <span data-ttu-id="520e7-266">輸出</span><span class="sxs-lookup"><span data-stu-id="520e7-266">Outputs</span></span>

### <span data-ttu-id="520e7-267">System.Xml.Xml檔，Microsoft.PowerShell.Commands.HtmlWebResponseObject，System.string</span><span class="sxs-lookup"><span data-stu-id="520e7-267">System.Xml.XmlDocument, Microsoft.PowerShell.Commands.HtmlWebResponseObject, System.String</span></span>

<span data-ttu-id="520e7-268">Cmdlet 的輸出取決於抓取內容的格式。</span><span class="sxs-lookup"><span data-stu-id="520e7-268">The output of the cmdlet depends upon the format of the content that is retrieved.</span></span>

### <span data-ttu-id="520e7-269">PSObject</span><span class="sxs-lookup"><span data-stu-id="520e7-269">PSObject</span></span>

<span data-ttu-id="520e7-270">如果要求傳回 JSON 字串，則 `Invoke-RestMethod` 會傳回代表字串的 PSObject。</span><span class="sxs-lookup"><span data-stu-id="520e7-270">If the request returns JSON strings, `Invoke-RestMethod` returns a PSObject that represents the strings.</span></span>

## <span data-ttu-id="520e7-271">備忘稿</span><span class="sxs-lookup"><span data-stu-id="520e7-271">Notes</span></span>

## <span data-ttu-id="520e7-272">相關連結</span><span class="sxs-lookup"><span data-stu-id="520e7-272">Related Links</span></span>

[<span data-ttu-id="520e7-273">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="520e7-273">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="520e7-274">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="520e7-274">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="520e7-275">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="520e7-275">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)
