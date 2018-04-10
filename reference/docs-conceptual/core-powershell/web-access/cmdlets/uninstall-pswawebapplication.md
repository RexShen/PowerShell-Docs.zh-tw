---
description: ''
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: uninstall pswawebapplication
ms.technology: powershell
ms.openlocfilehash: 139c8358a24e54dec630f8c78737728330ba4aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="95504-103">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="95504-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="95504-104">概要</span><span class="sxs-lookup"><span data-stu-id="95504-104">SYNOPSIS</span></span>

<span data-ttu-id="95504-105">解除安裝 Windows PowerShell® Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="95504-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="95504-106">語法</span><span class="sxs-lookup"><span data-stu-id="95504-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="95504-107">Default</span><span class="sxs-lookup"><span data-stu-id="95504-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="95504-108">描述</span><span class="sxs-lookup"><span data-stu-id="95504-108">DESCRIPTION</span></span>

<span data-ttu-id="95504-109">**Uninstall-PswaWebApplication** Cmdlet 會解除安裝 Windows PowerShell Web 應用程式並從 IIS 移除網站。</span><span class="sxs-lookup"><span data-stu-id="95504-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="95504-110">此 Cmdlet 不會解除安裝 IIS 或已安裝的任何其他功能，因為 Windows PowerShell 需要這些功能才能執行。</span><span class="sxs-lookup"><span data-stu-id="95504-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="95504-111">參數</span><span class="sxs-lookup"><span data-stu-id="95504-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="95504-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="95504-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="95504-113">表示已刪除 **Install\_PswaWebApplication** Cmdlet (搭配 **UseTestCertificate** 參數) 所建立的測試憑證。</span><span class="sxs-lookup"><span data-stu-id="95504-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="95504-114">只會移除與 **Install-PswaWebApplication** Cmdlet 所建立的測試憑證同名的測試憑證。</span><span class="sxs-lookup"><span data-stu-id="95504-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||
|-|-|
| <span data-ttu-id="95504-115">別名</span><span class="sxs-lookup"><span data-stu-id="95504-115">Aliases</span></span>                              | <span data-ttu-id="95504-116">無</span><span class="sxs-lookup"><span data-stu-id="95504-116">none</span></span>                                 |
| <span data-ttu-id="95504-117">必要？</span><span class="sxs-lookup"><span data-stu-id="95504-117">Required?</span></span>                            | <span data-ttu-id="95504-118">false</span><span class="sxs-lookup"><span data-stu-id="95504-118">false</span></span>                                |
| <span data-ttu-id="95504-119">位置？</span><span class="sxs-lookup"><span data-stu-id="95504-119">Position?</span></span>                            | <span data-ttu-id="95504-120">具名</span><span class="sxs-lookup"><span data-stu-id="95504-120">named</span></span>                                |
| <span data-ttu-id="95504-121">預設值</span><span class="sxs-lookup"><span data-stu-id="95504-121">Default Value</span></span>                        | <span data-ttu-id="95504-122">true</span><span class="sxs-lookup"><span data-stu-id="95504-122">true</span></span>                                 |
| <span data-ttu-id="95504-123">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="95504-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="95504-124">false</span><span class="sxs-lookup"><span data-stu-id="95504-124">false</span></span>                                |
| <span data-ttu-id="95504-125">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="95504-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="95504-126">false</span><span class="sxs-lookup"><span data-stu-id="95504-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="95504-127">-WebApplicationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="95504-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="95504-128">指定要解除安裝的 Web 應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="95504-128">Specifies the name of the web application to uninstall.</span></span>

