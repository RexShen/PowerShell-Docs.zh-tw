---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Remove-PswaAuthorizationRule
ms.openlocfilehash: 6a3720bb9b8df3e1c6bb9f4a6196c9868b85b67d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="cc367-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="cc367-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="cc367-104">概要</span><span class="sxs-lookup"><span data-stu-id="cc367-104">SYNOPSIS</span></span>

<span data-ttu-id="cc367-105">從 Windows PowerShell® Web 存取移除指定的授權規則。</span><span class="sxs-lookup"><span data-stu-id="cc367-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="cc367-106">語法</span><span class="sxs-lookup"><span data-stu-id="cc367-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="cc367-107">Id</span><span class="sxs-lookup"><span data-stu-id="cc367-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="cc367-108">規則</span><span class="sxs-lookup"><span data-stu-id="cc367-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="cc367-109">描述</span><span class="sxs-lookup"><span data-stu-id="cc367-109">DESCRIPTION</span></span>

<span data-ttu-id="cc367-110">從 Windows PowerShell Web 存取中移除指定的授權規則。</span><span class="sxs-lookup"><span data-stu-id="cc367-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="cc367-111">參數</span><span class="sxs-lookup"><span data-stu-id="cc367-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="cc367-112">-Force</span><span class="sxs-lookup"><span data-stu-id="cc367-112">-Force</span></span>

<span data-ttu-id="cc367-113">在不提示確認的情況下執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cc367-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="cc367-114">根據預設，此 Cmdlet 會先要求確認，再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="cc367-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||
|-|-|
| <span data-ttu-id="cc367-115">別名</span><span class="sxs-lookup"><span data-stu-id="cc367-115">Aliases</span></span>                              | <span data-ttu-id="cc367-116">無</span><span class="sxs-lookup"><span data-stu-id="cc367-116">none</span></span>                                 |
| <span data-ttu-id="cc367-117">必要？</span><span class="sxs-lookup"><span data-stu-id="cc367-117">Required?</span></span>                            | <span data-ttu-id="cc367-118">false</span><span class="sxs-lookup"><span data-stu-id="cc367-118">false</span></span>                                |
| <span data-ttu-id="cc367-119">位置？</span><span class="sxs-lookup"><span data-stu-id="cc367-119">Position?</span></span>                            | <span data-ttu-id="cc367-120">具名</span><span class="sxs-lookup"><span data-stu-id="cc367-120">named</span></span>                                |
| <span data-ttu-id="cc367-121">預設值</span><span class="sxs-lookup"><span data-stu-id="cc367-121">Default Value</span></span>                        | <span data-ttu-id="cc367-122">無</span><span class="sxs-lookup"><span data-stu-id="cc367-122">none</span></span>                                 |
| <span data-ttu-id="cc367-123">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="cc367-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="cc367-124">false</span><span class="sxs-lookup"><span data-stu-id="cc367-124">false</span></span>                                |
| <span data-ttu-id="cc367-125">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="cc367-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="cc367-126">false</span><span class="sxs-lookup"><span data-stu-id="cc367-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="cc367-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="cc367-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="cc367-128">指定要移除之一或多個規則的識別碼。</span><span class="sxs-lookup"><span data-stu-id="cc367-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="cc367-129">別名</span><span class="sxs-lookup"><span data-stu-id="cc367-129">Aliases</span></span>                              | <span data-ttu-id="cc367-130">無</span><span class="sxs-lookup"><span data-stu-id="cc367-130">none</span></span>                                 |
| <span data-ttu-id="cc367-131">必要？</span><span class="sxs-lookup"><span data-stu-id="cc367-131">Required?</span></span>                            | <span data-ttu-id="cc367-132">true</span><span class="sxs-lookup"><span data-stu-id="cc367-132">true</span></span>                                 |
| <span data-ttu-id="cc367-133">位置？</span><span class="sxs-lookup"><span data-stu-id="cc367-133">Position?</span></span>                            | <span data-ttu-id="cc367-134">2</span><span class="sxs-lookup"><span data-stu-id="cc367-134">2</span></span>                                    |
| <span data-ttu-id="cc367-135">預設值</span><span class="sxs-lookup"><span data-stu-id="cc367-135">Default Value</span></span>                        | <span data-ttu-id="cc367-136">無</span><span class="sxs-lookup"><span data-stu-id="cc367-136">none</span></span>                                 |
| <span data-ttu-id="cc367-137">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="cc367-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="cc367-138">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="cc367-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="cc367-139">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="cc367-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="cc367-140">false</span><span class="sxs-lookup"><span data-stu-id="cc367-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="cc367-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="cc367-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="cc367-142">指定要移除的規則。</span><span class="sxs-lookup"><span data-stu-id="cc367-142">Specifies the rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="cc367-143">別名</span><span class="sxs-lookup"><span data-stu-id="cc367-143">Aliases</span></span>                              | <span data-ttu-id="cc367-144">無</span><span class="sxs-lookup"><span data-stu-id="cc367-144">none</span></span>                                 |
| <span data-ttu-id="cc367-145">必要？</span><span class="sxs-lookup"><span data-stu-id="cc367-145">Required?</span></span>                            | <span data-ttu-id="cc367-146">true</span><span class="sxs-lookup"><span data-stu-id="cc367-146">true</span></span>                                 |
| <span data-ttu-id="cc367-147">位置？</span><span class="sxs-lookup"><span data-stu-id="cc367-147">Position?</span></span>                            | <span data-ttu-id="cc367-148">2</span><span class="sxs-lookup"><span data-stu-id="cc367-148">2</span></span>                                    |
| <span data-ttu-id="cc367-149">預設值</span><span class="sxs-lookup"><span data-stu-id="cc367-149">Default Value</span></span>                        | <span data-ttu-id="cc367-150">無</span><span class="sxs-lookup"><span data-stu-id="cc367-150">none</span></span>                                 |
| <span data-ttu-id="cc367-151">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="cc367-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="cc367-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="cc367-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="cc367-153">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="cc367-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="cc367-154">false</span><span class="sxs-lookup"><span data-stu-id="cc367-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="cc367-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cc367-155">-Confirm</span></span>

