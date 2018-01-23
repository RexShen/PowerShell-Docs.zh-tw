---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: remove pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 4d039e7e00f87bc7aebb89217251edbbb5c3f5be
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="63f03-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="63f03-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="63f03-104">概要</span><span class="sxs-lookup"><span data-stu-id="63f03-104">SYNOPSIS</span></span>

<span data-ttu-id="63f03-105">從 Windows PowerShell® Web 存取移除指定的授權規則。</span><span class="sxs-lookup"><span data-stu-id="63f03-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="63f03-106">語法</span><span class="sxs-lookup"><span data-stu-id="63f03-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="63f03-107">Id</span><span class="sxs-lookup"><span data-stu-id="63f03-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="63f03-108">規則</span><span class="sxs-lookup"><span data-stu-id="63f03-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="63f03-109">描述</span><span class="sxs-lookup"><span data-stu-id="63f03-109">DESCRIPTION</span></span>

<span data-ttu-id="63f03-110">從 Windows PowerShell Web 存取中移除指定的授權規則。</span><span class="sxs-lookup"><span data-stu-id="63f03-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="63f03-111">參數</span><span class="sxs-lookup"><span data-stu-id="63f03-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="63f03-112">-Force</span><span class="sxs-lookup"><span data-stu-id="63f03-112">-Force</span></span>

<span data-ttu-id="63f03-113">在不提示確認的情況下執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="63f03-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="63f03-114">根據預設，此 Cmdlet 會先要求確認，再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="63f03-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||  
|-|-|
| <span data-ttu-id="63f03-115">別名</span><span class="sxs-lookup"><span data-stu-id="63f03-115">Aliases</span></span>                              | <span data-ttu-id="63f03-116">無</span><span class="sxs-lookup"><span data-stu-id="63f03-116">none</span></span>                                 |
| <span data-ttu-id="63f03-117">必要？</span><span class="sxs-lookup"><span data-stu-id="63f03-117">Required?</span></span>                            | <span data-ttu-id="63f03-118">false</span><span class="sxs-lookup"><span data-stu-id="63f03-118">false</span></span>                                |
| <span data-ttu-id="63f03-119">位置？</span><span class="sxs-lookup"><span data-stu-id="63f03-119">Position?</span></span>                            | <span data-ttu-id="63f03-120">具名</span><span class="sxs-lookup"><span data-stu-id="63f03-120">named</span></span>                                |
| <span data-ttu-id="63f03-121">預設值</span><span class="sxs-lookup"><span data-stu-id="63f03-121">Default Value</span></span>                        | <span data-ttu-id="63f03-122">無</span><span class="sxs-lookup"><span data-stu-id="63f03-122">none</span></span>                                 |
| <span data-ttu-id="63f03-123">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="63f03-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="63f03-124">false</span><span class="sxs-lookup"><span data-stu-id="63f03-124">false</span></span>                                |
| <span data-ttu-id="63f03-125">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="63f03-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="63f03-126">false</span><span class="sxs-lookup"><span data-stu-id="63f03-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="63f03-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="63f03-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="63f03-128">指定要移除之一或多個規則的識別碼。</span><span class="sxs-lookup"><span data-stu-id="63f03-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="63f03-129">別名</span><span class="sxs-lookup"><span data-stu-id="63f03-129">Aliases</span></span>                              | <span data-ttu-id="63f03-130">無</span><span class="sxs-lookup"><span data-stu-id="63f03-130">none</span></span>                                 |
| <span data-ttu-id="63f03-131">必要？</span><span class="sxs-lookup"><span data-stu-id="63f03-131">Required?</span></span>                            | <span data-ttu-id="63f03-132">true</span><span class="sxs-lookup"><span data-stu-id="63f03-132">true</span></span>                                 |
| <span data-ttu-id="63f03-133">位置？</span><span class="sxs-lookup"><span data-stu-id="63f03-133">Position?</span></span>                            | <span data-ttu-id="63f03-134">2</span><span class="sxs-lookup"><span data-stu-id="63f03-134">2</span></span>                                    |
| <span data-ttu-id="63f03-135">預設值</span><span class="sxs-lookup"><span data-stu-id="63f03-135">Default Value</span></span>                        | <span data-ttu-id="63f03-136">無</span><span class="sxs-lookup"><span data-stu-id="63f03-136">none</span></span>                                 |
| <span data-ttu-id="63f03-137">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="63f03-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="63f03-138">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="63f03-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="63f03-139">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="63f03-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="63f03-140">false</span><span class="sxs-lookup"><span data-stu-id="63f03-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="63f03-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="63f03-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="63f03-142">指定要移除的規則。</span><span class="sxs-lookup"><span data-stu-id="63f03-142">Specifies the rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="63f03-143">別名</span><span class="sxs-lookup"><span data-stu-id="63f03-143">Aliases</span></span>                              | <span data-ttu-id="63f03-144">無</span><span class="sxs-lookup"><span data-stu-id="63f03-144">none</span></span>                                 |
| <span data-ttu-id="63f03-145">必要？</span><span class="sxs-lookup"><span data-stu-id="63f03-145">Required?</span></span>                            | <span data-ttu-id="63f03-146">true</span><span class="sxs-lookup"><span data-stu-id="63f03-146">true</span></span>                                 |
| <span data-ttu-id="63f03-147">位置？</span><span class="sxs-lookup"><span data-stu-id="63f03-147">Position?</span></span>                            | <span data-ttu-id="63f03-148">2</span><span class="sxs-lookup"><span data-stu-id="63f03-148">2</span></span>                                    |
| <span data-ttu-id="63f03-149">預設值</span><span class="sxs-lookup"><span data-stu-id="63f03-149">Default Value</span></span>                        | <span data-ttu-id="63f03-150">無</span><span class="sxs-lookup"><span data-stu-id="63f03-150">none</span></span>                                 |
| <span data-ttu-id="63f03-151">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="63f03-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="63f03-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="63f03-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="63f03-153">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="63f03-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="63f03-154">false</span><span class="sxs-lookup"><span data-stu-id="63f03-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="63f03-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="63f03-155">-Confirm</span></span>

