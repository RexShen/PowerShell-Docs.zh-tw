---
title: ValidateLength 屬性聲明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: a25fa2410fcc6803563573596af1bc99052c3ffa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369177"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="c1cef-102">ValidateLength 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="c1cef-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="c1cef-103">ValidateLength 屬性會指定 Cmdlet 參數引數的最小和最大字元數。</span><span class="sxs-lookup"><span data-stu-id="c1cef-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="c1cef-104">Windows PowerShell 函數也可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="c1cef-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="c1cef-105">語法</span><span class="sxs-lookup"><span data-stu-id="c1cef-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="c1cef-106">參數</span><span class="sxs-lookup"><span data-stu-id="c1cef-106">Parameters</span></span>

<span data-ttu-id="c1cef-107">需要 `MinLength` （[system.object](/dotnet/api/System.Int32)）。</span><span class="sxs-lookup"><span data-stu-id="c1cef-107">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="c1cef-108">指定允許的最小字元數。</span><span class="sxs-lookup"><span data-stu-id="c1cef-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="c1cef-109">需要 `MaxLength` （[system.object](/dotnet/api/System.Int32)）。</span><span class="sxs-lookup"><span data-stu-id="c1cef-109">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="c1cef-110">指定允許的最大字元數。</span><span class="sxs-lookup"><span data-stu-id="c1cef-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="c1cef-111">備註</span><span class="sxs-lookup"><span data-stu-id="c1cef-111">Remarks</span></span>

- <span data-ttu-id="c1cef-112">如需如何宣告此屬性的詳細資訊，請參閱[如何宣告輸入驗證規則](./how-to-validate-parameter-input.md)。</span><span class="sxs-lookup"><span data-stu-id="c1cef-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="c1cef-113">未使用此屬性時，對應的參數引數可以是任何長度。</span><span class="sxs-lookup"><span data-stu-id="c1cef-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="c1cef-114">在下列情況下，Windows PowerShell 執行時間會擲回錯誤：</span><span class="sxs-lookup"><span data-stu-id="c1cef-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="c1cef-115">當 `MaxLength` 屬性參數的值小於 `MinLength` 屬性參數的值時。</span><span class="sxs-lookup"><span data-stu-id="c1cef-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="c1cef-116">當 `MaxLength` 屬性參數設為0時。</span><span class="sxs-lookup"><span data-stu-id="c1cef-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="c1cef-117">當引數不是字串時。</span><span class="sxs-lookup"><span data-stu-id="c1cef-117">When the argument is not a string.</span></span>

- <span data-ttu-id="c1cef-118">ValidateLength 屬性是由[Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)類別所定義。</span><span class="sxs-lookup"><span data-stu-id="c1cef-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1cef-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1cef-119">See Also</span></span>

[<span data-ttu-id="c1cef-120">Validatelengthattribute。</span><span class="sxs-lookup"><span data-stu-id="c1cef-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="c1cef-121">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c1cef-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
