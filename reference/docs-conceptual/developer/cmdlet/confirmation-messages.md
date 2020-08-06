---
title: 確認訊息 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8f8192f6ed96b1eeb22e3b28ce1366eee8e7c16a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782186"
---
# <a name="confirmation-messages"></a><span data-ttu-id="d4063-102">確認訊息</span><span class="sxs-lookup"><span data-stu-id="d4063-102">Confirmation Messages</span></span>

<span data-ttu-id="d4063-103">以下是不同的確認訊息，可以根據所呼叫的[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的變體來顯示這些資訊，以供您看到。</span><span class="sxs-lookup"><span data-stu-id="d4063-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4063-104">如需說明如何要求確認的範例程式碼，請參閱[如何要求確認](./how-to-request-confirmations.md)。</span><span class="sxs-lookup"><span data-stu-id="d4063-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="d4063-105">指定資源</span><span class="sxs-lookup"><span data-stu-id="d4063-105">Specifying the Resource</span></span>

<span data-ttu-id="d4063-106">您可以藉由呼叫[Shouldprocess% 2a 來指定即將變更的資源，然後使用。Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0)方法。</span><span class="sxs-lookup"><span data-stu-id="d4063-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="d4063-107">在此情況下，您會使用方法的參數來提供資源 `target` ，而此作業是由 Windows PowerShell 新增。</span><span class="sxs-lookup"><span data-stu-id="d4063-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="d4063-108">在下列訊息中，"MyResource" 文字是要處理的資源，而作業則是進行呼叫的命令名稱。</span><span class="sxs-lookup"><span data-stu-id="d4063-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="d4063-109">如果使用者在確認要求中選取 **[是]** 或 **[全部皆是]** (如下列範例) 所示，則會呼叫[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，這會導致第二個確認訊息顯示。</span><span class="sxs-lookup"><span data-stu-id="d4063-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="d4063-110">指定作業和資源</span><span class="sxs-lookup"><span data-stu-id="d4063-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="d4063-111">您可以藉由呼叫[Shouldprocess% 2a？來指定即將變更的資源，以及命令即將執行的作業，以進行操作。Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0)方法。</span><span class="sxs-lookup"><span data-stu-id="d4063-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="d4063-112">在這種情況下，您可以使用參數和作業來提供資源， `target` 方法是使用 `target` 參數。</span><span class="sxs-lookup"><span data-stu-id="d4063-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="d4063-113">在下列訊息中，文字 "MyResource" 是所處理的資源，而 "MyAction" 是要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="d4063-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="d4063-114">如果使用者對先前的訊息選取 **[是]** 或 **[全部皆是]** ，就會呼叫[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，這會導致第二個確認訊息顯示。</span><span class="sxs-lookup"><span data-stu-id="d4063-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="d4063-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4063-115">See Also</span></span>

[<span data-ttu-id="d4063-116">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d4063-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
