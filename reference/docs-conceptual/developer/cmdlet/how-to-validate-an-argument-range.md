---
title: 如何驗證引數範圍 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateRange attribute, example
ms.openlocfilehash: b48b1b87425add51e855c48ec700c78c3ae296c1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782067"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="6a9b2-102">如何驗證引數範圍</span><span class="sxs-lookup"><span data-stu-id="6a9b2-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="6a9b2-103">這個範例示範如何指定 Windows PowerShell 執行時間可用來檢查參數引數的最小和最大值，然後再執行 Cmdlet 的驗證規則。</span><span class="sxs-lookup"><span data-stu-id="6a9b2-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="6a9b2-104">您可以藉由宣告 ValidateRange 屬性來設定此驗證規則。</span><span class="sxs-lookup"><span data-stu-id="6a9b2-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="6a9b2-105">如需定義此屬性之類別的詳細資訊，請參閱[Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)。</span><span class="sxs-lookup"><span data-stu-id="6a9b2-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="6a9b2-106">驗證引數範圍</span><span class="sxs-lookup"><span data-stu-id="6a9b2-106">To validate an argument range</span></span>

- <span data-ttu-id="6a9b2-107">新增 ValidateRange 屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="6a9b2-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="6a9b2-108">這個範例會針對參數指定0到5的範圍 `InputData` 。</span><span class="sxs-lookup"><span data-stu-id="6a9b2-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

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

<span data-ttu-id="6a9b2-109">如需如何宣告這個屬性的詳細資訊，請參閱[ValidateRange 屬性](./validaterange-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="6a9b2-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6a9b2-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a9b2-110">See Also</span></span>

[<span data-ttu-id="6a9b2-111">ValidateRange 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="6a9b2-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="6a9b2-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6a9b2-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
