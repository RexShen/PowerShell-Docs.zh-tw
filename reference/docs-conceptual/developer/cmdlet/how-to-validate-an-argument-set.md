---
ms.date: 09/13/2016
ms.topic: reference
title: 如何驗證引數集
description: 如何驗證引數集
ms.openlocfilehash: 50ec0a48277893584d896e14ad6aa843682a28cc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650377"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="68be3-103">如何驗證引數集</span><span class="sxs-lookup"><span data-stu-id="68be3-103">How to Validate an Argument Set</span></span>

<span data-ttu-id="68be3-104">這個範例示範如何指定 Windows PowerShell 執行時間可在執行 Cmdlet 之前用來檢查參數引數的驗證規則。</span><span class="sxs-lookup"><span data-stu-id="68be3-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="68be3-105">這項驗證規則會為參數引數提供一組有效值。</span><span class="sxs-lookup"><span data-stu-id="68be3-105">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="68be3-106">如需定義這個屬性之類別的詳細資訊，請參閱 [Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)。</span><span class="sxs-lookup"><span data-stu-id="68be3-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="68be3-107">驗證引數集</span><span class="sxs-lookup"><span data-stu-id="68be3-107">To validate an argument set</span></span>

- <span data-ttu-id="68be3-108">加入 ValidateSet 屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="68be3-108">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="68be3-109">此範例會為參數指定三個可能值的集合 `UserName` 。</span><span class="sxs-lookup"><span data-stu-id="68be3-109">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

<span data-ttu-id="68be3-110">如需如何宣告這個屬性的詳細資訊，請參閱 [ValidateSet 屬性聲明](./validateset-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="68be3-110">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="68be3-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68be3-111">See Also</span></span>

[<span data-ttu-id="68be3-112">Validatesetattribute。</span><span class="sxs-lookup"><span data-stu-id="68be3-112">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="68be3-113">ValidateSet 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="68be3-113">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="68be3-114">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="68be3-114">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
