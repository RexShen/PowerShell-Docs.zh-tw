---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: get pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: eb9f42ab4d9cec111e03a096b2f00740e97ee1b7
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2017
---
# <a name="get-pswaauthorizationrule"></a><span data-ttu-id="69db4-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="69db4-103">Get-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="69db4-104">概要</span><span class="sxs-lookup"><span data-stu-id="69db4-104">SYNOPSIS</span></span>

<span data-ttu-id="69db4-105">傳回一組 Windows PowerShell® Web 存取授權規則。</span><span class="sxs-lookup"><span data-stu-id="69db4-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

## <a name="syntax"></a><span data-ttu-id="69db4-106">語法</span><span class="sxs-lookup"><span data-stu-id="69db4-106">Syntax</span></span>

### <a name="id"></a><span data-ttu-id="69db4-107">ID</span><span class="sxs-lookup"><span data-stu-id="69db4-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a><span data-ttu-id="69db4-108">名稱</span><span class="sxs-lookup"><span data-stu-id="69db4-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="69db4-109">描述</span><span class="sxs-lookup"><span data-stu-id="69db4-109">DESCRIPTION</span></span>

<span data-ttu-id="69db4-110">**Get-PswaAuthorizationRule** Cmdlet 會傳回一組 Windows PowerShell® Web 存取授權規則。</span><span class="sxs-lookup"><span data-stu-id="69db4-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="69db4-111">如果未指定 **Id** 參數和 **RuleName** 參數，則此 Cmdlet 會列出所有規則。</span><span class="sxs-lookup"><span data-stu-id="69db4-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="69db4-112">**Id** 參數可用來篩選結果。</span><span class="sxs-lookup"><span data-stu-id="69db4-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="69db4-113">參數</span><span class="sxs-lookup"><span data-stu-id="69db4-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="69db4-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="69db4-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="69db4-115">指定此 Cmdlet 應該會取得之規則的識別碼。</span><span class="sxs-lookup"><span data-stu-id="69db4-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="69db4-116">如果未指定任何識別碼，此 Cmdlet 會傳回所有授權規則。</span><span class="sxs-lookup"><span data-stu-id="69db4-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="69db4-117">別名</span><span class="sxs-lookup"><span data-stu-id="69db4-117">Aliases</span></span>                              | <span data-ttu-id="69db4-118">無</span><span class="sxs-lookup"><span data-stu-id="69db4-118">none</span></span>                                 |
| <span data-ttu-id="69db4-119">必要？</span><span class="sxs-lookup"><span data-stu-id="69db4-119">Required?</span></span>                            | <span data-ttu-id="69db4-120">false</span><span class="sxs-lookup"><span data-stu-id="69db4-120">false</span></span>                                |
| <span data-ttu-id="69db4-121">位置？</span><span class="sxs-lookup"><span data-stu-id="69db4-121">Position?</span></span>                            | <span data-ttu-id="69db4-122">2</span><span class="sxs-lookup"><span data-stu-id="69db4-122">2</span></span>                                    |
| <span data-ttu-id="69db4-123">預設值</span><span class="sxs-lookup"><span data-stu-id="69db4-123">Default Value</span></span>                        | <span data-ttu-id="69db4-124">無</span><span class="sxs-lookup"><span data-stu-id="69db4-124">none</span></span>                                 |
| <span data-ttu-id="69db4-125">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="69db4-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="69db4-126">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="69db4-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="69db4-127">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="69db4-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="69db4-128">false</span><span class="sxs-lookup"><span data-stu-id="69db4-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="69db4-129">-RuleName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="69db4-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="69db4-130">指定要擷取之授權規則的名稱。</span><span class="sxs-lookup"><span data-stu-id="69db4-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="69db4-131">此參數會傳回完全符合此陣列中字串之規則名稱的任何規則。</span><span class="sxs-lookup"><span data-stu-id="69db4-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||  
|-|-|
| <span data-ttu-id="69db4-132">別名</span><span class="sxs-lookup"><span data-stu-id="69db4-132">Aliases</span></span>                              | <span data-ttu-id="69db4-133">無</span><span class="sxs-lookup"><span data-stu-id="69db4-133">none</span></span>                                 |
| <span data-ttu-id="69db4-134">必要？</span><span class="sxs-lookup"><span data-stu-id="69db4-134">Required?</span></span>                            | <span data-ttu-id="69db4-135">true</span><span class="sxs-lookup"><span data-stu-id="69db4-135">true</span></span>                                 |
| <span data-ttu-id="69db4-136">位置？</span><span class="sxs-lookup"><span data-stu-id="69db4-136">Position?</span></span>                            | <span data-ttu-id="69db4-137">2</span><span class="sxs-lookup"><span data-stu-id="69db4-137">2</span></span>                                    |
| <span data-ttu-id="69db4-138">預設值</span><span class="sxs-lookup"><span data-stu-id="69db4-138">Default Value</span></span>                        | <span data-ttu-id="69db4-139">無</span><span class="sxs-lookup"><span data-stu-id="69db4-139">none</span></span>                                 |
| <span data-ttu-id="69db4-140">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="69db4-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="69db4-141">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="69db4-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="69db4-142">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="69db4-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="69db4-143">false</span><span class="sxs-lookup"><span data-stu-id="69db4-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="69db4-144">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="69db4-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="69db4-145">這個 Cmdlet 支援一般參數：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。</span><span class="sxs-lookup"><span data-stu-id="69db4-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="69db4-146">如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="69db4-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="69db4-147">輸入</span><span class="sxs-lookup"><span data-stu-id="69db4-147">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="69db4-148">int\[\]</span><span class="sxs-lookup"><span data-stu-id="69db4-148">int\[\]</span></span>

