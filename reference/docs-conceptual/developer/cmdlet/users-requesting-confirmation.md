---
title: 要求確認的使用者 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6f0effb35a110f33248a582fab874e3ab95c7df4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786334"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="e2a81-102">使用者要求確認</span><span class="sxs-lookup"><span data-stu-id="e2a81-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="e2a81-103">當您 `true` 針對 Cmdlet 屬性宣告的參數指定的值時 `SupportsShouldProcess` ，使用者可以 `Confirm` 在命令提示字元指定參數。</span><span class="sxs-lookup"><span data-stu-id="e2a81-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="e2a81-104">在預設的環境中，使用者可以指定 `Confirm` 參數，或在 `"-Confirm:$true` 呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法時要求該確認。</span><span class="sxs-lookup"><span data-stu-id="e2a81-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="e2a81-105">這會略過[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)確認要求，即使是對高影響力的作業也一樣。</span><span class="sxs-lookup"><span data-stu-id="e2a81-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="e2a81-106">如果 `Confirm` 未指定，則[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫 `$ConfirmPreference` 會在喜好設定變數等於或大於 `ConfirmImpact` Cmdlet 或提供者的設定時要求確認。</span><span class="sxs-lookup"><span data-stu-id="e2a81-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="e2a81-107">的預設設定 `$ConfirmPreference` 為 [高]。</span><span class="sxs-lookup"><span data-stu-id="e2a81-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="e2a81-108">因此，在預設環境中，只有指定高影響動作要求確認的 Cmdlet 和提供者。</span><span class="sxs-lookup"><span data-stu-id="e2a81-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="e2a81-109">如果 `Confirm` 為 false，或 `"-Confirm:$false` 指定了，則[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫會向使用者要求確認，並 `$ConfirmPreference` 忽略 shell 變數。</span><span class="sxs-lookup"><span data-stu-id="e2a81-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2a81-110">備註</span><span class="sxs-lookup"><span data-stu-id="e2a81-110">Remarks</span></span>

- <span data-ttu-id="e2a81-111">對於指定（但不是）的 Cmdlet 和提供者， `SupportsShouldProcess` `ConfirmImpact` 這些動作會當做「中度影響」動作來處理，而且預設不會提示。</span><span class="sxs-lookup"><span data-stu-id="e2a81-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="e2a81-112">其影響層級小於喜好設定變數的預設值 `$ConfirmPreference` 。</span><span class="sxs-lookup"><span data-stu-id="e2a81-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="e2a81-113">如果使用者指定參數，則會收到作業的 `Verbose` 通知，即使系統不會提示您進行確認。</span><span class="sxs-lookup"><span data-stu-id="e2a81-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2a81-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2a81-114">See Also</span></span>

[<span data-ttu-id="e2a81-115">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e2a81-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
