---
ms.date: 09/13/2016
ms.topic: reference
title: 如何驗證引數長度
description: 如何驗證引數長度
ms.openlocfilehash: 460aedbe6847033f976cb7bf70b6c77ac5a3a3c9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652638"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="88c25-103">如何驗證引數長度</span><span class="sxs-lookup"><span data-stu-id="88c25-103">How to Validate the Argument Length</span></span>

<span data-ttu-id="88c25-104">這個範例示範如何指定 Windows PowerShell 執行時間可在執行 Cmdlet 之前，用來檢查參數引數) 長度 (字元數的驗證規則。</span><span class="sxs-lookup"><span data-stu-id="88c25-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="88c25-105">您可以藉由宣告 ValidateLength 屬性來設定此驗證規則。</span><span class="sxs-lookup"><span data-stu-id="88c25-105">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="88c25-106">如需定義這個屬性之類別的詳細資訊，請參閱 [Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)。</span><span class="sxs-lookup"><span data-stu-id="88c25-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="88c25-107">驗證引數長度</span><span class="sxs-lookup"><span data-stu-id="88c25-107">To validate the argument length</span></span>

- <span data-ttu-id="88c25-108">加入 Validate 屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="88c25-108">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="88c25-109">這個範例會指定引數長度的長度應為0到10個字元。</span><span class="sxs-lookup"><span data-stu-id="88c25-109">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

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

<span data-ttu-id="88c25-110">如需如何宣告這個屬性的詳細資訊，請參閱 [ValidateLength 屬性聲明](./validatelength-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="88c25-110">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="88c25-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88c25-111">See Also</span></span>

[<span data-ttu-id="88c25-112">ValidateLength 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="88c25-112">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="88c25-113">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="88c25-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
