---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: test pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 900547301c815ba6fe3a9507f975503fec864e4e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2017
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="31e24-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="31e24-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="31e24-104">概要</span><span class="sxs-lookup"><span data-stu-id="31e24-104">SYNOPSIS</span></span>

<span data-ttu-id="31e24-105">確認是否有指定使用者、電腦或端點的規則。</span><span class="sxs-lookup"><span data-stu-id="31e24-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="31e24-106">語法</span><span class="sxs-lookup"><span data-stu-id="31e24-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="31e24-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="31e24-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="31e24-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="31e24-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="31e24-109">描述</span><span class="sxs-lookup"><span data-stu-id="31e24-109">DESCRIPTION</span></span>

<span data-ttu-id="31e24-110">**Test-PswaAuthorizationRule** Cmdlet 會確認是否有指定使用者、電腦或端點的規則。</span><span class="sxs-lookup"><span data-stu-id="31e24-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="31e24-111">此 Cmdlet 也可用來測試授權規則，以驗證特定使用者、電腦或端點存取要求是否已獲授權。</span><span class="sxs-lookup"><span data-stu-id="31e24-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="31e24-112">根據預設，此 Cmdlet 會評估授權檔案中的所有規則。</span><span class="sxs-lookup"><span data-stu-id="31e24-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="31e24-113">不過，您可以指定要測試的規則子集。</span><span class="sxs-lookup"><span data-stu-id="31e24-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="31e24-114">您可以使用此 Cmdlet 來為驗證失敗進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="31e24-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="31e24-115">此 Cmdlet 的參數會對應至 Windows PowerShell® Web 存取登入頁面上的欄位。</span><span class="sxs-lookup"><span data-stu-id="31e24-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="31e24-116">參數</span><span class="sxs-lookup"><span data-stu-id="31e24-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="31e24-117">-ComputerName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="31e24-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="31e24-118">指定要測試的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="31e24-118">Specifies the name of the computer to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="31e24-119">別名</span><span class="sxs-lookup"><span data-stu-id="31e24-119">Aliases</span></span>                              | <span data-ttu-id="31e24-120">無</span><span class="sxs-lookup"><span data-stu-id="31e24-120">none</span></span>                                 |
| <span data-ttu-id="31e24-121">必要？</span><span class="sxs-lookup"><span data-stu-id="31e24-121">Required?</span></span>                            | <span data-ttu-id="31e24-122">true</span><span class="sxs-lookup"><span data-stu-id="31e24-122">true</span></span>                                 |
| <span data-ttu-id="31e24-123">位置？</span><span class="sxs-lookup"><span data-stu-id="31e24-123">Position?</span></span>                            | <span data-ttu-id="31e24-124">2</span><span class="sxs-lookup"><span data-stu-id="31e24-124">2</span></span>                                    |
| <span data-ttu-id="31e24-125">預設值</span><span class="sxs-lookup"><span data-stu-id="31e24-125">Default Value</span></span>                        | <span data-ttu-id="31e24-126">無</span><span class="sxs-lookup"><span data-stu-id="31e24-126">none</span></span>                                 |
| <span data-ttu-id="31e24-127">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="31e24-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="31e24-128">false</span><span class="sxs-lookup"><span data-stu-id="31e24-128">false</span></span>                                |
| <span data-ttu-id="31e24-129">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="31e24-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="31e24-130">false</span><span class="sxs-lookup"><span data-stu-id="31e24-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="31e24-131">-ConfigurationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="31e24-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="31e24-132">指定要測試的 Windows PowerShell 工作階段設定名稱，也稱為端點或 Runspace。</span><span class="sxs-lookup"><span data-stu-id="31e24-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="31e24-133">別名</span><span class="sxs-lookup"><span data-stu-id="31e24-133">Aliases</span></span>                              | <span data-ttu-id="31e24-134">無</span><span class="sxs-lookup"><span data-stu-id="31e24-134">none</span></span>                                 |
| <span data-ttu-id="31e24-135">必要？</span><span class="sxs-lookup"><span data-stu-id="31e24-135">Required?</span></span>                            | <span data-ttu-id="31e24-136">false</span><span class="sxs-lookup"><span data-stu-id="31e24-136">false</span></span>                                |
| <span data-ttu-id="31e24-137">位置？</span><span class="sxs-lookup"><span data-stu-id="31e24-137">Position?</span></span>                            | <span data-ttu-id="31e24-138">3</span><span class="sxs-lookup"><span data-stu-id="31e24-138">3</span></span>                                    |
| <span data-ttu-id="31e24-139">預設值</span><span class="sxs-lookup"><span data-stu-id="31e24-139">Default Value</span></span>                        | <span data-ttu-id="31e24-140">無</span><span class="sxs-lookup"><span data-stu-id="31e24-140">none</span></span>                                 |
| <span data-ttu-id="31e24-141">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="31e24-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="31e24-142">false</span><span class="sxs-lookup"><span data-stu-id="31e24-142">false</span></span>                                |
| <span data-ttu-id="31e24-143">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="31e24-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="31e24-144">false</span><span class="sxs-lookup"><span data-stu-id="31e24-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="31e24-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="31e24-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="31e24-146">指定要測試的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="31e24-146">Specifies the connection URI to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="31e24-147">別名</span><span class="sxs-lookup"><span data-stu-id="31e24-147">Aliases</span></span>                              | <span data-ttu-id="31e24-148">無</span><span class="sxs-lookup"><span data-stu-id="31e24-148">none</span></span>                                 |
| <span data-ttu-id="31e24-149">必要？</span><span class="sxs-lookup"><span data-stu-id="31e24-149">Required?</span></span>                            | <span data-ttu-id="31e24-150">true</span><span class="sxs-lookup"><span data-stu-id="31e24-150">true</span></span>                                 |
| <span data-ttu-id="31e24-151">位置？</span><span class="sxs-lookup"><span data-stu-id="31e24-151">Position?</span></span>                            | <span data-ttu-id="31e24-152">2</span><span class="sxs-lookup"><span data-stu-id="31e24-152">2</span></span>                                    |
| <span data-ttu-id="31e24-153">預設值</span><span class="sxs-lookup"><span data-stu-id="31e24-153">Default Value</span></span>                        | <span data-ttu-id="31e24-154">無</span><span class="sxs-lookup"><span data-stu-id="31e24-154">none</span></span>                                 |
| <span data-ttu-id="31e24-155">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="31e24-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="31e24-156">false</span><span class="sxs-lookup"><span data-stu-id="31e24-156">false</span></span>                                |
| <span data-ttu-id="31e24-157">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="31e24-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="31e24-158">false</span><span class="sxs-lookup"><span data-stu-id="31e24-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="31e24-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="31e24-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="31e24-160">指定您要用來測試 Windows PowerShell Web 存取授權規則之使用者帳戶的 **PSCredential** 物件。</span><span class="sxs-lookup"><span data-stu-id="31e24-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="31e24-161">如果您未新增這個參數，此 Cmdlet 就會使用目前登入的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="31e24-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="31e24-162">若要取得從遠端測試授權規則所需的 **PSCredential** 物件，請執行 [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="31e24-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="31e24-163">別名</span><span class="sxs-lookup"><span data-stu-id="31e24-163">Aliases</span></span>                              | <span data-ttu-id="31e24-164">無</span><span class="sxs-lookup"><span data-stu-id="31e24-164">none</span></span>                                 |
| <span data-ttu-id="31e24-165">必要？</span><span class="sxs-lookup"><span data-stu-id="31e24-165">Required?</span></span>                            | <span data-ttu-id="31e24-166">false</span><span class="sxs-lookup"><span data-stu-id="31e24-166">false</span></span>                                |
| <span data-ttu-id="31e24-167">位置？</span><span class="sxs-lookup"><span data-stu-id="31e24-167">Position?</span></span>                            | <span data-ttu-id="31e24-168">具名</span><span class="sxs-lookup"><span data-stu-id="31e24-168">named</span></span>                                |
| <span data-ttu-id="31e24-169">預設值</span><span class="sxs-lookup"><span data-stu-id="31e24-169">Default Value</span></span>                        | <span data-ttu-id="31e24-170">無</span><span class="sxs-lookup"><span data-stu-id="31e24-170">none</span></span>                                 |
| <span data-ttu-id="31e24-171">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="31e24-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="31e24-172">false</span><span class="sxs-lookup"><span data-stu-id="31e24-172">false</span></span>                                |
| <span data-ttu-id="31e24-173">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="31e24-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="31e24-174">false</span><span class="sxs-lookup"><span data-stu-id="31e24-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="31e24-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="31e24-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="31e24-176">指定要測試的規則子集。</span><span class="sxs-lookup"><span data-stu-id="31e24-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="31e24-177">如果未指定這個參數，則此 Cmdlet 會測試所有授權規則。</span><span class="sxs-lookup"><span data-stu-id="31e24-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="31e24-178">別名</span><span class="sxs-lookup"><span data-stu-id="31e24-178">Aliases</span></span>                              | <span data-ttu-id="31e24-179">無</span><span class="sxs-lookup"><span data-stu-id="31e24-179">none</span></span>                                 |
| <span data-ttu-id="31e24-180">必要？</span><span class="sxs-lookup"><span data-stu-id="31e24-180">Required?</span></span>                            | <span data-ttu-id="31e24-181">false</span><span class="sxs-lookup"><span data-stu-id="31e24-181">false</span></span>                                |
| <span data-ttu-id="31e24-182">位置？</span><span class="sxs-lookup"><span data-stu-id="31e24-182">Position?</span></span>                            | <span data-ttu-id="31e24-183">具名</span><span class="sxs-lookup"><span data-stu-id="31e24-183">named</span></span>                                |
| <span data-ttu-id="31e24-184">預設值</span><span class="sxs-lookup"><span data-stu-id="31e24-184">Default Value</span></span>                        | <span data-ttu-id="31e24-185">無</span><span class="sxs-lookup"><span data-stu-id="31e24-185">none</span></span>                                 |
| <span data-ttu-id="31e24-186">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="31e24-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="31e24-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="31e24-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="31e24-188">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="31e24-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="31e24-189">false</span><span class="sxs-lookup"><span data-stu-id="31e24-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="31e24-190">-UserName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="31e24-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="31e24-191">指定要測試的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="31e24-191">Specifies the name of the user to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="31e24-192">別名</span><span class="sxs-lookup"><span data-stu-id="31e24-192">Aliases</span></span>                              | <span data-ttu-id="31e24-193">無</span><span class="sxs-lookup"><span data-stu-id="31e24-193">none</span></span>                                 |
| <span data-ttu-id="31e24-194">必要？</span><span class="sxs-lookup"><span data-stu-id="31e24-194">Required?</span></span>                            | <span data-ttu-id="31e24-195">true</span><span class="sxs-lookup"><span data-stu-id="31e24-195">true</span></span>                                 |
| <span data-ttu-id="31e24-196">位置？</span><span class="sxs-lookup"><span data-stu-id="31e24-196">Position?</span></span>                            | <span data-ttu-id="31e24-197">1</span><span class="sxs-lookup"><span data-stu-id="31e24-197">1</span></span>                                    |
| <span data-ttu-id="31e24-198">預設值</span><span class="sxs-lookup"><span data-stu-id="31e24-198">Default Value</span></span>                        | <span data-ttu-id="31e24-199">無</span><span class="sxs-lookup"><span data-stu-id="31e24-199">none</span></span>                                 |
| <span data-ttu-id="31e24-200">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="31e24-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="31e24-201">false</span><span class="sxs-lookup"><span data-stu-id="31e24-201">false</span></span>                                |
| <span data-ttu-id="31e24-202">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="31e24-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="31e24-203">false</span><span class="sxs-lookup"><span data-stu-id="31e24-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="31e24-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="31e24-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="31e24-205">這個 Cmdlet 支援一般參數：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。</span><span class="sxs-lookup"><span data-stu-id="31e24-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="31e24-206">如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="31e24-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="31e24-207">輸入</span><span class="sxs-lookup"><span data-stu-id="31e24-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="31e24-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="31e24-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="31e24-209">此 Cmdlet 會接受 PswaAuthorizationRule 物件的陣列作為輸入。</span><span class="sxs-lookup"><span data-stu-id="31e24-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="31e24-210">輸出</span><span class="sxs-lookup"><span data-stu-id="31e24-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="31e24-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="31e24-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="31e24-212">此 Cmdlet 會產生 PswaAuthorizationRule 物件的陣列作為輸出。</span><span class="sxs-lookup"><span data-stu-id="31e24-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="31e24-213">範例</span><span class="sxs-lookup"><span data-stu-id="31e24-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="31e24-214">範例 1</span><span class="sxs-lookup"><span data-stu-id="31e24-214">EXAMPLE 1</span></span>

<span data-ttu-id="31e24-215">此範例會測試所有授權規則，以顯示允許使用者 *contoso\\mhanson* 連線到電腦 *srv2* 並使用名為 *test* 之 Windows PowerShell 工作階段設定的所有規則。</span><span class="sxs-lookup"><span data-stu-id="31e24-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="31e24-216">範例 2</span><span class="sxs-lookup"><span data-stu-id="31e24-216">EXAMPLE 2</span></span>

<span data-ttu-id="31e24-217">此範例會測試所有授權規則，以確認哪些授權規則適用於使用者 *contoso\\mhanson*。</span><span class="sxs-lookup"><span data-stu-id="31e24-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="31e24-218">相關主題</span><span class="sxs-lookup"><span data-stu-id="31e24-218">Related topics</span></span>

- [<span data-ttu-id="31e24-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="31e24-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="31e24-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="31e24-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="31e24-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="31e24-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="31e24-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="31e24-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
