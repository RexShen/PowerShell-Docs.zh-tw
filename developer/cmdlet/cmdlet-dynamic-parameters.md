---
title: Cmdlet 的動態參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853804"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="e366f-102">Cmdlet 動態參數</span><span class="sxs-lookup"><span data-stu-id="e366f-102">Cmdlet Dynamic Parameters</span></span>

<span data-ttu-id="e366f-103">Cmdlet 可以定義參數，例如，當另一個參數的引數為特定值的特殊情況下，使用者可以使用。</span><span class="sxs-lookup"><span data-stu-id="e366f-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="e366f-104">這些參數會加入在執行階段，並稱為*動態參數*因為只在需要時才新增。</span><span class="sxs-lookup"><span data-stu-id="e366f-104">These parameters are added at runtime and are referred to as *dynamic parameters* because they are added only when they are needed.</span></span> <span data-ttu-id="e366f-105">比方說，您可以設計一個特定的切換參數指定時，才會將數個參數加入 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e366f-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="e366f-106">提供者和 Windows PowerShell 函式也可以定義的動態參數。</span><span class="sxs-lookup"><span data-stu-id="e366f-106">Providers and Windows PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a><span data-ttu-id="e366f-107">Windows PowerShell Cmdlet 中的動態參數</span><span class="sxs-lookup"><span data-stu-id="e366f-107">Dynamic Parameters in Windows PowerShell Cmdlets</span></span>

<span data-ttu-id="e366f-108">Windows PowerShell 會使用動態參數，在數個提供者 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e366f-108">Windows PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="e366f-109">例如，`Get-Item`並`Get-ChildItem`cmdlet 新增`CodeSigningCert`參數在執行階段時`Path`指令程式參數指定的憑證提供者路徑。</span><span class="sxs-lookup"><span data-stu-id="e366f-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a `CodeSigningCert` parameter at runtime when the `Path` parameter of the cmdlet specifies the Certificate provider path.</span></span> <span data-ttu-id="e366f-110">如果`Path`指令程式參數指定的路徑為不同的提供者，`CodeSigningCert`參數不是可用。</span><span class="sxs-lookup"><span data-stu-id="e366f-110">If the `Path` parameter of the cmdlet specifies a path for a different provider, the `CodeSigningCert` parameter is not available.</span></span>

<span data-ttu-id="e366f-111">下列範例會顯示如何`CodeSigningCert`參數會加入在執行階段時`Get-Item`執行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e366f-111">The following examples show how the `CodeSigningCert` parameter is added at runtime when the `Get-Item` cmdlet is run.</span></span>

<span data-ttu-id="e366f-112">在第一個範例中，Windows PowerShell 執行階段已新增參數，且此 cmdlet 成功。</span><span class="sxs-lookup"><span data-stu-id="e366f-112">In the first example, the Windows PowerShell runtime has added the parameter, and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="e366f-113">在第二個範例中，指定檔案系統磁碟機，而且會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="e366f-113">In the second example, a FileSystem drive is specified, and an error is returned.</span></span> <span data-ttu-id="e366f-114">錯誤訊息表示`CodeSigningCert`找不到參數。</span><span class="sxs-lookup"><span data-stu-id="e366f-114">The error message indicates that the `CodeSigningCert` parameter cannot be found.</span></span>

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="e366f-115">動態參數的支援</span><span class="sxs-lookup"><span data-stu-id="e366f-115">Support for Dynamic Parameters</span></span>

<span data-ttu-id="e366f-116">若要支援的動態參數，cmdlet 程式碼必須包含下列項目。</span><span class="sxs-lookup"><span data-stu-id="e366f-116">To support dynamic parameters, the cmdlet code must include the following elements.</span></span>

<span data-ttu-id="e366f-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)這個介面會提供擷取動態參數的方法。</span><span class="sxs-lookup"><span data-stu-id="e366f-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="e366f-118">範例：</span><span class="sxs-lookup"><span data-stu-id="e366f-118">Example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

<span data-ttu-id="e366f-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)這個方法會擷取包含的動態參數定義的物件。</span><span class="sxs-lookup"><span data-stu-id="e366f-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="e366f-120">範例：</span><span class="sxs-lookup"><span data-stu-id="e366f-120">Example:</span></span>

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

<span data-ttu-id="e366f-121">動態參數類別此類別會定義要加入的參數。</span><span class="sxs-lookup"><span data-stu-id="e366f-121">Dynamic Parameter class This class defines the parameters to be added.</span></span> <span data-ttu-id="e366f-122">這個類別必須包含每個參數以及此指令程式所需的任何選擇性別名和驗證屬性的參數屬性。</span><span class="sxs-lookup"><span data-stu-id="e366f-122">This class must include a Parameter attribute for each parameter and any optional Alias and Validation attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="e366f-123">範例：</span><span class="sxs-lookup"><span data-stu-id="e366f-123">Example:</span></span>

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

<span data-ttu-id="e366f-124">支援動態參數的 cmdlet 的完整範例，請參閱 <<c0> [ 宣告的動態參數如何](./how-to-declare-dynamic-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="e366f-124">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e366f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e366f-125">See Also</span></span>

[<span data-ttu-id="e366f-126">System.Management.Automation.Idynamicparameters</span><span class="sxs-lookup"><span data-stu-id="e366f-126">System.Management.Automation.Idynamicparameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="e366f-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="e366f-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="e366f-128">如何宣告動態參數</span><span class="sxs-lookup"><span data-stu-id="e366f-128">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="e366f-129">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e366f-129">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
