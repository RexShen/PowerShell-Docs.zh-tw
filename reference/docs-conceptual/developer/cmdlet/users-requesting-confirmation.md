---
ms.date: 09/13/2016
ms.topic: reference
title: 使用者要求確認
description: 使用者要求確認
ms.openlocfilehash: 58dbe27635ca38886b728f585fec063645b3597e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646313"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="00c4a-103">使用者要求確認</span><span class="sxs-lookup"><span data-stu-id="00c4a-103">Users Requesting Confirmation</span></span>

<span data-ttu-id="00c4a-104">當您針對 Cmdlet 屬性宣告的參數指定值時 `true` `SupportsShouldProcess` ，使用者可以 `Confirm` 在命令提示字元指定參數。</span><span class="sxs-lookup"><span data-stu-id="00c4a-104">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="00c4a-105">在預設環境中，使用者可以指定 `Confirm` 參數，或在 `"-Confirm:$true` 呼叫 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 方法時，要求您確認。</span><span class="sxs-lookup"><span data-stu-id="00c4a-105">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="00c4a-106">這會略過 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 確認要求，即使是對高影響的作業也是如此。</span><span class="sxs-lookup"><span data-stu-id="00c4a-106">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="00c4a-107">如果 `Confirm` 未指定，則 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 呼叫會在 `$ConfirmPreference` 喜好設定變數等於或大於 `ConfirmImpact` Cmdlet 或提供者的設定時，要求確認。</span><span class="sxs-lookup"><span data-stu-id="00c4a-107">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="00c4a-108">的預設設定 `$ConfirmPreference` 為 High。</span><span class="sxs-lookup"><span data-stu-id="00c4a-108">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="00c4a-109">因此，在預設環境中，只有指定高影響動作要求確認的 Cmdlet 和提供者。</span><span class="sxs-lookup"><span data-stu-id="00c4a-109">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="00c4a-110">如果 `Confirm` 為 false 或 `"-Confirm:$false` 已指定，則 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 呼叫會要求使用者確認，而且 `$ConfirmPreference` 會忽略 shell 變數的功能。</span><span class="sxs-lookup"><span data-stu-id="00c4a-110">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="00c4a-111">備註</span><span class="sxs-lookup"><span data-stu-id="00c4a-111">Remarks</span></span>

- <span data-ttu-id="00c4a-112">針對指定的 Cmdlet 和提供者（ `SupportsShouldProcess` 但不 `ConfirmImpact` 是），這些動作會被視為「影響」的動作，而且預設不會提示。</span><span class="sxs-lookup"><span data-stu-id="00c4a-112">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="00c4a-113">其影響層級小於喜好設定變數的預設設定 `$ConfirmPreference` 。</span><span class="sxs-lookup"><span data-stu-id="00c4a-113">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="00c4a-114">如果使用者指定 `Verbose` 參數，即使系統未提示您進行確認，這些參數也會收到操作的通知。</span><span class="sxs-lookup"><span data-stu-id="00c4a-114">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="00c4a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00c4a-115">See Also</span></span>

[<span data-ttu-id="00c4a-116">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="00c4a-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
