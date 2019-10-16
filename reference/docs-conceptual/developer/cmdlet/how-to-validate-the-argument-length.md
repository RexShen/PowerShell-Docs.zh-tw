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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365487"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="b4087-102">如何驗證引數長度</span><span class="sxs-lookup"><span data-stu-id="b4087-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="b4087-103">這個範例示範如何指定驗證規則，讓 Windows PowerShell 執行時間可以在執行 Cmdlet 之前，用來檢查參數引數的字元數（長度）。</span><span class="sxs-lookup"><span data-stu-id="b4087-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="b4087-104">您可以藉由宣告 ValidateLength 屬性來設定此驗證規則。</span><span class="sxs-lookup"><span data-stu-id="b4087-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="b4087-105">如需定義此屬性之類別的詳細資訊，請參閱[Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)。</span><span class="sxs-lookup"><span data-stu-id="b4087-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="b4087-106">驗證引數長度</span><span class="sxs-lookup"><span data-stu-id="b4087-106">To validate the argument length</span></span>

- <span data-ttu-id="b4087-107">加入 Validate 屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="b4087-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="b4087-108">這個範例會指定引數長度的長度應為0到10個字元。</span><span class="sxs-lookup"><span data-stu-id="b4087-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

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

<span data-ttu-id="b4087-109">如需如何宣告這個屬性的詳細資訊，請參閱[ValidateLength 屬性](./validatelength-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="b4087-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4087-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4087-110">See Also</span></span>

[<span data-ttu-id="b4087-111">ValidateLength 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="b4087-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="b4087-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b4087-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
