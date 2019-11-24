---
title: ValidateRange 屬性聲明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369127"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="d069f-102">ValidateRange 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="d069f-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="d069f-103">ValidateRange 屬性會指定 Cmdlet 參數引數的最小和最大值（範圍）。</span><span class="sxs-lookup"><span data-stu-id="d069f-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="d069f-104">Windows PowerShell 函數也可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="d069f-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="d069f-105">語法</span><span class="sxs-lookup"><span data-stu-id="d069f-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="d069f-106">參數</span><span class="sxs-lookup"><span data-stu-id="d069f-106">Parameters</span></span>

<span data-ttu-id="d069f-107">需要 `MinRange` （[system.object](/dotnet/api/system.object)）。</span><span class="sxs-lookup"><span data-stu-id="d069f-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="d069f-108">指定允許的最小值。</span><span class="sxs-lookup"><span data-stu-id="d069f-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="d069f-109">需要 `MaxRange` （[system.object](/dotnet/api/system.object)）。</span><span class="sxs-lookup"><span data-stu-id="d069f-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="d069f-110">指定允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="d069f-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="d069f-111">備註</span><span class="sxs-lookup"><span data-stu-id="d069f-111">Remarks</span></span>

- <span data-ttu-id="d069f-112">當 `MinRange` 參數的值大於 `MaxRange` 參數的值時，Windows PowerShell 執行時間會擲回結構錯誤。</span><span class="sxs-lookup"><span data-stu-id="d069f-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="d069f-113">在下列情況下，Windows PowerShell 執行時間會擲回驗證錯誤：</span><span class="sxs-lookup"><span data-stu-id="d069f-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

    - <span data-ttu-id="d069f-114">當引數的值小於 `MinRange` 限制或大於 `MaxRange` 限制時。</span><span class="sxs-lookup"><span data-stu-id="d069f-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

    - <span data-ttu-id="d069f-115">當引數與 `MinRange` 和 `MaxRange` 參數的類型不同時。</span><span class="sxs-lookup"><span data-stu-id="d069f-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="d069f-116">ValidateRange 屬性是由[Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)類別所定義。</span><span class="sxs-lookup"><span data-stu-id="d069f-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="d069f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d069f-117">See Also</span></span>

[<span data-ttu-id="d069f-118">Validaterangeattribute。</span><span class="sxs-lookup"><span data-stu-id="d069f-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="d069f-119">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d069f-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
