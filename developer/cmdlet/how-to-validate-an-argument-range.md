---
title: 如何驗證引數範圍 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange attribute, example
ms.assetid: 3cba3ab7-c3b6-4d17-aa17-88377496551b
caps.latest.revision: 9
ms.openlocfilehash: a39e34d1f1c333185f09b4a934819e1368d29a48
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859734"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="5a8e0-102">如何驗證引數範圍</span><span class="sxs-lookup"><span data-stu-id="5a8e0-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="5a8e0-103">此範例示範如何指定驗證規則，Windows PowerShell 執行階段可以用來執行此指令程式之前，檢查參數引數的最小和最大值。</span><span class="sxs-lookup"><span data-stu-id="5a8e0-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="5a8e0-104">您可以設定這項驗證規則宣告 ValidateRange 屬性。</span><span class="sxs-lookup"><span data-stu-id="5a8e0-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="5a8e0-105">如需有關定義這個屬性的類別的詳細資訊，請參閱[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)。</span><span class="sxs-lookup"><span data-stu-id="5a8e0-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="5a8e0-106">若要驗證的引數範圍</span><span class="sxs-lookup"><span data-stu-id="5a8e0-106">To validate an argument range</span></span>

- <span data-ttu-id="5a8e0-107">下列程式碼所示，請新增 ValidateRange 屬性。</span><span class="sxs-lookup"><span data-stu-id="5a8e0-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="5a8e0-108">這個範例會指定 0 到 5 的各種`InputData`參數。</span><span class="sxs-lookup"><span data-stu-id="5a8e0-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

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

<span data-ttu-id="5a8e0-109">如需如何宣告這個屬性的詳細資訊，請參閱[ValidateRange 屬性宣告](./validaterange-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8e0-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5a8e0-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a8e0-110">See Also</span></span>

[<span data-ttu-id="5a8e0-111">ValidateRange 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="5a8e0-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="5a8e0-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5a8e0-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
