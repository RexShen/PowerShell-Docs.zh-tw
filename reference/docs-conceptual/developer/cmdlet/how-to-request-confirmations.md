---
ms.date: 09/13/2016
ms.topic: reference
title: 如何要求確認
description: 如何要求確認
ms.openlocfilehash: 3e29803407bd9fbf13e6db0d0a02239c34e9c4fa
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666989"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="59769-103">如何要求確認</span><span class="sxs-lookup"><span data-stu-id="59769-103">How to Request Confirmations</span></span>

<span data-ttu-id="59769-104">這個範例會示範如何呼叫 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 和 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法，在採取動作之前，要求使用者提出確認的方法，並在採取動作之前要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="59769-104">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59769-105">如需 Windows PowerShell 如何處理這些要求的詳細資訊，請參閱 [要求確認](./requesting-confirmation-from-cmdlets.md)。</span><span class="sxs-lookup"><span data-stu-id="59769-105">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="59769-106">要求確認</span><span class="sxs-lookup"><span data-stu-id="59769-106">To request confirmation</span></span>

1. <span data-ttu-id="59769-107">確定 `SupportsShouldProcess` Cmdlet 屬性的參數設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="59769-107">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="59769-108">函數的 (這是 CmdletBinding 屬性的參數。 ) </span><span class="sxs-lookup"><span data-stu-id="59769-108">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="59769-109">將 `Force` 參數新增至 Cmdlet，讓使用者可以覆寫確認要求。</span><span class="sxs-lookup"><span data-stu-id="59769-109">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="59769-110">加入 `if` 使用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法之傳回值的語句，以判斷是否已呼叫 ShouldContinue 方法，以判斷是否已呼叫[](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法。</span><span class="sxs-lookup"><span data-stu-id="59769-110">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="59769-111">新增第二個 `if` 語句，此語句會使用 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法的傳回值和參數的值， `Force` 以判斷是否應執行作業。</span><span class="sxs-lookup"><span data-stu-id="59769-111">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="59769-112">範例</span><span class="sxs-lookup"><span data-stu-id="59769-112">Example</span></span>

<span data-ttu-id="59769-113">在下列程式碼範例中， [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 和 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法是從 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法的覆寫中呼叫的方法所呼叫的程式碼中的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="59769-113">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="59769-114">不過，您也可以從其他輸入處理方法呼叫這些方法。</span><span class="sxs-lookup"><span data-stu-id="59769-114">However, you can also call these methods from the other input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="59769-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59769-115">See Also</span></span>

[<span data-ttu-id="59769-116">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="59769-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
