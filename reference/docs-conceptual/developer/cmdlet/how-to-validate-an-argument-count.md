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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365527"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="8aab1-102">如何驗證引數計數</span><span class="sxs-lookup"><span data-stu-id="8aab1-102">How to Validate an Argument Count</span></span>

<span data-ttu-id="8aab1-103">這個範例示範如何指定驗證規則，讓 Windows PowerShell 執行時間用來檢查參數在執行 Cmdlet 之前可接受的引數數目（計數）。</span><span class="sxs-lookup"><span data-stu-id="8aab1-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="8aab1-104">您可以藉由宣告 ValidateCount 屬性來設定此驗證規則。</span><span class="sxs-lookup"><span data-stu-id="8aab1-104">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="8aab1-105">如需定義此屬性之類別的詳細資訊，請參閱[Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute)。</span><span class="sxs-lookup"><span data-stu-id="8aab1-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="8aab1-106">驗證引數計數</span><span class="sxs-lookup"><span data-stu-id="8aab1-106">To validate an argument count</span></span>

- <span data-ttu-id="8aab1-107">加入 Validate 屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="8aab1-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="8aab1-108">這個範例會指定參數會接受一個引數，或最多三個引數。</span><span class="sxs-lookup"><span data-stu-id="8aab1-108">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

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

<span data-ttu-id="8aab1-109">如需如何宣告這個屬性的詳細資訊，請參閱[ValidateCount 屬性](./validatecount-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="8aab1-109">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8aab1-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8aab1-110">See Also</span></span>

[<span data-ttu-id="8aab1-111">ValidateCount 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="8aab1-111">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="8aab1-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8aab1-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