|||
|-|-|
| <span data-ttu-id="95504-129">別名</span><span class="sxs-lookup"><span data-stu-id="95504-129">Aliases</span></span>                              | <span data-ttu-id="95504-130">無</span><span class="sxs-lookup"><span data-stu-id="95504-130">none</span></span>                                 |
| <span data-ttu-id="95504-131">必要？</span><span class="sxs-lookup"><span data-stu-id="95504-131">Required?</span></span>                            | <span data-ttu-id="95504-132">false</span><span class="sxs-lookup"><span data-stu-id="95504-132">false</span></span>                                |
| <span data-ttu-id="95504-133">位置？</span><span class="sxs-lookup"><span data-stu-id="95504-133">Position?</span></span>                            | <span data-ttu-id="95504-134">1</span><span class="sxs-lookup"><span data-stu-id="95504-134">1</span></span>                                    |
| <span data-ttu-id="95504-135">預設值</span><span class="sxs-lookup"><span data-stu-id="95504-135">Default Value</span></span>                        | <span data-ttu-id="95504-136">pswa</span><span class="sxs-lookup"><span data-stu-id="95504-136">pswa</span></span>                                 |
| <span data-ttu-id="95504-137">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="95504-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="95504-138">false</span><span class="sxs-lookup"><span data-stu-id="95504-138">false</span></span>                                |
| <span data-ttu-id="95504-139">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="95504-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="95504-140">false</span><span class="sxs-lookup"><span data-stu-id="95504-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="95504-141">-WebSiteName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="95504-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="95504-142">指定 Web 應用程式安裝所在的網站名稱。</span><span class="sxs-lookup"><span data-stu-id="95504-142">Specifies the name of the web site where the web application is installed.</span></span>

|||
|-|-|
| <span data-ttu-id="95504-143">別名</span><span class="sxs-lookup"><span data-stu-id="95504-143">Aliases</span></span>                              | <span data-ttu-id="95504-144">無</span><span class="sxs-lookup"><span data-stu-id="95504-144">none</span></span>                                 |
| <span data-ttu-id="95504-145">必要？</span><span class="sxs-lookup"><span data-stu-id="95504-145">Required?</span></span>                            | <span data-ttu-id="95504-146">false</span><span class="sxs-lookup"><span data-stu-id="95504-146">false</span></span>                                |
| <span data-ttu-id="95504-147">位置？</span><span class="sxs-lookup"><span data-stu-id="95504-147">Position?</span></span>                            | <span data-ttu-id="95504-148">具名</span><span class="sxs-lookup"><span data-stu-id="95504-148">named</span></span>                                |
| <span data-ttu-id="95504-149">預設值</span><span class="sxs-lookup"><span data-stu-id="95504-149">Default Value</span></span>                        | <span data-ttu-id="95504-150">預設網站</span><span class="sxs-lookup"><span data-stu-id="95504-150">Default Web Site</span></span>                     |
| <span data-ttu-id="95504-151">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="95504-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="95504-152">false</span><span class="sxs-lookup"><span data-stu-id="95504-152">false</span></span>                                |
| <span data-ttu-id="95504-153">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="95504-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="95504-154">false</span><span class="sxs-lookup"><span data-stu-id="95504-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="95504-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="95504-155">-Confirm</span></span>

<span data-ttu-id="95504-156">執行 Cmdlet 之前先提示您確認。</span><span class="sxs-lookup"><span data-stu-id="95504-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="95504-157">必要？</span><span class="sxs-lookup"><span data-stu-id="95504-157">Required?</span></span>                            | <span data-ttu-id="95504-158">false</span><span class="sxs-lookup"><span data-stu-id="95504-158">false</span></span>                                |
| <span data-ttu-id="95504-159">位置？</span><span class="sxs-lookup"><span data-stu-id="95504-159">Position?</span></span>                            | <span data-ttu-id="95504-160">具名</span><span class="sxs-lookup"><span data-stu-id="95504-160">named</span></span>                                |
| <span data-ttu-id="95504-161">預設值</span><span class="sxs-lookup"><span data-stu-id="95504-161">Default Value</span></span>                        | <span data-ttu-id="95504-162">false</span><span class="sxs-lookup"><span data-stu-id="95504-162">false</span></span>                                |
| <span data-ttu-id="95504-163">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="95504-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="95504-164">false</span><span class="sxs-lookup"><span data-stu-id="95504-164">false</span></span>                                |
| <span data-ttu-id="95504-165">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="95504-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="95504-166">false</span><span class="sxs-lookup"><span data-stu-id="95504-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="95504-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="95504-167">-WhatIf</span></span>

