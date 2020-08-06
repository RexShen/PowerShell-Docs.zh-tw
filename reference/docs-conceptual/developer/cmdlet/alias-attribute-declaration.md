---
title: Alias 屬性宣告 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.openlocfilehash: 4c1ff34a244611173ca919a44d6598189b19dc98
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782407"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="dda12-102">別名屬性宣告</span><span class="sxs-lookup"><span data-stu-id="dda12-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="dda12-103">Alias 屬性可讓使用者指定不同的 Cmdlet 參數名稱。</span><span class="sxs-lookup"><span data-stu-id="dda12-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="dda12-104">別名可以用來提供參數名稱的快捷方式，或者可以針對不同的案例提供不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="dda12-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="dda12-105">語法</span><span class="sxs-lookup"><span data-stu-id="dda12-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="dda12-106">參數</span><span class="sxs-lookup"><span data-stu-id="dda12-106">Parameters</span></span>

<span data-ttu-id="dda12-107">`aliasName`需要 (String [] ) 。</span><span class="sxs-lookup"><span data-stu-id="dda12-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="dda12-108">為 Cmdlet 參數指定一組以逗號分隔的別名名稱。</span><span class="sxs-lookup"><span data-stu-id="dda12-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="dda12-109">備註</span><span class="sxs-lookup"><span data-stu-id="dda12-109">Remarks</span></span>

- <span data-ttu-id="dda12-110">當您指定 Cmdlet 參數時，Alias 屬性會與參數屬性搭配使用。</span><span class="sxs-lookup"><span data-stu-id="dda12-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="dda12-111">如需如何宣告這些屬性的詳細資訊，請參閱 how [To Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="dda12-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="dda12-112">每個別名名稱在 Cmdlet 中都必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="dda12-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="dda12-113">Windows PowerShell 不會檢查重複的別名名稱。</span><span class="sxs-lookup"><span data-stu-id="dda12-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="dda12-114">Alias 屬性會針對 Cmdlet 中的每個參數使用一次。</span><span class="sxs-lookup"><span data-stu-id="dda12-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="dda12-115">Alias 屬性是由[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)類別所定義。</span><span class="sxs-lookup"><span data-stu-id="dda12-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="dda12-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dda12-116">See Also</span></span>

[<span data-ttu-id="dda12-117">參數別名</span><span class="sxs-lookup"><span data-stu-id="dda12-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="dda12-118">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="dda12-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
