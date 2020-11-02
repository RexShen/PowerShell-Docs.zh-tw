---
ms.date: 07/29/2020
title: PowerShell 5.0 的新語言功能
description: PowerShell 5.0 新增了功能，可使用類似其他物件導向程式設計語言的正式語法和語意，來定義類別和其他使用者定義類型。
ms.openlocfilehash: 31ff54ba6f2800a0680c1a2db3832ca97246973d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663310"
---
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="612be-103">PowerShell 5.0 的新語言功能</span><span class="sxs-lookup"><span data-stu-id="612be-103">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="612be-104">PowerShell 5.0 新增了功能，可使用類似其他物件導向程式設計語言的正式語法和語意，來定義類別和其他使用者定義類型。</span><span class="sxs-lookup"><span data-stu-id="612be-104">PowerShell 5.0 added the ability to define classes and other user-defined types using formal syntax and semantics like other object-oriented programming languages.</span></span> <span data-ttu-id="612be-105">目標是要讓開發人員和 IT 專業人員能夠掌握更多面向的 PowerShell 使用案例、簡化 PowerShell 成品的開發 (例如 DSC 資源)，並擴大管理介面的涵蓋範圍。</span><span class="sxs-lookup"><span data-stu-id="612be-105">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

<span data-ttu-id="612be-106">PowerShell 5.0 會在 PowerShell 中引進下列新的語言元素︰</span><span class="sxs-lookup"><span data-stu-id="612be-106">PowerShell 5.0 introduces the following new language elements in PowerShell:</span></span>

### <a name="class-keyword"></a><span data-ttu-id="612be-107">Class 關鍵字</span><span class="sxs-lookup"><span data-stu-id="612be-107">Class keyword</span></span>

<span data-ttu-id="612be-108">`class` 關鍵字會定義新類別。</span><span class="sxs-lookup"><span data-stu-id="612be-108">The `class` keyword defines a new class.</span></span> <span data-ttu-id="612be-109">這是真的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="612be-109">This is a true .NET Framework type.</span></span> <span data-ttu-id="612be-110">類別成員是公用的，但只在模組範圍內公用。</span><span class="sxs-lookup"><span data-stu-id="612be-110">Class members are public, but only public within the module scope.</span></span> <span data-ttu-id="612be-111">您不能將類型名稱當作字串來參考 (例如，`New-Object` 不會運作)，而且在這個版本中，您無法在類別定義所在的指令碼或模組檔案外部使用類型常值 (例如 `[MyClass]`)。</span><span class="sxs-lookup"><span data-stu-id="612be-111">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script or module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="612be-112">Enum 關鍵字和列舉</span><span class="sxs-lookup"><span data-stu-id="612be-112">Enum keyword and enumerations</span></span>

<span data-ttu-id="612be-113">已新增對 `enum` 關鍵字的支援，其會使用新行字元作為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="612be-113">Support for the `enum` keyword has been added, which uses newline as the delimiter.</span></span> <span data-ttu-id="612be-114">您目前無法根據列舉本身來定義它。</span><span class="sxs-lookup"><span data-stu-id="612be-114">Currently, you cannot define an enumerator in terms of itself.</span></span> <span data-ttu-id="612be-115">不過，您可以根據另一個列舉來將某個列舉初始化，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="612be-115">However, you can initialize an enum in terms of another enum, as shown in the following example.</span></span> <span data-ttu-id="612be-116">此外，無法指定基底類型，它一律是 `[int]`。</span><span class="sxs-lookup"><span data-stu-id="612be-116">Also, the base type cannot be specified; it is always `[int]`.</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="612be-117">列舉程式值必須是剖析時間常數。</span><span class="sxs-lookup"><span data-stu-id="612be-117">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="612be-118">您無法將它設定為所叫用命令的結果。</span><span class="sxs-lookup"><span data-stu-id="612be-118">You cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="612be-119">Enum 支援算數運算，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="612be-119">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a><span data-ttu-id="612be-120">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="612be-120">Import-DscResource</span></span>

<span data-ttu-id="612be-121">`Import-DscResource` 現在是真正的動態關鍵字。</span><span class="sxs-lookup"><span data-stu-id="612be-121">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="612be-122">PowerShell 會剖析所指定模組的根模組，其會搜尋包含 **DscResource** 屬性的類別。</span><span class="sxs-lookup"><span data-stu-id="612be-122">PowerShell parses the specified module's root module, searching for classes that contain the **DscResource** attribute.</span></span>

### <a name="implementingassembly"></a><span data-ttu-id="612be-123">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="612be-123">ImplementingAssembly</span></span>

<span data-ttu-id="612be-124">已將新欄位 **ImplementingAssembly** 新增至 **ModuleInfo** 。</span><span class="sxs-lookup"><span data-stu-id="612be-124">A new field, **ImplementingAssembly** , has been added to **ModuleInfo** .</span></span> <span data-ttu-id="612be-125">如果指令碼定義類別，它會設定成為指令碼模組所建立的動態組件，或二進位模組的載入組件。</span><span class="sxs-lookup"><span data-stu-id="612be-125">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="612be-126">若 **ModuleType** 為 **Manifest** ，則不會設定它。</span><span class="sxs-lookup"><span data-stu-id="612be-126">It is not set when **ModuleType** is **Manifest** .</span></span>

<span data-ttu-id="612be-127">**ImplementingAssembly** 欄位的反映會探索模組中的資源。</span><span class="sxs-lookup"><span data-stu-id="612be-127">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="612be-128">這表示您可以探索以 PowerShell 或其他 Managed 語言撰寫的資源。</span><span class="sxs-lookup"><span data-stu-id="612be-128">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

## <a name="further-reading"></a><span data-ttu-id="612be-129">進一步閱讀</span><span class="sxs-lookup"><span data-stu-id="612be-129">Further reading</span></span>

- [<span data-ttu-id="612be-130">about_Classes</span><span class="sxs-lookup"><span data-stu-id="612be-130">about_Classes</span></span>](/powershell/module/microsoft.powershell.core/about/about_classes)
- [<span data-ttu-id="612be-131">about_Enum</span><span class="sxs-lookup"><span data-stu-id="612be-131">about_Enum</span></span>](/powershell/module/microsoft.powershell.core/about/about_enum)
- [<span data-ttu-id="612be-132">about_Classes_and_DSC</span><span class="sxs-lookup"><span data-stu-id="612be-132">about_Classes_and_DSC</span></span>](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)
