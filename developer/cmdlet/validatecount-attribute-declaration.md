---
title: ValidateCount 屬性宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 1a7b5ea340fe5212d003c97a9017278d6c631355
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859154"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="667d1-102">ValidateCount 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="667d1-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="667d1-103">ValidateCount 屬性會指定允許針對 cmdlet 參數的引數的最小和最大數目。</span><span class="sxs-lookup"><span data-stu-id="667d1-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="667d1-104">語法</span><span class="sxs-lookup"><span data-stu-id="667d1-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="667d1-105">參數</span><span class="sxs-lookup"><span data-stu-id="667d1-105">Parameters</span></span>

<span data-ttu-id="667d1-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) 所需。</span><span class="sxs-lookup"><span data-stu-id="667d1-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="667d1-107">指定引數的數目下限。</span><span class="sxs-lookup"><span data-stu-id="667d1-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="667d1-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) 所需。</span><span class="sxs-lookup"><span data-stu-id="667d1-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="667d1-109">指定的引數的數目上限。</span><span class="sxs-lookup"><span data-stu-id="667d1-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="667d1-110">備註</span><span class="sxs-lookup"><span data-stu-id="667d1-110">Remarks</span></span>

- <span data-ttu-id="667d1-111">如需如何宣告這個屬性的詳細資訊，請參閱[宣告輸入驗證規則如何](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)。</span><span class="sxs-lookup"><span data-stu-id="667d1-111">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="667d1-112">無法叫用這個屬性時，對應的 cmdlet 參數可以有任意數目的引數。</span><span class="sxs-lookup"><span data-stu-id="667d1-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="667d1-113">Windows PowerShell 執行階段會擲回錯誤，在下列情況下：</span><span class="sxs-lookup"><span data-stu-id="667d1-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="667d1-114">`MinLength`並`MaxLength`屬性參數不是型別[System.Int32](/dotnet/api/System.Int32)。</span><span class="sxs-lookup"><span data-stu-id="667d1-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32](/dotnet/api/System.Int32).</span></span>

    - <span data-ttu-id="667d1-115">值`MaxLength`屬性的參數小於值`MinLength`屬性參數。</span><span class="sxs-lookup"><span data-stu-id="667d1-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="667d1-116">ValidateCount 屬性所定義[System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount)類別。</span><span class="sxs-lookup"><span data-stu-id="667d1-116">The ValidateCount attribute is defined by the [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="667d1-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="667d1-117">See Also</span></span>

[<span data-ttu-id="667d1-118">System.Management.Automation.Validatecount</span><span class="sxs-lookup"><span data-stu-id="667d1-118">System.Management.Automation.Validatecount</span></span>](/dotnet/api/System.Management.Automation.ValidateCount)

[<span data-ttu-id="667d1-119">如何宣告輸入的驗證規則</span><span class="sxs-lookup"><span data-stu-id="667d1-119">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="667d1-120">如何宣告輸入的驗證規則</span><span class="sxs-lookup"><span data-stu-id="667d1-120">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="667d1-121">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="667d1-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
