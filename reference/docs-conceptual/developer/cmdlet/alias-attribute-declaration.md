---
ms.date: 09/13/2016
ms.topic: reference
title: 別名屬性宣告
description: 別名屬性宣告
ms.openlocfilehash: f2fe49578da2c795643b1f80fa44deefe1dbff09
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668298"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="71244-103">別名屬性宣告</span><span class="sxs-lookup"><span data-stu-id="71244-103">Alias Attribute Declaration</span></span>

<span data-ttu-id="71244-104">Alias 屬性可讓使用者指定不同的 Cmdlet 參數名稱。</span><span class="sxs-lookup"><span data-stu-id="71244-104">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="71244-105">別名可以用來提供參數名稱的快捷方式，也可以提供適用于不同案例的不同名稱。</span><span class="sxs-lookup"><span data-stu-id="71244-105">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="71244-106">語法</span><span class="sxs-lookup"><span data-stu-id="71244-106">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="71244-107">參數</span><span class="sxs-lookup"><span data-stu-id="71244-107">Parameters</span></span>

<span data-ttu-id="71244-108">`aliasName` 需要 (String [] ) 。</span><span class="sxs-lookup"><span data-stu-id="71244-108">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="71244-109">針對 Cmdlet 參數指定一組以逗號分隔的別名名稱。</span><span class="sxs-lookup"><span data-stu-id="71244-109">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="71244-110">備註</span><span class="sxs-lookup"><span data-stu-id="71244-110">Remarks</span></span>

- <span data-ttu-id="71244-111">當您指定 Cmdlet 參數時，別名屬性會與參數屬性搭配使用。</span><span class="sxs-lookup"><span data-stu-id="71244-111">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="71244-112">如需如何宣告這些屬性的詳細資訊，請參閱 [如何宣告 Cmdlet 參數](./how-to-declare-cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="71244-112">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="71244-113">每個別名名稱在 Cmdlet 內都必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="71244-113">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="71244-114">Windows PowerShell 不會檢查重複的別名名稱。</span><span class="sxs-lookup"><span data-stu-id="71244-114">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="71244-115">針對 Cmdlet 中的每個參數使用 Alias 屬性一次。</span><span class="sxs-lookup"><span data-stu-id="71244-115">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="71244-116">Alias 屬性是由 [Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 類別所定義。</span><span class="sxs-lookup"><span data-stu-id="71244-116">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="71244-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71244-117">See Also</span></span>

[<span data-ttu-id="71244-118">參數別名</span><span class="sxs-lookup"><span data-stu-id="71244-118">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="71244-119">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="71244-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
