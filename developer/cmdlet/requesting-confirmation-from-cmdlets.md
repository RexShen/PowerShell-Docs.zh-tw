---
title: Cmdlet 從要求確認 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConfirmImpact [PowerShell Programmer's Guide], described
- ShouldContinue [PowerShell Programmer's Guide], described
- user feedback [PowerShell Programmer's Guide], requesting
- ShouldProcess [PowerShell Programmer's Guide], described
- ConfirmPreference [PowerShell Programmer's Guide], described
ms.assetid: 37d6e87f-57b7-40bd-b645-392cf0b6e88e
caps.latest.revision: 13
ms.openlocfilehash: 0c0517ef7fbd5ae6434773a2dfe276f3a8c35f39
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057396"
---
# <a name="requesting-confirmation-from-cmdlets"></a><span data-ttu-id="84b2c-102">從 Cmdlet 要求確認</span><span class="sxs-lookup"><span data-stu-id="84b2c-102">Requesting Confirmation from Cmdlets</span></span>

<span data-ttu-id="84b2c-103">他們即將進行之系統的 Windows PowerShell 環境以外變更時，Cmdlet 就應該要求確認。</span><span class="sxs-lookup"><span data-stu-id="84b2c-103">Cmdlets should request confirmation when they are about to make a change to the system that is outside of the Windows PowerShell environment.</span></span> <span data-ttu-id="84b2c-104">比方說，cmdlet 是否新增使用者帳戶，或停止的處理序，此 cmdlet 應該要求使用者確認之前它會繼續。</span><span class="sxs-lookup"><span data-stu-id="84b2c-104">For example, if a cmdlet is about to add a user account or stop a process, the cmdlet should require confirmation from the user before it proceeds.</span></span> <span data-ttu-id="84b2c-105">相較之下，如果 cmdlet 是將要變更的 Windows PowerShell 變數，此 cmdlet 不需要要求確認。</span><span class="sxs-lookup"><span data-stu-id="84b2c-105">In contrast, if a cmdlet is about to change a Windows PowerShell variable, the cmdlet does not need to require confirmation.</span></span>

<span data-ttu-id="84b2c-106">若要確認要求，它支援確認要求，且必須呼叫，必須指出此 cmdlet [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) （選擇性） 的方法，以顯示一則確認要求訊息。</span><span class="sxs-lookup"><span data-stu-id="84b2c-106">In order to make a confirmation request, the cmdlet must indicate that it supports confirmation requests, and it must call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (optional) methods to display a confirmation request message.</span></span>

## <a name="supporting-confirmation-requests"></a><span data-ttu-id="84b2c-107">確認要求的支援</span><span class="sxs-lookup"><span data-stu-id="84b2c-107">Supporting Confirmation Requests</span></span>

<span data-ttu-id="84b2c-108">若要支援確認要求，必須設定 cmdlet`SupportsShouldProcess`參數到 Cmdlet 屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="84b2c-108">To support confirmation requests, the cmdlet must set the `SupportsShouldProcess` parameter of the Cmdlet attribute to `true`.</span></span> <span data-ttu-id="84b2c-109">這可讓`Confirm`和`WhatIf`所提供的 Windows PowerShell 的 cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="84b2c-109">This enables the `Confirm` and `WhatIf` cmdlet parameters that are provided by Windows PowerShell.</span></span> <span data-ttu-id="84b2c-110">`Confirm`參數可讓使用者控制是否顯示確認要求。</span><span class="sxs-lookup"><span data-stu-id="84b2c-110">The `Confirm` parameter allows the user to control whether the confirmation request is displayed.</span></span> <span data-ttu-id="84b2c-111">`WhatIf`參數可讓使用者判斷 cmdlet 是否應該顯示一則訊息，或執行其動作。</span><span class="sxs-lookup"><span data-stu-id="84b2c-111">The `WhatIf` parameter allows the user to determine whether the cmdlet should display a message or perform its action.</span></span> <span data-ttu-id="84b2c-112">不要以手動方式新增`Confirm`和`WhatIf`cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="84b2c-112">Do not manually add the `Confirm` and `WhatIf` parameters to a cmdlet.</span></span>

<span data-ttu-id="84b2c-113">下列範例會示範支援確認要求 Cmdlet 屬性宣告。</span><span class="sxs-lookup"><span data-stu-id="84b2c-113">The following example shows a Cmdlet attribute declaration that supports confirmation requests.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a><span data-ttu-id="84b2c-114">呼叫確認要求方法</span><span class="sxs-lookup"><span data-stu-id="84b2c-114">Calling the Confirmation request methods</span></span>

<span data-ttu-id="84b2c-115">Cmdlet 程式碼中呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法之前執行變更系統的作業。</span><span class="sxs-lookup"><span data-stu-id="84b2c-115">In the cmdlet code, call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method before the operation that changes the system is performed.</span></span> <span data-ttu-id="84b2c-116">因此，如果在呼叫傳回的值，設計 cmdlet `false`、 未執行此作業，和 cmdlet 所處理的下一個作業。</span><span class="sxs-lookup"><span data-stu-id="84b2c-116">Design the cmdlet so that if the call returns a value of `false`, the operation is not performed, and the cmdlet processes the next operation.</span></span>

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="84b2c-117">呼叫 ShouldContinue 方法</span><span class="sxs-lookup"><span data-stu-id="84b2c-117">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="84b2c-118">大多數的 cmdlet 會要求確認只會使用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。</span><span class="sxs-lookup"><span data-stu-id="84b2c-118">Most cmdlets request confirmation using only the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="84b2c-119">不過，某些情況下可能需要再次確認。</span><span class="sxs-lookup"><span data-stu-id="84b2c-119">However, some cases might require additional confirmation.</span></span> <span data-ttu-id="84b2c-120">在這些情況下，補充[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫透過呼叫[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法。</span><span class="sxs-lookup"><span data-stu-id="84b2c-120">For these cases, supplement the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call with a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method.</span></span> <span data-ttu-id="84b2c-121">這可讓 cmdlet 或提供者，以更細微控制的領域**全部皆是**回應的確認提示。</span><span class="sxs-lookup"><span data-stu-id="84b2c-121">This allows the cmdlet or provider to more finely control the scope of the **Yes to all** response to the confirmation prompt.</span></span>

<span data-ttu-id="84b2c-122">如果指令程式會呼叫[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，此 cmdlet 也必須提供`Force`切換參數。</span><span class="sxs-lookup"><span data-stu-id="84b2c-122">If a cmdlet calls the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method, the cmdlet must also provide a `Force` switch parameter.</span></span> <span data-ttu-id="84b2c-123">如果使用者指定`Force`當使用者叫用此指令程式，仍應該呼叫此 cmdlet [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)，但它應該略過呼叫[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)。</span><span class="sxs-lookup"><span data-stu-id="84b2c-123">If the user specifies `Force` when the user invokes the cmdlet, the cmdlet should still call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), but it should bypass the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span>

<span data-ttu-id="84b2c-124">[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)呼叫不會提示使用者從非互動式環境時將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="84b2c-124">[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) will throw an exception when it is called from a non-interactive environment where the user cannot be prompted.</span></span> <span data-ttu-id="84b2c-125">新增`Force`參數可確保在非互動式環境中叫用時，仍然可以執行命令。</span><span class="sxs-lookup"><span data-stu-id="84b2c-125">Adding a `Force` parameter ensures that the command can still be performed when it is invoked in a non-interactive environment.</span></span>

<span data-ttu-id="84b2c-126">下列範例示範如何呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)並[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)。</span><span class="sxs-lookup"><span data-stu-id="84b2c-126">The following example shows how to call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span>

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

<span data-ttu-id="84b2c-127">行為[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫而異的指令程式會叫用的環境。</span><span class="sxs-lookup"><span data-stu-id="84b2c-127">The behavior of a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call can vary depending on the environment in which the cmdlet is invoked.</span></span> <span data-ttu-id="84b2c-128">使用先前的指導方針，可協助確保 cmdlet 與其他 cmdlet，不論主機環境以一致的方式運作。</span><span class="sxs-lookup"><span data-stu-id="84b2c-128">Using the previous guidelines will help ensure that the cmdlet behaves consistently with other cmdlets, regardless of the host environment.</span></span>

<span data-ttu-id="84b2c-129">如需呼叫的範例[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，請參閱[如何要求確認](./how-to-request-confirmations.md)。</span><span class="sxs-lookup"><span data-stu-id="84b2c-129">For an example of calling the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specify-the-impact-level"></a><span data-ttu-id="84b2c-130">指定影響層級</span><span class="sxs-lookup"><span data-stu-id="84b2c-130">Specify the Impact Level</span></span>

<span data-ttu-id="84b2c-131">當您建立 cmdlet 時，指定變更的影響等級 （嚴重性）。</span><span class="sxs-lookup"><span data-stu-id="84b2c-131">When you create the cmdlet, specify the impact level (the severity) of the change.</span></span> <span data-ttu-id="84b2c-132">若要這樣做，請將設定的值`ConfirmImpact`高、 中或低 Cmdlet 屬性的參數。</span><span class="sxs-lookup"><span data-stu-id="84b2c-132">To do this, set the value of the `ConfirmImpact` parameter of the Cmdlet attribute to High, Medium, or Low.</span></span> <span data-ttu-id="84b2c-133">您可以指定的值`ConfirmImpact`只有當您也指定`SupportsShouldProcess`cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="84b2c-133">You can specify a value for `ConfirmImpact` only when you also specify the `SupportsShouldProcess` parameter for the cmdlet.</span></span>

<span data-ttu-id="84b2c-134">對於大多數的 cmdlet，您不必明確指定`ConfirmImpact`。</span><span class="sxs-lookup"><span data-stu-id="84b2c-134">For most cmdlets, you do not have to explicitly specify `ConfirmImpact`.</span></span>  <span data-ttu-id="84b2c-135">相反地，使用預設設定的參數，這也是媒介。</span><span class="sxs-lookup"><span data-stu-id="84b2c-135">Instead, use the default setting of the parameter, which is Medium.</span></span> <span data-ttu-id="84b2c-136">如果您將設定`ConfirmImpact`為 [高]，作業將會確認預設。</span><span class="sxs-lookup"><span data-stu-id="84b2c-136">If you set `ConfirmImpact` to High, the operation will be confirmed by default.</span></span> <span data-ttu-id="84b2c-137">保留這項設定高度干擾性的動作，例如重新格式化硬碟磁碟區。</span><span class="sxs-lookup"><span data-stu-id="84b2c-137">Reserve this setting for highly disruptive actions, such as reformatting a hard-disk volume.</span></span>

## <a name="calling-non-confirmation-methods"></a><span data-ttu-id="84b2c-138">呼叫非確認方法</span><span class="sxs-lookup"><span data-stu-id="84b2c-138">Calling Non-Confirmation Methods</span></span>

<span data-ttu-id="84b2c-139">如果 cmdlet 或提供者必須將訊息傳送，但不是要求確認，它可以呼叫下列三種方法。</span><span class="sxs-lookup"><span data-stu-id="84b2c-139">If the cmdlet or provider must send a message but not request confirmation, it can call the following three methods.</span></span> <span data-ttu-id="84b2c-140">請避免使用[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法來傳送這些類型的訊息，因為[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)輸出會互相混合您的 cmdlet 或提供者的一般輸出，這會使得指令碼撰寫困難。</span><span class="sxs-lookup"><span data-stu-id="84b2c-140">Avoid using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method to send messages of these types because [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) output is intermingled with the normal output of your cmdlet or provider, which makes script writing difficult.</span></span>

- <span data-ttu-id="84b2c-141">若要想要提醒使用者，並繼續進行此作業，cmdlet 或提供者可以呼叫[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法。</span><span class="sxs-lookup"><span data-stu-id="84b2c-141">To caution the user and continue with the operation, the cmdlet or provider can call the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method.</span></span>

- <span data-ttu-id="84b2c-142">若要提供使用者可以使用擷取的其他資訊`Verbose`參數，cmdlet 或提供者可以呼叫[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法。</span><span class="sxs-lookup"><span data-stu-id="84b2c-142">To provide additional information that the user can retrieve using the `Verbose` parameter, the cmdlet or provider can call the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method.</span></span>

- <span data-ttu-id="84b2c-143">若要讓其他開發人員，或取得產品支援，請提供偵錯層級詳細資料，該 cmdlet 或提供者可以呼叫[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法。</span><span class="sxs-lookup"><span data-stu-id="84b2c-143">To provide debugging-level detail for other developers or for product support, the cmdlet or provider can call the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method.</span></span> <span data-ttu-id="84b2c-144">使用者可以使用此資訊來擷取`Debug`參數。</span><span class="sxs-lookup"><span data-stu-id="84b2c-144">The user can retrieve this information using the `Debug` parameter.</span></span>

<span data-ttu-id="84b2c-145">Cmdlet 與提供者先呼叫下列方法來要求確認，以免他們發動執行作業，以變更在 Windows PowerShell 之外的系統：</span><span class="sxs-lookup"><span data-stu-id="84b2c-145">Cmdlets and providers first call the following methods to request confirmation before they attempt to perform an operation that changes a system outside of Windows PowerShell:</span></span>

- [<span data-ttu-id="84b2c-146">System.Management.Automation.Cmdlet.Shouldprocess</span><span class="sxs-lookup"><span data-stu-id="84b2c-146">System.Management.Automation.Cmdlet.Shouldprocess</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [<span data-ttu-id="84b2c-147">System.Management.Automation.Provider.Cmdletprovider.Shouldprocess</span><span class="sxs-lookup"><span data-stu-id="84b2c-147">System.Management.Automation.Provider.Cmdletprovider.Shouldprocess</span></span>](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

<span data-ttu-id="84b2c-148">藉由呼叫會進行[System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，它會提示使用者確認是否要根據使用者如何叫用命令的作業。</span><span class="sxs-lookup"><span data-stu-id="84b2c-148">They do so by calling the [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method, which prompts the user to confirm the operation based on how the user invoked the command.</span></span>

## <a name="see-also"></a><span data-ttu-id="84b2c-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84b2c-149">See Also</span></span>

[<span data-ttu-id="84b2c-150">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="84b2c-150">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
