---
description: 描述指定屬性的函式如何 `CmdletBinding` 使用可用於已編譯 Cmdlet 的方法和屬性。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Methods
ms.openlocfilehash: 0da0efdacdf76fca590e338dce7d4f41dc9c5026
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206620"
---
# <a name="about-functions-advanced-methods"></a><span data-ttu-id="e0169-104">關於函數的 Advanced 方法</span><span class="sxs-lookup"><span data-stu-id="e0169-104">About Functions Advanced Methods</span></span>

## <a name="short-description"></a><span data-ttu-id="e0169-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="e0169-105">Short description</span></span>

<span data-ttu-id="e0169-106">描述指定屬性的函式如何 `CmdletBinding` 使用可用於已編譯 Cmdlet 的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="e0169-106">Describes how functions that specify the `CmdletBinding` attribute can use the methods and properties that are available to compiled cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="e0169-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="e0169-107">Long description</span></span>

<span data-ttu-id="e0169-108">指定屬性的函式 `CmdletBinding` 可以透過變數存取許多方法和屬性 `$PSCmdlet` 。</span><span class="sxs-lookup"><span data-stu-id="e0169-108">Functions that specify the `CmdletBinding` attribute can access a number of methods and properties through the `$PSCmdlet` variable.</span></span> <span data-ttu-id="e0169-109">這些方法包括下列方法：</span><span class="sxs-lookup"><span data-stu-id="e0169-109">These methods include the following methods:</span></span>

- <span data-ttu-id="e0169-110">編譯 Cmdlet 用來執行其工作的輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="e0169-110">Input-processing methods that compiled cmdlets use to do their work.</span></span>
- <span data-ttu-id="e0169-111">`ShouldProcess` `ShouldContinue` 用來在執行動作之前取得使用者意見反應的和方法。</span><span class="sxs-lookup"><span data-stu-id="e0169-111">The `ShouldProcess` and `ShouldContinue` methods that are used to get user feedback before an action is performed.</span></span>
- <span data-ttu-id="e0169-112">`ThrowTerminatingError`產生錯誤記錄的方法。</span><span class="sxs-lookup"><span data-stu-id="e0169-112">The `ThrowTerminatingError` method for generating error records.</span></span>
- <span data-ttu-id="e0169-113">傳回 `Write` 不同輸出類型的數個方法。</span><span class="sxs-lookup"><span data-stu-id="e0169-113">Several `Write` methods that return different types of output.</span></span>

<span data-ttu-id="e0169-114">**PSCmdlet** 類別的所有方法和屬性都可用於 advanced 函數。</span><span class="sxs-lookup"><span data-stu-id="e0169-114">All the methods and properties of the **PSCmdlet** class are available to advanced functions.</span></span> <span data-ttu-id="e0169-115">如需詳細資訊，請參閱 [PSCmdlet](/dotnet/api/system.management.automation.pscmdlet)。</span><span class="sxs-lookup"><span data-stu-id="e0169-115">For more information, see [System.Management.Automation.PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).</span></span>

<span data-ttu-id="e0169-116">如需屬性的詳細資訊 `CmdletBinding` ，請參閱 [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)。</span><span class="sxs-lookup"><span data-stu-id="e0169-116">For more information about the `CmdletBinding` attribute, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>
<span data-ttu-id="e0169-117">如需 **CmdletBindingAttribute** 類別，請參閱 [CmdletBindingAttribute](/dotnet/api/system.management.automation.cmdletbindingattribute)。</span><span class="sxs-lookup"><span data-stu-id="e0169-117">For the **CmdletBindingAttribute** class, see [System.Management.Automation.Cmdlet.CmdletBindingAttribute](/dotnet/api/system.management.automation.cmdletbindingattribute).</span></span>

### <a name="input-processing-methods"></a><span data-ttu-id="e0169-118">輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="e0169-118">Input processing methods</span></span>

<span data-ttu-id="e0169-119">本節所述的方法稱為輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="e0169-119">The methods described in this section are referred to as the input processing methods.</span></span> <span data-ttu-id="e0169-120">針對函式，這三種方法是由函式的 `Begin` 、 `Process` 和區塊所表示 `End` 。</span><span class="sxs-lookup"><span data-stu-id="e0169-120">For functions, these three methods are represented by the `Begin`, `Process`, and `End` blocks of the function.</span></span> <span data-ttu-id="e0169-121">您不需要在函式中使用任何這些區塊。</span><span class="sxs-lookup"><span data-stu-id="e0169-121">You aren't required to use any of these blocks in your functions.</span></span>