<span data-ttu-id="cc367-156">執行 Cmdlet 之前先提示您確認。</span><span class="sxs-lookup"><span data-stu-id="cc367-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="cc367-157">必要？</span><span class="sxs-lookup"><span data-stu-id="cc367-157">Required?</span></span>                            | <span data-ttu-id="cc367-158">false</span><span class="sxs-lookup"><span data-stu-id="cc367-158">false</span></span>                                |
| <span data-ttu-id="cc367-159">位置？</span><span class="sxs-lookup"><span data-stu-id="cc367-159">Position?</span></span>                            | <span data-ttu-id="cc367-160">具名</span><span class="sxs-lookup"><span data-stu-id="cc367-160">named</span></span>                                |
| <span data-ttu-id="cc367-161">預設值</span><span class="sxs-lookup"><span data-stu-id="cc367-161">Default Value</span></span>                        | <span data-ttu-id="cc367-162">false</span><span class="sxs-lookup"><span data-stu-id="cc367-162">false</span></span>                                |
| <span data-ttu-id="cc367-163">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="cc367-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="cc367-164">false</span><span class="sxs-lookup"><span data-stu-id="cc367-164">false</span></span>                                |
| <span data-ttu-id="cc367-165">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="cc367-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="cc367-166">false</span><span class="sxs-lookup"><span data-stu-id="cc367-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="cc367-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cc367-167">-WhatIf</span></span>

<span data-ttu-id="cc367-168">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="cc367-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="cc367-169">未執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cc367-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="cc367-170">必要？</span><span class="sxs-lookup"><span data-stu-id="cc367-170">Required?</span></span>                            | <span data-ttu-id="cc367-171">false</span><span class="sxs-lookup"><span data-stu-id="cc367-171">false</span></span>                                |
| <span data-ttu-id="cc367-172">位置？</span><span class="sxs-lookup"><span data-stu-id="cc367-172">Position?</span></span>                            | <span data-ttu-id="cc367-173">具名</span><span class="sxs-lookup"><span data-stu-id="cc367-173">named</span></span>                                |
| <span data-ttu-id="cc367-174">預設值</span><span class="sxs-lookup"><span data-stu-id="cc367-174">Default Value</span></span>                        | <span data-ttu-id="cc367-175">false</span><span class="sxs-lookup"><span data-stu-id="cc367-175">false</span></span>                                |
| <span data-ttu-id="cc367-176">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="cc367-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="cc367-177">false</span><span class="sxs-lookup"><span data-stu-id="cc367-177">false</span></span>                                |
| <span data-ttu-id="cc367-178">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="cc367-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="cc367-179">false</span><span class="sxs-lookup"><span data-stu-id="cc367-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="cc367-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="cc367-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="cc367-181">這個 Cmdlet 支援一般參數：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。</span><span class="sxs-lookup"><span data-stu-id="cc367-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="cc367-182">如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="cc367-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="cc367-183">輸入</span><span class="sxs-lookup"><span data-stu-id="cc367-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="cc367-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="cc367-184">int\[\]</span></span>

<span data-ttu-id="cc367-185">此 Cmdlet 會接受整數陣列或 PswaAuthorizationRule 物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="cc367-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="cc367-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="cc367-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="cc367-187">此 Cmdlet 會接受整數陣列或 PswaAuthorizationRule 物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="cc367-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="cc367-188">輸出</span><span class="sxs-lookup"><span data-stu-id="cc367-188">OUTPUTS</span></span>

<span data-ttu-id="cc367-189">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="cc367-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="cc367-190">範例</span><span class="sxs-lookup"><span data-stu-id="cc367-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="cc367-191">範例 1</span><span class="sxs-lookup"><span data-stu-id="cc367-191">EXAMPLE 1</span></span>

<span data-ttu-id="cc367-192">此範例會移除識別碼為 *2* 的授權規則。</span><span class="sxs-lookup"><span data-stu-id="cc367-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="cc367-193">範例 2 {#example-2 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="cc367-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="cc367-194">此範例會移除所有授權規則，也會要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="cc367-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="cc367-195">相關主題</span><span class="sxs-lookup"><span data-stu-id="cc367-195">Related topics</span></span>

- [<span data-ttu-id="cc367-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="cc367-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="cc367-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="cc367-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="cc367-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="cc367-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="cc367-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="cc367-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)