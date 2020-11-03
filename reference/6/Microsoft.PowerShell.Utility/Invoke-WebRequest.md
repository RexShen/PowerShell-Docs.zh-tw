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
# <span data-ttu-id="12821-103">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="12821-103">Invoke-WebRequest</span></span>

## <span data-ttu-id="12821-104">概要</span><span class="sxs-lookup"><span data-stu-id="12821-104">SYNOPSIS</span></span>
<span data-ttu-id="12821-105">從網際網路上的網頁取得內容。</span><span class="sxs-lookup"><span data-stu-id="12821-105">Gets content from a web page on the internet.</span></span>

## <span data-ttu-id="12821-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="12821-106">SYNTAX</span></span>

### <span data-ttu-id="12821-107">StandardMethod (預設) </span><span class="sxs-lookup"><span data-stu-id="12821-107">StandardMethod (Default)</span></span>

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

### <span data-ttu-id="12821-108">StandardMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="12821-108">StandardMethodNoProxy</span></span>

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

### <span data-ttu-id="12821-109">CustomMethod</span><span class="sxs-lookup"><span data-stu-id="12821-109">CustomMethod</span></span>

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

### <span data-ttu-id="12821-110">CustomMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="12821-110">CustomMethodNoProxy</span></span>

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

## <span data-ttu-id="12821-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="12821-111">DESCRIPTION</span></span>

<span data-ttu-id="12821-112">`Invoke-WebRequest`Cmdlet 會將 HTTP 和 HTTPS 要求傳送至網頁或 web 服務。</span><span class="sxs-lookup"><span data-stu-id="12821-112">The `Invoke-WebRequest` cmdlet sends HTTP and HTTPS requests to a web page or web service.</span></span> <span data-ttu-id="12821-113">它會剖析回應並傳回連結、影像和其他重要 HTML 元素的集合。</span><span class="sxs-lookup"><span data-stu-id="12821-113">It parses the response and returns collections of links, images, and other significant HTML elements.</span></span>

<span data-ttu-id="12821-114">此 Cmdlet 是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="12821-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="12821-115">範例</span><span class="sxs-lookup"><span data-stu-id="12821-115">EXAMPLES</span></span>

### <span data-ttu-id="12821-116">範例1：傳送 web 要求</span><span class="sxs-lookup"><span data-stu-id="12821-116">Example 1: Send a web request</span></span>

<span data-ttu-id="12821-117">此範例會使用 `Invoke-WebRequest` Cmdlet 將 web 要求傳送至 Bing.com 網站。</span><span class="sxs-lookup"><span data-stu-id="12821-117">This example uses the `Invoke-WebRequest` cmdlet to send a web request to the Bing.com site.</span></span>

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

<span data-ttu-id="12821-118">第一個命令會發出要求，並將回應儲存在 `$Response` 變數中。</span><span class="sxs-lookup"><span data-stu-id="12821-118">The first command issues the request and saves the response in the `$Response` variable.</span></span>

<span data-ttu-id="12821-119">第二個命令會取得 **名稱** 屬性類似的任何 **InputField** `"* Value"` 。</span><span class="sxs-lookup"><span data-stu-id="12821-119">The second command gets any **InputField** where the **Name** property is like `"* Value"`.</span></span> <span data-ttu-id="12821-120">篩選後的結果會以管道傳送至， `Select-Object` 以選取 [ **名稱** ] 和 [ **值** ] 屬性。</span><span class="sxs-lookup"><span data-stu-id="12821-120">The filtered results are piped to `Select-Object` to select the **Name** and **Value** properties.</span></span>

### <span data-ttu-id="12821-121">範例2：使用具狀態的 web 服務</span><span class="sxs-lookup"><span data-stu-id="12821-121">Example 2: Use a stateful web service</span></span>

<span data-ttu-id="12821-122">這個範例會示範如何搭配可設定 `Invoke-WebRequest` 狀態的 web 服務使用 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="12821-122">This example shows how to use the `Invoke-WebRequest` cmdlet with a stateful web service.</span></span>

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

<span data-ttu-id="12821-123">第一個傳送登 `Invoke-WebRequest` 入要求的呼叫。</span><span class="sxs-lookup"><span data-stu-id="12821-123">The first call to `Invoke-WebRequest` sends a sign-in request.</span></span> <span data-ttu-id="12821-124">此命令會針對 **-SessionVariable** 參數的值指定 "Session" 值，並將結果儲存在 `$LoginResponse` 變數中。</span><span class="sxs-lookup"><span data-stu-id="12821-124">The command specifies a value of "Session" for the value of the **-SessionVariable** parameter, and saves the result in the `$LoginResponse` variable.</span></span> <span data-ttu-id="12821-125">當命令完成時， `$LoginResponse` 變數會包含 `BasicHtmlWebResponseObject` ，而且 `$Session` 變數包含 `WebRequestSession` 物件。</span><span class="sxs-lookup"><span data-stu-id="12821-125">When the command completes, the `$LoginResponse` variable contains an `BasicHtmlWebResponseObject` and the `$Session` variable contains a `WebRequestSession` object.</span></span> <span data-ttu-id="12821-126">這會將使用者登入網站。</span><span class="sxs-lookup"><span data-stu-id="12821-126">This logs the user into the site.</span></span>

<span data-ttu-id="12821-127">的呼叫 `$Session` 本身會顯示 `WebRequestSession` 變數中的物件。</span><span class="sxs-lookup"><span data-stu-id="12821-127">The call to `$Session` by itself shows the `WebRequestSession` object in the variable.</span></span>

<span data-ttu-id="12821-128">第二個呼叫 `Invoke-WebRequest` 會提取使用者的設定檔，要求使用者必須登入網站。</span><span class="sxs-lookup"><span data-stu-id="12821-128">The second call to `Invoke-WebRequest` fetches the user's profile which requires that the user be logged into the site.</span></span> <span data-ttu-id="12821-129">變數中所儲存的會話資料 `$Session` 會用來提供會話 cookie 給登入期間所建立的網站。</span><span class="sxs-lookup"><span data-stu-id="12821-129">The session data stored in the `$Session` variable is used to provide session cookies to the site created during the login.</span></span> <span data-ttu-id="12821-130">結果會儲存在變數中 `$ProfileResponse` 。</span><span class="sxs-lookup"><span data-stu-id="12821-130">The result is saved in the `$ProfileResponse` variable.</span></span>

<span data-ttu-id="12821-131">的呼叫 `$ProfileResponse` 本身會顯示 `BasicHtmlWebResponseObject` 變數中的。</span><span class="sxs-lookup"><span data-stu-id="12821-131">The call to `$ProfileResponse` by itself shows the `BasicHtmlWebResponseObject` in the variable.</span></span>

### <span data-ttu-id="12821-132">範例3：取得網頁的連結</span><span class="sxs-lookup"><span data-stu-id="12821-132">Example 3: Get links from a web page</span></span>

<span data-ttu-id="12821-133">這個範例會取得網頁中的連結。</span><span class="sxs-lookup"><span data-stu-id="12821-133">This example gets the links in a web page.</span></span> <span data-ttu-id="12821-134">它會使用 `Invoke-WebRequest` Cmdlet 來取得網頁內容。</span><span class="sxs-lookup"><span data-stu-id="12821-134">It uses the `Invoke-WebRequest` cmdlet to get the web page content.</span></span> <span data-ttu-id="12821-135">然後，它會使用傳回之的 **Links** 屬性 `BasicHtmlWebResponseObject` `Invoke-WebRequest` ，以及每個連結的 **Href** 屬性。</span><span class="sxs-lookup"><span data-stu-id="12821-135">Then it uses the **Links** property of the `BasicHtmlWebResponseObject` that `Invoke-WebRequest` returns, and the **Href** property of each link.</span></span>

```powershell
(Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs").Links.Href
```

### <span data-ttu-id="12821-136">範例4：使用要求的頁面中定義的編碼，將回應內容寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="12821-136">Example 4: Writes the response content to a file using the encoding defined in the requested page.</span></span>

