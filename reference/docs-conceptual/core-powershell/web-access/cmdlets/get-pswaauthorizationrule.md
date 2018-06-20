---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Get-PswaAuthorizationRule
ms.openlocfilehash: d61dce18e87311d7d815a689ba675db44aaec3cb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188903"
---
# <a name="get-pswaauthorizationrule"></a><span data-ttu-id="4243f-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4243f-103">Get-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="4243f-104">概要</span><span class="sxs-lookup"><span data-stu-id="4243f-104">SYNOPSIS</span></span>

<span data-ttu-id="4243f-105">傳回一組 Windows PowerShell® Web 存取授權規則。</span><span class="sxs-lookup"><span data-stu-id="4243f-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

## <a name="syntax"></a><span data-ttu-id="4243f-106">語法</span><span class="sxs-lookup"><span data-stu-id="4243f-106">Syntax</span></span>

### <a name="id"></a><span data-ttu-id="4243f-107">ID</span><span class="sxs-lookup"><span data-stu-id="4243f-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a><span data-ttu-id="4243f-108">名稱</span><span class="sxs-lookup"><span data-stu-id="4243f-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="4243f-109">描述</span><span class="sxs-lookup"><span data-stu-id="4243f-109">DESCRIPTION</span></span>

<span data-ttu-id="4243f-110">**Get-PswaAuthorizationRule** Cmdlet 會傳回一組 Windows PowerShell® Web 存取授權規則。</span><span class="sxs-lookup"><span data-stu-id="4243f-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="4243f-111">如果未指定 **Id** 參數和 **RuleName** 參數，則此 Cmdlet 會列出所有規則。</span><span class="sxs-lookup"><span data-stu-id="4243f-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="4243f-112">**Id** 參數可用來篩選結果。</span><span class="sxs-lookup"><span data-stu-id="4243f-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="4243f-113">參數</span><span class="sxs-lookup"><span data-stu-id="4243f-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="4243f-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="4243f-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="4243f-115">指定此 Cmdlet 應該會取得之規則的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4243f-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="4243f-116">如果未指定任何識別碼，此 Cmdlet 會傳回所有授權規則。</span><span class="sxs-lookup"><span data-stu-id="4243f-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="4243f-117">別名</span><span class="sxs-lookup"><span data-stu-id="4243f-117">Aliases</span></span>                              | <span data-ttu-id="4243f-118">無</span><span class="sxs-lookup"><span data-stu-id="4243f-118">none</span></span>                                 |
| <span data-ttu-id="4243f-119">必要？</span><span class="sxs-lookup"><span data-stu-id="4243f-119">Required?</span></span>                            | <span data-ttu-id="4243f-120">false</span><span class="sxs-lookup"><span data-stu-id="4243f-120">false</span></span>                                |
| <span data-ttu-id="4243f-121">位置？</span><span class="sxs-lookup"><span data-stu-id="4243f-121">Position?</span></span>                            | <span data-ttu-id="4243f-122">2</span><span class="sxs-lookup"><span data-stu-id="4243f-122">2</span></span>                                    |
| <span data-ttu-id="4243f-123">預設值</span><span class="sxs-lookup"><span data-stu-id="4243f-123">Default Value</span></span>                        | <span data-ttu-id="4243f-124">無</span><span class="sxs-lookup"><span data-stu-id="4243f-124">none</span></span>                                 |
| <span data-ttu-id="4243f-125">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="4243f-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4243f-126">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="4243f-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="4243f-127">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="4243f-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4243f-128">false</span><span class="sxs-lookup"><span data-stu-id="4243f-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="4243f-129">-RuleName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="4243f-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="4243f-130">指定要擷取之授權規則的名稱。</span><span class="sxs-lookup"><span data-stu-id="4243f-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="4243f-131">此參數會傳回完全符合此陣列中字串之規則名稱的任何規則。</span><span class="sxs-lookup"><span data-stu-id="4243f-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||
|-|-|
| <span data-ttu-id="4243f-132">別名</span><span class="sxs-lookup"><span data-stu-id="4243f-132">Aliases</span></span>                              | <span data-ttu-id="4243f-133">無</span><span class="sxs-lookup"><span data-stu-id="4243f-133">none</span></span>                                 |
| <span data-ttu-id="4243f-134">必要？</span><span class="sxs-lookup"><span data-stu-id="4243f-134">Required?</span></span>                            | <span data-ttu-id="4243f-135">true</span><span class="sxs-lookup"><span data-stu-id="4243f-135">true</span></span>                                 |
| <span data-ttu-id="4243f-136">位置？</span><span class="sxs-lookup"><span data-stu-id="4243f-136">Position?</span></span>                            | <span data-ttu-id="4243f-137">2</span><span class="sxs-lookup"><span data-stu-id="4243f-137">2</span></span>                                    |
| <span data-ttu-id="4243f-138">預設值</span><span class="sxs-lookup"><span data-stu-id="4243f-138">Default Value</span></span>                        | <span data-ttu-id="4243f-139">無</span><span class="sxs-lookup"><span data-stu-id="4243f-139">none</span></span>                                 |
| <span data-ttu-id="4243f-140">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="4243f-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4243f-141">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="4243f-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="4243f-142">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="4243f-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4243f-143">false</span><span class="sxs-lookup"><span data-stu-id="4243f-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="4243f-144">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="4243f-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="4243f-145">這個 Cmdlet 支援一般參數：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。</span><span class="sxs-lookup"><span data-stu-id="4243f-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="4243f-146">如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4243f-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="4243f-147">輸入</span><span class="sxs-lookup"><span data-stu-id="4243f-147">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="4243f-148">int\[\]</span><span class="sxs-lookup"><span data-stu-id="4243f-148">int\[\]</span></span>