<span data-ttu-id="63f03-156">執行 Cmdlet 之前先提示您確認。</span><span class="sxs-lookup"><span data-stu-id="63f03-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="63f03-157">必要？</span><span class="sxs-lookup"><span data-stu-id="63f03-157">Required?</span></span>                            | <span data-ttu-id="63f03-158">false</span><span class="sxs-lookup"><span data-stu-id="63f03-158">false</span></span>                                |
| <span data-ttu-id="63f03-159">位置？</span><span class="sxs-lookup"><span data-stu-id="63f03-159">Position?</span></span>                            | <span data-ttu-id="63f03-160">具名</span><span class="sxs-lookup"><span data-stu-id="63f03-160">named</span></span>                                |
| <span data-ttu-id="63f03-161">預設值</span><span class="sxs-lookup"><span data-stu-id="63f03-161">Default Value</span></span>                        | <span data-ttu-id="63f03-162">false</span><span class="sxs-lookup"><span data-stu-id="63f03-162">false</span></span>                                |
| <span data-ttu-id="63f03-163">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="63f03-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="63f03-164">false</span><span class="sxs-lookup"><span data-stu-id="63f03-164">false</span></span>                                |
| <span data-ttu-id="63f03-165">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="63f03-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="63f03-166">false</span><span class="sxs-lookup"><span data-stu-id="63f03-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="63f03-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="63f03-167">-WhatIf</span></span>

<span data-ttu-id="63f03-168">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="63f03-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="63f03-169">未執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="63f03-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="63f03-170">必要？</span><span class="sxs-lookup"><span data-stu-id="63f03-170">Required?</span></span>                            | <span data-ttu-id="63f03-171">false</span><span class="sxs-lookup"><span data-stu-id="63f03-171">false</span></span>                                |
| <span data-ttu-id="63f03-172">位置？</span><span class="sxs-lookup"><span data-stu-id="63f03-172">Position?</span></span>                            | <span data-ttu-id="63f03-173">具名</span><span class="sxs-lookup"><span data-stu-id="63f03-173">named</span></span>                                |
| <span data-ttu-id="63f03-174">預設值</span><span class="sxs-lookup"><span data-stu-id="63f03-174">Default Value</span></span>                        | <span data-ttu-id="63f03-175">false</span><span class="sxs-lookup"><span data-stu-id="63f03-175">false</span></span>                                |
| <span data-ttu-id="63f03-176">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="63f03-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="63f03-177">false</span><span class="sxs-lookup"><span data-stu-id="63f03-177">false</span></span>                                |
| <span data-ttu-id="63f03-178">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="63f03-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="63f03-179">false</span><span class="sxs-lookup"><span data-stu-id="63f03-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="63f03-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="63f03-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="63f03-181">這個 Cmdlet 支援一般參數：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。</span><span class="sxs-lookup"><span data-stu-id="63f03-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="63f03-182">如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="63f03-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="63f03-183">輸入</span><span class="sxs-lookup"><span data-stu-id="63f03-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="63f03-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="63f03-184">int\[\]</span></span>

<span data-ttu-id="63f03-185">此 Cmdlet 會接受整數陣列或 PswaAuthorizationRule 物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="63f03-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="63f03-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="63f03-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="63f03-187">此 Cmdlet 會接受整數陣列或 PswaAuthorizationRule 物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="63f03-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="63f03-188">輸出</span><span class="sxs-lookup"><span data-stu-id="63f03-188">OUTPUTS</span></span>

<span data-ttu-id="63f03-189">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="63f03-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="63f03-190">範例</span><span class="sxs-lookup"><span data-stu-id="63f03-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="63f03-191">範例 1</span><span class="sxs-lookup"><span data-stu-id="63f03-191">EXAMPLE 1</span></span>

<span data-ttu-id="63f03-192">此範例會移除識別碼為 *2* 的授權規則。</span><span class="sxs-lookup"><span data-stu-id="63f03-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="63f03-193">範例 2 {#example-2 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="63f03-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="63f03-194">此範例會移除所有授權規則，也會要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="63f03-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="63f03-195">相關主題</span><span class="sxs-lookup"><span data-stu-id="63f03-195">Related topics</span></span>

- [<span data-ttu-id="63f03-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="63f03-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="63f03-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="63f03-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="63f03-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="63f03-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="63f03-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="63f03-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
