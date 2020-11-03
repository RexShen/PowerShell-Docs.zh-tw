---
description: 描述可讓函式運作的屬性，例如已編譯的 Cmdlet。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_CmdletBindingAttribute
ms.openlocfilehash: c4090910a72e2f68b5a710c76b20cc8af532c04b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207083"
---
# <a name="about-functions-cmdletbindingattribute"></a><span data-ttu-id="51120-104">關於函式 CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="51120-104">About Functions CmdletBindingAttribute</span></span>

## <a name="short-description"></a><span data-ttu-id="51120-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="51120-105">Short description</span></span>
<span data-ttu-id="51120-106">描述可讓函式運作的屬性，例如已編譯的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="51120-106">Describes the attribute that makes a function work like a compiled cmdlet.</span></span>

## <a name="long-description"></a><span data-ttu-id="51120-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="51120-107">Long description</span></span>

<span data-ttu-id="51120-108">`CmdletBinding`屬性是函式的屬性，可讓它們的運作方式就像以 c # 撰寫的編譯 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="51120-108">The `CmdletBinding` attribute is an attribute of functions that makes them operate like compiled cmdlets written in C#.</span></span> <span data-ttu-id="51120-109">它可讓您存取 Cmdlet 的功能。</span><span class="sxs-lookup"><span data-stu-id="51120-109">It provides access to the features of cmdlets.</span></span>

<span data-ttu-id="51120-110">PowerShell 會系結具有屬性之函式的參數，其方式與系結 `CmdletBinding` 已編譯 Cmdlet 的參數相同。</span><span class="sxs-lookup"><span data-stu-id="51120-110">PowerShell binds the parameters of functions that have the `CmdletBinding` attribute in the same way that it binds the parameters of compiled cmdlets.</span></span> <span data-ttu-id="51120-111">具有屬性的函式 `$PSCmdlet` 可使用自動變數 `CmdletBinding` ，但 `$Args` 變數無法使用。</span><span class="sxs-lookup"><span data-stu-id="51120-111">The `$PSCmdlet` automatic variable is available to functions with the `CmdletBinding` attribute, but the `$Args` variable is not available.</span></span>

<span data-ttu-id="51120-112">在具有屬性的函式中 `CmdletBinding` ，未知的參數和沒有相符位置參數的位置引數會導致參數系結失敗。</span><span class="sxs-lookup"><span data-stu-id="51120-112">In functions that have the `CmdletBinding` attribute, unknown parameters and positional arguments that have no matching positional parameters cause parameter binding to fail.</span></span>

> [!NOTE]
> <span data-ttu-id="51120-113">已編譯的 Cmdlet 會使用必要的 `Cmdlet` 屬性，其類似于 `CmdletBinding` 本主題中所述的屬性。</span><span class="sxs-lookup"><span data-stu-id="51120-113">Compiled cmdlets use the required `Cmdlet` attribute, which is similar to the `CmdletBinding` attribute that is described in this topic.</span></span>

## <a name="syntax"></a><span data-ttu-id="51120-114">Syntax</span><span class="sxs-lookup"><span data-stu-id="51120-114">Syntax</span></span>

<span data-ttu-id="51120-115">下列範例顯示指定屬性之所有選擇性引數的函數格式 `CmdletBinding` 。</span><span class="sxs-lookup"><span data-stu-id="51120-115">The following example shows the format of a function that specifies all the optional arguments of the `CmdletBinding` attribute.</span></span> <span data-ttu-id="51120-116">以下是每個引數的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="51120-116">A brief description of each argument follows this example.</span></span>

