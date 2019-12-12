---
title: 如何要求確認 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369677"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="a2a51-102">如何要求確認</span><span class="sxs-lookup"><span data-stu-id="a2a51-102">How to Request Confirmations</span></span>

<span data-ttu-id="a2a51-103">這個範例會示範如何呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，以在採取動作之前向使用者要求確認的情況下，進行這種方式。</span><span class="sxs-lookup"><span data-stu-id="a2a51-103">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a2a51-104">如需 Windows PowerShell 如何處理這些要求的詳細資訊，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。</span><span class="sxs-lookup"><span data-stu-id="a2a51-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="a2a51-105">若要要求確認</span><span class="sxs-lookup"><span data-stu-id="a2a51-105">To request confirmation</span></span>

1. <span data-ttu-id="a2a51-106">請確定 Cmdlet 屬性的 `SupportsShouldProcess` 參數已設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a2a51-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="a2a51-107">（針對函式，這是 CmdletBinding 屬性的參數。）</span><span class="sxs-lookup"><span data-stu-id="a2a51-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="a2a51-108">將 `Force` 參數新增至您的 Cmdlet，讓使用者可以覆寫確認要求。</span><span class="sxs-lookup"><span data-stu-id="a2a51-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="a2a51-109">加入 `if` 語句，其會使用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法的傳回值，以判斷是否呼叫[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，以判斷是否已呼叫。</span><span class="sxs-lookup"><span data-stu-id="a2a51-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="a2a51-110">加入第二個 `if` 語句，它會使用[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的傳回值和 `Force` 參數的值，來判斷是否應該執行運算。</span><span class="sxs-lookup"><span data-stu-id="a2a51-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="a2a51-111">範例</span><span class="sxs-lookup"><span data-stu-id="a2a51-111">Example</span></span>

<span data-ttu-id="a2a51-112">在下列程式碼範例中，系統會從的覆寫 中呼叫 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 和 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法，以進行呼叫。[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的.。</span><span class="sxs-lookup"><span data-stu-id="a2a51-112">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="a2a51-113">不過，您也可以從其他輸入處理方法呼叫這些方法。</span><span class="sxs-lookup"><span data-stu-id="a2a51-113">However, you can also call these methods from the other input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="a2a51-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2a51-114">See Also</span></span>

[<span data-ttu-id="a2a51-115">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a2a51-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
