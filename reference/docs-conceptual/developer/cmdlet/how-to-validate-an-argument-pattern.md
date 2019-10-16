---
title: 如何驗證引數模式 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidatePattern attribute, example
ms.assetid: 7ff76d4c-443a-4887-9ff8-241225f0aeec
caps.latest.revision: 9
ms.openlocfilehash: 5efc1210328c76e57a31d93b9eb52de114816c3c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365557"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="48e9f-102">如何驗證引數模式</span><span class="sxs-lookup"><span data-stu-id="48e9f-102">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="48e9f-103">這個範例示範如何指定驗證規則，讓 Windows PowerShell 執行時間在執行 Cmdlet 之前，用來檢查參數引數的字元模式。</span><span class="sxs-lookup"><span data-stu-id="48e9f-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="48e9f-104">您可以藉由宣告 ValidatePattern 屬性來設定此驗證規則。</span><span class="sxs-lookup"><span data-stu-id="48e9f-104">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="48e9f-105">如需定義此屬性之類別的詳細資訊，請參閱[Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)。</span><span class="sxs-lookup"><span data-stu-id="48e9f-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="48e9f-106">驗證引數模式</span><span class="sxs-lookup"><span data-stu-id="48e9f-106">To validate an argument pattern</span></span>

- <span data-ttu-id="48e9f-107">加入 Validate 屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="48e9f-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="48e9f-108">這個範例會指定四位數的模式，其中每個數位的值為0到9。</span><span class="sxs-lookup"><span data-stu-id="48e9f-108">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

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

<span data-ttu-id="48e9f-109">如需如何宣告這個屬性的詳細資訊，請參閱[ValidatePattern 屬性](./validatepattern-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="48e9f-109">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="48e9f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48e9f-110">See Also</span></span>

[<span data-ttu-id="48e9f-111">ValidatePattern 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="48e9f-111">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="48e9f-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="48e9f-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
