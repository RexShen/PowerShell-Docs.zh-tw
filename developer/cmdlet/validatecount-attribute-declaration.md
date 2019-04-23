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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59983893"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="ca821-102">ValidateCount 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="ca821-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="ca821-103">ValidateCount 屬性會指定允許針對 cmdlet 參數的引數的最小和最大數目。</span><span class="sxs-lookup"><span data-stu-id="ca821-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="ca821-104">語法</span><span class="sxs-lookup"><span data-stu-id="ca821-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="ca821-105">參數</span><span class="sxs-lookup"><span data-stu-id="ca821-105">Parameters</span></span>

<span data-ttu-id="ca821-106">`MinLength` ([System.Int32][]) 所需。</span><span class="sxs-lookup"><span data-stu-id="ca821-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="ca821-107">指定引數的數目下限。</span><span class="sxs-lookup"><span data-stu-id="ca821-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="ca821-108">`MaxLength`([System.Int32][]) 所需。</span><span class="sxs-lookup"><span data-stu-id="ca821-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="ca821-109">指定的引數的數目上限。</span><span class="sxs-lookup"><span data-stu-id="ca821-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="ca821-110">備註</span><span class="sxs-lookup"><span data-stu-id="ca821-110">Remarks</span></span>

- <span data-ttu-id="ca821-111">如需如何宣告這個屬性的詳細資訊，請參閱[如何驗證引數計數][]。</span><span class="sxs-lookup"><span data-stu-id="ca821-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="ca821-112">無法叫用這個屬性時，對應的 cmdlet 參數可以有任意數目的引數。</span><span class="sxs-lookup"><span data-stu-id="ca821-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="ca821-113">Windows PowerShell 執行階段會擲回錯誤，在下列情況下：</span><span class="sxs-lookup"><span data-stu-id="ca821-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="ca821-114">`MinLength`並`MaxLength`屬性參數不是型別[System.Int32][]。</span><span class="sxs-lookup"><span data-stu-id="ca821-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

    - <span data-ttu-id="ca821-115">值`MaxLength`屬性的參數小於值`MinLength`屬性參數。</span><span class="sxs-lookup"><span data-stu-id="ca821-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="ca821-116">ValidateCount 屬性所定義[System.Management.Automation.ValidateCountAttribute][]類別。</span><span class="sxs-lookup"><span data-stu-id="ca821-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca821-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca821-117">See Also</span></span>

<span data-ttu-id="ca821-118">[System.Management.Automation.ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="ca821-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="ca821-119">[如何驗證引數計數][]</span><span class="sxs-lookup"><span data-stu-id="ca821-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="ca821-120">[撰寫 Windows PowerShell Cmdlet][]</span><span class="sxs-lookup"><span data-stu-id="ca821-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[如何驗證引數計數]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[撰寫 Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
