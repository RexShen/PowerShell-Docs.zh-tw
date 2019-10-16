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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365507"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="f8199-102">如何驗證引數集</span><span class="sxs-lookup"><span data-stu-id="f8199-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="f8199-103">這個範例示範如何指定 Windows PowerShell 執行時間可用來檢查參數引數的驗證規則，然後再執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f8199-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="f8199-104">此驗證規則會為參數引數提供一組有效的值。</span><span class="sxs-lookup"><span data-stu-id="f8199-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="f8199-105">如需定義此屬性之類別的詳細資訊，請參閱[Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)。</span><span class="sxs-lookup"><span data-stu-id="f8199-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="f8199-106">驗證引數集</span><span class="sxs-lookup"><span data-stu-id="f8199-106">To validate an argument set</span></span>

- <span data-ttu-id="f8199-107">新增 ValidateSet 屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="f8199-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="f8199-108">這個範例會為 `UserName` 參數指定三個可能值的集合。</span><span class="sxs-lookup"><span data-stu-id="f8199-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

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

<span data-ttu-id="f8199-109">如需如何宣告這個屬性的詳細資訊，請參閱[ValidateSet 屬性](./validateset-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="f8199-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f8199-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8199-110">See Also</span></span>

[<span data-ttu-id="f8199-111">Validatesetattribute。</span><span class="sxs-lookup"><span data-stu-id="f8199-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="f8199-112">ValidateSet 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="f8199-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="f8199-113">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8199-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