<span data-ttu-id="69db4-149">此 Cmdlet 會接受整數陣列或字串值陣列作為輸入。</span><span class="sxs-lookup"><span data-stu-id="69db4-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

### <a name="string"></a><span data-ttu-id="69db4-150">String\[\]</span><span class="sxs-lookup"><span data-stu-id="69db4-150">String\[\]</span></span>

<span data-ttu-id="69db4-151">此 Cmdlet 會接受整數陣列或字串值陣列作為輸入。</span><span class="sxs-lookup"><span data-stu-id="69db4-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="69db4-152">輸出</span><span class="sxs-lookup"><span data-stu-id="69db4-152">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="69db4-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="69db4-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="69db4-154">此 Cmdlet 會產生 PswaAuthorizationRule 物件作為輸出。</span><span class="sxs-lookup"><span data-stu-id="69db4-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="69db4-155">範例</span><span class="sxs-lookup"><span data-stu-id="69db4-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="69db4-156">範例 1</span><span class="sxs-lookup"><span data-stu-id="69db4-156">EXAMPLE 1</span></span>

<span data-ttu-id="69db4-157">此範例會取得所有規則。</span><span class="sxs-lookup"><span data-stu-id="69db4-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="69db4-158">範例 2</span><span class="sxs-lookup"><span data-stu-id="69db4-158">EXAMPLE 2</span></span>

<span data-ttu-id="69db4-159">此範例會取得識別碼為 *2* 的規則。</span><span class="sxs-lookup"><span data-stu-id="69db4-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="69db4-160">範例 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="69db4-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="69db4-161">此範例示範該 Cmdlet 如何接受來自管線的值。</span><span class="sxs-lookup"><span data-stu-id="69db4-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="69db4-162">此 Cmdlet 會傳遞規則識別碼和規則名稱。</span><span class="sxs-lookup"><span data-stu-id="69db4-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a><span data-ttu-id="69db4-163">相關主題</span><span class="sxs-lookup"><span data-stu-id="69db4-163">Related topics</span></span>

- [<span data-ttu-id="69db4-164">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="69db4-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="69db4-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="69db4-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="69db4-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="69db4-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
- [<span data-ttu-id="69db4-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="69db4-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