> [!NOTE]
> <span data-ttu-id="e0169-122">這些區塊也適用于未使用屬性的函式 `CmdletBinding` 。</span><span class="sxs-lookup"><span data-stu-id="e0169-122">These blocks are also available to functions that don't use the `CmdletBinding` attribute.</span></span>

#### <a name="begin"></a><span data-ttu-id="e0169-123">開始</span><span class="sxs-lookup"><span data-stu-id="e0169-123">Begin</span></span>

<span data-ttu-id="e0169-124">此區塊會用來為函式提供選擇性的一次性前置處理。</span><span class="sxs-lookup"><span data-stu-id="e0169-124">This block is used to provide optional one-time preprocessing for the function.</span></span>
<span data-ttu-id="e0169-125">PowerShell 執行時間會針對管線中的每個函式實例，使用這個區塊中的程式碼一次。</span><span class="sxs-lookup"><span data-stu-id="e0169-125">The PowerShell runtime uses the code in this block once for each instance of the function in the pipeline.</span></span>

#### <a name="process"></a><span data-ttu-id="e0169-126">程序</span><span class="sxs-lookup"><span data-stu-id="e0169-126">Process</span></span>

<span data-ttu-id="e0169-127">此區塊用來提供函數的記錄記錄處理。</span><span class="sxs-lookup"><span data-stu-id="e0169-127">This block is used to provide record-by-record processing for the function.</span></span> <span data-ttu-id="e0169-128">您可以使用 `Process` 區塊，而不需要定義其他區塊。</span><span class="sxs-lookup"><span data-stu-id="e0169-128">You can use a `Process` block without defining the other blocks.</span></span> <span data-ttu-id="e0169-129">`Process`區塊執行數目取決於您使用函式的方式，以及函式接收的輸入。</span><span class="sxs-lookup"><span data-stu-id="e0169-129">The number of `Process` block executions depends on how you use the function and what input the function receives.</span></span>

