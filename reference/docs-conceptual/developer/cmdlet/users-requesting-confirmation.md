---
title: 要求確認的使用者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369247"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="3d82c-102">使用者要求確認</span><span class="sxs-lookup"><span data-stu-id="3d82c-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="3d82c-103">當您為 Cmdlet 屬性宣告的 `SupportsShouldProcess` 參數指定 `true` 的值時，使用者可以在命令提示字元中指定 `Confirm` 參數。</span><span class="sxs-lookup"><span data-stu-id="3d82c-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="3d82c-104">在預設環境中，使用者可以指定 `Confirm` 參數或 `"-Confirm:$true`，以便在呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法時要求確認。</span><span class="sxs-lookup"><span data-stu-id="3d82c-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="3d82c-105">這會略過[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)確認要求，即使是對高影響力的作業也一樣。</span><span class="sxs-lookup"><span data-stu-id="3d82c-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="3d82c-106">如果未指定 `Confirm`，則[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫會在 `$ConfirmPreference` 喜好設定變數等於或大於 Cmdlet 或提供者的 `ConfirmImpact` 設定時要求確認。</span><span class="sxs-lookup"><span data-stu-id="3d82c-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="3d82c-107">`$ConfirmPreference` 的預設設定為 [高]。</span><span class="sxs-lookup"><span data-stu-id="3d82c-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="3d82c-108">因此，在預設環境中，只有指定高影響動作要求確認的 Cmdlet 和提供者。</span><span class="sxs-lookup"><span data-stu-id="3d82c-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="3d82c-109">如果 `Confirm` 為 false，或指定了 `"-Confirm:$false`，則[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫會向使用者要求確認，而 `$ConfirmPreference` shell 變數會被忽略。</span><span class="sxs-lookup"><span data-stu-id="3d82c-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="3d82c-110">備註</span><span class="sxs-lookup"><span data-stu-id="3d82c-110">Remarks</span></span>

- <span data-ttu-id="3d82c-111">對於指定 `SupportsShouldProcess`，但不 `ConfirmImpact`的 Cmdlet 和提供者，這些動作會當做「中度影響」動作來處理，而且預設不會提示。</span><span class="sxs-lookup"><span data-stu-id="3d82c-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="3d82c-112">其影響層級小於 `$ConfirmPreference` 喜好設定變數的預設值。</span><span class="sxs-lookup"><span data-stu-id="3d82c-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="3d82c-113">如果使用者指定 `Verbose` 參數，則即使系統不會提示您進行確認，它們也會收到操作的通知。</span><span class="sxs-lookup"><span data-stu-id="3d82c-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d82c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d82c-114">See Also</span></span>

[<span data-ttu-id="3d82c-115">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3d82c-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
