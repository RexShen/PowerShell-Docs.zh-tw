---
title: 如何驗證引數長度 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, example
ms.assetid: d5ddaa6e-4904-46da-beb0-0295a8f38332
caps.latest.revision: 12
ms.openlocfilehash: 8a21675acd087df93f93c25952c78931255d60b3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857124"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="d4c6e-102">如何驗證引數長度</span><span class="sxs-lookup"><span data-stu-id="d4c6e-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="d4c6e-103">此範例示範如何指定驗證規則，Windows PowerShell 執行階段可用來執行此指令程式之前檢查的字元 （長度） 的參數引數數目。</span><span class="sxs-lookup"><span data-stu-id="d4c6e-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="d4c6e-104">您可以設定這項驗證規則宣告 ValidateLength 屬性。</span><span class="sxs-lookup"><span data-stu-id="d4c6e-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="d4c6e-105">如需有關定義這個屬性的類別的詳細資訊，請參閱[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)。</span><span class="sxs-lookup"><span data-stu-id="d4c6e-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="d4c6e-106">若要驗證的引數長度</span><span class="sxs-lookup"><span data-stu-id="d4c6e-106">To validate the argument length</span></span>

- <span data-ttu-id="d4c6e-107">下列程式碼所示，請新增驗證屬性。</span><span class="sxs-lookup"><span data-stu-id="d4c6e-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="d4c6e-108">此範例中指定的引數的長度應該有 0 到 10 個字元的長度。</span><span class="sxs-lookup"><span data-stu-id="d4c6e-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

    ```csharp
    [ValidateLength(0, 10)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="d4c6e-109">如需如何宣告這個屬性的詳細資訊，請參閱[ValidateLength 屬性宣告](./validatelength-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="d4c6e-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d4c6e-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4c6e-110">See Also</span></span>

[<span data-ttu-id="d4c6e-111">ValidateLength 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="d4c6e-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="d4c6e-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d4c6e-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
