---
ms.date: 09/13/2016
ms.topic: reference
title: 如何驗證引數計數
description: 如何驗證引數計數
ms.openlocfilehash: 46a32d61138fb50bceea98171f76749c9d96734d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666938"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="d0b33-103">如何驗證引數計數</span><span class="sxs-lookup"><span data-stu-id="d0b33-103">How to Validate an Argument Count</span></span>

<span data-ttu-id="d0b33-104">這個範例會示範如何指定 Windows PowerShell 執行時間可用來檢查在執行 Cmdlet 之前，參數所接受的引數數目 () 的驗證規則。</span><span class="sxs-lookup"><span data-stu-id="d0b33-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="d0b33-105">您可以藉由宣告 ValidateCount 屬性來設定此驗證規則。</span><span class="sxs-lookup"><span data-stu-id="d0b33-105">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="d0b33-106">如需定義這個屬性之類別的詳細資訊，請參閱 [Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute)。</span><span class="sxs-lookup"><span data-stu-id="d0b33-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="d0b33-107">驗證引數計數</span><span class="sxs-lookup"><span data-stu-id="d0b33-107">To validate an argument count</span></span>

- <span data-ttu-id="d0b33-108">加入 Validate 屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="d0b33-108">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="d0b33-109">此範例會指定參數會接受一個引數，或最多三個引數。</span><span class="sxs-lookup"><span data-stu-id="d0b33-109">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

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

<span data-ttu-id="d0b33-110">如需如何宣告這個屬性的詳細資訊，請參閱 [ValidateCount 屬性聲明](./validatecount-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="d0b33-110">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0b33-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0b33-111">See Also</span></span>

[<span data-ttu-id="d0b33-112">ValidateCount 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="d0b33-112">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="d0b33-113">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d0b33-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
