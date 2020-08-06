---
title: 如何驗證引數集 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateSet attribute, example
ms.openlocfilehash: 6173f1380583f5b27e2b188990a5ea041f447c57
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781999"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="ad544-102">如何驗證引數集</span><span class="sxs-lookup"><span data-stu-id="ad544-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="ad544-103">這個範例示範如何指定 Windows PowerShell 執行時間可用來檢查參數引數的驗證規則，然後再執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ad544-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="ad544-104">此驗證規則會為參數引數提供一組有效的值。</span><span class="sxs-lookup"><span data-stu-id="ad544-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="ad544-105">如需定義此屬性之類別的詳細資訊，請參閱[Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)。</span><span class="sxs-lookup"><span data-stu-id="ad544-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="ad544-106">驗證引數集</span><span class="sxs-lookup"><span data-stu-id="ad544-106">To validate an argument set</span></span>

- <span data-ttu-id="ad544-107">新增 ValidateSet 屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ad544-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="ad544-108">這個範例會為參數指定三個可能值的集合 `UserName` 。</span><span class="sxs-lookup"><span data-stu-id="ad544-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

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

<span data-ttu-id="ad544-109">如需如何宣告這個屬性的詳細資訊，請參閱[ValidateSet 屬性](./validateset-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="ad544-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ad544-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad544-110">See Also</span></span>

[<span data-ttu-id="ad544-111">Validatesetattribute。</span><span class="sxs-lookup"><span data-stu-id="ad544-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="ad544-112">ValidateSet 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="ad544-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="ad544-113">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ad544-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
