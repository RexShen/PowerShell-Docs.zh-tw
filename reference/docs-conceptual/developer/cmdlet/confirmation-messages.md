---
ms.date: 09/13/2016
ms.topic: reference
title: 確認訊息
description: 確認訊息
ms.openlocfilehash: 76302b2f8d8ca6dcdfe1b3c36f71aad23a53f7cf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355182"
---
# <a name="confirmation-messages"></a><span data-ttu-id="90c54-103">確認訊息</span><span class="sxs-lookup"><span data-stu-id="90c54-103">Confirmation Messages</span></span>

<span data-ttu-id="90c54-104">以下是不同的確認訊息，這些訊息會根據所呼叫的 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 和 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法的變異數而顯示出來，如下所示。</span><span class="sxs-lookup"><span data-stu-id="90c54-104">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="90c54-105">如需顯示如何要求確認的範例程式碼，請參閱 [如何要求確認](./how-to-request-confirmations.md)。</span><span class="sxs-lookup"><span data-stu-id="90c54-105">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="90c54-106">指定資源</span><span class="sxs-lookup"><span data-stu-id="90c54-106">Specifying the Resource</span></span>

<span data-ttu-id="90c54-107">您可以藉由呼叫 [Shouldprocess% 2a 來指定即將變更的資源，而不需要變更資源。Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 方法。</span><span class="sxs-lookup"><span data-stu-id="90c54-107">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="90c54-108">在此情況下，您會使用方法的參數來提供資源 `target` ，而作業會由 Windows PowerShell 加入。</span><span class="sxs-lookup"><span data-stu-id="90c54-108">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="90c54-109">在下列訊息中，文字 "MyResource" 是處理的資源，而作業則是發出呼叫的命令名稱。</span><span class="sxs-lookup"><span data-stu-id="90c54-109">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="90c54-110">如果使用者選取 [ **是]** 或 [ **全部]** 至確認要求 (如下列範例) 所示，則會呼叫 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法，這會導致第二個確認訊息顯示。</span><span class="sxs-lookup"><span data-stu-id="90c54-110">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="90c54-111">指定作業和資源</span><span class="sxs-lookup"><span data-stu-id="90c54-111">Specifying the Operation and Resource</span></span>

<span data-ttu-id="90c54-112">您可以藉由呼叫 Shouldprocess% 2A 來指定即將變更的資源，以及該命令即將執行的 [作業？（System。Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 方法。</span><span class="sxs-lookup"><span data-stu-id="90c54-112">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="90c54-113">在此情況下，您可以使用參數 `target` ，並使用參數來提供資源 `target` 。</span><span class="sxs-lookup"><span data-stu-id="90c54-113">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="90c54-114">在下列訊息中，文字 "MyResource" 是所採取的資源，而 "MyAction" 是要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="90c54-114">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="90c54-115">如果使用者選取 [ **是]** 或 [ **全部]** 至先前的訊息，則會呼叫 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法，這會導致第二個確認訊息顯示。</span><span class="sxs-lookup"><span data-stu-id="90c54-115">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="90c54-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90c54-116">See Also</span></span>

[<span data-ttu-id="90c54-117">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="90c54-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
