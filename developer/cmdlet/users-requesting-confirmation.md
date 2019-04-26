---
title: 使用者要求確認 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067209"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="0ccec-102">使用者要求確認</span><span class="sxs-lookup"><span data-stu-id="0ccec-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="0ccec-103">當您指定的值`true`for `SupportsShouldProcess` Cmdlet 屬性宣告的參數，使用者可以指定`Confirm`參數在命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="0ccec-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="0ccec-104">在預設環境中，使用者可以指定`Confirm`參數或`"-Confirm:$true`，因此會要求確認時[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="0ccec-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="0ccec-105">這會略過[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)確認要求，甚至是具有強烈影響的作業。</span><span class="sxs-lookup"><span data-stu-id="0ccec-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="0ccec-106">如果`Confirm`未指定，則[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫要求您確認如果`$ConfirmPreference`喜好設定變數是等於或大於`ConfirmImpact`設定cmdlet 或提供者。</span><span class="sxs-lookup"><span data-stu-id="0ccec-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="0ccec-107">預設設定`$ConfirmPreference`是 「 高 」。</span><span class="sxs-lookup"><span data-stu-id="0ccec-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="0ccec-108">因此，在預設環境中，唯一的 cmdlet 和提供者，指定具有強烈影響動作要求確認。</span><span class="sxs-lookup"><span data-stu-id="0ccec-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="0ccec-109">如果`Confirm`為 false 或如果`"-Confirm:$false`指定，則[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫，不讓使用者要求確認和`$ConfirmPreference`殼層變數會被忽略。</span><span class="sxs-lookup"><span data-stu-id="0ccec-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="0ccec-110">備註</span><span class="sxs-lookup"><span data-stu-id="0ccec-110">Remarks</span></span>

- <span data-ttu-id="0ccec-111">Cmdlet 和指定的提供者`SupportsShouldProcess`，而非`ConfirmImpact`，做為 「 中度影響 」 動作，處理這些動作，而且預設不會提示他們。</span><span class="sxs-lookup"><span data-stu-id="0ccec-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="0ccec-112">其影響層級小於預設值`$ConfirmPreference`喜好設定變數。</span><span class="sxs-lookup"><span data-stu-id="0ccec-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="0ccec-113">如果使用者指定`Verbose`參數，系統會通知的作業即使它們不會提示進行確認。</span><span class="sxs-lookup"><span data-stu-id="0ccec-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ccec-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ccec-114">See Also</span></span>

[<span data-ttu-id="0ccec-115">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0ccec-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