<span data-ttu-id="12821-137">此範例會使用 `Invoke-WebRequest` Cmdlet 來取得 PowerShell 檔頁面的網頁內容。</span><span class="sxs-lookup"><span data-stu-id="12821-137">This example uses the `Invoke-WebRequest` cmdlet to retrieve the web page content of a PowerShell documentation page.</span></span>

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

<span data-ttu-id="12821-138">第一個命令會抓取頁面，並將回應物件儲存在 `$Response` 變數中。</span><span class="sxs-lookup"><span data-stu-id="12821-138">The first command retrieves the page and saves the response object in the `$Response` variable.</span></span>

<span data-ttu-id="12821-139">第二個命令會建立 `StreamWriter` 用來將回應內容寫入檔案的。</span><span class="sxs-lookup"><span data-stu-id="12821-139">The second command creates a `StreamWriter` to use to write the response content to a file.</span></span> <span data-ttu-id="12821-140">Response 物件的 **encoding** 屬性是用來設定檔案的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="12821-140">The **Encoding** property of the response object is used to set the encoding for the file.</span></span>

<span data-ttu-id="12821-141">最後幾個命令會將 **Content** 屬性寫入檔案，然後處置 `StreamWriter` 。</span><span class="sxs-lookup"><span data-stu-id="12821-141">The final few commands write the **Content** property to the file then disposes the `StreamWriter`.</span></span>

<span data-ttu-id="12821-142">請注意，如果 web 要求未傳回文字內容，則 [ **編碼** ] 屬性會是 null。</span><span class="sxs-lookup"><span data-stu-id="12821-142">Note that the **Encoding** property is null if the web request doesn't return text content.</span></span>

### <span data-ttu-id="12821-143">範例5：提交多部分/表單資料檔案</span><span class="sxs-lookup"><span data-stu-id="12821-143">Example 5: Submit a multipart/form-data file</span></span>

<span data-ttu-id="12821-144">此範例會使用 `Invoke-WebRequest` Cmdlet 將檔案上傳為 `multipart/form-data` 提交。</span><span class="sxs-lookup"><span data-stu-id="12821-144">This example uses the `Invoke-WebRequest` cmdlet upload a file as a `multipart/form-data` submission.</span></span> <span data-ttu-id="12821-145">檔案 `c:\document.txt` 會提交為的表單欄位，以及 `document` `Content-Type` 的 `text/plain` 。</span><span class="sxs-lookup"><span data-stu-id="12821-145">The file `c:\document.txt` is submitted as the form field `document` with the `Content-Type` of `text/plain`.</span></span>

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

### <span data-ttu-id="12821-146">範例6：簡化多部分/表單資料提交</span><span class="sxs-lookup"><span data-stu-id="12821-146">Example 6: Simplified Multipart/Form-Data Submission</span></span>

<span data-ttu-id="12821-147">某些 Api 需要 `multipart/form-data` 提交才能上傳檔案和混合的內容。</span><span class="sxs-lookup"><span data-stu-id="12821-147">Some APIs require `multipart/form-data` submissions to upload files and mixed content.</span></span> <span data-ttu-id="12821-148">此範例示範如何更新使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="12821-148">This example demonstrates updating a user profile.</span></span>

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

<span data-ttu-id="12821-149">設定檔表單需要下欄欄位： `firstName` 、 `lastName` 、 `email` 、 `avatar` 、 `birthday` 和 `hobbies` 。</span><span class="sxs-lookup"><span data-stu-id="12821-149">The profile form requires these fields: `firstName`, `lastName`, `email`, `avatar`, `birthday`, and `hobbies`.</span></span> <span data-ttu-id="12821-150">API 預期會在欄位中提供使用者設定檔 pic 的影像 `avatar` 。</span><span class="sxs-lookup"><span data-stu-id="12821-150">The API is expecting an image for the user profile pic to be supplied in the `avatar` field.</span></span> <span data-ttu-id="12821-151">此 API 也會接受 `hobbies` 以相同形式提交的多個專案。</span><span class="sxs-lookup"><span data-stu-id="12821-151">The API also accepts multiple `hobbies` entries to be submitted in the same form.</span></span>

<span data-ttu-id="12821-152">建立 `$Form` 雜湊表時，索引鍵名稱會用來做為表單欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="12821-152">When creating the `$Form` HashTable, the key names are used as form field names.</span></span> <span data-ttu-id="12821-153">根據預設，雜湊表的值會轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="12821-153">By default, the values of the HashTable are converted to strings.</span></span> <span data-ttu-id="12821-154">如果有 **FileInfo** 值，則會提交檔案內容。</span><span class="sxs-lookup"><span data-stu-id="12821-154">If a **System.IO.FileInfo** value is present, the file contents are submitted.</span></span> <span data-ttu-id="12821-155">如果有集合（例如陣列或清單）存在，就會提交表單欄位多次。</span><span class="sxs-lookup"><span data-stu-id="12821-155">If a collection such as arrays or lists are present, the form field is submitted multiple times.</span></span>

<span data-ttu-id="12821-156">藉由 `Get-Item` 在索引 `avatar` 鍵上使用， `FileInfo` 就會將物件設定為值。</span><span class="sxs-lookup"><span data-stu-id="12821-156">By using `Get-Item` on the `avatar` key, the `FileInfo` object is set as the value.</span></span> <span data-ttu-id="12821-157">結果是提交的影像資料 `jdoe.png` 。</span><span class="sxs-lookup"><span data-stu-id="12821-157">The result is that the image data for `jdoe.png` is submitted.</span></span>

<span data-ttu-id="12821-158">藉由提供清單給 `hobbies` 金鑰， `hobbies` 每個清單專案的提交一次就會出現此欄位。</span><span class="sxs-lookup"><span data-stu-id="12821-158">By supplying a list to the `hobbies` key, the `hobbies` field is present in the submissions once for each list item.</span></span>

### <span data-ttu-id="12821-159">範例7：攔截 Invoke-WebRequest 的非成功訊息</span><span class="sxs-lookup"><span data-stu-id="12821-159">Example 7: Catch non success messages from Invoke-WebRequest</span></span>

<span data-ttu-id="12821-160">當 `Invoke-WebRequest` (404、500等 ) 遇到非成功的 HTTP 訊息時，它不會傳回任何輸出並擲回終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="12821-160">When `Invoke-WebRequest` encounters a non-success HTTP message (404, 500, etc.), it returns no output and throws a terminating error.</span></span> <span data-ttu-id="12821-161">若要攔截錯誤並查看 **StatusCode** ，您可以在區塊中包含執行 `try/catch` 。</span><span class="sxs-lookup"><span data-stu-id="12821-161">To catch the error and view the **StatusCode** you can enclose execution in a `try/catch` block.</span></span>

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

<span data-ttu-id="12821-162">命令會 `Invoke-WebRequest` 以 **Stop** 的 **ErrorAction** 呼叫，這會強制 `Invoke-WebRequest` 在任何失敗的要求上擲回終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="12821-162">The command calls `Invoke-WebRequest` with an **ErrorAction** of **Stop** , which forces `Invoke-WebRequest` to throw a terminating error on any failed requests.</span></span> <span data-ttu-id="12821-163">`catch`從 **例外** 狀況物件抓取 **StatusCode** 的區塊攔截到終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="12821-163">The terminating error is caught by the `catch` block which retrieves the **StatusCode** from the **Exception** object.</span></span>

## <span data-ttu-id="12821-164">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="12821-164">PARAMETERS</span></span>

### <span data-ttu-id="12821-165">-AllowUnencryptedAuthentication</span><span class="sxs-lookup"><span data-stu-id="12821-165">-AllowUnencryptedAuthentication</span></span>

