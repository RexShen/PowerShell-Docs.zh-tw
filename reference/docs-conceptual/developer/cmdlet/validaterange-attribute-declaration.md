---
ms.date: 09/13/2016
ms.topic: reference
title: ValidateRange 屬性宣告
description: ValidateRange 屬性宣告
ms.openlocfilehash: 1fec9d1bd36cd21b7f0f23bf6d72338d276dce91
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660595"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="1c2e2-103">ValidateRange 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="1c2e2-103">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="1c2e2-104">ValidateRange 屬性會指定 Cmdlet 參數引數) 範圍 (的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="1c2e2-104">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="1c2e2-105">Windows PowerShell 函數也可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="1c2e2-105">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="1c2e2-106">語法</span><span class="sxs-lookup"><span data-stu-id="1c2e2-106">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="1c2e2-107">參數</span><span class="sxs-lookup"><span data-stu-id="1c2e2-107">Parameters</span></span>

<span data-ttu-id="1c2e2-108">`MinRange` ([system.object](/dotnet/api/system.object)) 需要的物件。</span><span class="sxs-lookup"><span data-stu-id="1c2e2-108">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="1c2e2-109">指定允許的最小值。</span><span class="sxs-lookup"><span data-stu-id="1c2e2-109">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="1c2e2-110">`MaxRange` ([system.object](/dotnet/api/system.object)) 需要的物件。</span><span class="sxs-lookup"><span data-stu-id="1c2e2-110">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="1c2e2-111">指定允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="1c2e2-111">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c2e2-112">備註</span><span class="sxs-lookup"><span data-stu-id="1c2e2-112">Remarks</span></span>

- <span data-ttu-id="1c2e2-113">當參數的值大於參數的值時，Windows PowerShell 執行時間會擲回結構錯誤 `MinRange` `MaxRange` 。</span><span class="sxs-lookup"><span data-stu-id="1c2e2-113">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="1c2e2-114">在下列情況下，Windows PowerShell 執行時間會擲回驗證錯誤：</span><span class="sxs-lookup"><span data-stu-id="1c2e2-114">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

  - <span data-ttu-id="1c2e2-115">當引數的值小於 `MinRange` 限制或大於 `MaxRange` 限制時。</span><span class="sxs-lookup"><span data-stu-id="1c2e2-115">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

  - <span data-ttu-id="1c2e2-116">當引數與和參數的類型不同時 `MinRange` `MaxRange` 。</span><span class="sxs-lookup"><span data-stu-id="1c2e2-116">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="1c2e2-117">ValidateRange 屬性是由 [Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) 類別所定義。</span><span class="sxs-lookup"><span data-stu-id="1c2e2-117">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c2e2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c2e2-118">See Also</span></span>

[<span data-ttu-id="1c2e2-119">Validaterangeattribute。</span><span class="sxs-lookup"><span data-stu-id="1c2e2-119">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="1c2e2-120">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1c2e2-120">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