<span data-ttu-id="95504-168">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="95504-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="95504-169">未執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="95504-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="95504-170">必要？</span><span class="sxs-lookup"><span data-stu-id="95504-170">Required?</span></span>                            | <span data-ttu-id="95504-171">false</span><span class="sxs-lookup"><span data-stu-id="95504-171">false</span></span>                                |
| <span data-ttu-id="95504-172">位置？</span><span class="sxs-lookup"><span data-stu-id="95504-172">Position?</span></span>                            | <span data-ttu-id="95504-173">具名</span><span class="sxs-lookup"><span data-stu-id="95504-173">named</span></span>                                |
| <span data-ttu-id="95504-174">預設值</span><span class="sxs-lookup"><span data-stu-id="95504-174">Default Value</span></span>                        | <span data-ttu-id="95504-175">false</span><span class="sxs-lookup"><span data-stu-id="95504-175">false</span></span>                                |
| <span data-ttu-id="95504-176">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="95504-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="95504-177">false</span><span class="sxs-lookup"><span data-stu-id="95504-177">false</span></span>                                |
| <span data-ttu-id="95504-178">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="95504-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="95504-179">false</span><span class="sxs-lookup"><span data-stu-id="95504-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="95504-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="95504-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="95504-181">這個 Cmdlet 支援一般參數：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。</span><span class="sxs-lookup"><span data-stu-id="95504-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="95504-182">如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="95504-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="95504-183">輸入</span><span class="sxs-lookup"><span data-stu-id="95504-183">INPUTS</span></span>

<span data-ttu-id="95504-184">此 Cmdlet 不會接受任何輸入。</span><span class="sxs-lookup"><span data-stu-id="95504-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="95504-185">輸出</span><span class="sxs-lookup"><span data-stu-id="95504-185">OUTPUTS</span></span>

<span data-ttu-id="95504-186">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="95504-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="95504-187">範例</span><span class="sxs-lookup"><span data-stu-id="95504-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="95504-188">範例 1</span><span class="sxs-lookup"><span data-stu-id="95504-188">EXAMPLE 1</span></span>

<span data-ttu-id="95504-189">此命令會解除安裝 Windows PowerShell Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="95504-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="95504-190">如果您使用預設值來安裝 Windows PowerShell Web 應用程式，則可以使用此 Cmdlet 將它解除安裝。</span><span class="sxs-lookup"><span data-stu-id="95504-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="95504-191">範例 2</span><span class="sxs-lookup"><span data-stu-id="95504-191">EXAMPLE 2</span></span>

<span data-ttu-id="95504-192">此命令會解除安裝 Windows PowerShell Web 應用程式，並會刪除與應用程式建立關聯的測試憑證。</span><span class="sxs-lookup"><span data-stu-id="95504-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="95504-193">如果您使用預設值來安裝 Windows PowerShell Web 應用程式並建立測試憑證，則可以使用此 Cmdlet 將它解除安裝。</span><span class="sxs-lookup"><span data-stu-id="95504-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="95504-194">範例 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="95504-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="95504-195">此命令會在安裝期間指定自訂網站和應用程式時，解除安裝 Windows PowerShell Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="95504-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="95504-196">此命令會移除名為 *MySite* 的網站及名為 *TestApplication* 的應用程式，並指定同時刪除與應用程式建立關聯的測試憑證。</span><span class="sxs-lookup"><span data-stu-id="95504-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="95504-197">相關主題</span><span class="sxs-lookup"><span data-stu-id="95504-197">Related topics</span></span>

- [<span data-ttu-id="95504-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="95504-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="95504-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="95504-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="95504-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="95504-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="95504-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="95504-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="95504-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="95504-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)