<span data-ttu-id="4243f-149">此 Cmdlet 會接受整數陣列或字串值陣列作為輸入。</span><span class="sxs-lookup"><span data-stu-id="4243f-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

### <a name="string"></a><span data-ttu-id="4243f-150">String\[\]</span><span class="sxs-lookup"><span data-stu-id="4243f-150">String\[\]</span></span>

<span data-ttu-id="4243f-151">此 Cmdlet 會接受整數陣列或字串值陣列作為輸入。</span><span class="sxs-lookup"><span data-stu-id="4243f-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="4243f-152">輸出</span><span class="sxs-lookup"><span data-stu-id="4243f-152">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="4243f-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="4243f-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="4243f-154">此 Cmdlet 會產生 PswaAuthorizationRule 物件作為輸出。</span><span class="sxs-lookup"><span data-stu-id="4243f-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="4243f-155">範例</span><span class="sxs-lookup"><span data-stu-id="4243f-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="4243f-156">範例 1</span><span class="sxs-lookup"><span data-stu-id="4243f-156">EXAMPLE 1</span></span>

<span data-ttu-id="4243f-157">此範例會取得所有規則。</span><span class="sxs-lookup"><span data-stu-id="4243f-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="4243f-158">範例 2</span><span class="sxs-lookup"><span data-stu-id="4243f-158">EXAMPLE 2</span></span>

<span data-ttu-id="4243f-159">此範例會取得識別碼為 *2* 的規則。</span><span class="sxs-lookup"><span data-stu-id="4243f-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="4243f-160">範例 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="4243f-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="4243f-161">此範例示範該 Cmdlet 如何接受來自管線的值。</span><span class="sxs-lookup"><span data-stu-id="4243f-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="4243f-162">此 Cmdlet 會傳遞規則識別碼和規則名稱。</span><span class="sxs-lookup"><span data-stu-id="4243f-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a><span data-ttu-id="4243f-163">相關主題</span><span class="sxs-lookup"><span data-stu-id="4243f-163">Related topics</span></span>

- [<span data-ttu-id="4243f-164">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4243f-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="4243f-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4243f-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="4243f-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4243f-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
- [<span data-ttu-id="4243f-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="4243f-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)