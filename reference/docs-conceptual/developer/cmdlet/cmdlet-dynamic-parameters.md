---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 動態參數
description: Cmdlet 動態參數
ms.openlocfilehash: b44dda2354e8b689e419c7bf4deefadfc4edcb07
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653433"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="d2293-103">Cmdlet 動態參數</span><span class="sxs-lookup"><span data-stu-id="d2293-103">Cmdlet dynamic parameters</span></span>

<span data-ttu-id="d2293-104">Cmdlet 可以定義特殊條件下使用者可用的參數，例如，當另一個參數的引數為特定值時。</span><span class="sxs-lookup"><span data-stu-id="d2293-104">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="d2293-105">這些參數會在執行時間加入，而且會被稱為動態參數，因為它們只會在需要時才新增。</span><span class="sxs-lookup"><span data-stu-id="d2293-105">These parameters are added at runtime and are referred to as dynamic parameters because they're only added when needed.</span></span> <span data-ttu-id="d2293-106">例如，您可以設計一個 Cmdlet，只在指定特定切換參數時，才會新增數個參數。</span><span class="sxs-lookup"><span data-stu-id="d2293-106">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="d2293-107">提供者和 PowerShell 函數也可以定義動態參數。</span><span class="sxs-lookup"><span data-stu-id="d2293-107">Providers and PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-powershell-cmdlets"></a><span data-ttu-id="d2293-108">PowerShell Cmdlet 中的動態參數</span><span class="sxs-lookup"><span data-stu-id="d2293-108">Dynamic parameters in PowerShell cmdlets</span></span>

<span data-ttu-id="d2293-109">PowerShell 在許多提供者 Cmdlet 中使用動態參數。</span><span class="sxs-lookup"><span data-stu-id="d2293-109">PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="d2293-110">例如， `Get-Item` `Get-ChildItem` 當 **Path** 參數指定 **憑證** 提供者路徑時，和 Cmdlet 會在執行時間新增 **CodeSigningCert** 參數。</span><span class="sxs-lookup"><span data-stu-id="d2293-110">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a **CodeSigningCert** parameter at runtime when the **Path** parameter specifies the **Certificate** provider path.</span></span> <span data-ttu-id="d2293-111">如果 **path** 參數指定不同提供者的路徑，則無法使用 **CodeSigningCert** 參數。</span><span class="sxs-lookup"><span data-stu-id="d2293-111">If the **Path** parameter specifies a path for a different provider, the **CodeSigningCert** parameter isn't available.</span></span>

<span data-ttu-id="d2293-112">下列範例示範如何在執行時，于執行時間加入 **CodeSigningCert** 參數 `Get-Item` 。</span><span class="sxs-lookup"><span data-stu-id="d2293-112">The following examples show how the **CodeSigningCert** parameter is added at runtime when `Get-Item` is run.</span></span>

<span data-ttu-id="d2293-113">在此範例中，PowerShell 執行時間已新增參數，且 Cmdlet 成功。</span><span class="sxs-lookup"><span data-stu-id="d2293-113">In this example, the PowerShell runtime has added the parameter and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="d2293-114">在此範例中，會指定 **FileSystem** 磁片磁碟機，並傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="d2293-114">In this example, a **FileSystem** drive is specified and an error is returned.</span></span> <span data-ttu-id="d2293-115">錯誤訊息指出找不到 **CodeSigningCert** 參數。</span><span class="sxs-lookup"><span data-stu-id="d2293-115">The error message indicates that the **CodeSigningCert** parameter can't be found.</span></span>

```powershell
Get-Item -Path C:\ -CodeSigningCert
```

```Output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="d2293-116">支援動態參數</span><span class="sxs-lookup"><span data-stu-id="d2293-116">Support for dynamic parameters</span></span>

<span data-ttu-id="d2293-117">若要支援動態參數，Cmdlet 程式碼中必須包含下列元素。</span><span class="sxs-lookup"><span data-stu-id="d2293-117">To support dynamic parameters, the following elements must be included in the cmdlet code.</span></span>

### <a name="interface"></a><span data-ttu-id="d2293-118">介面</span><span class="sxs-lookup"><span data-stu-id="d2293-118">Interface</span></span>

<span data-ttu-id="d2293-119">[IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters)的。</span><span class="sxs-lookup"><span data-stu-id="d2293-119">[System.Management.Automation.IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span></span>
<span data-ttu-id="d2293-120">這個介面會提供可抓取動態參數的方法。</span><span class="sxs-lookup"><span data-stu-id="d2293-120">This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="d2293-121">例如：</span><span class="sxs-lookup"><span data-stu-id="d2293-121">For example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a><span data-ttu-id="d2293-122">方法</span><span class="sxs-lookup"><span data-stu-id="d2293-122">Method</span></span>

<span data-ttu-id="d2293-123">[IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)。</span><span class="sxs-lookup"><span data-stu-id="d2293-123">[System.Management.Automation.IDynamicParameters.GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span></span>
<span data-ttu-id="d2293-124">這個方法會抓取包含動態參數定義的物件。</span><span class="sxs-lookup"><span data-stu-id="d2293-124">This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="d2293-125">例如：</span><span class="sxs-lookup"><span data-stu-id="d2293-125">For example:</span></span>

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

### <a name="class"></a><span data-ttu-id="d2293-126">類別</span><span class="sxs-lookup"><span data-stu-id="d2293-126">Class</span></span>

<span data-ttu-id="d2293-127">定義要加入之動態參數的類別。</span><span class="sxs-lookup"><span data-stu-id="d2293-127">A class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="d2293-128">此類別必須包含每個參數的 **參數** 屬性，以及 Cmdlet 所需的任何選擇性 **別名** 和 **驗證** 屬性。</span><span class="sxs-lookup"><span data-stu-id="d2293-128">This class must include a **Parameter** attribute for each parameter and any optional **Alias** and **Validation** attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="d2293-129">例如：</span><span class="sxs-lookup"><span data-stu-id="d2293-129">For example:</span></span>

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

<span data-ttu-id="d2293-130">如需支援動態參數之 Cmdlet 的完整範例，請參閱 [如何宣告動態參數](./how-to-declare-dynamic-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="d2293-130">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d2293-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="d2293-131">See also</span></span>

[<span data-ttu-id="d2293-132">IDynamicParameters。</span><span class="sxs-lookup"><span data-stu-id="d2293-132">System.Management.Automation.IDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="d2293-133">IDynamicParameters. GetDynamicParameters。</span><span class="sxs-lookup"><span data-stu-id="d2293-133">System.Management.Automation.IDynamicParameters.GetDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="d2293-134">如何宣告動態參數</span><span class="sxs-lookup"><span data-stu-id="d2293-134">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="d2293-135">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d2293-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