<span data-ttu-id="e0169-130">自動變數 `$_` 或 `$PSItem` 包含管線中的目前物件，以便在區塊中使用 `Process` 。</span><span class="sxs-lookup"><span data-stu-id="e0169-130">The automatic variable `$_` or `$PSItem` contains the current object in the pipeline for use in the `Process` block.</span></span> <span data-ttu-id="e0169-131">`$input`自動變數包含僅適用于函式和腳本區塊的列舉值。</span><span class="sxs-lookup"><span data-stu-id="e0169-131">The `$input` automatic variable contains an enumerator that's only available to functions and script blocks.</span></span>
<span data-ttu-id="e0169-132">如需詳細資訊，請參閱 [about_Automatic_Variables](about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="e0169-132">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

- <span data-ttu-id="e0169-133">在管線的開頭或外部呼叫函式，會執行 `Process` 一次區塊。</span><span class="sxs-lookup"><span data-stu-id="e0169-133">Calling the function at the beginning, or outside of a pipeline, executes the `Process` block once.</span></span>
- <span data-ttu-id="e0169-134">在管線中， `Process` 區塊會針對到達函式的每個輸入物件執行一次。</span><span class="sxs-lookup"><span data-stu-id="e0169-134">Within a pipeline, the `Process` block executes once for each input object that reaches the function.</span></span>
- <span data-ttu-id="e0169-135">如果到達函式的管線輸入是空的，則 `Process` **不會** 執行區塊。</span><span class="sxs-lookup"><span data-stu-id="e0169-135">If the pipeline input that reaches the function is empty, the `Process` block **does not** execute.</span></span>
  - <span data-ttu-id="e0169-136">`Begin`和 `End` 區塊仍會執行。</span><span class="sxs-lookup"><span data-stu-id="e0169-136">The `Begin` and `End` blocks still execute.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e0169-137">如果函式參數設定為接受管線輸入，而且 `Process` 未定義區塊，則依記錄處理的記錄將會失敗。</span><span class="sxs-lookup"><span data-stu-id="e0169-137">If a function parameter is set to accept pipeline input, and a `Process` block isn't defined, record-by-record processing will fail.</span></span> <span data-ttu-id="e0169-138">在此情況下，您的函式只會執行一次，不論輸入為何。</span><span class="sxs-lookup"><span data-stu-id="e0169-138">In this case, your function will only execute once, regardless of the input.</span></span>

#### <a name="end"></a><span data-ttu-id="e0169-139">結束</span><span class="sxs-lookup"><span data-stu-id="e0169-139">End</span></span>

<span data-ttu-id="e0169-140">此區塊會用來為函式提供選擇性的一次性後續處理。</span><span class="sxs-lookup"><span data-stu-id="e0169-140">This block is used to provide optional one-time post-processing for the function.</span></span>

<span data-ttu-id="e0169-141">下列範例會顯示函式的外框，其中包含一次性前置處理的 `Begin` 區塊、多筆 `Process` 記錄處理的區塊，以及 `End` 一次性後處理的區塊。</span><span class="sxs-lookup"><span data-stu-id="e0169-141">The following example shows the outline of a function that contains a `Begin` block for one-time preprocessing, a `Process` block for multiple record processing, and an `End` block for one-time post-processing.</span></span>

```powershell
Function Test-ScriptCmdlet
{
[CmdletBinding(SupportsShouldProcess=$True)]
    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

> [!NOTE]
> <span data-ttu-id="e0169-142">使用 `Begin` 或 `End` 區塊需要您定義全部三個區塊。</span><span class="sxs-lookup"><span data-stu-id="e0169-142">Using either a `Begin` or `End` block requires that you define all three blocks.</span></span> <span data-ttu-id="e0169-143">使用全部三個區塊時，所有的 PowerShell 程式碼都必須在其中一個區塊內。</span><span class="sxs-lookup"><span data-stu-id="e0169-143">When using all three blocks, all PowerShell code must be inside one of the blocks.</span></span>

### <a name="confirmation-methods"></a><span data-ttu-id="e0169-144">確認方法</span><span class="sxs-lookup"><span data-stu-id="e0169-144">Confirmation methods</span></span>

#### <a name="shouldprocess"></a><span data-ttu-id="e0169-145">ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="e0169-145">ShouldProcess</span></span>

<span data-ttu-id="e0169-146">在函式執行會變更系統的動作之前，會呼叫這個方法來要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="e0169-146">This method is called to request confirmation from the user before the function performs an action that would change the system.</span></span> <span data-ttu-id="e0169-147">函數可以根據方法所傳回的布林值繼續進行。</span><span class="sxs-lookup"><span data-stu-id="e0169-147">The function can continue based on the Boolean value returned by the method.</span></span> <span data-ttu-id="e0169-148">只有從函式的區塊內才能呼叫這個方法 `Process{}` 。</span><span class="sxs-lookup"><span data-stu-id="e0169-148">This method can only be called only from within the `Process{}` block of the function.</span></span> <span data-ttu-id="e0169-149">`CmdletBinding`屬性也必須宣告函數支援 `ShouldProcess` (，如先前的範例) 所示。</span><span class="sxs-lookup"><span data-stu-id="e0169-149">The `CmdletBinding` attribute must also declare that the function supports `ShouldProcess` (as shown in the previous example).</span></span>

<span data-ttu-id="e0169-150">如需此方法的詳細資訊，請參閱 [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess)。</span><span class="sxs-lookup"><span data-stu-id="e0169-150">For more information about this method, see [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess).</span></span>

<span data-ttu-id="e0169-151">如需如何要求確認的詳細資訊，請參閱 [要求確認](/powershell/scripting/developer/cmdlet/requesting-confirmation)。</span><span class="sxs-lookup"><span data-stu-id="e0169-151">For more information about how to request confirmation, see [Requesting Confirmation](/powershell/scripting/developer/cmdlet/requesting-confirmation).</span></span>

#### <a name="shouldcontinue"></a><span data-ttu-id="e0169-152">ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="e0169-152">ShouldContinue</span></span>

<span data-ttu-id="e0169-153">呼叫這個方法來要求第二次確認訊息。</span><span class="sxs-lookup"><span data-stu-id="e0169-153">This method is called to request a second confirmation message.</span></span> <span data-ttu-id="e0169-154">它應該在方法傳回時呼叫 `ShouldProcess` `$true` 。</span><span class="sxs-lookup"><span data-stu-id="e0169-154">It should be called when the `ShouldProcess` method returns `$true`.</span></span> <span data-ttu-id="e0169-155">如需此方法的詳細資訊，請參閱 [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue)。</span><span class="sxs-lookup"><span data-stu-id="e0169-155">For more information about this method, see [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue).</span></span>

### <a name="error-methods"></a><span data-ttu-id="e0169-156">Error 方法</span><span class="sxs-lookup"><span data-stu-id="e0169-156">Error methods</span></span>

<span data-ttu-id="e0169-157">函數可以在發生錯誤時呼叫兩種不同的方法。</span><span class="sxs-lookup"><span data-stu-id="e0169-157">Functions can call two different methods when errors occur.</span></span> <span data-ttu-id="e0169-158">當非終止錯誤發生時，函式應該呼叫 `WriteError` 方法，如方法一節中所述 `Write` 。</span><span class="sxs-lookup"><span data-stu-id="e0169-158">When a non-terminating error occurs, the function should call the `WriteError` method, which is described in the `Write` methods section.</span></span> <span data-ttu-id="e0169-159">當發生終止錯誤且函式無法繼續時，它應該呼叫 `ThrowTerminatingError` 方法。</span><span class="sxs-lookup"><span data-stu-id="e0169-159">When a terminating error occurs and the function can't continue, it should call the `ThrowTerminatingError` method.</span></span> <span data-ttu-id="e0169-160">您也可以使用 `Throw` 語句來終止錯誤，並使用非終止錯誤的 [寫入錯誤](xref:Microsoft.PowerShell.Utility.Write-Error) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e0169-160">You can also use the `Throw` statement for terminating errors and the [Write-Error](xref:Microsoft.PowerShell.Utility.Write-Error) cmdlet for non-terminating errors.</span></span>

<span data-ttu-id="e0169-161">如需詳細資訊，請參閱 [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror)。</span><span class="sxs-lookup"><span data-stu-id="e0169-161">For more information, see [System.Management.Automation.Cmdlet.ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror).</span></span>

### <a name="write-methods"></a><span data-ttu-id="e0169-162">Write 方法</span><span class="sxs-lookup"><span data-stu-id="e0169-162">Write methods</span></span>

<span data-ttu-id="e0169-163">函數可以呼叫下列方法，以傳回不同類型的輸出。</span><span class="sxs-lookup"><span data-stu-id="e0169-163">A function can call the following methods to return different types of output.</span></span>
<span data-ttu-id="e0169-164">請注意，並非所有輸出都會移至管線中的下一個命令。</span><span class="sxs-lookup"><span data-stu-id="e0169-164">Notice that not all the output goes to the next command in the pipeline.</span></span> <span data-ttu-id="e0169-165">您也可以使用各種 `Write` Cmdlet，例如 `Write-Error` 。</span><span class="sxs-lookup"><span data-stu-id="e0169-165">You can also use the various `Write` cmdlets, such as `Write-Error`.</span></span>

#### <a name="writecommanddetail"></a><span data-ttu-id="e0169-166">WriteCommandDetail</span><span class="sxs-lookup"><span data-stu-id="e0169-166">WriteCommandDetail</span></span>

<span data-ttu-id="e0169-167">如需方法的詳細資訊 `WriteCommandDetails` ，請參閱 [WriteCommandDetail](/dotnet/api/system.management.automation.cmdlet.writecommanddetail)。</span><span class="sxs-lookup"><span data-stu-id="e0169-167">For information about the `WriteCommandDetails` method, see [System.Management.Automation.Cmdlet.WriteCommandDetail](/dotnet/api/system.management.automation.cmdlet.writecommanddetail).</span></span>

#### <a name="writedebug"></a><span data-ttu-id="e0169-168">WriteDebug</span><span class="sxs-lookup"><span data-stu-id="e0169-168">WriteDebug</span></span>

<span data-ttu-id="e0169-169">若要提供可用來對函式進行疑難排解的資訊，請讓函數呼叫 `WriteDebug` 方法。</span><span class="sxs-lookup"><span data-stu-id="e0169-169">To provide information that can be used to troubleshoot a function, make the function call the `WriteDebug` method.</span></span> <span data-ttu-id="e0169-170">`WriteDebug`方法會向使用者顯示 debug 訊息。</span><span class="sxs-lookup"><span data-stu-id="e0169-170">The `WriteDebug` method displays debug messages to the user.</span></span> <span data-ttu-id="e0169-171">如需詳細資訊，請參閱 [WriteDebug](/dotnet/api/system.management.automation.cmdlet.writedebug)。</span><span class="sxs-lookup"><span data-stu-id="e0169-171">For more information, see [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/system.management.automation.cmdlet.writedebug).</span></span>

#### <a name="writeerror"></a><span data-ttu-id="e0169-172">WriteError</span><span class="sxs-lookup"><span data-stu-id="e0169-172">WriteError</span></span>

<span data-ttu-id="e0169-173">當非終止錯誤發生時，函式應該呼叫這個方法，而函式則是設計來繼續處理記錄。</span><span class="sxs-lookup"><span data-stu-id="e0169-173">Functions should call this method when non-terminating errors occur and the function is designed to continue processing records.</span></span> <span data-ttu-id="e0169-174">如需詳細資訊，請參閱 [WriteError](/dotnet/api/system.management.automation.cmdlet.writeerror)。</span><span class="sxs-lookup"><span data-stu-id="e0169-174">For more information, see [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/system.management.automation.cmdlet.writeerror).</span></span>

> [!NOTE]
> <span data-ttu-id="e0169-175">如果發生終止錯誤，函式應該呼叫 [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror) 方法。</span><span class="sxs-lookup"><span data-stu-id="e0169-175">If a terminating error occurs, the function should call the [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror) method.</span></span>

#### <a name="writeobject"></a><span data-ttu-id="e0169-176">WriteObject</span><span class="sxs-lookup"><span data-stu-id="e0169-176">WriteObject</span></span>

<span data-ttu-id="e0169-177">`WriteObject`方法可讓函數將物件傳送至管線中的下一個命令。</span><span class="sxs-lookup"><span data-stu-id="e0169-177">The `WriteObject` method allows the function to send an object to the next command in the pipeline.</span></span> <span data-ttu-id="e0169-178">在大部分情況下， `WriteObject` 是函數傳回資料時所要使用的方法。</span><span class="sxs-lookup"><span data-stu-id="e0169-178">In most cases, `WriteObject` is the method to use when the function returns data.</span></span> <span data-ttu-id="e0169-179">如需詳細資訊，請參閱 [PSCmdlet. WriteObject](/dotnet/api/system.management.automation.cmdlet.writeobject)。</span><span class="sxs-lookup"><span data-stu-id="e0169-179">For more information, see [System.Management.Automation.PSCmdlet.WriteObject](/dotnet/api/system.management.automation.cmdlet.writeobject).</span></span>

#### <a name="writeprogress"></a><span data-ttu-id="e0169-180">WriteProgress</span><span class="sxs-lookup"><span data-stu-id="e0169-180">WriteProgress</span></span>

<span data-ttu-id="e0169-181">對於具有需要很長時間才能完成之動作的函式，這個方法可讓函式呼叫 `WriteProgress` 方法，以顯示進度資訊。</span><span class="sxs-lookup"><span data-stu-id="e0169-181">For functions with actions that take a long time to complete, this method allows the function to call the `WriteProgress` method so that progress information is displayed.</span></span> <span data-ttu-id="e0169-182">例如，您可以顯示已完成的百分比。</span><span class="sxs-lookup"><span data-stu-id="e0169-182">For example, you can display the percent completed.</span></span>
<span data-ttu-id="e0169-183">如需詳細資訊，請參閱 [PSCmdlet. WriteProgress](/dotnet/api/system.management.automation.cmdlet.writeprogress)。</span><span class="sxs-lookup"><span data-stu-id="e0169-183">For more information, see [System.Management.Automation.PSCmdlet.WriteProgress](/dotnet/api/system.management.automation.cmdlet.writeprogress).</span></span>

#### <a name="writeverbose"></a><span data-ttu-id="e0169-184">WriteVerbose</span><span class="sxs-lookup"><span data-stu-id="e0169-184">WriteVerbose</span></span>

<span data-ttu-id="e0169-185">若要提供函式運作方式的詳細資訊，請讓函數呼叫 `WriteVerbose` 方法，以向使用者顯示詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="e0169-185">To provide detailed information about what the function is doing, make the function call the `WriteVerbose` method to display verbose messages to the user.</span></span> <span data-ttu-id="e0169-186">依預設不會顯示詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="e0169-186">By default, verbose messages aren't displayed.</span></span> <span data-ttu-id="e0169-187">如需詳細資訊，請參閱 [PSCmdlet. WriteVerbose](/dotnet/api/system.management.automation.cmdlet.writeverbose)。</span><span class="sxs-lookup"><span data-stu-id="e0169-187">For more information, see [System.Management.Automation.PSCmdlet.WriteVerbose](/dotnet/api/system.management.automation.cmdlet.writeverbose).</span></span>

#### <a name="writewarning"></a><span data-ttu-id="e0169-188">WriteWarning</span><span class="sxs-lookup"><span data-stu-id="e0169-188">WriteWarning</span></span>

<span data-ttu-id="e0169-189">若要提供可能導致非預期結果的狀況相關資訊，請將函數呼叫 WriteWarning 方法，以向使用者顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="e0169-189">To provide information about conditions that may cause unexpected results, make the function call the WriteWarning method to display warning messages to the user.</span></span> <span data-ttu-id="e0169-190">根據預設，會顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="e0169-190">By default, warning messages are displayed.</span></span> <span data-ttu-id="e0169-191">如需詳細資訊，請參閱 [PSCmdlet. WriteWarning](/dotnet/api/system.management.automation.cmdlet.writewarning)。</span><span class="sxs-lookup"><span data-stu-id="e0169-191">For more information, see [System.Management.Automation.PSCmdlet.WriteWarning](/dotnet/api/system.management.automation.cmdlet.writewarning).</span></span>

> [!NOTE]
> <span data-ttu-id="e0169-192">您也可以藉由設定 `$WarningPreference` 變數，或使用 `Verbose` 和 `Debug` 命令列選項來顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="e0169-192">You can also display warning messages by configuring the `$WarningPreference` variable or by using the `Verbose` and `Debug` command-line options.</span></span> <span data-ttu-id="e0169-193">如需變數的詳細資訊 `$WarningPreference` ，請參閱 [about_Preference_Variables](about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="e0169-193">for more information about the `$WarningPreference` variable, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

### <a name="other-methods-and-properties"></a><span data-ttu-id="e0169-194">其他方法和屬性</span><span class="sxs-lookup"><span data-stu-id="e0169-194">Other methods and properties</span></span>

<span data-ttu-id="e0169-195">如需可透過變數存取之其他方法和屬性的詳細資訊 `$PSCmdlet` ，請參閱 [PSCmdlet](/dotnet/api/system.management.automation.pscmdlet)。</span><span class="sxs-lookup"><span data-stu-id="e0169-195">For information about the other methods and properties that can be accessed through the `$PSCmdlet` variable, see [System.Management.Automation.PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).</span></span>

<span data-ttu-id="e0169-196">例如， [ParameterSetName](/dotnet/api/system.management.automation.pscmdlet.parametersetname) 屬性可讓您查看正在使用的參數集。</span><span class="sxs-lookup"><span data-stu-id="e0169-196">For example, the [ParameterSetName](/dotnet/api/system.management.automation.pscmdlet.parametersetname) property allows you to see the parameter set that is being used.</span></span> <span data-ttu-id="e0169-197">參數集可讓您建立一個函式，該函式會根據執行函數時所指定的參數來執行不同的工作。</span><span class="sxs-lookup"><span data-stu-id="e0169-197">Parameter sets allow you to create a function that performs different tasks based on the parameters that are specified when the function is run.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0169-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0169-198">See also</span></span>

[<span data-ttu-id="e0169-199">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="e0169-199">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="e0169-200">about_Functions</span><span class="sxs-lookup"><span data-stu-id="e0169-200">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="e0169-201">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="e0169-201">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="e0169-202">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="e0169-202">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="e0169-203">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="e0169-203">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="e0169-204">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="e0169-204">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="e0169-205">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="e0169-205">about_Preference_Variables</span></span>](about_Preference_Variables.md)
