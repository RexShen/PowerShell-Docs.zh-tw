---
title: Cmdlet 動態參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 19d31f6b619dff23e7e35bb53d2397f4f41eb728
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369877"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="f17b1-102">Cmdlet 動態參數</span><span class="sxs-lookup"><span data-stu-id="f17b1-102">Cmdlet dynamic parameters</span></span>

<span data-ttu-id="f17b1-103">Cmdlet 可以定義使用者在特殊條件下可用的參數，例如當另一個參數的引數為特定值時。</span><span class="sxs-lookup"><span data-stu-id="f17b1-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="f17b1-104">這些參數會在執行時間加入，並稱為動態參數，因為只有在需要時才會新增這些參數。</span><span class="sxs-lookup"><span data-stu-id="f17b1-104">These parameters are added at runtime and are referred to as dynamic parameters because they're only added when needed.</span></span> <span data-ttu-id="f17b1-105">例如，您可以設計一個 Cmdlet，只在指定了特定的切換參數時，才會新增數個參數。</span><span class="sxs-lookup"><span data-stu-id="f17b1-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="f17b1-106">提供者和 PowerShell 函數也可以定義動態參數。</span><span class="sxs-lookup"><span data-stu-id="f17b1-106">Providers and PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-powershell-cmdlets"></a><span data-ttu-id="f17b1-107">PowerShell Cmdlet 中的動態參數</span><span class="sxs-lookup"><span data-stu-id="f17b1-107">Dynamic parameters in PowerShell cmdlets</span></span>

<span data-ttu-id="f17b1-108">PowerShell 會在其多個提供者 Cmdlet 中使用動態參數。</span><span class="sxs-lookup"><span data-stu-id="f17b1-108">PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="f17b1-109">例如，當**Path**參數指定**憑證**提供者路徑時，`Get-Item` 和 `Get-ChildItem` Cmdlet 會在執行時間新增**CodeSigningCert**參數。</span><span class="sxs-lookup"><span data-stu-id="f17b1-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a **CodeSigningCert** parameter at runtime when the **Path** parameter specifies the **Certificate** provider path.</span></span> <span data-ttu-id="f17b1-110">如果**path**參數指定不同提供者的路徑，則無法使用**CodeSigningCert**參數。</span><span class="sxs-lookup"><span data-stu-id="f17b1-110">If the **Path** parameter specifies a path for a different provider, the **CodeSigningCert** parameter isn't available.</span></span>

<span data-ttu-id="f17b1-111">下列範例顯示在執行 `Get-Item` 時，如何在執行時間新增**CodeSigningCert**參數。</span><span class="sxs-lookup"><span data-stu-id="f17b1-111">The following examples show how the **CodeSigningCert** parameter is added at runtime when `Get-Item` is run.</span></span>

<span data-ttu-id="f17b1-112">在此範例中，PowerShell 執行時間已新增參數，且 Cmdlet 成功。</span><span class="sxs-lookup"><span data-stu-id="f17b1-112">In this example, the PowerShell runtime has added the parameter and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="f17b1-113">在此範例中，指定了**FileSystem**磁片磁碟機，並傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="f17b1-113">In this example, a **FileSystem** drive is specified and an error is returned.</span></span> <span data-ttu-id="f17b1-114">錯誤訊息指出找不到**CodeSigningCert**參數。</span><span class="sxs-lookup"><span data-stu-id="f17b1-114">The error message indicates that the **CodeSigningCert** parameter can't be found.</span></span>

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

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="f17b1-115">支援動態參數</span><span class="sxs-lookup"><span data-stu-id="f17b1-115">Support for dynamic parameters</span></span>

<span data-ttu-id="f17b1-116">若要支援動態參數，Cmdlet 程式碼中必須包含下列元素。</span><span class="sxs-lookup"><span data-stu-id="f17b1-116">To support dynamic parameters, the following elements must be included in the cmdlet code.</span></span>

### <a name="interface"></a><span data-ttu-id="f17b1-117">介面</span><span class="sxs-lookup"><span data-stu-id="f17b1-117">Interface</span></span>

<span data-ttu-id="f17b1-118">[IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters)。</span><span class="sxs-lookup"><span data-stu-id="f17b1-118">[System.Management.Automation.IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span></span>
<span data-ttu-id="f17b1-119">這個介面提供可抓取動態參數的方法。</span><span class="sxs-lookup"><span data-stu-id="f17b1-119">This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="f17b1-120">例如：</span><span class="sxs-lookup"><span data-stu-id="f17b1-120">For example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a><span data-ttu-id="f17b1-121">Method</span><span class="sxs-lookup"><span data-stu-id="f17b1-121">Method</span></span>

<span data-ttu-id="f17b1-122">[IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)。</span><span class="sxs-lookup"><span data-stu-id="f17b1-122">[System.Management.Automation.IDynamicParameters.GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span></span>
<span data-ttu-id="f17b1-123">這個方法會抓取包含動態參數定義的物件。</span><span class="sxs-lookup"><span data-stu-id="f17b1-123">This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="f17b1-124">例如：</span><span class="sxs-lookup"><span data-stu-id="f17b1-124">For example:</span></span>

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

### <a name="class"></a><span data-ttu-id="f17b1-125">類別</span><span class="sxs-lookup"><span data-stu-id="f17b1-125">Class</span></span>

<span data-ttu-id="f17b1-126">定義要加入之動態參數的類別。</span><span class="sxs-lookup"><span data-stu-id="f17b1-126">A class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="f17b1-127">此類別必須包含每個參數的**參數**屬性，以及 Cmdlet 所需的任何選擇性**別名**和**驗證**屬性。</span><span class="sxs-lookup"><span data-stu-id="f17b1-127">This class must include a **Parameter** attribute for each parameter and any optional **Alias** and **Validation** attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="f17b1-128">例如：</span><span class="sxs-lookup"><span data-stu-id="f17b1-128">For example:</span></span>

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

<span data-ttu-id="f17b1-129">如需支援動態參數之 Cmdlet 的完整範例，請參閱[如何宣告動態參數](./how-to-declare-dynamic-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="f17b1-129">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f17b1-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f17b1-130">See also</span></span>

[<span data-ttu-id="f17b1-131">IDynamicParameters。</span><span class="sxs-lookup"><span data-stu-id="f17b1-131">System.Management.Automation.IDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="f17b1-132">System.web. IDynamicParameters. GetDynamicParameters</span><span class="sxs-lookup"><span data-stu-id="f17b1-132">System.Management.Automation.IDynamicParameters.GetDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="f17b1-133">如何宣告動態參數</span><span class="sxs-lookup"><span data-stu-id="f17b1-133">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="f17b1-134">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f17b1-134">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