```powershell
{
    [CmdletBinding(ConfirmImpact=<String>,
    DefaultParameterSetName=<String>,
    HelpURI=<URI>,
    SupportsPaging=<Boolean>,
    SupportsShouldProcess=<Boolean>,
    PositionalBinding=<Boolean>)]

    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

## <a name="confirmimpact"></a><span data-ttu-id="51120-117">ConfirmImpact</span><span class="sxs-lookup"><span data-stu-id="51120-117">ConfirmImpact</span></span>

<span data-ttu-id="51120-118">**ConfirmImpact** 引數會指定何時應透過呼叫 **ShouldProcess** 方法來確認函式的動作。</span><span class="sxs-lookup"><span data-stu-id="51120-118">The **ConfirmImpact** argument specifies when the action of the function should be confirmed by a call to the **ShouldProcess** method.</span></span> <span data-ttu-id="51120-119">只有當 **ConfirmImpact** 引數等於或大於喜好設定變數的值時， **ShouldProcess** 方法的呼叫才會顯示確認提示 `$ConfirmPreference` 。</span><span class="sxs-lookup"><span data-stu-id="51120-119">The call to the **ShouldProcess** method displays a confirmation prompt only when the **ConfirmImpact** argument is equal to or greater than the value of the `$ConfirmPreference` preference variable.</span></span> <span data-ttu-id="51120-120"> (引數的預設值為 [ **中** ]。只有在同時指定 **SupportsShouldProcess** 引數時，才 ) 指定此引數。</span><span class="sxs-lookup"><span data-stu-id="51120-120">(The default value of the argument is **Medium** .) Specify this argument only when the **SupportsShouldProcess** argument is also specified.</span></span>

<span data-ttu-id="51120-121">如需確認要求的詳細資訊，請參閱 [要求確認](/powershell/scripting/developer/cmdlet/requesting-confirmation)。</span><span class="sxs-lookup"><span data-stu-id="51120-121">For more information about confirmation requests, see [Requesting Confirmation](/powershell/scripting/developer/cmdlet/requesting-confirmation).</span></span>

## <a name="defaultparametersetname"></a><span data-ttu-id="51120-122">DefaultParameterSetName</span><span class="sxs-lookup"><span data-stu-id="51120-122">DefaultParameterSetName</span></span>

<span data-ttu-id="51120-123">**DefaultParameterSetName** 引數會指定當 PowerShell 無法判斷要使用哪個參數集時，所要嘗試使用的參數集名稱。</span><span class="sxs-lookup"><span data-stu-id="51120-123">The **DefaultParameterSetName** argument specifies the name of the parameter set that PowerShell will attempt to use when it cannot determine which parameter set to use.</span></span> <span data-ttu-id="51120-124">您可以讓每個參數的 unique 參數設定必要參數，以避免這個問題。</span><span class="sxs-lookup"><span data-stu-id="51120-124">You can avoid this issue by making the unique parameter of each parameter set a mandatory parameter.</span></span>

## <a name="helpuri"></a><span data-ttu-id="51120-125">HelpURI</span><span class="sxs-lookup"><span data-stu-id="51120-125">HelpURI</span></span>

<span data-ttu-id="51120-126">**HelpURI** 引數會指定描述函式之說明主題的線上版本的網際網路位址。</span><span class="sxs-lookup"><span data-stu-id="51120-126">The **HelpURI** argument specifies the internet address of the online version of the help topic that describes the function.</span></span> <span data-ttu-id="51120-127">**HelpURI** 引數的值必須以 "HTTP" 或 "HTTPs" 開頭。</span><span class="sxs-lookup"><span data-stu-id="51120-127">The value of the **HelpURI** argument must begin with "http" or "https".</span></span>

<span data-ttu-id="51120-128">**HelpURI** 引數值會用於針對函式所傳回之 **CommandInfo** 物件的 **HelpURI** 屬性值 `Get-Command` 。</span><span class="sxs-lookup"><span data-stu-id="51120-128">The **HelpURI** argument value is used for the value of the **HelpURI** property of the **CommandInfo** object that `Get-Command` returns for the function.</span></span>

<span data-ttu-id="51120-129">不過，當說明檔安裝在電腦上，且說明檔的 **RelatedLinks** 區段中的第一個連結值為 uri，或批註式說明中第一個指示詞的值為 `.Link` uri 時，說明檔中的 uri 會用來做為函式之 **HelpUri** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="51120-129">However, when help files are installed on the computer and the value of the first link in the **RelatedLinks** section of the help file is a URI, or the value of the first `.Link` directive in comment-based help is a URI, the URI in the help file is used as the value of the **HelpUri** property of the function.</span></span>

<span data-ttu-id="51120-130">`Get-Help`當命令中指定的 **online** 參數時，此 Cmdlet 會使用 **HelpURI** 屬性的值來尋找線上版本的函數說明主題 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="51120-130">The `Get-Help` cmdlet uses the value of the **HelpURI** property to locate the online version of the function help topic when the **Online** parameter of `Get-Help` is specified in a command.</span></span>

## <a name="supportspaging"></a><span data-ttu-id="51120-131">SupportsPaging</span><span class="sxs-lookup"><span data-stu-id="51120-131">SupportsPaging</span></span>

<span data-ttu-id="51120-132">**SupportsPaging** 引數會將 **First** 、 **Skip** 和 **IncludeTotalCount** 參數新增至函式。</span><span class="sxs-lookup"><span data-stu-id="51120-132">The **SupportsPaging** argument adds the **First** , **Skip** , and **IncludeTotalCount** parameters to the function.</span></span> <span data-ttu-id="51120-133">這些參數可讓使用者從非常大的結果集選取輸出。</span><span class="sxs-lookup"><span data-stu-id="51120-133">These parameters allow users to select output from a very large result set.</span></span> <span data-ttu-id="51120-134">此引數是針對從支援資料選取的大型資料存放區（例如 SQL 資料庫）傳回資料的 Cmdlet 和函式所設計。</span><span class="sxs-lookup"><span data-stu-id="51120-134">This argument is designed for cmdlets and functions that return data from large data stores that support data selection, such as an SQL database.</span></span>

<span data-ttu-id="51120-135">此引數是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="51120-135">This argument was introduced in Windows PowerShell 3.0.</span></span>

- <span data-ttu-id="51120-136">**First** ：只取得第一個 ' n ' 物件。</span><span class="sxs-lookup"><span data-stu-id="51120-136">**First** : Gets only the first 'n' objects.</span></span>
- <span data-ttu-id="51120-137">**Skip** ：忽略第一個 ' n ' 物件，然後取得剩餘的物件。</span><span class="sxs-lookup"><span data-stu-id="51120-137">**Skip** :  Ignores the first 'n' objects and then gets the remaining objects.</span></span>
- <span data-ttu-id="51120-138">**IncludeTotalCount** ：報告資料集中的物件數目 (整數) 後面接著物件。</span><span class="sxs-lookup"><span data-stu-id="51120-138">**IncludeTotalCount** : Reports the number of objects in the data set (an integer) followed by the objects.</span></span> <span data-ttu-id="51120-139">如果 Cmdlet 無法判斷總計數，則會傳回「未知的總計數」。</span><span class="sxs-lookup"><span data-stu-id="51120-139">If the cmdlet cannot determine the total count, it returns "Unknown total count".</span></span>

<span data-ttu-id="51120-140">PowerShell 包含 **NewTotalCount** ，這是一個 helper 方法，可取得要傳回的總計數值，並包含總計計數值的精確度估計值。</span><span class="sxs-lookup"><span data-stu-id="51120-140">PowerShell includes **NewTotalCount** , a helper method that gets the total count value to return and includes an estimate of the accuracy of the total count value.</span></span>

<span data-ttu-id="51120-141">下列範例函式示範如何將分頁參數的支援新增至 advanced 函數。</span><span class="sxs-lookup"><span data-stu-id="51120-141">The following sample function shows how to add support for the paging parameters to an advanced function.</span></span>

```powershell
function Get-Numbers {
    [CmdletBinding(SupportsPaging = $true)]
    param()

    $FirstNumber = [Math]::Min($PSCmdlet.PagingParameters.Skip, 100)
    $LastNumber = [Math]::Min($PSCmdlet.PagingParameters.First +
      $FirstNumber - 1, 100)

    if ($PSCmdlet.PagingParameters.IncludeTotalCount) {
        $TotalCountAccuracy = 1.0
        $TotalCount = $PSCmdlet.PagingParameters.NewTotalCount(100,
          $TotalCountAccuracy)
        Write-Output $TotalCount
    }
    $FirstNumber .. $LastNumber | Write-Output
}
```

## <a name="supportsshouldprocess"></a><span data-ttu-id="51120-142">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="51120-142">SupportsShouldProcess</span></span>

<span data-ttu-id="51120-143">**SupportsShouldProcess** 引數會將 **Confirm** 和 **WhatIf** 參數新增至函式。</span><span class="sxs-lookup"><span data-stu-id="51120-143">The **SupportsShouldProcess** argument adds **Confirm** and **WhatIf** parameters to the function.</span></span> <span data-ttu-id="51120-144">**Confirm** 參數會先提示使用者，然後才在管線中的每個物件上執行命令。</span><span class="sxs-lookup"><span data-stu-id="51120-144">The **Confirm** parameter prompts the user before it runs the command on each object in the pipeline.</span></span> <span data-ttu-id="51120-145">**WhatIf** 參數會列出命令所做的變更，而不是執行命令。</span><span class="sxs-lookup"><span data-stu-id="51120-145">The **WhatIf** parameter lists the changes that the command would make, instead of running the command.</span></span>

## <a name="positionalbinding"></a><span data-ttu-id="51120-146">PositionalBinding</span><span class="sxs-lookup"><span data-stu-id="51120-146">PositionalBinding</span></span>

<span data-ttu-id="51120-147">**PositionalBinding** 引數會決定函式中的參數是否預設為位置。</span><span class="sxs-lookup"><span data-stu-id="51120-147">The **PositionalBinding** argument determines whether parameters in the function are positional by default.</span></span> <span data-ttu-id="51120-148">預設值是 `$True`。</span><span class="sxs-lookup"><span data-stu-id="51120-148">The default value is `$True`.</span></span> <span data-ttu-id="51120-149">您可以使用 **PositionalBinding** 引數搭配的值 `$False` 來停用位置系結。</span><span class="sxs-lookup"><span data-stu-id="51120-149">You can use the **PositionalBinding** argument with a value of `$False` to disable positional binding.</span></span>

<span data-ttu-id="51120-150">**PositionalBinding** 引數是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="51120-150">The **PositionalBinding** argument is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="51120-151">當參數是位置時，參數名稱為選擇性。</span><span class="sxs-lookup"><span data-stu-id="51120-151">When parameters are positional, the parameter name is optional.</span></span>
<span data-ttu-id="51120-152">PowerShell 會根據函數命令中未命名之參數值的順序或位置，將未命名的參數值與函式參數產生關聯。</span><span class="sxs-lookup"><span data-stu-id="51120-152">PowerShell associates unnamed parameter values with the function parameters according to the order or position of the unnamed parameter values in the function command.</span></span>

<span data-ttu-id="51120-153">當參數不是位置時 (它們是「命名」 ) ，參數名稱 (或名稱的縮寫或別名) 在命令中都是必要的。</span><span class="sxs-lookup"><span data-stu-id="51120-153">When parameters are not positional (they are "named"), the parameter name (or an abbreviation or alias of the name) is required in the command.</span></span>

<span data-ttu-id="51120-154">當 **PositionalBinding** 為時 `$True` ，函數參數預設為位置。</span><span class="sxs-lookup"><span data-stu-id="51120-154">When **PositionalBinding** is `$True`, function parameters are positional by default.</span></span> <span data-ttu-id="51120-155">PowerShell 會依照在函式中宣告的順序，將位置編號指派給參數。</span><span class="sxs-lookup"><span data-stu-id="51120-155">PowerShell assigns position number to the parameters in the order in which they are declared in the function.</span></span>

<span data-ttu-id="51120-156">當 **PositionalBinding** 為時，函式 `$False` 參數預設不是位置。</span><span class="sxs-lookup"><span data-stu-id="51120-156">When **PositionalBinding** is `$False`, function parameters are not positional by default.</span></span> <span data-ttu-id="51120-157">除非在參數上宣告 **parameter** 屬性的 **Position** 引數，否則在函式中使用參數時，必須包含參數名稱 (或別名或縮寫) 。</span><span class="sxs-lookup"><span data-stu-id="51120-157">Unless the **Position** argument of the **Parameter** attribute is declared on the parameter, the parameter name (or an alias or abbreviation) must be included when the parameter is used in a function.</span></span>

<span data-ttu-id="51120-158">**Parameter** 屬性的 **Position** 引數優先于 **PositionalBinding** 預設值。</span><span class="sxs-lookup"><span data-stu-id="51120-158">The **Position** argument of the **Parameter** attribute takes precedence over the **PositionalBinding** default value.</span></span> <span data-ttu-id="51120-159">您可以使用 **Position** 引數來指定參數的位置值。</span><span class="sxs-lookup"><span data-stu-id="51120-159">You can use the **Position** argument to specify a position value for a parameter.</span></span> <span data-ttu-id="51120-160">如需 **Position** 引數的詳細資訊，請參閱 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="51120-160">For more information about the **Position** argument, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

## <a name="notes"></a><span data-ttu-id="51120-161">備忘稿</span><span class="sxs-lookup"><span data-stu-id="51120-161">Notes</span></span>

<span data-ttu-id="51120-162">Advanced 函數中不支援 **SupportsTransactions** 引數。</span><span class="sxs-lookup"><span data-stu-id="51120-162">The **SupportsTransactions** argument is not supported in advanced functions.</span></span>

## <a name="keywords"></a><span data-ttu-id="51120-163">關鍵字</span><span class="sxs-lookup"><span data-stu-id="51120-163">Keywords</span></span>

<span data-ttu-id="51120-164">about_Functions_CmdletBinding_Attribute</span><span class="sxs-lookup"><span data-stu-id="51120-164">about_Functions_CmdletBinding_Attribute</span></span>

## <a name="see-also"></a><span data-ttu-id="51120-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51120-165">See also</span></span>

[<span data-ttu-id="51120-166">about_Functions</span><span class="sxs-lookup"><span data-stu-id="51120-166">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="51120-167">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="51120-167">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="51120-168">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="51120-168">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="51120-169">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="51120-169">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="51120-170">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="51120-170">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)
