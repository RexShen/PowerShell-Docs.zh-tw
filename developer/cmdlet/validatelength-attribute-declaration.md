---
title: ValidateLength 屬性宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: 1e8364c78abba5272007019550ffcb2cedaf9fd0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858864"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="22eed-102">ValidateLength 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="22eed-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="22eed-103">ValidateLength 屬性會指定最小和最大的字元數的 cmdlet 參數引數。</span><span class="sxs-lookup"><span data-stu-id="22eed-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="22eed-104">這個屬性也可用 Windows PowerShell 函式。</span><span class="sxs-lookup"><span data-stu-id="22eed-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="22eed-105">語法</span><span class="sxs-lookup"><span data-stu-id="22eed-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="22eed-106">參數</span><span class="sxs-lookup"><span data-stu-id="22eed-106">Parameters</span></span>

<span data-ttu-id="22eed-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) 所需。</span><span class="sxs-lookup"><span data-stu-id="22eed-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="22eed-108">指定允許的字元數目下限。</span><span class="sxs-lookup"><span data-stu-id="22eed-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="22eed-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) 所需。</span><span class="sxs-lookup"><span data-stu-id="22eed-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="22eed-110">指定允許的字元數目上限。</span><span class="sxs-lookup"><span data-stu-id="22eed-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="22eed-111">備註</span><span class="sxs-lookup"><span data-stu-id="22eed-111">Remarks</span></span>

- <span data-ttu-id="22eed-112">如需如何宣告這個屬性的詳細資訊，請參閱[宣告輸入驗證規則如何](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)。</span><span class="sxs-lookup"><span data-stu-id="22eed-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>
- <span data-ttu-id="22eed-113">如需如何宣告這個屬性的詳細資訊，請參閱[宣告輸入驗證規則如何](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)。</span><span class="sxs-lookup"><span data-stu-id="22eed-113">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="22eed-114">不使用這個屬性時，對應參數的引數可以是任何長度。</span><span class="sxs-lookup"><span data-stu-id="22eed-114">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="22eed-115">Windows PowerShell 執行階段會擲回錯誤，在下列情況下：</span><span class="sxs-lookup"><span data-stu-id="22eed-115">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="22eed-116">當 windows 7`MaxLength`屬性的參數小於值`MinLength`屬性參數。</span><span class="sxs-lookup"><span data-stu-id="22eed-116">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="22eed-117">當`MaxLength`屬性參數設定為 0。</span><span class="sxs-lookup"><span data-stu-id="22eed-117">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="22eed-118">當引數不是字串。</span><span class="sxs-lookup"><span data-stu-id="22eed-118">When the argument is not a string.</span></span>

- <span data-ttu-id="22eed-119">ValidateLength 屬性所定義[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)類別。</span><span class="sxs-lookup"><span data-stu-id="22eed-119">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="22eed-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22eed-120">See Also</span></span>

[<span data-ttu-id="22eed-121">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="22eed-121">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="22eed-122">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="22eed-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
