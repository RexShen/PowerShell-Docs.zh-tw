---
ms.date: 09/13/2016
ms.topic: reference
title: 如何驗證引數模式
description: 如何驗證引數模式
ms.openlocfilehash: ab5777c918a53c0a3900f87c52e7f14f9cb9b726
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666904"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="bb6a9-103">如何驗證引數模式</span><span class="sxs-lookup"><span data-stu-id="bb6a9-103">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="bb6a9-104">這個範例示範如何指定 Windows PowerShell 執行時間可在執行 Cmdlet 之前用來檢查參數引數字元模式的驗證規則。</span><span class="sxs-lookup"><span data-stu-id="bb6a9-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="bb6a9-105">您可以藉由宣告 ValidatePattern 屬性來設定此驗證規則。</span><span class="sxs-lookup"><span data-stu-id="bb6a9-105">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="bb6a9-106">如需定義這個屬性之類別的詳細資訊，請參閱 [Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)。</span><span class="sxs-lookup"><span data-stu-id="bb6a9-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="bb6a9-107">驗證引數模式</span><span class="sxs-lookup"><span data-stu-id="bb6a9-107">To validate an argument pattern</span></span>

- <span data-ttu-id="bb6a9-108">加入 Validate 屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="bb6a9-108">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="bb6a9-109">此範例會指定四位數的模式，其中每個數位的值為0到9。</span><span class="sxs-lookup"><span data-stu-id="bb6a9-109">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

<span data-ttu-id="bb6a9-110">如需如何宣告這個屬性的詳細資訊，請參閱 [ValidatePattern 屬性聲明](./validatepattern-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="bb6a9-110">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bb6a9-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb6a9-111">See Also</span></span>

[<span data-ttu-id="bb6a9-112">ValidatePattern 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="bb6a9-112">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="bb6a9-113">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bb6a9-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
