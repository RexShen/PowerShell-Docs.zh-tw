---
title: ValidateRange 屬性聲明 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.openlocfilehash: 9aeaa6f03c170389ff61a058b505dbcf74df6958
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787779"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="681db-102">ValidateRange 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="681db-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="681db-103">ValidateRange 屬性會指定 Cmdlet 參數引數 (範圍) 的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="681db-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="681db-104">Windows PowerShell 函數也可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="681db-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="681db-105">語法</span><span class="sxs-lookup"><span data-stu-id="681db-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="681db-106">參數</span><span class="sxs-lookup"><span data-stu-id="681db-106">Parameters</span></span>

<span data-ttu-id="681db-107">`MinRange` (的[system.object](/dotnet/api/system.object)) 需要。</span><span class="sxs-lookup"><span data-stu-id="681db-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="681db-108">指定允許的最小值。</span><span class="sxs-lookup"><span data-stu-id="681db-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="681db-109">`MaxRange` (的[system.object](/dotnet/api/system.object)) 需要。</span><span class="sxs-lookup"><span data-stu-id="681db-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="681db-110">指定允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="681db-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="681db-111">備註</span><span class="sxs-lookup"><span data-stu-id="681db-111">Remarks</span></span>

- <span data-ttu-id="681db-112">當參數的值大於參數的值時，Windows PowerShell 執行時間會擲回結構錯誤 `MinRange` `MaxRange` 。</span><span class="sxs-lookup"><span data-stu-id="681db-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="681db-113">在下列情況下，Windows PowerShell 執行時間會擲回驗證錯誤：</span><span class="sxs-lookup"><span data-stu-id="681db-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

  - <span data-ttu-id="681db-114">當引數的值小於 `MinRange` 限制或大於 `MaxRange` 限制時。</span><span class="sxs-lookup"><span data-stu-id="681db-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

  - <span data-ttu-id="681db-115">當引數與和參數的類型不同時 `MinRange` `MaxRange` 。</span><span class="sxs-lookup"><span data-stu-id="681db-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="681db-116">ValidateRange 屬性是由[Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)類別所定義。</span><span class="sxs-lookup"><span data-stu-id="681db-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="681db-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="681db-117">See Also</span></span>

[<span data-ttu-id="681db-118">Validaterangeattribute。</span><span class="sxs-lookup"><span data-stu-id="681db-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="681db-119">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="681db-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