<span data-ttu-id="12821-166">允許透過未加密的連接傳送認證和密碼。</span><span class="sxs-lookup"><span data-stu-id="12821-166">Allows sending of credentials and secrets over unencrypted connections.</span></span> <span data-ttu-id="12821-167">依預設，以不是開頭的 **Uri** **提供認證** 或任何 **驗證** 選項會 `https://` 導致錯誤，並中止要求以防止不慎以純文字方式透過未加密的連接來傳達秘密。</span><span class="sxs-lookup"><span data-stu-id="12821-167">By default, supplying **Credential** or any **Authentication** option with a **Uri** that does not begin with `https://` results in an error and the request is aborted to prevent unintentionally communicating secrets in plain text over unencrypted connections.</span></span> <span data-ttu-id="12821-168">若要以您自己的風險覆寫此行為，請提供 **AllowUnencryptedAuthentication** 參數。</span><span class="sxs-lookup"><span data-stu-id="12821-168">To override this behavior at your own risk, supply the **AllowUnencryptedAuthentication** parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="12821-169">使用這個參數並不安全，因此不建議使用。</span><span class="sxs-lookup"><span data-stu-id="12821-169">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="12821-170">它僅提供給無法提供加密連接的舊版系統相容。</span><span class="sxs-lookup"><span data-stu-id="12821-170">It is provided only for compatibility with legacy systems that cannot provide encrypted connections.</span></span> <span data-ttu-id="12821-171">使用您自己的風險。</span><span class="sxs-lookup"><span data-stu-id="12821-171">Use at your own risk.</span></span>

<span data-ttu-id="12821-172">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="12821-172">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="12821-173">-Authentication</span><span class="sxs-lookup"><span data-stu-id="12821-173">-Authentication</span></span>

<span data-ttu-id="12821-174">指定要用於要求的明確驗證類型。</span><span class="sxs-lookup"><span data-stu-id="12821-174">Specifies the explicit authentication type to use for the request.</span></span> <span data-ttu-id="12821-175">預設值為 [無]。</span><span class="sxs-lookup"><span data-stu-id="12821-175">The default is **None** .</span></span>
<span data-ttu-id="12821-176">**驗證** 無法與 **UseDefaultCredentials** 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="12821-176">**Authentication** cannot be used with **UseDefaultCredentials** .</span></span>

<span data-ttu-id="12821-177">可用的驗證選項：</span><span class="sxs-lookup"><span data-stu-id="12821-177">Available Authentication Options:</span></span>

- <span data-ttu-id="12821-178">**無** ：當未提供 **驗證** 時，這是預設選項;未使用明確驗證。</span><span class="sxs-lookup"><span data-stu-id="12821-178">**None** : This is the default option when **Authentication** isn't supplied; no explicit authentication is used.</span></span>
- <span data-ttu-id="12821-179">**基本** ：需要 **認證** 。</span><span class="sxs-lookup"><span data-stu-id="12821-179">**Basic** : Requires **Credential** .</span></span> <span data-ttu-id="12821-180">認證會以的格式在 RFC 7617 基本驗證標頭中傳送 `base64(user:password)` 。</span><span class="sxs-lookup"><span data-stu-id="12821-180">The credentials are sent in an RFC 7617 Basic Authentication header in the format of `base64(user:password)`.</span></span>
- <span data-ttu-id="12821-181">**持有** 人：需要 **權杖** 。</span><span class="sxs-lookup"><span data-stu-id="12821-181">**Bearer** : Requires **Token** .</span></span> <span data-ttu-id="12821-182">傳送 `Authorization: Bearer` 具有所提供權杖的 RFC 6750 標頭。</span><span class="sxs-lookup"><span data-stu-id="12821-182">Sends an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="12821-183">這是 **OAuth** 的別名</span><span class="sxs-lookup"><span data-stu-id="12821-183">This is an alias for **OAuth**</span></span>
- <span data-ttu-id="12821-184">**OAuth** ：需要 **權杖** 。</span><span class="sxs-lookup"><span data-stu-id="12821-184">**OAuth** : Requires **Token** .</span></span> <span data-ttu-id="12821-185">傳送 `Authorization: Bearer` 具有所提供權杖的 RFC 6750 標頭。</span><span class="sxs-lookup"><span data-stu-id="12821-185">Sends an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="12821-186">這是 **持有** 人的別名</span><span class="sxs-lookup"><span data-stu-id="12821-186">This is an alias for **Bearer**</span></span>

<span data-ttu-id="12821-187">提供 **驗證** 會覆寫 `Authorization` 提供給 **標頭** 或包含在 **WebSession** 中的任何標頭。</span><span class="sxs-lookup"><span data-stu-id="12821-187">Supplying **Authentication** overrides any `Authorization` headers supplied to **Headers** or included in **WebSession** .</span></span>

<span data-ttu-id="12821-188">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="12821-188">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="12821-189">-Body</span><span class="sxs-lookup"><span data-stu-id="12821-189">-Body</span></span>

<span data-ttu-id="12821-190">指定要求的主體。</span><span class="sxs-lookup"><span data-stu-id="12821-190">Specifies the body of the request.</span></span> <span data-ttu-id="12821-191">主體為標頭之後的要求內容。</span><span class="sxs-lookup"><span data-stu-id="12821-191">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="12821-192">您也可以使用管線將主體值傳送至 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="12821-192">You can also pipe a body value to `Invoke-WebRequest`.</span></span>

