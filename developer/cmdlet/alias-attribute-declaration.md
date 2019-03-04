---
title: 別名屬性宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855044"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="a8b98-102">別名屬性宣告</span><span class="sxs-lookup"><span data-stu-id="a8b98-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="a8b98-103">Alias 屬性可讓使用者指定不同的 cmdlet 參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="a8b98-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="a8b98-104">別名可以用來提供參數名稱的捷徑，或者他們可以提供不同的名稱，適用於不同的案例。</span><span class="sxs-lookup"><span data-stu-id="a8b98-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="a8b98-105">語法</span><span class="sxs-lookup"><span data-stu-id="a8b98-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="a8b98-106">參數</span><span class="sxs-lookup"><span data-stu-id="a8b98-106">Parameters</span></span>

<span data-ttu-id="a8b98-107">`aliasName` (String必要的。</span><span class="sxs-lookup"><span data-stu-id="a8b98-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="a8b98-108">指定一組 cmdlet 參數的逗號分隔的別名名稱。</span><span class="sxs-lookup"><span data-stu-id="a8b98-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="a8b98-109">備註</span><span class="sxs-lookup"><span data-stu-id="a8b98-109">Remarks</span></span>

- <span data-ttu-id="a8b98-110">Alias 屬性搭配參數屬性，當您指定的 cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="a8b98-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="a8b98-111">如需如何宣告這些屬性的詳細資訊，請參閱[如何宣告 Cmdlet 參數](./how-to-declare-cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="a8b98-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="a8b98-112">每個別名名稱必須是唯一 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a8b98-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="a8b98-113">Windows PowerShell 不會檢查重複的別名名稱。</span><span class="sxs-lookup"><span data-stu-id="a8b98-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="a8b98-114">Alias 屬性使用一次，每個參數的 cmdlet 中。</span><span class="sxs-lookup"><span data-stu-id="a8b98-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="a8b98-115">Alias 屬性所定義[System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)類別。</span><span class="sxs-lookup"><span data-stu-id="a8b98-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8b98-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8b98-116">See Also</span></span>

[<span data-ttu-id="a8b98-117">參數別名</span><span class="sxs-lookup"><span data-stu-id="a8b98-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="a8b98-118">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a8b98-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
