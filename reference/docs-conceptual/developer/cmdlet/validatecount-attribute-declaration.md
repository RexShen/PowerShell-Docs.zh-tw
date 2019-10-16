---
title: ValidateCount 屬性聲明 |Microsoft Docs
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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369227"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="cd7c9-102">ValidateCount 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="cd7c9-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="cd7c9-103">ValidateCount 屬性會指定 Cmdlet 參數所允許的最小和最大引數數目。</span><span class="sxs-lookup"><span data-stu-id="cd7c9-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd7c9-104">語法</span><span class="sxs-lookup"><span data-stu-id="cd7c9-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="cd7c9-105">參數</span><span class="sxs-lookup"><span data-stu-id="cd7c9-105">Parameters</span></span>

<span data-ttu-id="cd7c9-106">需要 `MinLength` （[System. Int32][]）。</span><span class="sxs-lookup"><span data-stu-id="cd7c9-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="cd7c9-107">指定引數的最小數目。</span><span class="sxs-lookup"><span data-stu-id="cd7c9-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="cd7c9-108">需要 `MaxLength` （[System. Int32][]）。</span><span class="sxs-lookup"><span data-stu-id="cd7c9-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="cd7c9-109">指定引數的最大數目。</span><span class="sxs-lookup"><span data-stu-id="cd7c9-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="cd7c9-110">備註</span><span class="sxs-lookup"><span data-stu-id="cd7c9-110">Remarks</span></span>

- <span data-ttu-id="cd7c9-111">如需如何宣告這個屬性的詳細資訊，請參閱[如何驗證引數計數][]。</span><span class="sxs-lookup"><span data-stu-id="cd7c9-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="cd7c9-112">未叫用此屬性時，對應的 Cmdlet 參數可以有任意數目的引數。</span><span class="sxs-lookup"><span data-stu-id="cd7c9-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="cd7c9-113">在下列情況下，Windows PowerShell 執行時間會擲回錯誤：</span><span class="sxs-lookup"><span data-stu-id="cd7c9-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="cd7c9-114">@No__t-0 和 @no__t 1 屬性參數不是[System. Int32][]類型。</span><span class="sxs-lookup"><span data-stu-id="cd7c9-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

    - <span data-ttu-id="cd7c9-115">@No__t-0 屬性參數的值小於 `MinLength` 屬性參數的值。</span><span class="sxs-lookup"><span data-stu-id="cd7c9-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="cd7c9-116">ValidateCount 屬性是由[ValidateCountAttribute。][]類別所定義。</span><span class="sxs-lookup"><span data-stu-id="cd7c9-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd7c9-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd7c9-117">See Also</span></span>

<span data-ttu-id="cd7c9-118">[ValidateCountAttribute。][]</span><span class="sxs-lookup"><span data-stu-id="cd7c9-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="cd7c9-119">[如何驗證引數計數][]</span><span class="sxs-lookup"><span data-stu-id="cd7c9-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="cd7c9-120">[撰寫 Windows PowerShell Cmdlet][]</span><span class="sxs-lookup"><span data-stu-id="cd7c9-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[如何驗證引數計數]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[撰寫 Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System. Int32]: /dotnet/api/System.Int32
[System.Int32]: /dotnet/api/System.Int32
[ValidateCountAttribute。]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
