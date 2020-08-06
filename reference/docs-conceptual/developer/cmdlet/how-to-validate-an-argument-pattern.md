---
title: 如何驗證引數模式 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidatePattern attribute, example
ms.openlocfilehash: 35104e786d4b809a711d97fea52ae0e348dd5ca3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782084"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="fba11-102">如何驗證引數模式</span><span class="sxs-lookup"><span data-stu-id="fba11-102">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="fba11-103">這個範例示範如何指定驗證規則，讓 Windows PowerShell 執行時間在執行 Cmdlet 之前，用來檢查參數引數的字元模式。</span><span class="sxs-lookup"><span data-stu-id="fba11-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="fba11-104">您可以藉由宣告 ValidatePattern 屬性來設定此驗證規則。</span><span class="sxs-lookup"><span data-stu-id="fba11-104">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="fba11-105">如需定義此屬性之類別的詳細資訊，請參閱[Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)。</span><span class="sxs-lookup"><span data-stu-id="fba11-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="fba11-106">驗證引數模式</span><span class="sxs-lookup"><span data-stu-id="fba11-106">To validate an argument pattern</span></span>

- <span data-ttu-id="fba11-107">加入 Validate 屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="fba11-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="fba11-108">這個範例會指定四位數的模式，其中每個數位的值為0到9。</span><span class="sxs-lookup"><span data-stu-id="fba11-108">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

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

<span data-ttu-id="fba11-109">如需如何宣告這個屬性的詳細資訊，請參閱[ValidatePattern 屬性](./validatepattern-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="fba11-109">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fba11-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fba11-110">See Also</span></span>

[<span data-ttu-id="fba11-111">ValidatePattern 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="fba11-111">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="fba11-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fba11-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
