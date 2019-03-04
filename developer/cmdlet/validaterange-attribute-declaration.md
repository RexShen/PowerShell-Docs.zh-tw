---
title: ValidateRange 屬性宣告 |Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857034"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="3185a-102">ValidateRange 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="3185a-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="3185a-103">ValidateRange 屬性指定的最小和最大值 （範圍） 的 cmdlet 參數引數。</span><span class="sxs-lookup"><span data-stu-id="3185a-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="3185a-104">這個屬性也可用 Windows PowerShell 函式。</span><span class="sxs-lookup"><span data-stu-id="3185a-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="3185a-105">語法</span><span class="sxs-lookup"><span data-stu-id="3185a-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="3185a-106">參數</span><span class="sxs-lookup"><span data-stu-id="3185a-106">Parameters</span></span>

<span data-ttu-id="3185a-107">`MinRange` ([System.Object](/dotnet/api/system.object)) 所需。</span><span class="sxs-lookup"><span data-stu-id="3185a-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="3185a-108">指定允許的最小值。</span><span class="sxs-lookup"><span data-stu-id="3185a-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="3185a-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) 所需。</span><span class="sxs-lookup"><span data-stu-id="3185a-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="3185a-110">指定允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="3185a-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="3185a-111">備註</span><span class="sxs-lookup"><span data-stu-id="3185a-111">Remarks</span></span>

- <span data-ttu-id="3185a-112">Windows PowerShell 執行階段會擲回建構錯誤時的值`MinRange`參數的值大於`MaxRange`參數。</span><span class="sxs-lookup"><span data-stu-id="3185a-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="3185a-113">Windows PowerShell 執行階段會擲回下列情況下的驗證錯誤：</span><span class="sxs-lookup"><span data-stu-id="3185a-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

    - <span data-ttu-id="3185a-114">當引數的值是小於`MinRange`限制或大於`MaxRange`限制。</span><span class="sxs-lookup"><span data-stu-id="3185a-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

    - <span data-ttu-id="3185a-115">當引數不是相同的型別`MinRange`而`MaxRange`參數。</span><span class="sxs-lookup"><span data-stu-id="3185a-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="3185a-116">ValidateRange 屬性所定義[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)類別。</span><span class="sxs-lookup"><span data-stu-id="3185a-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="3185a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3185a-117">See Also</span></span>

[<span data-ttu-id="3185a-118">System.Management.Automation.Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="3185a-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="3185a-119">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3185a-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
