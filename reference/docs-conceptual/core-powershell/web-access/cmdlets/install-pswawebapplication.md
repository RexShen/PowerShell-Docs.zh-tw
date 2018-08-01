---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 29e074b75eeb387640831229c63142e6dd5e991a
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268294"
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="62638-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="62638-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="62638-104">概要</span><span class="sxs-lookup"><span data-stu-id="62638-104">SYNOPSIS</span></span>

<span data-ttu-id="62638-105">在 IIS 中設定 Windows PowerShell Web 存取 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="62638-105">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="62638-106">語法</span><span class="sxs-lookup"><span data-stu-id="62638-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="62638-107">Default</span><span class="sxs-lookup"><span data-stu-id="62638-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="62638-108">描述</span><span class="sxs-lookup"><span data-stu-id="62638-108">DESCRIPTION</span></span>

<span data-ttu-id="62638-109">**Install-PswaWebApplication** Cmdlet 會設定 Windows PowerShell Web 存取 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="62638-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span>
<span data-ttu-id="62638-110">此 Cmdlet 會安裝 Web 應用程式、將它與網站建立關聯，並選擇性地使用 **useTestCertificate** 參數建立測試 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="62638-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="62638-111">為了安全起見，網站管理員不應該將測試憑證用於生產環境。</span><span class="sxs-lookup"><span data-stu-id="62638-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="62638-112">參數</span><span class="sxs-lookup"><span data-stu-id="62638-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="62638-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="62638-113">-UseTestCertificate</span></span>

<span data-ttu-id="62638-114">指定建立測試憑證。</span><span class="sxs-lookup"><span data-stu-id="62638-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="62638-115">如果這個參數設定為 true，則此 Cmdlet 會建立測試憑證，並設定 Windows PowerShell Web 存取 Web 應用程式針對 HTTPS 要求使用憑證。</span><span class="sxs-lookup"><span data-stu-id="62638-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="62638-116">如果這個參數設定為 false，則不會建立憑證或繫結。</span><span class="sxs-lookup"><span data-stu-id="62638-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="62638-117">如果使用其他憑證進行 Windows PowerShell Web 存取，請將此值設定為 false。</span><span class="sxs-lookup"><span data-stu-id="62638-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||
|-|-|
| <span data-ttu-id="62638-118">別名</span><span class="sxs-lookup"><span data-stu-id="62638-118">Aliases</span></span>                              | <span data-ttu-id="62638-119">無</span><span class="sxs-lookup"><span data-stu-id="62638-119">none</span></span>                                 |
| <span data-ttu-id="62638-120">必要？</span><span class="sxs-lookup"><span data-stu-id="62638-120">Required?</span></span>                            | <span data-ttu-id="62638-121">false</span><span class="sxs-lookup"><span data-stu-id="62638-121">false</span></span>                                |
| <span data-ttu-id="62638-122">位置？</span><span class="sxs-lookup"><span data-stu-id="62638-122">Position?</span></span>                            | <span data-ttu-id="62638-123">具名</span><span class="sxs-lookup"><span data-stu-id="62638-123">named</span></span>                                |
| <span data-ttu-id="62638-124">預設值</span><span class="sxs-lookup"><span data-stu-id="62638-124">Default Value</span></span>                        | <span data-ttu-id="62638-125">true</span><span class="sxs-lookup"><span data-stu-id="62638-125">true</span></span>                                 |
| <span data-ttu-id="62638-126">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="62638-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="62638-127">false</span><span class="sxs-lookup"><span data-stu-id="62638-127">false</span></span>                                |
| <span data-ttu-id="62638-128">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="62638-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="62638-129">false</span><span class="sxs-lookup"><span data-stu-id="62638-129">false</span></span>                                |

### <a name="-webapplicationname"></a><span data-ttu-id="62638-130">-WebApplicationName</span><span class="sxs-lookup"><span data-stu-id="62638-130">-WebApplicationName</span></span>

