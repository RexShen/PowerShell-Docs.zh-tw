---
title: ValidateCount 屬性聲明 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.openlocfilehash: c013a354ee339bd14508fe30549673bc79d5c616
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786317"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="337dc-102">ValidateCount 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="337dc-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="337dc-103">ValidateCount 屬性會指定 Cmdlet 參數所允許的最小和最大引數數目。</span><span class="sxs-lookup"><span data-stu-id="337dc-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="337dc-104">語法</span><span class="sxs-lookup"><span data-stu-id="337dc-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="337dc-105">參數</span><span class="sxs-lookup"><span data-stu-id="337dc-105">Parameters</span></span>

<span data-ttu-id="337dc-106">`MinLength`需要 ([system.object][]) 。</span><span class="sxs-lookup"><span data-stu-id="337dc-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="337dc-107">指定引數的最小數目。</span><span class="sxs-lookup"><span data-stu-id="337dc-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="337dc-108">`MaxLength`需要 ([system.object][]) 。</span><span class="sxs-lookup"><span data-stu-id="337dc-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="337dc-109">指定引數的最大數目。</span><span class="sxs-lookup"><span data-stu-id="337dc-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="337dc-110">備註</span><span class="sxs-lookup"><span data-stu-id="337dc-110">Remarks</span></span>

- <span data-ttu-id="337dc-111">如需如何宣告這個屬性的詳細資訊，請參閱[如何驗證引數計數][]。</span><span class="sxs-lookup"><span data-stu-id="337dc-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="337dc-112">未叫用此屬性時，對應的 Cmdlet 參數可以有任意數目的引數。</span><span class="sxs-lookup"><span data-stu-id="337dc-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="337dc-113">在下列情況下，Windows PowerShell 執行時間會擲回錯誤：</span><span class="sxs-lookup"><span data-stu-id="337dc-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="337dc-114">`MinLength`和 `MaxLength` 屬性參數的類型不是[system.object][]。</span><span class="sxs-lookup"><span data-stu-id="337dc-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

  - <span data-ttu-id="337dc-115">屬性參數的值 `MaxLength` 小於 `MinLength` 屬性參數的值。</span><span class="sxs-lookup"><span data-stu-id="337dc-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="337dc-116">ValidateCount 屬性是由[ValidateCountAttribute][]類別所定義。</span><span class="sxs-lookup"><span data-stu-id="337dc-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="337dc-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="337dc-117">See Also</span></span>

<span data-ttu-id="337dc-118">[ValidateCountAttribute。][]</span><span class="sxs-lookup"><span data-stu-id="337dc-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="337dc-119">[如何驗證引數計數][]</span><span class="sxs-lookup"><span data-stu-id="337dc-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="337dc-120">[撰寫 Windows PowerShell Cmdlet][]</span><span class="sxs-lookup"><span data-stu-id="337dc-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[如何驗證引數計數]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[撰寫 Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System. Int32]: /dotnet/api/System.Int32
[System.Int32]: /dotnet/api/System.Int32
[ValidateCountAttribute。]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
