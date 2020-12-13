---
ms.date: 09/13/2016
ms.topic: reference
title: 如何驗證引數範圍
description: 如何驗證引數範圍
ms.openlocfilehash: 1c1c53d43350a38beb2193200de3bd6b689366a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666921"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="6113a-103">如何驗證引數範圍</span><span class="sxs-lookup"><span data-stu-id="6113a-103">How to Validate an Argument Range</span></span>

<span data-ttu-id="6113a-104">這個範例示範如何指定 Windows PowerShell 執行時間可在執行 Cmdlet 之前，用來檢查參數引數的最小值和最大值的驗證規則。</span><span class="sxs-lookup"><span data-stu-id="6113a-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="6113a-105">您可以藉由宣告 ValidateRange 屬性來設定此驗證規則。</span><span class="sxs-lookup"><span data-stu-id="6113a-105">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="6113a-106">如需定義這個屬性之類別的詳細資訊，請參閱 [Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)。</span><span class="sxs-lookup"><span data-stu-id="6113a-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="6113a-107">驗證引數範圍</span><span class="sxs-lookup"><span data-stu-id="6113a-107">To validate an argument range</span></span>

- <span data-ttu-id="6113a-108">加入 ValidateRange 屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="6113a-108">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="6113a-109">此範例指定參數的範圍為0到 5 `InputData` 。</span><span class="sxs-lookup"><span data-stu-id="6113a-109">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

<span data-ttu-id="6113a-110">如需如何宣告這個屬性的詳細資訊，請參閱 [ValidateRange 屬性聲明](./validaterange-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="6113a-110">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6113a-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6113a-111">See Also</span></span>

[<span data-ttu-id="6113a-112">ValidateRange 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="6113a-112">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="6113a-113">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6113a-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
