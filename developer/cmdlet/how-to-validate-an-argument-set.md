---
title: 如何驗證引數集 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861364"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="d2aeb-102">如何驗證引數集</span><span class="sxs-lookup"><span data-stu-id="d2aeb-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="d2aeb-103">此範例示範如何指定 Windows PowerShell 執行階段可用來執行此指令程式之前，請檢查參數引數的驗證規則。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="d2aeb-104">這項驗證規則參數引數提供一組有效的值。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="d2aeb-105">如需有關定義這個屬性的類別的詳細資訊，請參閱[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="d2aeb-106">若要驗證的引數設定</span><span class="sxs-lookup"><span data-stu-id="d2aeb-106">To validate an argument set</span></span>

- <span data-ttu-id="d2aeb-107">下列程式碼所示，請新增 ValidateSet 屬性。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="d2aeb-108">這個範例會指定三個可能值的一組`UserName`參數。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

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

<span data-ttu-id="d2aeb-109">如需如何宣告這個屬性的詳細資訊，請參閱[ValidateSet 屬性宣告](./validateset-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d2aeb-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2aeb-110">See Also</span></span>

[<span data-ttu-id="d2aeb-111">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="d2aeb-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="d2aeb-112">ValidateSet 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="d2aeb-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="d2aeb-113">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d2aeb-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
