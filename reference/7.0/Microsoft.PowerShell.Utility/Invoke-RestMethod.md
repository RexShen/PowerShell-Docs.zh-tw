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
# <span data-ttu-id="4bda0-103">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="4bda0-103">Invoke-RestMethod</span></span>

## <span data-ttu-id="4bda0-104">概要</span><span class="sxs-lookup"><span data-stu-id="4bda0-104">SYNOPSIS</span></span>
<span data-ttu-id="4bda0-105">傳送 HTTP 或 HTTPS 要求至 RESTful Web 服務。</span><span class="sxs-lookup"><span data-stu-id="4bda0-105">Sends an HTTP or HTTPS request to a RESTful web service.</span></span>

## <span data-ttu-id="4bda0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4bda0-106">SYNTAX</span></span>

### <span data-ttu-id="4bda0-107">StandardMethod (預設) </span><span class="sxs-lookup"><span data-stu-id="4bda0-107">StandardMethod (Default)</span></span>

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

### <span data-ttu-id="4bda0-108">StandardMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="4bda0-108">StandardMethodNoProxy</span></span>

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

### <span data-ttu-id="4bda0-109">CustomMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="4bda0-109">CustomMethodNoProxy</span></span>

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

### <span data-ttu-id="4bda0-110">CustomMethod</span><span class="sxs-lookup"><span data-stu-id="4bda0-110">CustomMethod</span></span>

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

## <span data-ttu-id="4bda0-111">描述</span><span class="sxs-lookup"><span data-stu-id="4bda0-111">Description</span></span>

<span data-ttu-id="4bda0-112">此 `Invoke-RestMethod` Cmdlet 會將 HTTP 和 HTTPS 要求傳送至具象狀態傳輸 (REST) web 服務，以傳回豐富的結構化資料。</span><span class="sxs-lookup"><span data-stu-id="4bda0-112">The `Invoke-RestMethod` cmdlet sends HTTP and HTTPS requests to Representational State Transfer (REST) web services that return richly structured data.</span></span>

<span data-ttu-id="4bda0-113">PowerShell 會根據資料類型來格式化回應。</span><span class="sxs-lookup"><span data-stu-id="4bda0-113">PowerShell formats the response based to the data type.</span></span> <span data-ttu-id="4bda0-114">針對 RSS 或 ATOM 摘要，PowerShell 會傳回專案 XML 節點。</span><span class="sxs-lookup"><span data-stu-id="4bda0-114">For an RSS or ATOM feed, PowerShell returns the Item or Entry XML nodes.</span></span> <span data-ttu-id="4bda0-115">針對 JavaScript 物件標記法 (JSON) 或 XML，PowerShell 會將內容轉換或還原序列化為物件。</span><span class="sxs-lookup"><span data-stu-id="4bda0-115">For JavaScript Object Notation (JSON) or XML, PowerShell converts, or deserializes, the content into objects.</span></span>