<span data-ttu-id="12821-193">**Body** 參數可用來指定查詢參數的清單，或指定回應的內容。</span><span class="sxs-lookup"><span data-stu-id="12821-193">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="12821-194">當輸入為 GET 要求且主體為 `IDictionary` (時，雜湊表) ，主體會新增至 URI 作為查詢參數。</span><span class="sxs-lookup"><span data-stu-id="12821-194">When the input is a GET request and the body is an `IDictionary` (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="12821-195">針對其他要求類型 (例如 POST) ，主體會設定為標準格式的要求主體值 `name=value` 。</span><span class="sxs-lookup"><span data-stu-id="12821-195">For other request types (such as POST), the body is set as the value of the request body in the standard `name=value` format.</span></span>

<span data-ttu-id="12821-196">**Body** 參數也可以接受 `System.Net.Http.MultipartFormDataContent` 物件。</span><span class="sxs-lookup"><span data-stu-id="12821-196">The **Body** parameter may also accept a `System.Net.Http.MultipartFormDataContent` object.</span></span> <span data-ttu-id="12821-197">這可協助 `multipart/form-data` 要求。</span><span class="sxs-lookup"><span data-stu-id="12821-197">This facilitates `multipart/form-data` requests.</span></span> <span data-ttu-id="12821-198">提供 **主體** 的 **>multipartformdatacontent** 物件時，提供給 **ContentType** 、 **標頭** 或 **WebSession** 參數的任何內容相關標頭都會由 **>multipartformdatacontent** 物件的內容標頭覆寫。</span><span class="sxs-lookup"><span data-stu-id="12821-198">When a **MultipartFormDataContent** object is supplied for **Body** , any Content related headers supplied to the **ContentType** , **Headers** , or **WebSession** parameters is overridden by the Content headers of the **MultipartFormDataContent** object.</span></span> <span data-ttu-id="12821-199">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="12821-199">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="12821-200">-Certificate</span><span class="sxs-lookup"><span data-stu-id="12821-200">-Certificate</span></span>

<span data-ttu-id="12821-201">指定用於安全 web 要求的用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="12821-201">Specifies the client certificate that's used for a secure web request.</span></span> <span data-ttu-id="12821-202">輸入包含憑證的變數，或可取得憑證的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="12821-202">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="12821-203">若要尋找憑證，請使用 `Get-PfxCertificate` 或使用 `Get-ChildItem` 憑證 (`Cert:`) 磁片磁碟機中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="12821-203">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="12821-204">若憑證無效或沒有足夠的許可權，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="12821-204">If the certificate isn't valid or doesn't have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="12821-205">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="12821-205">-CertificateThumbprint</span></span>

<span data-ttu-id="12821-206">指定具有傳送要求權限之使用者帳戶的數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="12821-206">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="12821-207">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="12821-207">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="12821-208">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="12821-208">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="12821-209">這些帳戶只能對應至本機使用者帳戶;它們無法使用網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="12821-209">They can be mapped only to local user accounts; they don't work with domain accounts.</span></span>

<span data-ttu-id="12821-210">若要取得憑證指紋，請使用 `Get-Item` `Get-ChildItem` PowerShell 磁片磁碟機中的或命令 `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="12821-210">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

> [!NOTE]
> <span data-ttu-id="12821-211">這項功能目前僅支援 Windows OS 平臺。</span><span class="sxs-lookup"><span data-stu-id="12821-211">This feature is currently only supported on Windows OS platforms.</span></span>

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

### <span data-ttu-id="12821-212">-ContentType</span><span class="sxs-lookup"><span data-stu-id="12821-212">-ContentType</span></span>

<span data-ttu-id="12821-213">指定 Web 要求的內容類型。</span><span class="sxs-lookup"><span data-stu-id="12821-213">Specifies the content type of the web request.</span></span>

<span data-ttu-id="12821-214">如果省略此參數且要求方法為 POST，則會 `Invoke-WebRequest` 將內容類型設定為 `application/x-www-form-urlencoded` 。</span><span class="sxs-lookup"><span data-stu-id="12821-214">If this parameter is omitted and the request method is POST, `Invoke-WebRequest` sets the content type to `application/x-www-form-urlencoded`.</span></span> <span data-ttu-id="12821-215">否則，呼叫中不會指定內容類型。</span><span class="sxs-lookup"><span data-stu-id="12821-215">Otherwise, the content type isn't specified in the call.</span></span>

<span data-ttu-id="12821-216">提供 **主體** 的 **>multipartformdatacontent** 物件時，會覆寫 **ContentType** 。</span><span class="sxs-lookup"><span data-stu-id="12821-216">**ContentType** is overridden when a **MultipartFormDataContent** object is supplied for **Body** .</span></span>

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

### <span data-ttu-id="12821-217">-Credential</span><span class="sxs-lookup"><span data-stu-id="12821-217">-Credential</span></span>

<span data-ttu-id="12821-218">指定具有傳送要求權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="12821-218">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="12821-219">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="12821-219">The default is the current user.</span></span>

<span data-ttu-id="12821-220">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="12821-220">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="12821-221">**認證可以** 單獨使用，也可以搭配特定的 **驗證** 參數選項使用。</span><span class="sxs-lookup"><span data-stu-id="12821-221">**Credential** can be used alone or in conjunction with certain **Authentication** parameter options.</span></span> <span data-ttu-id="12821-222">單獨使用時，如果遠端伺服器傳送驗證挑戰要求，它只會提供遠端伺服器的認證。</span><span class="sxs-lookup"><span data-stu-id="12821-222">When used alone, it only supplies credentials to the remote server if the remote server sends an authentication challenge request.</span></span> <span data-ttu-id="12821-223">與 **驗證** 選項搭配使用時，會明確地傳送認證。</span><span class="sxs-lookup"><span data-stu-id="12821-223">When used with **Authentication** options, the credentials are explicitly sent.</span></span>

<span data-ttu-id="12821-224">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="12821-224">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="12821-225">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="12821-225">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="12821-226">-CustomMethod</span><span class="sxs-lookup"><span data-stu-id="12821-226">-CustomMethod</span></span>

<span data-ttu-id="12821-227">指定用於 web 要求的自訂方法。</span><span class="sxs-lookup"><span data-stu-id="12821-227">Specifies a custom method used for the web request.</span></span> <span data-ttu-id="12821-228">如果端點所要求的要求方法不是 **方法** 的可用選項，就可以使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="12821-228">This can be used if the Request Method required by the endpoint isn't an available option on the **Method** .</span></span> <span data-ttu-id="12821-229">**方法** 和 **CustomMethod** 無法一起使用。</span><span class="sxs-lookup"><span data-stu-id="12821-229">**Method** and **CustomMethod** can't be used together.</span></span>

<span data-ttu-id="12821-230">此範例會對 `TEST` API 提出 HTTP 要求：</span><span class="sxs-lookup"><span data-stu-id="12821-230">This example makes a `TEST` HTTP request to the API:</span></span>

`Invoke-WebRequest -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

<span data-ttu-id="12821-231">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="12821-231">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="12821-232">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="12821-232">-DisableKeepAlive</span></span>

<span data-ttu-id="12821-233">指出此 Cmdlet 會將 HTTP 標頭中的 **KeepAlive** 值設定為 **False** 。</span><span class="sxs-lookup"><span data-stu-id="12821-233">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to **False** .</span></span> <span data-ttu-id="12821-234">**KeepAlive** 預設為 **True** 。</span><span class="sxs-lookup"><span data-stu-id="12821-234">By default, **KeepAlive** is **True** .</span></span> <span data-ttu-id="12821-235">**KeepAlive** 會建立伺服器持續連線，有助於後續要求。</span><span class="sxs-lookup"><span data-stu-id="12821-235">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="12821-236">-Form</span><span class="sxs-lookup"><span data-stu-id="12821-236">-Form</span></span>

<span data-ttu-id="12821-237">將字典轉換為 `multipart/form-data` 提交。</span><span class="sxs-lookup"><span data-stu-id="12821-237">Converts a dictionary to a `multipart/form-data` submission.</span></span> <span data-ttu-id="12821-238">**表單\*\*\*\*不得與內文一起使用** 。</span><span class="sxs-lookup"><span data-stu-id="12821-238">**Form** may not be used with **Body** .</span></span>
<span data-ttu-id="12821-239">如果使用 **ContentType** ，則會予以忽略。</span><span class="sxs-lookup"><span data-stu-id="12821-239">If **ContentType** is used, it's ignored.</span></span>

<span data-ttu-id="12821-240">字典的索引鍵會用來做為表單欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="12821-240">The keys of the dictionary are used as the form field names.</span></span> <span data-ttu-id="12821-241">根據預設，表單值會轉換成字串值。</span><span class="sxs-lookup"><span data-stu-id="12821-241">By default, form values are converted to string values.</span></span>

<span data-ttu-id="12821-242">如果值是 **FileInfo** 物件，則會提交二進位檔案內容。</span><span class="sxs-lookup"><span data-stu-id="12821-242">If the value is a **System.IO.FileInfo** object, then the binary file contents are submitted.</span></span> <span data-ttu-id="12821-243">檔案的名稱會提交為 **filename** 屬性。</span><span class="sxs-lookup"><span data-stu-id="12821-243">The name of the file is submitted as the **filename** property.</span></span> <span data-ttu-id="12821-244">MIME 類型設定為 `application/octet-stream` 。</span><span class="sxs-lookup"><span data-stu-id="12821-244">The MIME type is set as `application/octet-stream`.</span></span> <span data-ttu-id="12821-245">`Get-Item` 可以用來簡化 **FileInfo** 物件的提供。</span><span class="sxs-lookup"><span data-stu-id="12821-245">`Get-Item` can be used to simplify supplying the **System.IO.FileInfo** object.</span></span>

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

<span data-ttu-id="12821-246">如果值是集合型別（例如陣列或清單），則會多次提交 for 欄位。</span><span class="sxs-lookup"><span data-stu-id="12821-246">If the value is a collection type, such Arrays or Lists, the for field are submitted multiple times.</span></span>
<span data-ttu-id="12821-247">依預設，系統會將清單的值視為字串。</span><span class="sxs-lookup"><span data-stu-id="12821-247">The values of the list are treated as strings by default.</span></span> <span data-ttu-id="12821-248">如果值是 **FileInfo** 物件，則會提交二進位檔案內容。</span><span class="sxs-lookup"><span data-stu-id="12821-248">If the value is a **System.IO.FileInfo** object, then the binary file contents are submitted.</span></span> <span data-ttu-id="12821-249">不支援嵌套集合。</span><span class="sxs-lookup"><span data-stu-id="12821-249">Nested collections aren't supported.</span></span>

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

<span data-ttu-id="12821-250">在上述範例中， `tags` 欄位會在表單中提供三次，每一個、和都提供一次 `Vacation` `Italy` `2017` 。</span><span class="sxs-lookup"><span data-stu-id="12821-250">In the above example the `tags` field are supplied three times in the form, once for each of `Vacation`, `Italy`, and `2017`.</span></span> <span data-ttu-id="12821-251">此 `pictures` 欄位也會針對資料夾中的每個檔案提交一次 `2017-Italy` 。</span><span class="sxs-lookup"><span data-stu-id="12821-251">The `pictures` field is also submitted once for each file in the `2017-Italy` folder.</span></span> <span data-ttu-id="12821-252">該資料夾中檔案的二進位內容會以值的形式提交。</span><span class="sxs-lookup"><span data-stu-id="12821-252">The binary contents of the files in that folder are submitted as the values.</span></span>

<span data-ttu-id="12821-253">這項功能已在 PowerShell 6.1.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="12821-253">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="12821-254">-Headers</span><span class="sxs-lookup"><span data-stu-id="12821-254">-Headers</span></span>

<span data-ttu-id="12821-255">指定 Web 要求的標頭。</span><span class="sxs-lookup"><span data-stu-id="12821-255">Specifies the headers of the web request.</span></span> <span data-ttu-id="12821-256">輸入雜湊表或字典。</span><span class="sxs-lookup"><span data-stu-id="12821-256">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="12821-257">若要設定 UserAgent 標頭，請使用 **UserAgent** 參數。</span><span class="sxs-lookup"><span data-stu-id="12821-257">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="12821-258">您無法使用這個參數來指定 **使用者代理程式** 或 cookie 標頭。</span><span class="sxs-lookup"><span data-stu-id="12821-258">You can't use this parameter to specify **User-Agent** or cookie headers.</span></span>

<span data-ttu-id="12821-259">`Content-Type`當提供 **主體** 的 **>multipartformdatacontent** 物件時，會覆寫內容相關的標頭（例如）。</span><span class="sxs-lookup"><span data-stu-id="12821-259">Content related headers, such as `Content-Type` is overridden when a **MultipartFormDataContent** object is supplied for **Body** .</span></span>

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

### <span data-ttu-id="12821-260">-InFile</span><span class="sxs-lookup"><span data-stu-id="12821-260">-InFile</span></span>

<span data-ttu-id="12821-261">從檔案取得 Web 要求的內容。</span><span class="sxs-lookup"><span data-stu-id="12821-261">Gets the content of the web request from a file.</span></span> <span data-ttu-id="12821-262">輸入路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="12821-262">Enter a path and file name.</span></span> <span data-ttu-id="12821-263">若省略路徑，則預設為目前位置。</span><span class="sxs-lookup"><span data-stu-id="12821-263">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="12821-264">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="12821-264">-MaximumRedirection</span></span>

<span data-ttu-id="12821-265">指定在連接失敗之前，PowerShell 將連接重新導向至替代統一資源識別項 (URI) 的次數。</span><span class="sxs-lookup"><span data-stu-id="12821-265">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="12821-266">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="12821-266">The default value is 5.</span></span> <span data-ttu-id="12821-267">值為 0 (零) 將禁止所有重新導向。</span><span class="sxs-lookup"><span data-stu-id="12821-267">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="12821-268">-MaximumRetryCount</span><span class="sxs-lookup"><span data-stu-id="12821-268">-MaximumRetryCount</span></span>

<span data-ttu-id="12821-269">指定當收到400到599（含）或304之間的失敗代碼時，PowerShell 重試連接的次數。</span><span class="sxs-lookup"><span data-stu-id="12821-269">Specifies how many times PowerShell retries a connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="12821-270">另請參閱 **RetryIntervalSec** 參數，以指定重試次數。</span><span class="sxs-lookup"><span data-stu-id="12821-270">Also see **RetryIntervalSec** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="12821-271">-Method</span><span class="sxs-lookup"><span data-stu-id="12821-271">-Method</span></span>

<span data-ttu-id="12821-272">指定用於 Web 要求的方法。</span><span class="sxs-lookup"><span data-stu-id="12821-272">Specifies the method used for the web request.</span></span> <span data-ttu-id="12821-273">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="12821-273">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="12821-274">預設</span><span class="sxs-lookup"><span data-stu-id="12821-274">Default</span></span>
- <span data-ttu-id="12821-275">刪除</span><span class="sxs-lookup"><span data-stu-id="12821-275">Delete</span></span>
- <span data-ttu-id="12821-276">Get</span><span class="sxs-lookup"><span data-stu-id="12821-276">Get</span></span>
- <span data-ttu-id="12821-277">Head</span><span class="sxs-lookup"><span data-stu-id="12821-277">Head</span></span>
- <span data-ttu-id="12821-278">合併</span><span class="sxs-lookup"><span data-stu-id="12821-278">Merge</span></span>
- <span data-ttu-id="12821-279">選項</span><span class="sxs-lookup"><span data-stu-id="12821-279">Options</span></span>
- <span data-ttu-id="12821-280">Patch</span><span class="sxs-lookup"><span data-stu-id="12821-280">Patch</span></span>
- <span data-ttu-id="12821-281">郵寄</span><span class="sxs-lookup"><span data-stu-id="12821-281">Post</span></span>
- <span data-ttu-id="12821-282">Put</span><span class="sxs-lookup"><span data-stu-id="12821-282">Put</span></span>
- <span data-ttu-id="12821-283">追蹤</span><span class="sxs-lookup"><span data-stu-id="12821-283">Trace</span></span>

<span data-ttu-id="12821-284">**CustomMethod** 參數可以用於上面未列出的要求方法。</span><span class="sxs-lookup"><span data-stu-id="12821-284">The **CustomMethod** parameter can be used for Request Methods not listed above.</span></span>

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

### <span data-ttu-id="12821-285">-NoProxy</span><span class="sxs-lookup"><span data-stu-id="12821-285">-NoProxy</span></span>

<span data-ttu-id="12821-286">指出 Cmdlet 不應使用 proxy 來連線至目的地。</span><span class="sxs-lookup"><span data-stu-id="12821-286">Indicates that the cmdlet shouldn't use a proxy to reach the destination.</span></span> <span data-ttu-id="12821-287">當您需要略過環境中設定的 proxy 時，請使用此參數。</span><span class="sxs-lookup"><span data-stu-id="12821-287">When you need to bypass the proxy configured in the environment, use this switch.</span></span> <span data-ttu-id="12821-288">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="12821-288">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="12821-289">-OutFile</span><span class="sxs-lookup"><span data-stu-id="12821-289">-OutFile</span></span>

<span data-ttu-id="12821-290">指定此 Cmdlet 儲存回應主體的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="12821-290">Specifies the output file for which this cmdlet saves the response body.</span></span> <span data-ttu-id="12821-291">輸入路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="12821-291">Enter a path and file name.</span></span>
<span data-ttu-id="12821-292">若省略路徑，則預設為目前位置。</span><span class="sxs-lookup"><span data-stu-id="12821-292">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="12821-293">依預設，會將 `Invoke-WebRequest` 結果傳回至管線。</span><span class="sxs-lookup"><span data-stu-id="12821-293">By default, `Invoke-WebRequest` returns the results to the pipeline.</span></span> <span data-ttu-id="12821-294">若要傳送結果至檔案與管線，請使用 **Passthru** 參數。</span><span class="sxs-lookup"><span data-stu-id="12821-294">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="12821-295">-PassThru</span><span class="sxs-lookup"><span data-stu-id="12821-295">-PassThru</span></span>

<span data-ttu-id="12821-296">指出除了將結果寫入檔案之外，指令程式還會傳回結果。</span><span class="sxs-lookup"><span data-stu-id="12821-296">Indicates that the cmdlet returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="12821-297">只有當命令中也使用 **OutFile** 參數時，此參數才會有效。</span><span class="sxs-lookup"><span data-stu-id="12821-297">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="12821-298">-PreserveAuthorizationOnRedirect</span><span class="sxs-lookup"><span data-stu-id="12821-298">-PreserveAuthorizationOnRedirect</span></span>

<span data-ttu-id="12821-299">指出 Cmdlet 應該在重新導向 `Authorization` 之間保留標頭（若有的話）。</span><span class="sxs-lookup"><span data-stu-id="12821-299">Indicates the cmdlet should preserve the `Authorization` header, when present, across redirections.</span></span>

<span data-ttu-id="12821-300">根據預設，此 Cmdlet 會在重新導向 `Authorization` 之前先移除標頭。</span><span class="sxs-lookup"><span data-stu-id="12821-300">By default, the cmdlet strips the `Authorization` header before redirecting.</span></span> <span data-ttu-id="12821-301">指定此參數會在標頭必須傳送至重新導向位置的情況下，停用此邏輯。</span><span class="sxs-lookup"><span data-stu-id="12821-301">Specifying this parameter disables this logic for cases where the header needs to be sent to the redirection location.</span></span>

<span data-ttu-id="12821-302">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="12821-302">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="12821-303">-Proxy</span><span class="sxs-lookup"><span data-stu-id="12821-303">-Proxy</span></span>

<span data-ttu-id="12821-304">指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="12821-304">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>
<span data-ttu-id="12821-305">輸入網路 Proxy 伺服器的 URI。</span><span class="sxs-lookup"><span data-stu-id="12821-305">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="12821-306">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="12821-306">-ProxyCredential</span></span>

<span data-ttu-id="12821-307">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="12821-307">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="12821-308">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="12821-308">The default is the current user.</span></span>

<span data-ttu-id="12821-309">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ）， **User@Domain.Com** 或輸入一個 `PSCredential` 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="12821-309">Type a user name, such as **User01** or **Domain01\User01** , **User@Domain.Com** , or enter a `PSCredential` object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="12821-310">只有當命令中也使用 **Proxy** 參數時，此參數才會有效。</span><span class="sxs-lookup"><span data-stu-id="12821-310">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="12821-311">您無法在同一個命令中使用 **ProxyCredential** 和 **ProxyUseDefaultCredentials** 參數。</span><span class="sxs-lookup"><span data-stu-id="12821-311">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="12821-312">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="12821-312">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="12821-313">指出此 Cmdlet 會使用目前使用者的認證來存取 **proxy** 參數所指定的 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="12821-313">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="12821-314">只有當命令中也使用 **Proxy** 參數時，此參數才會有效。</span><span class="sxs-lookup"><span data-stu-id="12821-314">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="12821-315">您無法在同一個命令中使用 **ProxyCredential** 和 **ProxyUseDefaultCredentials** 參數。</span><span class="sxs-lookup"><span data-stu-id="12821-315">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="12821-316">-Resume</span><span class="sxs-lookup"><span data-stu-id="12821-316">-Resume</span></span>

<span data-ttu-id="12821-317">盡力嘗試繼續下載部分檔案。</span><span class="sxs-lookup"><span data-stu-id="12821-317">Performs a best effort attempt to resume downloading a partial file.</span></span> <span data-ttu-id="12821-318">**Resume** 需要 **OutFile** 。</span><span class="sxs-lookup"><span data-stu-id="12821-318">**Resume** requires **OutFile** .</span></span>

<span data-ttu-id="12821-319">**Resume** 只會在本機檔案和遠端檔案的大小上運作，而且不會執行本機檔案和遠端檔案相同的其他驗證。</span><span class="sxs-lookup"><span data-stu-id="12821-319">**Resume** only operates on the size of the local file and remote file and performs no other validation that the local file and the remote file are the same.</span></span>

<span data-ttu-id="12821-320">如果本機檔案大小小於遠端檔案大小，則 Cmdlet 會嘗試繼續下載檔案，並將剩餘的位元組附加至檔案結尾。</span><span class="sxs-lookup"><span data-stu-id="12821-320">If the local file size is smaller than the remote file size, then the cmdlet attempts to resume downloading the file and append the remaining bytes to the end of the file.</span></span>

<span data-ttu-id="12821-321">如果本機檔案大小與遠端檔案大小相同，則不會採取任何動作，而且 Cmdlet 會假設下載已完成。</span><span class="sxs-lookup"><span data-stu-id="12821-321">If the local file size is the same as the remote file size, then no action is taken and the cmdlet assumes the download already complete.</span></span>

<span data-ttu-id="12821-322">如果本機檔案大小大於遠端檔案大小，則會覆寫本機檔案，並重新下載整個遠端檔案。</span><span class="sxs-lookup"><span data-stu-id="12821-322">If the local file size is larger than the remote file size, then the local file is overwritten and the entire remote file is re-downloaded.</span></span> <span data-ttu-id="12821-323">這種行為與使用 **OutFile** 而不需要 **Resume** 的行為相同。</span><span class="sxs-lookup"><span data-stu-id="12821-323">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="12821-324">如果遠端伺服器不支援下載繼續，則會覆寫本機檔案，並重新下載整個遠端檔案。</span><span class="sxs-lookup"><span data-stu-id="12821-324">If the remote server does not support download resuming, then the local file is overwritten and the entire remote file is re-downloaded.</span></span> <span data-ttu-id="12821-325">這種行為與使用 **OutFile** 而不需要 **Resume** 的行為相同。</span><span class="sxs-lookup"><span data-stu-id="12821-325">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="12821-326">如果本機檔案不存在，則會建立本機檔案，並下載整個遠端檔案。</span><span class="sxs-lookup"><span data-stu-id="12821-326">If the local file does not exist, then the local file is created and the entire remote file is downloaded.</span></span> <span data-ttu-id="12821-327">這種行為與使用 **OutFile** 而不需要 **Resume** 的行為相同。</span><span class="sxs-lookup"><span data-stu-id="12821-327">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="12821-328">這項功能已在 PowerShell 6.1.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="12821-328">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="12821-329">-RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="12821-329">-RetryIntervalSec</span></span>

<span data-ttu-id="12821-330">指定當收到400和599（含或304）之間的失敗代碼時，連接重試之間的間隔。</span><span class="sxs-lookup"><span data-stu-id="12821-330">Specifies the interval between retries for the connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="12821-331">另請參閱 **MaximumRetryCount** 參數，以指定重試次數。</span><span class="sxs-lookup"><span data-stu-id="12821-331">Also see **MaximumRetryCount** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="12821-332">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="12821-332">-SessionVariable</span></span>

<span data-ttu-id="12821-333">指定此 Cmdlet 會建立 web 要求會話，並將其儲存在值中的變數。</span><span class="sxs-lookup"><span data-stu-id="12821-333">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="12821-334">輸入不含貨幣符號 () 符號的變數名稱 `$` 。</span><span class="sxs-lookup"><span data-stu-id="12821-334">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="12821-335">當您指定會話變數時，會 `Invoke-WebRequest` 建立 web 要求會話物件，並將它指派給您的 PowerShell 會話中具有指定名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="12821-335">When you specify a session variable, `Invoke-WebRequest` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="12821-336">一旦命令完成，便可在工作階段中使用變數。</span><span class="sxs-lookup"><span data-stu-id="12821-336">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="12821-337">Web 要求工作階段不同於遠端工作階段，並非持續連線。</span><span class="sxs-lookup"><span data-stu-id="12821-337">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="12821-338">它是一個物件，其中包含連線和要求的相關資訊，包括 cookie、認證、最大重新導向值，以及使用者代理字串。</span><span class="sxs-lookup"><span data-stu-id="12821-338">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="12821-339">您可以使用它在 Web 要求之間共用狀態與資料。</span><span class="sxs-lookup"><span data-stu-id="12821-339">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="12821-340">若要在後續 Web 要求中使用 Web 要求工作階段，請在 **WebSession** 參數值指定工作階段變數。</span><span class="sxs-lookup"><span data-stu-id="12821-340">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="12821-341">建立新連接時，PowerShell 會使用 web 要求會話物件中的資料。</span><span class="sxs-lookup"><span data-stu-id="12821-341">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="12821-342">若要覆寫 Web 要求工作階段中的值，請使用 Cmdlet 參數，例如 **UserAgent** 或 **Credential** 。</span><span class="sxs-lookup"><span data-stu-id="12821-342">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="12821-343">參數值的優先順序高於 Web 要求工作階段中的值。</span><span class="sxs-lookup"><span data-stu-id="12821-343">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="12821-344">您無法在同一個命令中使用 **SessionVariable** 和 **WebSession** 參數。</span><span class="sxs-lookup"><span data-stu-id="12821-344">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="12821-345">-SkipCertificateCheck</span><span class="sxs-lookup"><span data-stu-id="12821-345">-SkipCertificateCheck</span></span>

<span data-ttu-id="12821-346">略過憑證驗證檢查。</span><span class="sxs-lookup"><span data-stu-id="12821-346">Skips certificate validation checks.</span></span> <span data-ttu-id="12821-347">這包括所有驗證，例如到期、撤銷、受信任的根授權單位等等。</span><span class="sxs-lookup"><span data-stu-id="12821-347">This includes all validations such as expiration, revocation, trusted root authority, etc.</span></span>

> [!WARNING]
> <span data-ttu-id="12821-348">使用這個參數並不安全，因此不建議使用。</span><span class="sxs-lookup"><span data-stu-id="12821-348">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="12821-349">此參數僅適用于使用自我簽署憑證的已知主機，以供測試之用。</span><span class="sxs-lookup"><span data-stu-id="12821-349">This switch is only intended to be used against known hosts using a self-signed certificate for testing purposes.</span></span> <span data-ttu-id="12821-350">使用您自己的風險。</span><span class="sxs-lookup"><span data-stu-id="12821-350">Use at your own risk.</span></span>

<span data-ttu-id="12821-351">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="12821-351">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="12821-352">-SkipHeaderValidation</span><span class="sxs-lookup"><span data-stu-id="12821-352">-SkipHeaderValidation</span></span>

<span data-ttu-id="12821-353">指出 Cmdlet 應該在沒有驗證的情況下，將標頭新增至要求。</span><span class="sxs-lookup"><span data-stu-id="12821-353">Indicates the cmdlet should add headers to the request without validation.</span></span>

<span data-ttu-id="12821-354">此參數應用於需要不符合標準之標頭值的網站。</span><span class="sxs-lookup"><span data-stu-id="12821-354">This switch should be used for sites that require header values that do not conform to standards.</span></span>
<span data-ttu-id="12821-355">指定此參數會停用驗證，以允許未核取值的傳遞。</span><span class="sxs-lookup"><span data-stu-id="12821-355">Specifying this switch disables validation to allow the value to be passed unchecked.</span></span> <span data-ttu-id="12821-356">若有指定，則會新增所有標頭，而不進行驗證。</span><span class="sxs-lookup"><span data-stu-id="12821-356">When specified, all headers are added without validation.</span></span>

<span data-ttu-id="12821-357">此參數會針對傳遞給 **ContentType** 、 **標頭** 和 **UserAgent** 參數的值停用驗證。</span><span class="sxs-lookup"><span data-stu-id="12821-357">This switch disables validation for values passed to the **ContentType** , **Headers** and **UserAgent** parameters.</span></span>

<span data-ttu-id="12821-358">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="12821-358">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="12821-359">-SslProtocol</span><span class="sxs-lookup"><span data-stu-id="12821-359">-SslProtocol</span></span>

<span data-ttu-id="12821-360">設定 web 要求所允許的 SSL/TLS 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="12821-360">Sets the SSL/TLS protocols that are permissible for the web request.</span></span> <span data-ttu-id="12821-361">預設會允許系統支援的 SSL/TLS 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="12821-361">By default all, SSL/TLS protocols supported by the system are allowed.</span></span> <span data-ttu-id="12821-362">**SslProtocol** 可基於合規性目的限制特定的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="12821-362">**SslProtocol** allows for limiting to specific protocols for compliance purposes.</span></span>

<span data-ttu-id="12821-363">**SslProtocol** 使用 **WebSslProtocol** 旗標列舉。</span><span class="sxs-lookup"><span data-stu-id="12821-363">**SslProtocol** uses the **WebSslProtocol** Flag Enum.</span></span> <span data-ttu-id="12821-364">您可以使用旗標標記法來提供多個通訊協定，或結合多個 **WebSslProtocol** 選項與 **bor** ，但在所有平臺上都不支援提供多個通訊協定。</span><span class="sxs-lookup"><span data-stu-id="12821-364">It is possible to supply more than one protocol using flag notation or combining multiple **WebSslProtocol** options with **bor** , however supplying multiple protocols is not supported on all platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="12821-365">在非 Windows 平臺上，可能無法提供 `'Tls, Tls12'` 作為選項。</span><span class="sxs-lookup"><span data-stu-id="12821-365">On non-Windows platforms it may not be possible to supply `'Tls, Tls12'` as an option.</span></span>

<span data-ttu-id="12821-366">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="12821-366">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="12821-367">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="12821-367">-TimeoutSec</span></span>

<span data-ttu-id="12821-368">指定要求可在一段時間之前暫止的時間長度。輸入以秒為單位的值。</span><span class="sxs-lookup"><span data-stu-id="12821-368">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="12821-369">預設值為 0，會指定無限逾時。</span><span class="sxs-lookup"><span data-stu-id="12821-369">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="12821-370">網域名稱系統 (DNS) 查詢最多可能需要15秒的時間才會傳回或超時。如果您的要求包含需要解析的主機名稱，而且您將 **TimeoutSec** 設定為大於零的值，但不超過15秒，則在擲回 WebException 之前，可能需要15秒或更長的時間，而且您的要求超時。</span><span class="sxs-lookup"><span data-stu-id="12821-370">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="12821-371">-Token</span><span class="sxs-lookup"><span data-stu-id="12821-371">-Token</span></span>

<span data-ttu-id="12821-372">要包含在要求中的 OAuth 或持有人權杖。</span><span class="sxs-lookup"><span data-stu-id="12821-372">The OAuth or Bearer token to include in the request.</span></span> <span data-ttu-id="12821-373">某些 **驗證** 選項需要 **權杖** 。</span><span class="sxs-lookup"><span data-stu-id="12821-373">**Token** is required by certain **Authentication** options.</span></span> <span data-ttu-id="12821-374">無法獨立使用。</span><span class="sxs-lookup"><span data-stu-id="12821-374">It cannot be used independently.</span></span>

<span data-ttu-id="12821-375">**權杖** 會採用 `SecureString` 包含權杖的。</span><span class="sxs-lookup"><span data-stu-id="12821-375">**Token** takes a `SecureString` containing the token.</span></span> <span data-ttu-id="12821-376">若要以手動方式提供權杖，請使用下列各項：</span><span class="sxs-lookup"><span data-stu-id="12821-376">To supply the token manually use the following:</span></span>

`Invoke-WebRequest -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

<span data-ttu-id="12821-377">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="12821-377">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="12821-378">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="12821-378">-TransferEncoding</span></span>

<span data-ttu-id="12821-379">指定傳輸編碼 HTTP 回應標頭的值。</span><span class="sxs-lookup"><span data-stu-id="12821-379">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="12821-380">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="12821-380">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="12821-381">區塊</span><span class="sxs-lookup"><span data-stu-id="12821-381">Chunked</span></span>
- <span data-ttu-id="12821-382">壓縮</span><span class="sxs-lookup"><span data-stu-id="12821-382">Compress</span></span>
- <span data-ttu-id="12821-383">上下凹陷</span><span class="sxs-lookup"><span data-stu-id="12821-383">Deflate</span></span>
- <span data-ttu-id="12821-384">GZip</span><span class="sxs-lookup"><span data-stu-id="12821-384">GZip</span></span>
- <span data-ttu-id="12821-385">身分識別</span><span class="sxs-lookup"><span data-stu-id="12821-385">Identity</span></span>

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

### <span data-ttu-id="12821-386">-Uri</span><span class="sxs-lookup"><span data-stu-id="12821-386">-Uri</span></span>

<span data-ttu-id="12821-387">指定傳送 web 要求的網際網路資源 (URI) 的統一資源識別項。</span><span class="sxs-lookup"><span data-stu-id="12821-387">Specifies the Uniform Resource Identifier (URI) of the internet resource to which the web request is sent.</span></span> <span data-ttu-id="12821-388">輸入 URI。</span><span class="sxs-lookup"><span data-stu-id="12821-388">Enter a URI.</span></span> <span data-ttu-id="12821-389">此參數僅支援 HTTP 或 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="12821-389">This parameter supports HTTP or HTTPS only.</span></span>

<span data-ttu-id="12821-390">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="12821-390">This parameter is required.</span></span> <span data-ttu-id="12821-391">參數名稱 **Uri** 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="12821-391">The parameter name **Uri** is optional.</span></span>

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

### <span data-ttu-id="12821-392">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="12821-392">-UseBasicParsing</span></span>

<span data-ttu-id="12821-393">此參數已被取代。</span><span class="sxs-lookup"><span data-stu-id="12821-393">This parameter has been deprecated.</span></span> <span data-ttu-id="12821-394">從 PowerShell 6.0.0 開始，所有 Web 要求都會使用基本剖析。</span><span class="sxs-lookup"><span data-stu-id="12821-394">Beginning with PowerShell 6.0.0, all Web requests use basic parsing only.</span></span> <span data-ttu-id="12821-395">此參數是為了回溯相容性而包含，而且任何使用它都不會影響 Cmdlet 的操作。</span><span class="sxs-lookup"><span data-stu-id="12821-395">This parameter is included for backwards compatibility only and any use of it has no effect on the operation of the cmdlet.</span></span>

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

### <span data-ttu-id="12821-396">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="12821-396">-UseDefaultCredentials</span></span>

<span data-ttu-id="12821-397">指出此 Cmdlet 會使用目前使用者的認證來傳送 web 要求。</span><span class="sxs-lookup"><span data-stu-id="12821-397">Indicates that the cmdlet uses the credentials of the current user to send the web request.</span></span> <span data-ttu-id="12821-398">這不能與 **驗證\*\*\*\*或認證** 搭配使用，而且在所有平臺上都可能不受支援。</span><span class="sxs-lookup"><span data-stu-id="12821-398">This can't be used with **Authentication** or **Credential** and may not be supported on all platforms.</span></span>

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

### <span data-ttu-id="12821-399">-UserAgent</span><span class="sxs-lookup"><span data-stu-id="12821-399">-UserAgent</span></span>

<span data-ttu-id="12821-400">指定 Web 要求的使用者代理字串。</span><span class="sxs-lookup"><span data-stu-id="12821-400">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="12821-401">預設使用者代理程式類似于 `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` 每個作業系統和平臺的些許變化。</span><span class="sxs-lookup"><span data-stu-id="12821-401">The default user agent is similar to `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="12821-402">若要使用大部分網際網路瀏覽器所使用的標準使用者代理程式字串來測試網站，請使用 [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) 類別的屬性，例如 Chrome、FireFox、Microsoft-windows-ie-internetexplorer、Opera 和 Safari。</span><span class="sxs-lookup"><span data-stu-id="12821-402">To test a website with the standard user agent string that is used by most internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span>

<span data-ttu-id="12821-403">例如，下列命令會使用使用者代理字串進行 Internet Explorer：</span><span class="sxs-lookup"><span data-stu-id="12821-403">For example, the following command uses the user agent string for Internet Explorer:</span></span>

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

### <span data-ttu-id="12821-404">-WebSession</span><span class="sxs-lookup"><span data-stu-id="12821-404">-WebSession</span></span>

<span data-ttu-id="12821-405">指定 Web 要求工作階段。</span><span class="sxs-lookup"><span data-stu-id="12821-405">Specifies a web request session.</span></span> <span data-ttu-id="12821-406">輸入變數名稱，包括貨幣符號 (`$`) 。</span><span class="sxs-lookup"><span data-stu-id="12821-406">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="12821-407">若要覆寫 Web 要求工作階段中的值，請使用 Cmdlet 參數，例如 **UserAgent** 或 **Credential** 。</span><span class="sxs-lookup"><span data-stu-id="12821-407">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="12821-408">參數值的優先順序高於 Web 要求工作階段中的值。</span><span class="sxs-lookup"><span data-stu-id="12821-408">Parameter values take precedence over values in the web request session.</span></span> <span data-ttu-id="12821-409">`Content-Type`當提供 **主體** 的 **>multipartformdatacontent** 物件時，也會覆寫內容相關的標頭（例如）。</span><span class="sxs-lookup"><span data-stu-id="12821-409">Content related headers, such as `Content-Type`, are also be overridden when a **MultipartFormDataContent** object is supplied for **Body** .</span></span>

<span data-ttu-id="12821-410">不同于遠端會話，web 要求會話不是持續性連接。</span><span class="sxs-lookup"><span data-stu-id="12821-410">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="12821-411">它是一個物件，其中包含連線和要求的相關資訊，包括 cookie、認證、最大重新導向值，以及使用者代理字串。</span><span class="sxs-lookup"><span data-stu-id="12821-411">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="12821-412">您可以使用它在 Web 要求之間共用狀態與資料。</span><span class="sxs-lookup"><span data-stu-id="12821-412">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="12821-413">若要建立 web 要求會話，請在命令的 **SessionVariable** 參數值中輸入不含貨幣符號的變數名稱 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="12821-413">To create a web request session, enter a variable name, without a dollar sign, in the value of the **SessionVariable** parameter of an `Invoke-WebRequest` command.</span></span> <span data-ttu-id="12821-414">`Invoke-WebRequest` 建立會話，並將它儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="12821-414">`Invoke-WebRequest` creates the session and saves it in the variable.</span></span> <span data-ttu-id="12821-415">在後續命令中，使用變數作為 **WebSession** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="12821-415">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="12821-416">您無法在同一個命令中使用 **SessionVariable** 和 **WebSession** 參數。</span><span class="sxs-lookup"><span data-stu-id="12821-416">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="12821-417">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="12821-417">CommonParameters</span></span>

<span data-ttu-id="12821-418">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="12821-418">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="12821-419">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="12821-419">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="12821-420">輸入</span><span class="sxs-lookup"><span data-stu-id="12821-420">INPUTS</span></span>

### <span data-ttu-id="12821-421">System.Object</span><span class="sxs-lookup"><span data-stu-id="12821-421">System.Object</span></span>

<span data-ttu-id="12821-422">您可以使用管線將 web 要求的主體傳送至 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="12821-422">You can pipe the body of a web request to `Invoke-WebRequest`.</span></span>

## <span data-ttu-id="12821-423">輸出</span><span class="sxs-lookup"><span data-stu-id="12821-423">OUTPUTS</span></span>

### <span data-ttu-id="12821-424">BasicHtmlWebResponseObject。</span><span class="sxs-lookup"><span data-stu-id="12821-424">Microsoft.PowerShell.Commands.BasicHtmlWebResponseObject</span></span>

## <span data-ttu-id="12821-425">注意</span><span class="sxs-lookup"><span data-stu-id="12821-425">NOTES</span></span>

<span data-ttu-id="12821-426">從 PowerShell 6.0.0 開始 `Invoke-WebRequest` 僅支援基本剖析。</span><span class="sxs-lookup"><span data-stu-id="12821-426">Beginning with PowerShell 6.0.0 `Invoke-WebRequest` supports basic parsing only.</span></span>

<span data-ttu-id="12821-427">如需 **BasicHtmlWebResponseObject** 物件類型的詳細資訊，請參閱 [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject)。</span><span class="sxs-lookup"><span data-stu-id="12821-427">For more information about the **Microsoft.PowerShell.Commands.BasicHtmlWebResponseObject** object type, see [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject).</span></span>

<span data-ttu-id="12821-428">如需 .NET 如何提供 proxy 服務給 PowerShell 的詳細資訊，請參閱 [透過 Proxy 存取網際網路](/dotnet/framework/network-programming/accessing-the-internet-through-a-proxy)。</span><span class="sxs-lookup"><span data-stu-id="12821-428">For more information about how .NET provides proxy services to PowerShell, see [Accessing the Internet Through a Proxy](/dotnet/framework/network-programming/accessing-the-internet-through-a-proxy).</span></span>

## <span data-ttu-id="12821-429">相關連結</span><span class="sxs-lookup"><span data-stu-id="12821-429">RELATED LINKS</span></span>

[<span data-ttu-id="12821-430">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="12821-430">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="12821-431">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="12821-431">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="12821-432">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="12821-432">ConvertTo-Json</span></span>](ConvertTo-Json.md)
