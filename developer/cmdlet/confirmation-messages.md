---
title: 確認訊息 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 75214a3fe4bc019836f75db19fb873bd081f200f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861414"
---
# <a name="confirmation-messages"></a><span data-ttu-id="693ff-102">確認訊息</span><span class="sxs-lookup"><span data-stu-id="693ff-102">Confirmation Messages</span></span>

<span data-ttu-id="693ff-103">以下是不同的確認訊息，可以顯示不同的變化[System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="693ff-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="693ff-104">示範如何要求確認的範例程式碼，請參閱[如何要求確認](./how-to-request-confirmations.md)。</span><span class="sxs-lookup"><span data-stu-id="693ff-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="693ff-105">指定資源</span><span class="sxs-lookup"><span data-stu-id="693ff-105">Specifying the Resource</span></span>

<span data-ttu-id="693ff-106">您可以指定的資源，藉由呼叫即將變更[System.Management.Automation.Cmdlet.Shouldprocess%2A 嗎？Displayproperty = Fullname>](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0)方法。</span><span class="sxs-lookup"><span data-stu-id="693ff-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="693ff-107">在此情況下，您提供資源使用`target`方法，以及作業的參數已加入 Windows powershell。</span><span class="sxs-lookup"><span data-stu-id="693ff-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="693ff-108">在下列的訊息中，「 MyResource 」 的文字是採取行動的資源，而且作業是發出呼叫的命令名稱。</span><span class="sxs-lookup"><span data-stu-id="693ff-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="693ff-109">如果使用者選取 **[是]** 或**全部**若要確認要求 （如所示在下列範例中），呼叫[System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法為止，這會導致要顯示的第二個確認訊息。</span><span class="sxs-lookup"><span data-stu-id="693ff-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="693ff-110">指定的作業和資源</span><span class="sxs-lookup"><span data-stu-id="693ff-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="693ff-111">您可以指定是即將變更的資源和作業的命令即將執行的呼叫[System.Management.Automation.Cmdlet.Shouldprocess%2A 嗎？Displayproperty = Fullname>](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0)方法。</span><span class="sxs-lookup"><span data-stu-id="693ff-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="693ff-112">在此情況下，您使用提供的資源時`target`參數和使用作業`target`參數。</span><span class="sxs-lookup"><span data-stu-id="693ff-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="693ff-113">在下列訊息: 「 MyResource 」 的文字是採取行動的資源，「 MyAction 」 是要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="693ff-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="693ff-114">如果使用者選取 **[是]** 或是**全部**至上一個訊息，也就是呼叫[System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法進行時，會造成第二個要顯示的確認訊息。</span><span class="sxs-lookup"><span data-stu-id="693ff-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="693ff-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="693ff-115">See Also</span></span>

[<span data-ttu-id="693ff-116">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="693ff-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