<span data-ttu-id="4bda0-116">此 Cmdlet 是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="4bda0-116">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="4bda0-117">從 PowerShell 7.0 開始，可 `Invoke-RestMethod` 支援環境變數所定義的 proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="4bda0-117">Beginning in PowerShell 7.0, `Invoke-RestMethod` supports proxy configuration defined by environment variables.</span></span> <span data-ttu-id="4bda0-118">請參閱本文的「 [附注](#notes) 」一節。</span><span class="sxs-lookup"><span data-stu-id="4bda0-118">See the [Notes](#notes) section of this article.</span></span>

## <span data-ttu-id="4bda0-119">範例</span><span class="sxs-lookup"><span data-stu-id="4bda0-119">EXAMPLES</span></span>

### <span data-ttu-id="4bda0-120">範例1：取得 PowerShell RSS 摘要</span><span class="sxs-lookup"><span data-stu-id="4bda0-120">Example 1: Get the PowerShell RSS feed</span></span>

<span data-ttu-id="4bda0-121">此範例會使用 `Invoke-RestMethod` Cmdlet 從 PowerShell Blog 的 rss 摘要中取得資訊。</span><span class="sxs-lookup"><span data-stu-id="4bda0-121">This example uses the `Invoke-RestMethod` cmdlet to get information from the PowerShell Blog RSS feed.</span></span> <span data-ttu-id="4bda0-122">此命令會使用 `Format-Table` Cmdlet，在資料表中顯示每個 blog 的 **Title** 和 **pubDate** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4bda0-122">The command uses the `Format-Table` cmdlet to display the values of the **Title** and **pubDate** properties of each blog in a table.</span></span>

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

### <span data-ttu-id="4bda0-123">範例2：執行 POST 要求</span><span class="sxs-lookup"><span data-stu-id="4bda0-123">Example 2: Run a POST request</span></span>

<span data-ttu-id="4bda0-124">在此範例中，使用者會 `Invoke-RestMethod` 執行，以在使用者組織內部網路網站上執行 POST 要求。</span><span class="sxs-lookup"><span data-stu-id="4bda0-124">In this example, a user runs `Invoke-RestMethod` to do a POST request on an intranet website in the user's organization.</span></span>

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

<span data-ttu-id="4bda0-125">系統會提示您輸入認證，然後將其儲存在中 `$Cred` ，並在中定義將存取的 URL `$Url` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-125">The credentials are prompted for and then stored in `$Cred` and the URL that will be access is defined in `$Url`.</span></span>

<span data-ttu-id="4bda0-126">`$Body`變數描述搜尋準則、將 CSV 指定為輸出模式，並指定在兩天前開始並結束一天前的傳回資料的時間週期。</span><span class="sxs-lookup"><span data-stu-id="4bda0-126">The `$Body` variable describes the search criteria, specifies CSV as the output mode, and specifies a time period for returned data that starts two days ago and ends one day ago.</span></span> <span data-ttu-id="4bda0-127">本文變數指定的參數值適用于 `Invoke-RestMethod` 正在進行通訊的特定 REST API。</span><span class="sxs-lookup"><span data-stu-id="4bda0-127">The body variable specifies values for parameters that apply to the particular REST API with which `Invoke-RestMethod` is communicating.</span></span>

<span data-ttu-id="4bda0-128">此 `Invoke-RestMethod` 命令會使用所有變數來執行，並指定所產生 CSV 輸出檔的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="4bda0-128">The `Invoke-RestMethod` command is run with all variables in place, specifying a path and file name for the resulting CSV output file.</span></span>

### <span data-ttu-id="4bda0-129">範例3：遵循關聯連結</span><span class="sxs-lookup"><span data-stu-id="4bda0-129">Example 3: Follow relation links</span></span>

<span data-ttu-id="4bda0-130">某些 REST Api 支援每個 [RFC5988](https://tools.ietf.org/html/rfc5988#page-6)的關聯性連結的分頁。</span><span class="sxs-lookup"><span data-stu-id="4bda0-130">Some REST APIs support pagination via Relation Links per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6).</span></span> <span data-ttu-id="4bda0-131">您可以讓 Cmdlet 為您完成此動作，而不是剖析標頭來取得下一個頁面的 URL。</span><span class="sxs-lookup"><span data-stu-id="4bda0-131">Instead of parsing the header to get the URL for the next page, you can have the cmdlet do this for you.</span></span> <span data-ttu-id="4bda0-132">此範例會傳回來自 PowerShell GitHub 存放庫的前兩個問題頁面。</span><span class="sxs-lookup"><span data-stu-id="4bda0-132">This example returns the first two pages of issues from the PowerShell GitHub repository.</span></span>

```powershell
$url = 'https://api.github.com/repos/powershell/powershell/issues'
Invoke-RestMethod $url -FollowRelLink -MaximumFollowRelLink 2
```

### <span data-ttu-id="4bda0-133">範例4：簡化的多部分/表單資料提交</span><span class="sxs-lookup"><span data-stu-id="4bda0-133">Example 4: Simplified Multipart/Form-Data Submission</span></span>

<span data-ttu-id="4bda0-134">某些 Api 需要 `multipart/form-data` 提交才能上傳檔案和混合的內容。</span><span class="sxs-lookup"><span data-stu-id="4bda0-134">Some APIs require `multipart/form-data` submissions to upload files and mixed content.</span></span> <span data-ttu-id="4bda0-135">此範例示範如何更新使用者的設定檔。</span><span class="sxs-lookup"><span data-stu-id="4bda0-135">This example demonstrates how to update a user's profile.</span></span>

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

<span data-ttu-id="4bda0-136">設定檔表單需要下欄欄位： `firstName` 、 `lastName` 、 `email` 、 `avatar` 、 `birthday` 和 `hobbies` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-136">The profile form requires these fields: `firstName`, `lastName`, `email`, `avatar`, `birthday`, and `hobbies`.</span></span> <span data-ttu-id="4bda0-137">API 預期會在欄位中提供使用者設定檔 pic 的影像 `avatar` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-137">The API is expecting an image for the user profile pic to be supplied in the `avatar` field.</span></span> <span data-ttu-id="4bda0-138">此 API 也會接受 `hobbies` 以相同形式提交的多個專案。</span><span class="sxs-lookup"><span data-stu-id="4bda0-138">The API will also accept multiple `hobbies` entries to be submitted in the same form.</span></span>

<span data-ttu-id="4bda0-139">建立 `$Form` 雜湊表時，索引鍵名稱會用來做為表單欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="4bda0-139">When creating the `$Form` HashTable, the key names are used as form field names.</span></span> <span data-ttu-id="4bda0-140">根據預設，雜湊表的值會轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="4bda0-140">By default, the values of the HashTable will be converted to strings.</span></span> <span data-ttu-id="4bda0-141">如果有某個 `System.IO.FileInfo` 值，則會提交檔案內容。</span><span class="sxs-lookup"><span data-stu-id="4bda0-141">If a `System.IO.FileInfo` value is present, the file contents will be submitted.</span></span> <span data-ttu-id="4bda0-142">如果有集合（例如陣列或清單），則會提交表單欄位多次。</span><span class="sxs-lookup"><span data-stu-id="4bda0-142">If a collection such as arrays or lists are present, the form field will be submitted multiple times.</span></span>

<span data-ttu-id="4bda0-143">藉由 `Get-Item` 在索引 `avatar` 鍵上使用， `FileInfo` 物件將會設定為值。</span><span class="sxs-lookup"><span data-stu-id="4bda0-143">By using `Get-Item` on the `avatar` key, the `FileInfo` object will be set as the value.</span></span> <span data-ttu-id="4bda0-144">結果是將會提交的影像資料 `jdoe.png` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-144">The result is that the image data for `jdoe.png` will be submitted.</span></span>

<span data-ttu-id="4bda0-145">藉由提供清單給 `hobbies` 金鑰， `hobbies` 每個清單專案的提交一次就會出現此欄位。</span><span class="sxs-lookup"><span data-stu-id="4bda0-145">By supplying a list to the `hobbies` key, the `hobbies` field will be present in the submissions once for each list item.</span></span>

### <span data-ttu-id="4bda0-146">範例5：傳遞多個標頭</span><span class="sxs-lookup"><span data-stu-id="4bda0-146">Example 5: Pass multiple headers</span></span>

<span data-ttu-id="4bda0-147">Api 通常需要經過傳遞的標頭以進行驗證或驗證。</span><span class="sxs-lookup"><span data-stu-id="4bda0-147">APIs often require passed headers for authentication or validation.</span></span> <span data-ttu-id="4bda0-148">此範例示範如何將多個標頭從傳遞 `hash-table` 至 REST API。</span><span class="sxs-lookup"><span data-stu-id="4bda0-148">This example demonstrates, how to pass multiple headers from a `hash-table` to a REST API.</span></span>

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

## <span data-ttu-id="4bda0-149">參數</span><span class="sxs-lookup"><span data-stu-id="4bda0-149">Parameters</span></span>

### <span data-ttu-id="4bda0-150">-AllowUnencryptedAuthentication</span><span class="sxs-lookup"><span data-stu-id="4bda0-150">-AllowUnencryptedAuthentication</span></span>

<span data-ttu-id="4bda0-151">允許透過未加密的連接傳送認證和密碼。</span><span class="sxs-lookup"><span data-stu-id="4bda0-151">Allows sending of credentials and secrets over unencrypted connections.</span></span> <span data-ttu-id="4bda0-152">根據預設，如果提供的認證 **或任何\*\*\*\*驗證** 選項的 **Uri** 不是以開頭， `https://` 將會產生錯誤，而且要求將會中止，以防止不慎以純文字方式透過未加密的連接來傳達秘密。</span><span class="sxs-lookup"><span data-stu-id="4bda0-152">By default, supplying **Credential** or any **Authentication** option with a **Uri** that does not begin with `https://` will result in an error and the request will abort to prevent unintentionally communicating secrets in plain text over unencrypted connections.</span></span> <span data-ttu-id="4bda0-153">若要以您自己的風險覆寫此行為，請提供 **AllowUnencryptedAuthentication** 參數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-153">To override this behavior at your own risk, supply the **AllowUnencryptedAuthentication** parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="4bda0-154">使用這個參數並不安全，因此不建議使用。</span><span class="sxs-lookup"><span data-stu-id="4bda0-154">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="4bda0-155">它僅提供給無法提供加密連接的舊版系統相容。</span><span class="sxs-lookup"><span data-stu-id="4bda0-155">It is provided only for compatibility with legacy systems that cannot provide encrypted connections.</span></span> <span data-ttu-id="4bda0-156">使用您自己的風險。</span><span class="sxs-lookup"><span data-stu-id="4bda0-156">Use at your own risk.</span></span>

<span data-ttu-id="4bda0-157">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="4bda0-157">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="4bda0-158">-Authentication</span><span class="sxs-lookup"><span data-stu-id="4bda0-158">-Authentication</span></span>

<span data-ttu-id="4bda0-159">指定要用於要求的明確驗證類型。</span><span class="sxs-lookup"><span data-stu-id="4bda0-159">Specifies the explicit authentication type to use for the request.</span></span> <span data-ttu-id="4bda0-160">預設值為 [無]。</span><span class="sxs-lookup"><span data-stu-id="4bda0-160">The default is **None** .</span></span>
<span data-ttu-id="4bda0-161">**驗證** 無法與 **UseDefaultCredentials** 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="4bda0-161">**Authentication** can't be used with **UseDefaultCredentials** .</span></span>

<span data-ttu-id="4bda0-162">可用的驗證選項：</span><span class="sxs-lookup"><span data-stu-id="4bda0-162">Available Authentication Options:</span></span>

- <span data-ttu-id="4bda0-163">**無** ：當未提供 **驗證** 時，這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="4bda0-163">**None** : This is the default option when **Authentication** is not supplied.</span></span> <span data-ttu-id="4bda0-164">不會使用任何明確驗證。</span><span class="sxs-lookup"><span data-stu-id="4bda0-164">No explicit authentication will be used.</span></span>
- <span data-ttu-id="4bda0-165">**基本** ：需要 **認證** 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-165">**Basic** : Requires **Credential** .</span></span> <span data-ttu-id="4bda0-166">認證將用來傳送的格式為 RFC 7617 基本驗證 `Authorization: Basic` 標頭 `base64(user:password)` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-166">The credentials will be used to send an RFC 7617 Basic Authentication `Authorization: Basic` header in the format of `base64(user:password)`.</span></span>
- <span data-ttu-id="4bda0-167">**持有** 人：需要 **權杖** 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-167">**Bearer** : Requires **Token** .</span></span> <span data-ttu-id="4bda0-168">將會傳送和 RFC 6750 `Authorization: Bearer` 標頭與提供的權杖。</span><span class="sxs-lookup"><span data-stu-id="4bda0-168">Will send and RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="4bda0-169">這是 **OAuth** 的別名</span><span class="sxs-lookup"><span data-stu-id="4bda0-169">This is an alias for **OAuth**</span></span>
- <span data-ttu-id="4bda0-170">**OAuth** ：需要 **權杖** 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-170">**OAuth** : Requires **Token** .</span></span> <span data-ttu-id="4bda0-171">將會傳送 `Authorization: Bearer` 具有所提供權杖的 RFC 6750 標頭。</span><span class="sxs-lookup"><span data-stu-id="4bda0-171">Will send an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="4bda0-172">這是 **持有** 人的別名</span><span class="sxs-lookup"><span data-stu-id="4bda0-172">This is an alias for **Bearer**</span></span>

<span data-ttu-id="4bda0-173">提供 **驗證** 將會覆寫 `Authorization` 提供給 **標頭** 或包含在 **WebSession** 中的任何標頭。</span><span class="sxs-lookup"><span data-stu-id="4bda0-173">Supplying **Authentication** will override any `Authorization` headers supplied to **Headers** or included in **WebSession** .</span></span>

<span data-ttu-id="4bda0-174">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="4bda0-174">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="4bda0-175">-Body</span><span class="sxs-lookup"><span data-stu-id="4bda0-175">-Body</span></span>

<span data-ttu-id="4bda0-176">指定要求的主體。</span><span class="sxs-lookup"><span data-stu-id="4bda0-176">Specifies the body of the request.</span></span> <span data-ttu-id="4bda0-177">主體為標頭之後的要求內容。</span><span class="sxs-lookup"><span data-stu-id="4bda0-177">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="4bda0-178">您也可以使用管線將主體值傳送至 `Invoke-RestMethod` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-178">You can also pipe a body value to `Invoke-RestMethod`.</span></span>

<span data-ttu-id="4bda0-179">**Body** 參數可用來指定查詢參數的清單，或指定回應的內容。</span><span class="sxs-lookup"><span data-stu-id="4bda0-179">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="4bda0-180">當輸入為 GET 要求且主體為 `IDictionary` (通常會) 雜湊表時，主體會新增至統一資源識別項 (URI) 作為查詢參數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-180">When the input is a GET request, and the body is an `IDictionary` (typically, a hash table), the body is added to the Uniform Resource Identifier (URI) as query parameters.</span></span> <span data-ttu-id="4bda0-181">對於其他要求類型 (例如，POST)，會以標準「名稱=值」格式將主體設定為要求主體的值。</span><span class="sxs-lookup"><span data-stu-id="4bda0-181">For other request types (such as POST), the body is set as the value of the request body in the standard name=value format.</span></span>

<span data-ttu-id="4bda0-182">當主體為表單，或它是另一個呼叫的輸出時 `Invoke-WebRequest` ，PowerShell 會將要求內容設定為表單欄位。</span><span class="sxs-lookup"><span data-stu-id="4bda0-182">When the body is a form, or it's the output of another `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>

<span data-ttu-id="4bda0-183">**Body** 參數也可以接受 **>multipartformdatacontent** 物件。</span><span class="sxs-lookup"><span data-stu-id="4bda0-183">The **Body** parameter may also accept a **System.Net.Http.MultipartFormDataContent** object.</span></span> <span data-ttu-id="4bda0-184">這將有助於 `multipart/form-data` 要求。</span><span class="sxs-lookup"><span data-stu-id="4bda0-184">This will facilitate `multipart/form-data` requests.</span></span> <span data-ttu-id="4bda0-185">提供 **主體** 的 **>multipartformdatacontent** 物件時，提供給 **ContentType** 、 **標頭** 或 **WebSession** 參數的任何內容相關標頭都會被物件的內容標頭覆寫 `MultipartFormDataContent` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-185">When a **MultipartFormDataContent** object is supplied for **Body** , any content related headers supplied to the **ContentType** , **Headers** , or **WebSession** parameters will be overridden by the content headers of the `MultipartFormDataContent` object.</span></span> <span data-ttu-id="4bda0-186">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="4bda0-186">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="4bda0-187">-Certificate</span><span class="sxs-lookup"><span data-stu-id="4bda0-187">-Certificate</span></span>

<span data-ttu-id="4bda0-188">指定用於安全 Web 要求的用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="4bda0-188">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="4bda0-189">輸入包含憑證的變數，或可取得憑證的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="4bda0-189">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="4bda0-190">若要尋找憑證，請使用 `Get-PfxCertificate` 或使用 `Get-ChildItem` 憑證 (`Cert:`) 磁片磁碟機中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4bda0-190">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="4bda0-191">若憑證無效或沒有足夠的許可權，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="4bda0-191">If the certificate isn't valid or doesn't have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="4bda0-192">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="4bda0-192">-CertificateThumbprint</span></span>

<span data-ttu-id="4bda0-193">指定具有傳送要求權限之使用者帳戶的數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="4bda0-193">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="4bda0-194">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="4bda0-194">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="4bda0-195">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="4bda0-195">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="4bda0-196">這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="4bda0-196">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="4bda0-197">若要取得憑證指紋，請使用 `Get-Item` `Get-ChildItem` PowerShell 磁片磁碟機中的或命令 `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-197">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

> [!NOTE]
> <span data-ttu-id="4bda0-198">這項功能目前僅支援 Windows OS 平臺。</span><span class="sxs-lookup"><span data-stu-id="4bda0-198">This feature is currently only supported on Windows OS platforms.</span></span>

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

### <span data-ttu-id="4bda0-199">-ContentType</span><span class="sxs-lookup"><span data-stu-id="4bda0-199">-ContentType</span></span>

<span data-ttu-id="4bda0-200">指定 Web 要求的內容類型。</span><span class="sxs-lookup"><span data-stu-id="4bda0-200">Specifies the content type of the web request.</span></span>

<span data-ttu-id="4bda0-201">如果省略此參數且要求方法為 POST，則會 `Invoke-RestMethod` 將內容類型設定為 `application/x-www-form-urlencoded` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-201">If this parameter is omitted and the request method is POST, `Invoke-RestMethod` sets the content type to `application/x-www-form-urlencoded`.</span></span> <span data-ttu-id="4bda0-202">否則，呼叫中不會指定內容類型。</span><span class="sxs-lookup"><span data-stu-id="4bda0-202">Otherwise, the content type isn't specified in the call.</span></span>

<span data-ttu-id="4bda0-203">**ContentType** `MultipartFormDataContent` 提供 **主體** 的物件時，會覆寫 ContentType。</span><span class="sxs-lookup"><span data-stu-id="4bda0-203">**ContentType** will be overridden when a `MultipartFormDataContent` object is supplied for **Body** .</span></span>

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

### <span data-ttu-id="4bda0-204">-Credential</span><span class="sxs-lookup"><span data-stu-id="4bda0-204">-Credential</span></span>

<span data-ttu-id="4bda0-205">指定具有傳送要求權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="4bda0-205">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="4bda0-206">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="4bda0-206">The default is the current user.</span></span>

<span data-ttu-id="4bda0-207">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-207">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="4bda0-208">**認證可以** 單獨使用，也可以搭配特定的 **驗證** 參數選項使用。</span><span class="sxs-lookup"><span data-stu-id="4bda0-208">**Credential** can be used alone or in conjunction with certain **Authentication** parameter options.</span></span> <span data-ttu-id="4bda0-209">單獨使用時，如果遠端伺服器傳送驗證挑戰要求，它只會提供遠端伺服器的認證。</span><span class="sxs-lookup"><span data-stu-id="4bda0-209">When used alone, it will only supply credentials to the remote server if the remote server sends an authentication challenge request.</span></span> <span data-ttu-id="4bda0-210">與 **驗證** 選項搭配使用時，將會明確地傳送認證。</span><span class="sxs-lookup"><span data-stu-id="4bda0-210">When used with **Authentication** options, the credentials will be explicitly sent.</span></span>

<span data-ttu-id="4bda0-211">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="4bda0-211">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="4bda0-212">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="4bda0-212">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="4bda0-213">-CustomMethod</span><span class="sxs-lookup"><span data-stu-id="4bda0-213">-CustomMethod</span></span>

<span data-ttu-id="4bda0-214">指定用於 web 要求的自訂方法。</span><span class="sxs-lookup"><span data-stu-id="4bda0-214">Specifies custom method used for the web request.</span></span> <span data-ttu-id="4bda0-215">這可以與端點所要求的要求方法搭配使用，而不是 **方法** 上的可用選項。</span><span class="sxs-lookup"><span data-stu-id="4bda0-215">This can be used with the Request Method required by the endpoint is not an available option on the **Method** .</span></span> <span data-ttu-id="4bda0-216">**方法** 和 **CustomMethod** 無法一起使用。</span><span class="sxs-lookup"><span data-stu-id="4bda0-216">**Method** and **CustomMethod** cannot be used together.</span></span>

<span data-ttu-id="4bda0-217">範例：</span><span class="sxs-lookup"><span data-stu-id="4bda0-217">Example:</span></span>

`Invoke-RestMethod -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

<span data-ttu-id="4bda0-218">這會對 `TEST` API 發出 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="4bda0-218">This makes a `TEST` HTTP request to the API.</span></span>

<span data-ttu-id="4bda0-219">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="4bda0-219">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="4bda0-220">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="4bda0-220">-DisableKeepAlive</span></span>

<span data-ttu-id="4bda0-221">指出此 Cmdlet 會將 HTTP 標頭中的 **KeepAlive** 值設定為 False。</span><span class="sxs-lookup"><span data-stu-id="4bda0-221">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to False.</span></span> <span data-ttu-id="4bda0-222">**KeepAlive** 預設為 True。</span><span class="sxs-lookup"><span data-stu-id="4bda0-222">By default, **KeepAlive** is True.</span></span> <span data-ttu-id="4bda0-223">**KeepAlive** 會建立伺服器持續連線，有助於後續要求。</span><span class="sxs-lookup"><span data-stu-id="4bda0-223">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="4bda0-224">-FollowRelLink</span><span class="sxs-lookup"><span data-stu-id="4bda0-224">-FollowRelLink</span></span>

<span data-ttu-id="4bda0-225">指出 Cmdlet 應遵循關聯連結。</span><span class="sxs-lookup"><span data-stu-id="4bda0-225">Indicates the cmdlet should follow relation links.</span></span>

<span data-ttu-id="4bda0-226">某些 REST Api 支援每個 [RFC5988](https://tools.ietf.org/html/rfc5988#page-6)的關聯性連結的分頁。</span><span class="sxs-lookup"><span data-stu-id="4bda0-226">Some REST APIs support pagination via Relation Links per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6).</span></span> <span data-ttu-id="4bda0-227">您可以讓 Cmdlet 為您完成此動作，而不是剖析標頭來取得下一個頁面的 URL。</span><span class="sxs-lookup"><span data-stu-id="4bda0-227">Instead of parsing the header to get the URL for the next page, you can have the cmdlet do this for you.</span></span> <span data-ttu-id="4bda0-228">若要設定要遵循關聯連結的次數，請使用 **MaximumFollowRelLink** 參數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-228">To set how many times to follow relation links, use the **MaximumFollowRelLink** parameter.</span></span>

<span data-ttu-id="4bda0-229">使用這個參數時，此 Cmdlet 會傳回結果的頁面集合。</span><span class="sxs-lookup"><span data-stu-id="4bda0-229">When using this switch, the cmdlet returns a collection of pages of results.</span></span> <span data-ttu-id="4bda0-230">每一頁的結果可能包含多個結果專案。</span><span class="sxs-lookup"><span data-stu-id="4bda0-230">Each page of results may contain multiple result items.</span></span>

<span data-ttu-id="4bda0-231">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="4bda0-231">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="4bda0-232">-Form</span><span class="sxs-lookup"><span data-stu-id="4bda0-232">-Form</span></span>

<span data-ttu-id="4bda0-233">將字典轉換為 `multipart/form-data` 提交。</span><span class="sxs-lookup"><span data-stu-id="4bda0-233">Converts a dictionary to a `multipart/form-data` submission.</span></span> <span data-ttu-id="4bda0-234">**表單\*\*\*\*不得與內文一起使用** 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-234">**Form** may not be used with **Body** .</span></span>
<span data-ttu-id="4bda0-235">如果將忽略 **ContentType** 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-235">If **ContentType** will be ignored.</span></span>

<span data-ttu-id="4bda0-236">字典的索引鍵將會用來做為表單功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="4bda0-236">The keys of the dictionary will be used as the form field names.</span></span> <span data-ttu-id="4bda0-237">根據預設，表單值會轉換成字串值。</span><span class="sxs-lookup"><span data-stu-id="4bda0-237">By default, form values will be converted to string values.</span></span>

<span data-ttu-id="4bda0-238">如果值是 **FileInfo** 物件，則會提交二進位檔案內容。</span><span class="sxs-lookup"><span data-stu-id="4bda0-238">If the value is a **System.IO.FileInfo** object, then the binary file contents will be submitted.</span></span>
<span data-ttu-id="4bda0-239">檔案的名稱將會提交為 `filename` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-239">The name of the file will be submitted as the `filename`.</span></span> <span data-ttu-id="4bda0-240">MIME 將設定為 `application/octet-stream` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-240">The MIME will be set as `application/octet-stream`.</span></span> <span data-ttu-id="4bda0-241">`Get-Item` 可以用來簡化 **FileInfo** 物件的提供。</span><span class="sxs-lookup"><span data-stu-id="4bda0-241">`Get-Item` can be used to simplify supplying the **System.IO.FileInfo** object.</span></span>

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

<span data-ttu-id="4bda0-242">如果值是集合型別（例如陣列或清單），則會多次提交 for 欄位。</span><span class="sxs-lookup"><span data-stu-id="4bda0-242">If the value is a collection type, such as an Array or List, the for field will be submitted multiple times.</span></span> <span data-ttu-id="4bda0-243">預設會將清單的值視為字串。</span><span class="sxs-lookup"><span data-stu-id="4bda0-243">The values of the list will be treated as strings by default.</span></span> <span data-ttu-id="4bda0-244">如果值是 **FileInfo** 物件，則會提交二進位檔案內容。</span><span class="sxs-lookup"><span data-stu-id="4bda0-244">If the value is a **System.IO.FileInfo** object, then the binary file contents will be submitted.</span></span> <span data-ttu-id="4bda0-245">不支援嵌套集合。</span><span class="sxs-lookup"><span data-stu-id="4bda0-245">Nested collections aren't supported.</span></span>

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

<span data-ttu-id="4bda0-246">在上述範例中， `tags` 欄位會在表單中提供三次，每一個、和都提供一次 `Vacation` `Italy` `2017` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-246">In the above example, the `tags` field will be supplied three times in the form, once for each of `Vacation`, `Italy`, and `2017`.</span></span> <span data-ttu-id="4bda0-247">此 `pictures` 欄位也會針對資料夾中的每個檔案提交一次 `2017-Italy` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-247">The `pictures` field will also be submitted once for each file in the `2017-Italy` folder.</span></span> <span data-ttu-id="4bda0-248">該資料夾中檔案的二進位內容將會以值的形式提交。</span><span class="sxs-lookup"><span data-stu-id="4bda0-248">The binary contents of the files in that folder will be submitted as the values.</span></span>

<span data-ttu-id="4bda0-249">這項功能已在 PowerShell 6.1.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="4bda0-249">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="4bda0-250">-Headers</span><span class="sxs-lookup"><span data-stu-id="4bda0-250">-Headers</span></span>

<span data-ttu-id="4bda0-251">指定 Web 要求的標頭。</span><span class="sxs-lookup"><span data-stu-id="4bda0-251">Specifies the headers of the web request.</span></span> <span data-ttu-id="4bda0-252">輸入雜湊表或字典。</span><span class="sxs-lookup"><span data-stu-id="4bda0-252">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="4bda0-253">若要設定 UserAgent 標頭，請使用 **UserAgent** 參數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-253">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="4bda0-254">您無法使用這個參數來指定 `User-Agent` 或 cookie 標頭。</span><span class="sxs-lookup"><span data-stu-id="4bda0-254">You cannot use this parameter to specify `User-Agent` or cookie headers.</span></span>

<span data-ttu-id="4bda0-255">`Content-Type`在 `MultipartFormDataContent` 提供 **主體** 的物件時，將會覆寫內容相關的標頭（例如）。</span><span class="sxs-lookup"><span data-stu-id="4bda0-255">Content related headers, such as `Content-Type` will be overridden when a `MultipartFormDataContent` object is supplied for **Body** .</span></span>

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

### <span data-ttu-id="4bda0-256">-InFile</span><span class="sxs-lookup"><span data-stu-id="4bda0-256">-InFile</span></span>

<span data-ttu-id="4bda0-257">從檔案取得 Web 要求的內容。</span><span class="sxs-lookup"><span data-stu-id="4bda0-257">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="4bda0-258">輸入路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="4bda0-258">Enter a path and file name.</span></span> <span data-ttu-id="4bda0-259">若省略路徑，則預設為目前位置。</span><span class="sxs-lookup"><span data-stu-id="4bda0-259">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="4bda0-260">-MaximumFollowRelLink</span><span class="sxs-lookup"><span data-stu-id="4bda0-260">-MaximumFollowRelLink</span></span>

<span data-ttu-id="4bda0-261">指定使用 **FollowRelLink** 時，要遵循關聯連結的次數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-261">Specifies how many times to follow relation links if **FollowRelLink** is used.</span></span> <span data-ttu-id="4bda0-262">如果 REST api 因為太多要求而進行節流，則可能需要較小的值。</span><span class="sxs-lookup"><span data-stu-id="4bda0-262">A smaller value may be needed if the REST api throttles due to too many requests.</span></span> <span data-ttu-id="4bda0-263">預設值是 `[Int32]::MaxValue`。</span><span class="sxs-lookup"><span data-stu-id="4bda0-263">The default value is `[Int32]::MaxValue`.</span></span> <span data-ttu-id="4bda0-264">值為 0 (零) 可防止下列關聯連結。</span><span class="sxs-lookup"><span data-stu-id="4bda0-264">A value of 0 (zero) prevents following relation links.</span></span>

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

### <span data-ttu-id="4bda0-265">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="4bda0-265">-MaximumRedirection</span></span>

<span data-ttu-id="4bda0-266">指定在連接失敗之前，PowerShell 將連接重新導向至替代統一資源識別項 (URI) 的次數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-266">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="4bda0-267">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="4bda0-267">The default value is 5.</span></span> <span data-ttu-id="4bda0-268">值為 0 (零) 將禁止所有重新導向。</span><span class="sxs-lookup"><span data-stu-id="4bda0-268">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="4bda0-269">-MaximumRetryCount</span><span class="sxs-lookup"><span data-stu-id="4bda0-269">-MaximumRetryCount</span></span>

<span data-ttu-id="4bda0-270">指定當收到400到599（含）或304之間的失敗代碼時，PowerShell 重試連接的次數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-270">Specifies how many times PowerShell retries a connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="4bda0-271">另請參閱 **RetryIntervalSec** 參數，以指定重試次數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-271">Also see **RetryIntervalSec** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="4bda0-272">-Method</span><span class="sxs-lookup"><span data-stu-id="4bda0-272">-Method</span></span>

<span data-ttu-id="4bda0-273">指定用於 Web 要求的方法。</span><span class="sxs-lookup"><span data-stu-id="4bda0-273">Specifies the method used for the web request.</span></span> <span data-ttu-id="4bda0-274">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="4bda0-274">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4bda0-275">預設</span><span class="sxs-lookup"><span data-stu-id="4bda0-275">Default</span></span>
- <span data-ttu-id="4bda0-276">刪除</span><span class="sxs-lookup"><span data-stu-id="4bda0-276">Delete</span></span>
- <span data-ttu-id="4bda0-277">Get</span><span class="sxs-lookup"><span data-stu-id="4bda0-277">Get</span></span>
- <span data-ttu-id="4bda0-278">Head</span><span class="sxs-lookup"><span data-stu-id="4bda0-278">Head</span></span>
- <span data-ttu-id="4bda0-279">合併</span><span class="sxs-lookup"><span data-stu-id="4bda0-279">Merge</span></span>
- <span data-ttu-id="4bda0-280">選項</span><span class="sxs-lookup"><span data-stu-id="4bda0-280">Options</span></span>
- <span data-ttu-id="4bda0-281">Patch</span><span class="sxs-lookup"><span data-stu-id="4bda0-281">Patch</span></span>
- <span data-ttu-id="4bda0-282">郵寄</span><span class="sxs-lookup"><span data-stu-id="4bda0-282">Post</span></span>
- <span data-ttu-id="4bda0-283">Put</span><span class="sxs-lookup"><span data-stu-id="4bda0-283">Put</span></span>
- <span data-ttu-id="4bda0-284">追蹤</span><span class="sxs-lookup"><span data-stu-id="4bda0-284">Trace</span></span>

<span data-ttu-id="4bda0-285">**CustomMethod** 參數可以用於上面未列出的要求方法。</span><span class="sxs-lookup"><span data-stu-id="4bda0-285">The **CustomMethod** parameter can be used for Request Methods not listed above.</span></span>

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

### <span data-ttu-id="4bda0-286">-NoProxy</span><span class="sxs-lookup"><span data-stu-id="4bda0-286">-NoProxy</span></span>

<span data-ttu-id="4bda0-287">指出此 Cmdlet 將不會使用 proxy 來連線至目的地。</span><span class="sxs-lookup"><span data-stu-id="4bda0-287">Indicates that the cmdlet will not use a proxy to reach the destination.</span></span>

<span data-ttu-id="4bda0-288">當您需要略過 Internet Explorer 中設定的 proxy 或環境中指定的 proxy 時，請使用此參數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-288">When you need to bypass the proxy configured in Internet Explorer, or a proxy specified in the environment, use this switch.</span></span>

<span data-ttu-id="4bda0-289">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="4bda0-289">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="4bda0-290">-OutFile</span><span class="sxs-lookup"><span data-stu-id="4bda0-290">-OutFile</span></span>

<span data-ttu-id="4bda0-291">將回應主體儲存在指定的輸出檔中。</span><span class="sxs-lookup"><span data-stu-id="4bda0-291">Saves the response body in the specified output file.</span></span> <span data-ttu-id="4bda0-292">輸入路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="4bda0-292">Enter a path and file name.</span></span> <span data-ttu-id="4bda0-293">若省略路徑，則預設為目前位置。</span><span class="sxs-lookup"><span data-stu-id="4bda0-293">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="4bda0-294">依預設，會將 `Invoke-RestMethod` 結果傳回至管線。</span><span class="sxs-lookup"><span data-stu-id="4bda0-294">By default, `Invoke-RestMethod` returns the results to the pipeline.</span></span> <span data-ttu-id="4bda0-295">若要傳送結果至檔案與管線，請使用 **Passthru** 參數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-295">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="4bda0-296">-PassThru</span><span class="sxs-lookup"><span data-stu-id="4bda0-296">-PassThru</span></span>

<span data-ttu-id="4bda0-297">除了將結果寫入檔案，也會傳回結果。</span><span class="sxs-lookup"><span data-stu-id="4bda0-297">Returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="4bda0-298">只有當命令中也使用 **OutFile** 參數時，此參數才會有效。</span><span class="sxs-lookup"><span data-stu-id="4bda0-298">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="4bda0-299">-PreserveAuthorizationOnRedirect</span><span class="sxs-lookup"><span data-stu-id="4bda0-299">-PreserveAuthorizationOnRedirect</span></span>

<span data-ttu-id="4bda0-300">指出 Cmdlet 應該在重新導向 `Authorization` 之間保留標頭（若有的話）。</span><span class="sxs-lookup"><span data-stu-id="4bda0-300">Indicates the cmdlet should preserve the `Authorization` header, when present, across redirections.</span></span>

<span data-ttu-id="4bda0-301">根據預設，此 Cmdlet 會在重新導向 `Authorization` 之前先移除標頭。</span><span class="sxs-lookup"><span data-stu-id="4bda0-301">By default, the cmdlet strips the `Authorization` header before redirecting.</span></span> <span data-ttu-id="4bda0-302">指定此參數會在標頭必須傳送至重新導向位置的情況下，停用此邏輯。</span><span class="sxs-lookup"><span data-stu-id="4bda0-302">Specifying this parameter disables this logic for cases where the header needs to be sent to the redirection location.</span></span>

<span data-ttu-id="4bda0-303">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="4bda0-303">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="4bda0-304">-Proxy</span><span class="sxs-lookup"><span data-stu-id="4bda0-304">-Proxy</span></span>

<span data-ttu-id="4bda0-305">針對要求使用 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="4bda0-305">Uses a proxy server for the request, rather than connecting directly to the internet resource.</span></span> <span data-ttu-id="4bda0-306">輸入網路 proxy 伺服器 (URI) 的統一資源識別項。</span><span class="sxs-lookup"><span data-stu-id="4bda0-306">Enter the Uniform Resource Identifier (URI) of a network proxy server.</span></span>

<span data-ttu-id="4bda0-307">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="4bda0-307">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="4bda0-308">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="4bda0-308">-ProxyCredential</span></span>

<span data-ttu-id="4bda0-309">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="4bda0-309">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="4bda0-310">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="4bda0-310">The default is the current user.</span></span>

<span data-ttu-id="4bda0-311">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ）， **User@Domain.Com** 或輸入一個 `PSCredential` 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-311">Type a user name, such as **User01** or **Domain01\User01** , **User@Domain.Com** , or enter a `PSCredential` object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="4bda0-312">只有當命令中也使用 **Proxy** 參數時，此參數才會有效。</span><span class="sxs-lookup"><span data-stu-id="4bda0-312">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="4bda0-313">您無法在同一個命令中使用 **ProxyCredential** 和 **ProxyUseDefaultCredentials** 參數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-313">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="4bda0-314">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="4bda0-314">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="4bda0-315">指出此 Cmdlet 會使用目前使用者的認證來存取 **proxy** 參數所指定的 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="4bda0-315">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="4bda0-316">只有當命令中也使用 **Proxy** 參數時，此參數才會有效。</span><span class="sxs-lookup"><span data-stu-id="4bda0-316">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="4bda0-317">您無法在同一個命令中使用 **ProxyCredential** 和 **ProxyUseDefaultCredentials** 參數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-317">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="4bda0-318">-ResponseHeadersVariable</span><span class="sxs-lookup"><span data-stu-id="4bda0-318">-ResponseHeadersVariable</span></span>

<span data-ttu-id="4bda0-319">建立回應標頭字典，並將它儲存在指定變數的值中。</span><span class="sxs-lookup"><span data-stu-id="4bda0-319">Creates a Response Headers Dictionary and saves it in the value of the specified variable.</span></span> <span data-ttu-id="4bda0-320">字典的索引鍵會包含 web 伺服器所傳回之回應標頭的功能變數名稱，而這些值會是各自的域值。</span><span class="sxs-lookup"><span data-stu-id="4bda0-320">The keys of the dictionary will contain the field names of the Response Header returned by the web server and the values will be the respective field values.</span></span>

<span data-ttu-id="4bda0-321">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="4bda0-321">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="4bda0-322">-Resume</span><span class="sxs-lookup"><span data-stu-id="4bda0-322">-Resume</span></span>

<span data-ttu-id="4bda0-323">盡力嘗試繼續下載部分檔案。</span><span class="sxs-lookup"><span data-stu-id="4bda0-323">Performs a best effort attempt to resume downloading a partial file.</span></span> <span data-ttu-id="4bda0-324">**Resume** 參數需要 **OutFile** 參數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-324">The **Resume** parameter requires the **OutFile** parameter.</span></span>

<span data-ttu-id="4bda0-325">**Resume** 只會在本機檔案和遠端檔案的大小上運作，而且不會執行本機檔案和遠端檔案相同的其他驗證。</span><span class="sxs-lookup"><span data-stu-id="4bda0-325">**Resume** only operates on the size of the local file and remote file and performs no other validation that the local file and the remote file are the same.</span></span>

<span data-ttu-id="4bda0-326">如果本機檔案大小小於遠端檔案大小，則 Cmdlet 會嘗試繼續下載檔案，並將剩餘的位元組附加至檔案結尾。</span><span class="sxs-lookup"><span data-stu-id="4bda0-326">If the local file size is smaller than the remote file size, then the cmdlet will attempt to resume downloading the file and append the remaining bytes to the end of the file.</span></span>

<span data-ttu-id="4bda0-327">如果本機檔案大小與遠端檔案大小相同，則不會採取任何動作，而且 Cmdlet 會假設下載已完成。</span><span class="sxs-lookup"><span data-stu-id="4bda0-327">If the local file size is the same as the remote file size, then no action is taken and the cmdlet assumes the download already completed.</span></span>

<span data-ttu-id="4bda0-328">如果本機檔案大小大於遠端檔案大小，則會覆寫本機檔案，而且整個遠端檔案將會完全重新下載。</span><span class="sxs-lookup"><span data-stu-id="4bda0-328">If the local file size is larger than the remote file size, then the local file will be overwritten and the entire remote file will be completely re-downloaded.</span></span> <span data-ttu-id="4bda0-329">這種行為與使用 **OutFile** 而不需要 **Resume** 的行為相同。</span><span class="sxs-lookup"><span data-stu-id="4bda0-329">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="4bda0-330">如果遠端伺服器不支援下載繼續，則會覆寫本機檔案，而且整個遠端檔案將會完全重新下載。</span><span class="sxs-lookup"><span data-stu-id="4bda0-330">If the remote server does not support download resuming, then the local file will be overwritten and the entire remote file will be completely re-downloaded.</span></span> <span data-ttu-id="4bda0-331">這種行為與使用 **OutFile** 而不需要 **Resume** 的行為相同。</span><span class="sxs-lookup"><span data-stu-id="4bda0-331">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="4bda0-332">如果本機檔案不存在，則會建立本機檔案，而且整個遠端檔案將會完整下載。</span><span class="sxs-lookup"><span data-stu-id="4bda0-332">If the local file doesn't exist, then the local file will be created and the entire remote file will be completely downloaded.</span></span> <span data-ttu-id="4bda0-333">這種行為與使用 **OutFile** 而不需要 **Resume** 的行為相同。</span><span class="sxs-lookup"><span data-stu-id="4bda0-333">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="4bda0-334">這項功能已在 PowerShell 6.1.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="4bda0-334">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="4bda0-335">-RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="4bda0-335">-RetryIntervalSec</span></span>

<span data-ttu-id="4bda0-336">指定當收到400和599（含或304）之間的失敗代碼時，連接重試之間的間隔。</span><span class="sxs-lookup"><span data-stu-id="4bda0-336">Specifies the interval between retries for the connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="4bda0-337">另請參閱 **MaximumRetryCount** 參數，以指定重試次數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-337">Also see **MaximumRetryCount** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="4bda0-338">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="4bda0-338">-SessionVariable</span></span>

<span data-ttu-id="4bda0-339">指定此 Cmdlet 會建立 web 要求會話，並將其儲存在值中的變數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-339">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="4bda0-340">輸入不含貨幣符號 () 符號的變數名稱 `$` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-340">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="4bda0-341">當您指定會話變數時，會 `Invoke-RestMethod` 建立 web 要求會話物件，並將它指派給您的 PowerShell 會話中具有指定名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-341">When you specify a session variable, `Invoke-RestMethod` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="4bda0-342">一旦命令完成，便可在工作階段中使用變數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-342">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="4bda0-343">不同于遠端會話，web 要求會話不是持續性連接。</span><span class="sxs-lookup"><span data-stu-id="4bda0-343">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="4bda0-344">它是一個物件，其中包含連線和要求的相關資訊，包括 cookie、認證、最大重新導向值，以及使用者代理字串。</span><span class="sxs-lookup"><span data-stu-id="4bda0-344">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="4bda0-345">您可以使用它在 Web 要求之間共用狀態與資料。</span><span class="sxs-lookup"><span data-stu-id="4bda0-345">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="4bda0-346">若要在後續 Web 要求中使用 Web 要求工作階段，請在 **WebSession** 參數值指定工作階段變數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-346">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="4bda0-347">建立新連接時，PowerShell 會使用 web 要求會話物件中的資料。</span><span class="sxs-lookup"><span data-stu-id="4bda0-347">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="4bda0-348">若要覆寫 Web 要求工作階段中的值，請使用 Cmdlet 參數，例如 **UserAgent** 或 **Credential** 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-348">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="4bda0-349">參數值的優先順序高於 Web 要求工作階段中的值。</span><span class="sxs-lookup"><span data-stu-id="4bda0-349">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="4bda0-350">您無法在同一個命令中使用 **SessionVariable** 和 **WebSession** 參數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-350">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="4bda0-351">-SkipCertificateCheck</span><span class="sxs-lookup"><span data-stu-id="4bda0-351">-SkipCertificateCheck</span></span>

<span data-ttu-id="4bda0-352">略過包含所有驗證的憑證驗證檢查，例如到期、撤銷、受信任的根授權單位等等。</span><span class="sxs-lookup"><span data-stu-id="4bda0-352">Skips certificate validation checks that include all validations such as expiration, revocation, trusted root authority, etc.</span></span>

> [!WARNING]
> <span data-ttu-id="4bda0-353">使用這個參數並不安全，因此不建議使用。</span><span class="sxs-lookup"><span data-stu-id="4bda0-353">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="4bda0-354">此參數僅適用于使用自我簽署憑證的已知主機，以供測試之用。</span><span class="sxs-lookup"><span data-stu-id="4bda0-354">This switch is only intended to be used against known hosts using a self-signed certificate for testing purposes.</span></span> <span data-ttu-id="4bda0-355">使用您自己的風險。</span><span class="sxs-lookup"><span data-stu-id="4bda0-355">Use at your own risk.</span></span>

<span data-ttu-id="4bda0-356">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="4bda0-356">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="4bda0-357">-SkipHeaderValidation</span><span class="sxs-lookup"><span data-stu-id="4bda0-357">-SkipHeaderValidation</span></span>

<span data-ttu-id="4bda0-358">指出 Cmdlet 應該在沒有驗證的情況下，將標頭新增至要求。</span><span class="sxs-lookup"><span data-stu-id="4bda0-358">Indicates the cmdlet should add headers to the request without validation.</span></span>

<span data-ttu-id="4bda0-359">此參數應用於需要不符合標準之標頭值的網站。</span><span class="sxs-lookup"><span data-stu-id="4bda0-359">This switch should be used for sites that require header values that do not conform to standards.</span></span>
<span data-ttu-id="4bda0-360">指定此參數會停用驗證，以允許未核取值的傳遞。</span><span class="sxs-lookup"><span data-stu-id="4bda0-360">Specifying this switch disables validation to allow the value to be passed unchecked.</span></span> <span data-ttu-id="4bda0-361">若有指定，則會新增所有標頭，而不進行驗證。</span><span class="sxs-lookup"><span data-stu-id="4bda0-361">When specified, all headers are added without validation.</span></span>

<span data-ttu-id="4bda0-362">這會針對傳遞給 **ContentType** 、 **標頭** 和 **UserAgent** 參數的值停用驗證。</span><span class="sxs-lookup"><span data-stu-id="4bda0-362">This will disable validation for values passed to the **ContentType** , **Headers** , and **UserAgent** parameters.</span></span>

<span data-ttu-id="4bda0-363">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="4bda0-363">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="4bda0-364">-SkipHttpErrorCheck</span><span class="sxs-lookup"><span data-stu-id="4bda0-364">-SkipHttpErrorCheck</span></span>

<span data-ttu-id="4bda0-365">此參數會讓 Cmdlet 忽略 HTTP 錯誤狀態，並繼續處理回應。</span><span class="sxs-lookup"><span data-stu-id="4bda0-365">This parameter causes the cmdlet to ignore HTTP error statuses and continue to process responses.</span></span>
<span data-ttu-id="4bda0-366">錯誤回應會寫入管線中，就如同成功一樣。</span><span class="sxs-lookup"><span data-stu-id="4bda0-366">The error responses are written to the pipeline just as if they were successful.</span></span>

<span data-ttu-id="4bda0-367">此參數是在 PowerShell 7 中引進。</span><span class="sxs-lookup"><span data-stu-id="4bda0-367">This parameter was introduced in PowerShell 7.</span></span>

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

### <span data-ttu-id="4bda0-368">-SslProtocol</span><span class="sxs-lookup"><span data-stu-id="4bda0-368">-SslProtocol</span></span>

<span data-ttu-id="4bda0-369">設定 web 要求所允許的 SSL/TLS 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="4bda0-369">Sets the SSL/TLS protocols that are permissible for the web request.</span></span> <span data-ttu-id="4bda0-370">預設會允許系統支援的 SSL/TLS 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="4bda0-370">By default all, SSL/TLS protocols supported by the system are allowed.</span></span> <span data-ttu-id="4bda0-371">**SslProtocol** 可基於合規性目的限制特定的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="4bda0-371">**SslProtocol** allows for limiting to specific protocols for compliance purposes.</span></span>

<span data-ttu-id="4bda0-372">**SslProtocol** 使用 `WebSslProtocol` 旗標列舉。</span><span class="sxs-lookup"><span data-stu-id="4bda0-372">**SslProtocol** uses the `WebSslProtocol` Flag Enum.</span></span> <span data-ttu-id="4bda0-373">您可以使用旗標標記法或結合多個選項來提供多個通訊協定 `WebSslProtocol` `-bor` ，但在所有平臺上都不支援提供多個通訊協定。</span><span class="sxs-lookup"><span data-stu-id="4bda0-373">It is possible to supply more than one protocol using flag notation or combining multiple `WebSslProtocol` options with `-bor`, however supplying multiple protocols is not supported on all platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="4bda0-374">在非 Windows 平臺上，可能無法提供 `'Tls, Tls12'` 作為選項。</span><span class="sxs-lookup"><span data-stu-id="4bda0-374">On non-Windows platforms it may not be possible to supply `'Tls, Tls12'` as an option.</span></span>

<span data-ttu-id="4bda0-375">這項功能已在 PowerShell 6.0.0 中新增。</span><span class="sxs-lookup"><span data-stu-id="4bda0-375">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="4bda0-376">-StatusCodeVariable</span><span class="sxs-lookup"><span data-stu-id="4bda0-376">-StatusCodeVariable</span></span>

<span data-ttu-id="4bda0-377">此參數會指定已指派狀態碼整數值的變數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-377">This parameter specifies a variable that's assigned a status code's integer value.</span></span> <span data-ttu-id="4bda0-378">參數可以在與 **SkipHttpErrorCheck** 參數搭配使用時，識別成功訊息或失敗訊息。</span><span class="sxs-lookup"><span data-stu-id="4bda0-378">The parameter can identify success messages or failure messages when used with the **SkipHttpErrorCheck** parameter.</span></span>

<span data-ttu-id="4bda0-379">以字串形式輸入參數的變數名稱，例如 `-StatusCodeVariable "scv"` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-379">Input the parameter's variable name as a string such as `-StatusCodeVariable "scv"`.</span></span>

<span data-ttu-id="4bda0-380">此參數是在 PowerShell 7 中引進。</span><span class="sxs-lookup"><span data-stu-id="4bda0-380">This parameter was introduced in PowerShell 7.</span></span>

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

### <span data-ttu-id="4bda0-381">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="4bda0-381">-TimeoutSec</span></span>

<span data-ttu-id="4bda0-382">指定要求可在一段時間之前暫止的時間長度。輸入以秒為單位的值。</span><span class="sxs-lookup"><span data-stu-id="4bda0-382">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="4bda0-383">預設值為 0，會指定無限逾時。</span><span class="sxs-lookup"><span data-stu-id="4bda0-383">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="4bda0-384">網域名稱系統 (DNS) 查詢最多可能需要15秒的時間才會傳回或超時。如果您的要求包含需要解析的主機名稱，而且您將 **TimeoutSec** 設定為大於零的值，但不超過15秒，則在擲回 WebException 之前，可能需要15秒或更長的時間，而且您的要求超時。</span><span class="sxs-lookup"><span data-stu-id="4bda0-384">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="4bda0-385">-Token</span><span class="sxs-lookup"><span data-stu-id="4bda0-385">-Token</span></span>

<span data-ttu-id="4bda0-386">要包含在要求中的 OAuth 或持有人權杖。</span><span class="sxs-lookup"><span data-stu-id="4bda0-386">The OAuth or Bearer token to include in the request.</span></span> <span data-ttu-id="4bda0-387">某些 **驗證** 選項需要 **權杖** 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-387">**Token** is required by certain **Authentication** options.</span></span> <span data-ttu-id="4bda0-388">無法獨立使用。</span><span class="sxs-lookup"><span data-stu-id="4bda0-388">It can't be used independently.</span></span>

<span data-ttu-id="4bda0-389">**權杖** 會採用 `SecureString` 包含權杖的。</span><span class="sxs-lookup"><span data-stu-id="4bda0-389">**Token** takes a `SecureString` that contains the token.</span></span> <span data-ttu-id="4bda0-390">若要提供權杖，請手動使用下列各項：</span><span class="sxs-lookup"><span data-stu-id="4bda0-390">To supply the token, manually use the following:</span></span>

`Invoke-RestMethod -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

<span data-ttu-id="4bda0-391">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="4bda0-391">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="4bda0-392">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="4bda0-392">-TransferEncoding</span></span>

<span data-ttu-id="4bda0-393">指定傳輸編碼 HTTP 回應標頭的值。</span><span class="sxs-lookup"><span data-stu-id="4bda0-393">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="4bda0-394">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="4bda0-394">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4bda0-395">區塊</span><span class="sxs-lookup"><span data-stu-id="4bda0-395">Chunked</span></span>
- <span data-ttu-id="4bda0-396">壓縮</span><span class="sxs-lookup"><span data-stu-id="4bda0-396">Compress</span></span>
- <span data-ttu-id="4bda0-397">上下凹陷</span><span class="sxs-lookup"><span data-stu-id="4bda0-397">Deflate</span></span>
- <span data-ttu-id="4bda0-398">GZip</span><span class="sxs-lookup"><span data-stu-id="4bda0-398">GZip</span></span>
- <span data-ttu-id="4bda0-399">身分識別</span><span class="sxs-lookup"><span data-stu-id="4bda0-399">Identity</span></span>

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

### <span data-ttu-id="4bda0-400">-Uri</span><span class="sxs-lookup"><span data-stu-id="4bda0-400">-Uri</span></span>

<span data-ttu-id="4bda0-401">指定傳送 web 要求的網際網路資源 (URI) 的統一資源識別項。</span><span class="sxs-lookup"><span data-stu-id="4bda0-401">Specifies the Uniform Resource Identifier (URI) of the internet resource to which the web request is sent.</span></span> <span data-ttu-id="4bda0-402">此參數支援 HTTP、HTTPS、FTP 與 FILE 值。</span><span class="sxs-lookup"><span data-stu-id="4bda0-402">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="4bda0-403">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-403">This parameter is required.</span></span> <span data-ttu-id="4bda0-404"> ( **Uri** ) 的參數名稱是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="4bda0-404">The parameter name ( **Uri** ) is optional.</span></span>

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

### <span data-ttu-id="4bda0-405">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="4bda0-405">-UseBasicParsing</span></span>

<span data-ttu-id="4bda0-406">此參數已被取代。</span><span class="sxs-lookup"><span data-stu-id="4bda0-406">This parameter has been deprecated.</span></span> <span data-ttu-id="4bda0-407">從 PowerShell 6.0.0 開始，所有 Web 要求都會使用基本剖析。</span><span class="sxs-lookup"><span data-stu-id="4bda0-407">Beginning with PowerShell 6.0.0, all Web requests use basic parsing only.</span></span> <span data-ttu-id="4bda0-408">此參數是為了回溯相容性而包含，而且任何使用它都不會影響 Cmdlet 的操作。</span><span class="sxs-lookup"><span data-stu-id="4bda0-408">This parameter is included for backwards compatibility only and any use of it will have no effect on the operation of the cmdlet.</span></span>

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

### <span data-ttu-id="4bda0-409">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="4bda0-409">-UseDefaultCredentials</span></span>

<span data-ttu-id="4bda0-410">指出此 Cmdlet 會使用目前使用者的認證來傳送 web 要求。</span><span class="sxs-lookup"><span data-stu-id="4bda0-410">Indicates that the cmdlet uses the credentials of the current user to send the web request.</span></span> <span data-ttu-id="4bda0-411">這不能與 **驗證\*\*\*\*或認證** 搭配使用，而且在所有平臺上都可能不受支援。</span><span class="sxs-lookup"><span data-stu-id="4bda0-411">This can't be used with **Authentication** or **Credential** and may not be supported on all platforms.</span></span>

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

### <span data-ttu-id="4bda0-412">-UserAgent</span><span class="sxs-lookup"><span data-stu-id="4bda0-412">-UserAgent</span></span>

<span data-ttu-id="4bda0-413">指定 Web 要求的使用者代理字串。</span><span class="sxs-lookup"><span data-stu-id="4bda0-413">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="4bda0-414">預設使用者代理程式類似于 `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` 每個作業系統和平臺的些許變化。</span><span class="sxs-lookup"><span data-stu-id="4bda0-414">The default user agent is similar to `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="4bda0-415">若要使用大部分網際網路瀏覽器所使用的標準使用者代理程式字串來測試網站，請使用 [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) 類別的屬性，例如 Chrome、FireFox、Microsoft-windows-ie-internetexplorer、Opera 和 Safari。</span><span class="sxs-lookup"><span data-stu-id="4bda0-415">To test a website with the standard user agent string that is used by most internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span>

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

### <span data-ttu-id="4bda0-416">-WebSession</span><span class="sxs-lookup"><span data-stu-id="4bda0-416">-WebSession</span></span>

<span data-ttu-id="4bda0-417">指定 Web 要求工作階段。</span><span class="sxs-lookup"><span data-stu-id="4bda0-417">Specifies a web request session.</span></span> <span data-ttu-id="4bda0-418">輸入變數名稱，包括貨幣符號 (`$`) 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-418">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="4bda0-419">若要覆寫 Web 要求工作階段中的值，請使用 Cmdlet 參數，例如 **UserAgent** 或 **Credential** 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-419">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="4bda0-420">參數值的優先順序高於 Web 要求工作階段中的值。</span><span class="sxs-lookup"><span data-stu-id="4bda0-420">Parameter values take precedence over values in the web request session.</span></span> <span data-ttu-id="4bda0-421">`Content-Type`當提供 **主體** 的 **>multipartformdatacontent** 物件時，也會覆寫內容相關的標頭（例如）。</span><span class="sxs-lookup"><span data-stu-id="4bda0-421">Content related headers, such as `Content-Type`, will be also be overridden when a **MultipartFormDataContent** object is supplied for **Body** .</span></span>

<span data-ttu-id="4bda0-422">不同于遠端會話，web 要求會話不是持續性連接。</span><span class="sxs-lookup"><span data-stu-id="4bda0-422">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="4bda0-423">它是一個物件，其中包含連線和要求的相關資訊，包括 cookie、認證、最大重新導向值，以及使用者代理字串。</span><span class="sxs-lookup"><span data-stu-id="4bda0-423">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="4bda0-424">您可以使用它在 Web 要求之間共用狀態與資料。</span><span class="sxs-lookup"><span data-stu-id="4bda0-424">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="4bda0-425">若要建立 web 要求會話，請在命令的 **SessionVariable** 參數值中輸入不含貨幣符號的變數名稱 `Invoke-RestMethod` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-425">To create a web request session, enter a variable name, without a dollar sign, in the value of the **SessionVariable** parameter of an `Invoke-RestMethod` command.</span></span> <span data-ttu-id="4bda0-426">`Invoke-RestMethod` 建立會話，並將它儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="4bda0-426">`Invoke-RestMethod` creates the session and saves it in the variable.</span></span> <span data-ttu-id="4bda0-427">在後續命令中，使用變數作為 **WebSession** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="4bda0-427">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="4bda0-428">您無法在同一個命令中使用 **SessionVariable** 和 **WebSession** 參數。</span><span class="sxs-lookup"><span data-stu-id="4bda0-428">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="4bda0-429">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4bda0-429">CommonParameters</span></span>

<span data-ttu-id="4bda0-430">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4bda0-430">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4bda0-431">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4bda0-431">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4bda0-432">輸入</span><span class="sxs-lookup"><span data-stu-id="4bda0-432">INPUTS</span></span>

### <span data-ttu-id="4bda0-433">System.Object</span><span class="sxs-lookup"><span data-stu-id="4bda0-433">System.Object</span></span>

<span data-ttu-id="4bda0-434">您可以使用管線將 web 要求的主體傳送至 `Invoke-RestMethod` 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-434">You can pipe the body of a web request to `Invoke-RestMethod`.</span></span>

## <span data-ttu-id="4bda0-435">輸出</span><span class="sxs-lookup"><span data-stu-id="4bda0-435">OUTPUTS</span></span>

### <span data-ttu-id="4bda0-436">系統 Int64、System.string、System.Xml.Xml檔</span><span class="sxs-lookup"><span data-stu-id="4bda0-436">System.Int64, System.String, System.Xml.XmlDocument</span></span>

<span data-ttu-id="4bda0-437">Cmdlet 的輸出取決於抓取內容的格式。</span><span class="sxs-lookup"><span data-stu-id="4bda0-437">The output of the cmdlet depends upon the format of the content that is retrieved.</span></span>

### <span data-ttu-id="4bda0-438">PSObject</span><span class="sxs-lookup"><span data-stu-id="4bda0-438">PSObject</span></span>

<span data-ttu-id="4bda0-439">如果要求傳回 JSON 字串，則 `Invoke-RestMethod` 會傳回代表字串的 **PSObject** 。</span><span class="sxs-lookup"><span data-stu-id="4bda0-439">If the request returns JSON strings, `Invoke-RestMethod` returns a **PSObject** that represents the strings.</span></span>

## <span data-ttu-id="4bda0-440">注意</span><span class="sxs-lookup"><span data-stu-id="4bda0-440">NOTES</span></span>

<span data-ttu-id="4bda0-441">某些功能可能無法在所有平臺上使用。</span><span class="sxs-lookup"><span data-stu-id="4bda0-441">Some features may not be available on all platforms.</span></span>

<span data-ttu-id="4bda0-442">由於 .NET Core 3.1 的變更，PowerShell 7.0 和更新版本會使用 [HttpClient. DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) 屬性來判斷 proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="4bda0-442">Because of changes in .NET Core 3.1, PowerShell 7.0 and higher use the [HttpClient.DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) property to determine the proxy configuration.</span></span>

<span data-ttu-id="4bda0-443">這個屬性的值取決於您的平臺：</span><span class="sxs-lookup"><span data-stu-id="4bda0-443">The value of this property is determined by your platform:</span></span>

- <span data-ttu-id="4bda0-444">若 **為 Windows** ：從環境變數讀取 proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="4bda0-444">**For Windows** : Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="4bda0-445">如果未定義這些變數，則屬性會衍生自使用者的 proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="4bda0-445">If those variables are not defined the property is derived from the user's proxy settings.</span></span>
- <span data-ttu-id="4bda0-446">若 **為 macOS** ：從環境變數讀取 proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="4bda0-446">**For macOS** : Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="4bda0-447">如果未定義這些變數，則屬性會衍生自系統的 proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="4bda0-447">If those variables are not defined the property is derived from the system's proxy settings.</span></span>
- <span data-ttu-id="4bda0-448">若 **為 Linux** ：從環境變數讀取 proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="4bda0-448">**For Linux** : Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="4bda0-449">如果未定義這些變數，屬性會初始化一個未設定的實例，以略過所有位址。</span><span class="sxs-lookup"><span data-stu-id="4bda0-449">If those variables are not defined the property initializes a non-configured instance that bypasses all addresses.</span></span>

<span data-ttu-id="4bda0-450">`DefaultProxy`在 Windows 和 Unix 平臺上用於初始化的環境變數如下：</span><span class="sxs-lookup"><span data-stu-id="4bda0-450">The environment variables used for `DefaultProxy` initialization on Windows and Unix-based platforms are:</span></span>

- <span data-ttu-id="4bda0-451">` HTTP_PROXY`：用於 HTTP 要求之 proxy 伺服器的主機名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="4bda0-451">` HTTP_PROXY`: the hostname or IP address of the proxy server used on HTTP requests.</span></span>
- <span data-ttu-id="4bda0-452">`HTTPS_PROXY`：用於 HTTPS 要求的 proxy 伺服器的主機名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="4bda0-452">`HTTPS_PROXY`: the hostname or IP address of the proxy server used on HTTPS requests.</span></span>
- <span data-ttu-id="4bda0-453">`ALL_PROXY`：用於 HTTP 和 HTTPS 要求的 proxy 伺服器的主機名稱或 IP 位址（若 `HTTP_PROXY` `HTTPS_PROXY` 未定義的話）。</span><span class="sxs-lookup"><span data-stu-id="4bda0-453">`ALL_PROXY`: the hostname or IP address of the proxy server used on HTTP and HTTPS requests in case `HTTP_PROXY` or `HTTPS_PROXY` are not defined.</span></span>
- <span data-ttu-id="4bda0-454">`NO_PROXY`：應從 proxy 排除的主機名稱（以逗號分隔）清單。</span><span class="sxs-lookup"><span data-stu-id="4bda0-454">`NO_PROXY`: a comma-separated list of hostnames that should be excluded from proxying.</span></span>

## <span data-ttu-id="4bda0-455">相關連結</span><span class="sxs-lookup"><span data-stu-id="4bda0-455">RELATED LINKS</span></span>

[<span data-ttu-id="4bda0-456">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="4bda0-456">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="4bda0-457">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="4bda0-457">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="4bda0-458">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="4bda0-458">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)
