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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855064"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="f577b-102">如何驗證引數模式</span><span class="sxs-lookup"><span data-stu-id="f577b-102">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="f577b-103">此範例示範如何指定 Windows PowerShell 執行階段可用來執行此指令程式之前，請檢查參數引數之字元模式的驗證規則。</span><span class="sxs-lookup"><span data-stu-id="f577b-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="f577b-104">您可以設定這項驗證規則宣告 ValidatePattern 屬性。</span><span class="sxs-lookup"><span data-stu-id="f577b-104">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="f577b-105">如需有關定義這個屬性的類別的詳細資訊，請參閱[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)。</span><span class="sxs-lookup"><span data-stu-id="f577b-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="f577b-106">若要驗證的引數的模式</span><span class="sxs-lookup"><span data-stu-id="f577b-106">To validate an argument pattern</span></span>

- <span data-ttu-id="f577b-107">下列程式碼所示，請新增驗證屬性。</span><span class="sxs-lookup"><span data-stu-id="f577b-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="f577b-108">這個範例會指定四位數，其中每一個數字都有值為 0 到 9 的模式。</span><span class="sxs-lookup"><span data-stu-id="f577b-108">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

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

<span data-ttu-id="f577b-109">如需如何宣告這個屬性的詳細資訊，請參閱[ValidatePattern 屬性宣告](./validatepattern-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="f577b-109">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f577b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f577b-110">See Also</span></span>

[<span data-ttu-id="f577b-111">ValidatePattern 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="f577b-111">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="f577b-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f577b-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
