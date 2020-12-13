---
ms.date: 09/13/2016
ms.topic: reference
title: ValidateLength 屬性宣告
description: ValidateLength 屬性宣告
ms.openlocfilehash: b35fe24c6fc44aaca6a39d819d6e3fc2d8a2cade
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646193"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="ee93a-103">ValidateLength 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="ee93a-103">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="ee93a-104">ValidateLength 屬性會指定 Cmdlet 參數引數的最小和最大字元數。</span><span class="sxs-lookup"><span data-stu-id="ee93a-104">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="ee93a-105">Windows PowerShell 函數也可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="ee93a-105">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="ee93a-106">語法</span><span class="sxs-lookup"><span data-stu-id="ee93a-106">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="ee93a-107">參數</span><span class="sxs-lookup"><span data-stu-id="ee93a-107">Parameters</span></span>

<span data-ttu-id="ee93a-108">`MinLength` 需要 ([system.object](/dotnet/api/System.Int32)) 。</span><span class="sxs-lookup"><span data-stu-id="ee93a-108">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="ee93a-109">指定允許的最小字元數。</span><span class="sxs-lookup"><span data-stu-id="ee93a-109">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="ee93a-110">`MaxLength` 需要 ([system.object](/dotnet/api/System.Int32)) 。</span><span class="sxs-lookup"><span data-stu-id="ee93a-110">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="ee93a-111">指定允許的最大字元數。</span><span class="sxs-lookup"><span data-stu-id="ee93a-111">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="ee93a-112">備註</span><span class="sxs-lookup"><span data-stu-id="ee93a-112">Remarks</span></span>

- <span data-ttu-id="ee93a-113">如需如何宣告這個屬性的詳細資訊，請參閱 [如何宣告輸入驗證規則](./how-to-validate-parameter-input.md)。</span><span class="sxs-lookup"><span data-stu-id="ee93a-113">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="ee93a-114">如果未使用此屬性，對應的參數引數可以是任何長度。</span><span class="sxs-lookup"><span data-stu-id="ee93a-114">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="ee93a-115">在下列情況下，Windows PowerShell 執行時間會擲回錯誤：</span><span class="sxs-lookup"><span data-stu-id="ee93a-115">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="ee93a-116">當 attribute 參數的值 `MaxLength` 小於 attribute 參數的值時 `MinLength` 。</span><span class="sxs-lookup"><span data-stu-id="ee93a-116">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

  - <span data-ttu-id="ee93a-117">當 `MaxLength` 屬性參數設定為0時。</span><span class="sxs-lookup"><span data-stu-id="ee93a-117">When the `MaxLength` attribute parameter is set to 0.</span></span>

  - <span data-ttu-id="ee93a-118">當引數不是字串時。</span><span class="sxs-lookup"><span data-stu-id="ee93a-118">When the argument is not a string.</span></span>

- <span data-ttu-id="ee93a-119">ValidateLength 屬性是由 [Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) 類別所定義。</span><span class="sxs-lookup"><span data-stu-id="ee93a-119">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee93a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee93a-120">See Also</span></span>

[<span data-ttu-id="ee93a-121">Validatelengthattribute。</span><span class="sxs-lookup"><span data-stu-id="ee93a-121">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="ee93a-122">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ee93a-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
