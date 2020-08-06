---
title: 正在從 Cmdlet 要求確認 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ConfirmImpact [PowerShell Programmer's Guide], described
- ShouldContinue [PowerShell Programmer's Guide], described
- user feedback [PowerShell Programmer's Guide], requesting
- ShouldProcess [PowerShell Programmer's Guide], described
- ConfirmPreference [PowerShell Programmer's Guide], described
ms.openlocfilehash: bcc4c766d0012e7173550e3b6cb3ef058baa06bb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781795"
---
# <a name="requesting-confirmation-from-cmdlets"></a><span data-ttu-id="a8382-102">從 Cmdlet 要求確認</span><span class="sxs-lookup"><span data-stu-id="a8382-102">Requesting Confirmation from Cmdlets</span></span>

<span data-ttu-id="a8382-103">當 Cmdlet 即將對 Windows PowerShell 環境以外的系統進行變更時，應要求確認。</span><span class="sxs-lookup"><span data-stu-id="a8382-103">Cmdlets should request confirmation when they are about to make a change to the system that is outside of the Windows PowerShell environment.</span></span> <span data-ttu-id="a8382-104">例如，如果 Cmdlet 即將新增使用者帳戶或停止進程，此 Cmdlet 應該會在繼續進行之前要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="a8382-104">For example, if a cmdlet is about to add a user account or stop a process, the cmdlet should require confirmation from the user before it proceeds.</span></span> <span data-ttu-id="a8382-105">相反地，如果 Cmdlet 即將變更 Windows PowerShell 變數，Cmdlet 就不需要確認。</span><span class="sxs-lookup"><span data-stu-id="a8382-105">In contrast, if a cmdlet is about to change a Windows PowerShell variable, the cmdlet does not need to require confirmation.</span></span>

<span data-ttu-id="a8382-106">若要提出確認要求，此 Cmdlet 必須指出它支援確認要求，而且必須呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (選擇性的) 方法來顯示確認要求訊息的方式，也就是如此。</span><span class="sxs-lookup"><span data-stu-id="a8382-106">In order to make a confirmation request, the cmdlet must indicate that it supports confirmation requests, and it must call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (optional) methods to display a confirmation request message.</span></span>

## <a name="supporting-confirmation-requests"></a><span data-ttu-id="a8382-107">支援確認要求</span><span class="sxs-lookup"><span data-stu-id="a8382-107">Supporting Confirmation Requests</span></span>

<span data-ttu-id="a8382-108">若要支援確認要求，Cmdlet 必須將 `SupportsShouldProcess` Cmdlet 屬性的參數設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="a8382-108">To support confirmation requests, the cmdlet must set the `SupportsShouldProcess` parameter of the Cmdlet attribute to `true`.</span></span> <span data-ttu-id="a8382-109">這會啟用 `Confirm` `WhatIf` Windows PowerShell 所提供的和 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="a8382-109">This enables the `Confirm` and `WhatIf` cmdlet parameters that are provided by Windows PowerShell.</span></span> <span data-ttu-id="a8382-110">`Confirm`參數可讓使用者控制是否顯示確認要求。</span><span class="sxs-lookup"><span data-stu-id="a8382-110">The `Confirm` parameter allows the user to control whether the confirmation request is displayed.</span></span> <span data-ttu-id="a8382-111">`WhatIf`參數可讓使用者判斷 Cmdlet 是否應該顯示訊息或執行其動作。</span><span class="sxs-lookup"><span data-stu-id="a8382-111">The `WhatIf` parameter allows the user to determine whether the cmdlet should display a message or perform its action.</span></span> <span data-ttu-id="a8382-112">請勿以手動方式將 `Confirm` 和 `WhatIf` 參數新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a8382-112">Do not manually add the `Confirm` and `WhatIf` parameters to a cmdlet.</span></span>

<span data-ttu-id="a8382-113">下列範例顯示支援確認要求的 Cmdlet 屬性宣告。</span><span class="sxs-lookup"><span data-stu-id="a8382-113">The following example shows a Cmdlet attribute declaration that supports confirmation requests.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a><span data-ttu-id="a8382-114">呼叫確認要求方法</span><span class="sxs-lookup"><span data-stu-id="a8382-114">Calling the Confirmation request methods</span></span>

<span data-ttu-id="a8382-115">在 Cmdlet 程式碼中，在執行變更系統的作業之前，呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。</span><span class="sxs-lookup"><span data-stu-id="a8382-115">In the cmdlet code, call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method before the operation that changes the system is performed.</span></span> <span data-ttu-id="a8382-116">設計 Cmdlet，如此一來，如果呼叫傳回的值為 `false` ，則不會執行此作業，且 Cmdlet 會處理下一個作業。</span><span class="sxs-lookup"><span data-stu-id="a8382-116">Design the cmdlet so that if the call returns a value of `false`, the operation is not performed, and the cmdlet processes the next operation.</span></span>

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="a8382-117">呼叫 ShouldContinue 方法</span><span class="sxs-lookup"><span data-stu-id="a8382-117">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="a8382-118">大部分的 Cmdlet 只會使用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法來要求確認。</span><span class="sxs-lookup"><span data-stu-id="a8382-118">Most cmdlets request confirmation using only the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="a8382-119">不過，某些情況下可能需要額外的確認。</span><span class="sxs-lookup"><span data-stu-id="a8382-119">However, some cases might require additional confirmation.</span></span> <span data-ttu-id="a8382-120">在這些情況下，請使用[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的呼叫，來補充 ShouldProcess 呼叫的相關[功能](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)，以進行。</span><span class="sxs-lookup"><span data-stu-id="a8382-120">For these cases, supplement the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call with a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method.</span></span> <span data-ttu-id="a8382-121">這可讓 Cmdlet 或提供者更精確地控制「是」對確認提示的**所有**回應範圍。</span><span class="sxs-lookup"><span data-stu-id="a8382-121">This allows the cmdlet or provider to more finely control the scope of the **Yes to all** response to the confirmation prompt.</span></span>

<span data-ttu-id="a8382-122">如果 Cmdlet 呼叫[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，此 Cmdlet 也必須提供 `Force` 切換參數（switch）。</span><span class="sxs-lookup"><span data-stu-id="a8382-122">If a cmdlet calls the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method, the cmdlet must also provide a `Force` switch parameter.</span></span> <span data-ttu-id="a8382-123">如果使用者指定 `Force` 使用者叫用 Cmdlet 的時間，Cmdlet 仍應呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)，但它應該會略過[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)的呼叫，而不應使用。</span><span class="sxs-lookup"><span data-stu-id="a8382-123">If the user specifies `Force` when the user invokes the cmdlet, the cmdlet should still call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), but it should bypass the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span>

<span data-ttu-id="a8382-124">[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)將會擲回例外狀況，因為它是從非互動式環境呼叫，而無法提示使用者。</span><span class="sxs-lookup"><span data-stu-id="a8382-124">[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) will throw an exception when it is called from a non-interactive environment where the user cannot be prompted.</span></span> <span data-ttu-id="a8382-125">新增 `Force` 參數可確保在非互動式環境中叫用該命令時，仍然可以執行此命令。</span><span class="sxs-lookup"><span data-stu-id="a8382-125">Adding a `Force` parameter ensures that the command can still be performed when it is invoked in a non-interactive environment.</span></span>

<span data-ttu-id="a8382-126">下列範例會示範如何呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)，以供您執行此動作的說明。</span><span class="sxs-lookup"><span data-stu-id="a8382-126">The following example shows how to call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span>

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

<span data-ttu-id="a8382-127">[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫的行為可能會因叫用 Cmdlet 的環境而異，而有所不同。</span><span class="sxs-lookup"><span data-stu-id="a8382-127">The behavior of a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call can vary depending on the environment in which the cmdlet is invoked.</span></span> <span data-ttu-id="a8382-128">使用先前的指導方針可協助確保 Cmdlet 與其他 Cmdlet 一致地運作，而不論主機環境為何。</span><span class="sxs-lookup"><span data-stu-id="a8382-128">Using the previous guidelines will help ensure that the cmdlet behaves consistently with other cmdlets, regardless of the host environment.</span></span>

<span data-ttu-id="a8382-129">如需呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法的範例，請參閱[如何要求確認](./how-to-request-confirmations.md)。</span><span class="sxs-lookup"><span data-stu-id="a8382-129">For an example of calling the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specify-the-impact-level"></a><span data-ttu-id="a8382-130">指定影響層級</span><span class="sxs-lookup"><span data-stu-id="a8382-130">Specify the Impact Level</span></span>

<span data-ttu-id="a8382-131">當您建立 Cmdlet 時，請指定變更 (嚴重性) 的影響層級。</span><span class="sxs-lookup"><span data-stu-id="a8382-131">When you create the cmdlet, specify the impact level (the severity) of the change.</span></span> <span data-ttu-id="a8382-132">若要這麼做，請將 `ConfirmImpact` Cmdlet 屬性的參數值設定為 [高]、[中] 或 [低]。</span><span class="sxs-lookup"><span data-stu-id="a8382-132">To do this, set the value of the `ConfirmImpact` parameter of the Cmdlet attribute to High, Medium, or Low.</span></span> <span data-ttu-id="a8382-133">`ConfirmImpact`只有當您同時指定 Cmdlet 的參數時，才可以指定的值 `SupportsShouldProcess` 。</span><span class="sxs-lookup"><span data-stu-id="a8382-133">You can specify a value for `ConfirmImpact` only when you also specify the `SupportsShouldProcess` parameter for the cmdlet.</span></span>

<span data-ttu-id="a8382-134">對於大部分的 Cmdlet，您不需要明確指定 `ConfirmImpact` 。</span><span class="sxs-lookup"><span data-stu-id="a8382-134">For most cmdlets, you do not have to explicitly specify `ConfirmImpact`.</span></span>  <span data-ttu-id="a8382-135">相反地，請使用參數的預設設定，也就是 Medium。</span><span class="sxs-lookup"><span data-stu-id="a8382-135">Instead, use the default setting of the parameter, which is Medium.</span></span> <span data-ttu-id="a8382-136">如果您將設定 `ConfirmImpact` 為 [高]，預設會確認作業。</span><span class="sxs-lookup"><span data-stu-id="a8382-136">If you set `ConfirmImpact` to High, the operation will be confirmed by default.</span></span> <span data-ttu-id="a8382-137">保留此設定以進行高度干擾性的動作，例如重新格式化硬碟磁片區。</span><span class="sxs-lookup"><span data-stu-id="a8382-137">Reserve this setting for highly disruptive actions, such as reformatting a hard-disk volume.</span></span>

## <a name="calling-non-confirmation-methods"></a><span data-ttu-id="a8382-138">呼叫非確認方法</span><span class="sxs-lookup"><span data-stu-id="a8382-138">Calling Non-Confirmation Methods</span></span>

<span data-ttu-id="a8382-139">如果 Cmdlet 或提供者必須傳送訊息但不要求確認，它可以呼叫下列三種方法。</span><span class="sxs-lookup"><span data-stu-id="a8382-139">If the cmdlet or provider must send a message but not request confirmation, it can call the following three methods.</span></span> <span data-ttu-id="a8382-140">請避免使用[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法來傳送這些類型的訊息，因為[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)輸出與 Cmdlet 或提供者的一般輸出混合在一起，使得腳本撰寫變得很棘手。</span><span class="sxs-lookup"><span data-stu-id="a8382-140">Avoid using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method to send messages of these types because [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) output is intermingled with the normal output of your cmdlet or provider, which makes script writing difficult.</span></span>

- <span data-ttu-id="a8382-141">為謹慎起見，此 Cmdlet 或提供者可以呼叫[WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法，並繼續操作。</span><span class="sxs-lookup"><span data-stu-id="a8382-141">To caution the user and continue with the operation, the cmdlet or provider can call the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method.</span></span>

- <span data-ttu-id="a8382-142">若要提供使用者可使用參數抓取的其他資訊 `Verbose` ，Cmdlet 或提供者可以呼叫[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法。</span><span class="sxs-lookup"><span data-stu-id="a8382-142">To provide additional information that the user can retrieve using the `Verbose` parameter, the cmdlet or provider can call the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method.</span></span>

- <span data-ttu-id="a8382-143">為了提供其他開發人員或產品支援的調試層級詳細資料，Cmdlet 或提供者可以呼叫[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法。</span><span class="sxs-lookup"><span data-stu-id="a8382-143">To provide debugging-level detail for other developers or for product support, the cmdlet or provider can call the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method.</span></span> <span data-ttu-id="a8382-144">使用者可以使用參數來捕獲此資訊 `Debug` 。</span><span class="sxs-lookup"><span data-stu-id="a8382-144">The user can retrieve this information using the `Debug` parameter.</span></span>

<span data-ttu-id="a8382-145">Cmdlet 和提供者會先呼叫下列方法來要求確認，然後才嘗試執行會變更 Windows PowerShell 外部系統的作業：</span><span class="sxs-lookup"><span data-stu-id="a8382-145">Cmdlets and providers first call the following methods to request confirmation before they attempt to perform an operation that changes a system outside of Windows PowerShell:</span></span>

- [<span data-ttu-id="a8382-146">Shouldprocess 的管理元件</span><span class="sxs-lookup"><span data-stu-id="a8382-146">System.Management.Automation.Cmdlet.Shouldprocess</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [<span data-ttu-id="a8382-147">提供者： Cmdletprovider. Shouldprocess</span><span class="sxs-lookup"><span data-stu-id="a8382-147">System.Management.Automation.Provider.Cmdletprovider.Shouldprocess</span></span>](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

<span data-ttu-id="a8382-148">他們會藉由呼叫[Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法來執行此動作，它會提示使用者根據使用者叫用命令的方式來確認操作。</span><span class="sxs-lookup"><span data-stu-id="a8382-148">They do so by calling the [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method, which prompts the user to confirm the operation based on how the user invoked the command.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8382-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8382-149">See Also</span></span>

[<span data-ttu-id="a8382-150">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a8382-150">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