<span data-ttu-id="62638-131">指定 Web 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="62638-131">Specifies the name for your web application.</span></span> <span data-ttu-id="62638-132">這會顯示為 Windows PowerShell Web 存取 URL 的最後一部分。</span><span class="sxs-lookup"><span data-stu-id="62638-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||
|-|-|
| <span data-ttu-id="62638-133">別名</span><span class="sxs-lookup"><span data-stu-id="62638-133">Aliases</span></span>                              | <span data-ttu-id="62638-134">無</span><span class="sxs-lookup"><span data-stu-id="62638-134">none</span></span>                                 |
| <span data-ttu-id="62638-135">必要？</span><span class="sxs-lookup"><span data-stu-id="62638-135">Required?</span></span>                            | <span data-ttu-id="62638-136">false</span><span class="sxs-lookup"><span data-stu-id="62638-136">false</span></span>                                |
| <span data-ttu-id="62638-137">位置？</span><span class="sxs-lookup"><span data-stu-id="62638-137">Position?</span></span>                            | <span data-ttu-id="62638-138">1</span><span class="sxs-lookup"><span data-stu-id="62638-138">1</span></span>                                    |
| <span data-ttu-id="62638-139">預設值</span><span class="sxs-lookup"><span data-stu-id="62638-139">Default Value</span></span>                        | <span data-ttu-id="62638-140">pswa</span><span class="sxs-lookup"><span data-stu-id="62638-140">pswa</span></span>                                 |
| <span data-ttu-id="62638-141">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="62638-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="62638-142">false</span><span class="sxs-lookup"><span data-stu-id="62638-142">false</span></span>                                |
| <span data-ttu-id="62638-143">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="62638-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="62638-144">false</span><span class="sxs-lookup"><span data-stu-id="62638-144">false</span></span>                                |

### <a name="-websitename"></a><span data-ttu-id="62638-145">-WebSiteName</span><span class="sxs-lookup"><span data-stu-id="62638-145">-WebSiteName</span></span>

<span data-ttu-id="62638-146">指定要安裝此 Windows PowerShell Web 存取 Web 應用程式之網頁伺服器 (IIS) 網站的名稱。</span><span class="sxs-lookup"><span data-stu-id="62638-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||
|-|-|
| <span data-ttu-id="62638-147">別名</span><span class="sxs-lookup"><span data-stu-id="62638-147">Aliases</span></span>                              | <span data-ttu-id="62638-148">無</span><span class="sxs-lookup"><span data-stu-id="62638-148">none</span></span>                                 |
| <span data-ttu-id="62638-149">必要？</span><span class="sxs-lookup"><span data-stu-id="62638-149">Required?</span></span>                            | <span data-ttu-id="62638-150">false</span><span class="sxs-lookup"><span data-stu-id="62638-150">false</span></span>                                |
| <span data-ttu-id="62638-151">位置？</span><span class="sxs-lookup"><span data-stu-id="62638-151">Position?</span></span>                            | <span data-ttu-id="62638-152">具名</span><span class="sxs-lookup"><span data-stu-id="62638-152">named</span></span>                                |
| <span data-ttu-id="62638-153">預設值</span><span class="sxs-lookup"><span data-stu-id="62638-153">Default Value</span></span>                        | <span data-ttu-id="62638-154">預設網站</span><span class="sxs-lookup"><span data-stu-id="62638-154">Default Web Site</span></span>                     |
| <span data-ttu-id="62638-155">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="62638-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="62638-156">false</span><span class="sxs-lookup"><span data-stu-id="62638-156">false</span></span>                                |
| <span data-ttu-id="62638-157">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="62638-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="62638-158">false</span><span class="sxs-lookup"><span data-stu-id="62638-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="62638-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="62638-159">-Confirm</span></span>

