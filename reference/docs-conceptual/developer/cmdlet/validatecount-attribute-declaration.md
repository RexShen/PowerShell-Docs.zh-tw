---
ms.date: 09/13/2016
ms.topic: reference
title: ValidateCount 屬性宣告
description: ValidateCount 屬性宣告
ms.openlocfilehash: 6acdd02a10ecc1bc2be0e6be88cf2f42a3673eb8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646272"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="67440-103">ValidateCount 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="67440-103">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="67440-104">ValidateCount 屬性會指定 Cmdlet 參數允許的最小和最大引數數目。</span><span class="sxs-lookup"><span data-stu-id="67440-104">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="67440-105">語法</span><span class="sxs-lookup"><span data-stu-id="67440-105">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="67440-106">參數</span><span class="sxs-lookup"><span data-stu-id="67440-106">Parameters</span></span>

<span data-ttu-id="67440-107">`MinLength` 需要 ([system.object][]) 。</span><span class="sxs-lookup"><span data-stu-id="67440-107">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="67440-108">指定引數的最小數目。</span><span class="sxs-lookup"><span data-stu-id="67440-108">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="67440-109">`MaxLength` 需要 ([system.object][]) 。</span><span class="sxs-lookup"><span data-stu-id="67440-109">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="67440-110">指定引數的最大數目。</span><span class="sxs-lookup"><span data-stu-id="67440-110">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="67440-111">備註</span><span class="sxs-lookup"><span data-stu-id="67440-111">Remarks</span></span>

- <span data-ttu-id="67440-112">如需如何宣告這個屬性的詳細資訊，請參閱 [如何驗證引數計數][]。</span><span class="sxs-lookup"><span data-stu-id="67440-112">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="67440-113">如果未叫用此屬性，對應的 Cmdlet 參數可以有任意數目的引數。</span><span class="sxs-lookup"><span data-stu-id="67440-113">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="67440-114">在下列情況下，Windows PowerShell 執行時間會擲回錯誤：</span><span class="sxs-lookup"><span data-stu-id="67440-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="67440-115">`MinLength`和 `MaxLength` 屬性參數的類型不是[system.object][]。</span><span class="sxs-lookup"><span data-stu-id="67440-115">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

  - <span data-ttu-id="67440-116">Attribute 參數的值 `MaxLength` 小於 `MinLength` attribute 參數的值。</span><span class="sxs-lookup"><span data-stu-id="67440-116">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="67440-117">ValidateCount 屬性是由 [ValidateCountAttribute][] 類別所定義。</span><span class="sxs-lookup"><span data-stu-id="67440-117">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="67440-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67440-118">See Also</span></span>

<span data-ttu-id="67440-119">[ValidateCountAttribute。][]</span><span class="sxs-lookup"><span data-stu-id="67440-119">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="67440-120">[如何驗證引數計數][]</span><span class="sxs-lookup"><span data-stu-id="67440-120">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="67440-121">[撰寫 Windows PowerShell Cmdlet][]</span><span class="sxs-lookup"><span data-stu-id="67440-121">[Writing a Windows PowerShell Cmdlet][]</span></span>

[如何驗證引數計數]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[撰寫 Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[ValidateCountAttribute。]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
