---
title: 如何驗證引數計數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateCount attribute, example
ms.assetid: 4e6b6ac4-1003-4e7e-9d4a-9f1cf74fc4af
caps.latest.revision: 8
ms.openlocfilehash: b6ddb8185f21a65b2e3142ebb640962047e11763
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067802"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="da5bc-102">如何驗證引數計數</span><span class="sxs-lookup"><span data-stu-id="da5bc-102">How to Validate an Argument Count</span></span>

<span data-ttu-id="da5bc-103">此範例示範如何指定驗證規則，Windows PowerShell 執行階段可用來檢查參數可接受的引數 （計數） 的數目在執行此指令程式之前。</span><span class="sxs-lookup"><span data-stu-id="da5bc-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="da5bc-104">您可以設定這項驗證規則宣告 ValidateCount 屬性。</span><span class="sxs-lookup"><span data-stu-id="da5bc-104">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="da5bc-105">如需有關定義這個屬性的類別的詳細資訊，請參閱[System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute)。</span><span class="sxs-lookup"><span data-stu-id="da5bc-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="da5bc-106">若要驗證的引數計數</span><span class="sxs-lookup"><span data-stu-id="da5bc-106">To validate an argument count</span></span>

- <span data-ttu-id="da5bc-107">下列程式碼所示，請新增驗證屬性。</span><span class="sxs-lookup"><span data-stu-id="da5bc-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="da5bc-108">這個範例會指定此參數會接受一個引數或最多可達三個引數。</span><span class="sxs-lookup"><span data-stu-id="da5bc-108">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

<span data-ttu-id="da5bc-109">如需如何宣告這個屬性的詳細資訊，請參閱[ValidateCount 屬性宣告](./validatecount-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="da5bc-109">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="da5bc-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da5bc-110">See Also</span></span>

[<span data-ttu-id="da5bc-111">ValidateCount 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="da5bc-111">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="da5bc-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="da5bc-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