<span data-ttu-id="62638-160">執行 Cmdlet 之前先提示您確認。</span><span class="sxs-lookup"><span data-stu-id="62638-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="62638-161">必要？</span><span class="sxs-lookup"><span data-stu-id="62638-161">Required?</span></span>                            | <span data-ttu-id="62638-162">false</span><span class="sxs-lookup"><span data-stu-id="62638-162">false</span></span>                                |
| <span data-ttu-id="62638-163">位置？</span><span class="sxs-lookup"><span data-stu-id="62638-163">Position?</span></span>                            | <span data-ttu-id="62638-164">具名</span><span class="sxs-lookup"><span data-stu-id="62638-164">named</span></span>                                |
| <span data-ttu-id="62638-165">預設值</span><span class="sxs-lookup"><span data-stu-id="62638-165">Default Value</span></span>                        | <span data-ttu-id="62638-166">false</span><span class="sxs-lookup"><span data-stu-id="62638-166">false</span></span>                                |
| <span data-ttu-id="62638-167">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="62638-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="62638-168">false</span><span class="sxs-lookup"><span data-stu-id="62638-168">false</span></span>                                |
| <span data-ttu-id="62638-169">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="62638-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="62638-170">false</span><span class="sxs-lookup"><span data-stu-id="62638-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="62638-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="62638-171">-WhatIf</span></span>

<span data-ttu-id="62638-172">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="62638-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="62638-173">未執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="62638-173">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="62638-174">必要？</span><span class="sxs-lookup"><span data-stu-id="62638-174">Required?</span></span>                            | <span data-ttu-id="62638-175">false</span><span class="sxs-lookup"><span data-stu-id="62638-175">false</span></span>                                |
| <span data-ttu-id="62638-176">位置？</span><span class="sxs-lookup"><span data-stu-id="62638-176">Position?</span></span>                            | <span data-ttu-id="62638-177">具名</span><span class="sxs-lookup"><span data-stu-id="62638-177">named</span></span>                                |
| <span data-ttu-id="62638-178">預設值</span><span class="sxs-lookup"><span data-stu-id="62638-178">Default Value</span></span>                        | <span data-ttu-id="62638-179">false</span><span class="sxs-lookup"><span data-stu-id="62638-179">false</span></span>                                |
| <span data-ttu-id="62638-180">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="62638-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="62638-181">false</span><span class="sxs-lookup"><span data-stu-id="62638-181">false</span></span>                                |
| <span data-ttu-id="62638-182">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="62638-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="62638-183">false</span><span class="sxs-lookup"><span data-stu-id="62638-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="62638-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="62638-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="62638-185">這個 Cmdlet 支援一般參數：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。</span><span class="sxs-lookup"><span data-stu-id="62638-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span> <span data-ttu-id="62638-186">如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="62638-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="62638-187">輸入</span><span class="sxs-lookup"><span data-stu-id="62638-187">INPUTS</span></span>

<span data-ttu-id="62638-188">此 Cmdlet 不會接受任何輸入。</span><span class="sxs-lookup"><span data-stu-id="62638-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="62638-189">輸出</span><span class="sxs-lookup"><span data-stu-id="62638-189">OUTPUTS</span></span>

<span data-ttu-id="62638-190">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="62638-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="62638-191">範例</span><span class="sxs-lookup"><span data-stu-id="62638-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="62638-192">範例 1</span><span class="sxs-lookup"><span data-stu-id="62638-192">EXAMPLE 1</span></span>

<span data-ttu-id="62638-193">此範例會使用 **WebApplicationName** (*pswa*) 和 **WebSiteName** (預設網站) 參數的預設值，來安裝 PSWA Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="62638-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="62638-194">範例 2</span><span class="sxs-lookup"><span data-stu-id="62638-194">EXAMPLE 2</span></span>

<span data-ttu-id="62638-195">此範例會使用 **WebApplicationName** 和 **WebSiteName** 參數的預設值，來安裝具有測試憑證的 PSWA Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="62638-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="62638-196">相關主題</span><span class="sxs-lookup"><span data-stu-id="62638-196">Related topics</span></span>

- [<span data-ttu-id="62638-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="62638-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="62638-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="62638-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="62638-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="62638-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="62638-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="62638-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)