---
title: 擴充類型系統總覽
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: 82170bd7e8943f68141159a7ac964f9ec1b2cfbc
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217941"
---
# <a name="extended-type-system-overview"></a><span data-ttu-id="e3325-102">擴充類型系統總覽</span><span class="sxs-lookup"><span data-stu-id="e3325-102">Extended Type System Overview</span></span>

<span data-ttu-id="e3325-103">PowerShell 會使用其**PSObject**物件，以兩種方式擴充物件的類型。</span><span class="sxs-lookup"><span data-stu-id="e3325-103">PowerShell uses its **PSObject** object to extend the types of objects in two ways.</span></span> <span data-ttu-id="e3325-104">首先， **PSObject**物件提供一種方式來顯示特定物件類型的不同視圖。</span><span class="sxs-lookup"><span data-stu-id="e3325-104">First, the **PSObject** object provides a way to show different views of specific object types.</span></span> <span data-ttu-id="e3325-105">這稱為顯示物件的改編視圖。</span><span class="sxs-lookup"><span data-stu-id="e3325-105">This is referred to as showing an adapted view of an object.</span></span> <span data-ttu-id="e3325-106">第二， **PSObject**物件提供將成員加入至現有物件的方法。</span><span class="sxs-lookup"><span data-stu-id="e3325-106">Second, the **PSObject** object provides a way to add members to existing object.</span></span> <span data-ttu-id="e3325-107">藉由包裝現有的物件（稱為基底物件）， **PSObject**物件會提供擴充型別系統 (ETS) 供腳本和 Cmdlet 開發人員用來在 shell 中操作 .net 物件。</span><span class="sxs-lookup"><span data-stu-id="e3325-107">Together, by wrapping an existing object, referred to as the base object, the **PSObject** object provides an extended type system (ETS) that script and cmdlet developers can use to manipulate .NET objects within the shell.</span></span>

## <a name="cmdlet-and-script-development-issues"></a><span data-ttu-id="e3325-108">Cmdlet 和腳本開發問題</span><span class="sxs-lookup"><span data-stu-id="e3325-108">Cmdlet and Script Development Issues</span></span>

<span data-ttu-id="e3325-109">ETS 可解決兩個基本問題：</span><span class="sxs-lookup"><span data-stu-id="e3325-109">ETS resolves two fundamental issues:</span></span>

<span data-ttu-id="e3325-110">首先，有些 .NET 物件並沒有必要的預設行為，無法做為 Cmdlet 之間的資料。</span><span class="sxs-lookup"><span data-stu-id="e3325-110">First, some .NET Objects do not have the necessary default behavior for acting as the data between cmdlets.</span></span>

- <span data-ttu-id="e3325-111">有些 .NET 物件是「中繼」物件 (例如： WMI 物件、ADO 物件和 XML 物件) 其成員會描述所包含的資料。</span><span class="sxs-lookup"><span data-stu-id="e3325-111">Some .NET objects are "meta" objects (for example: WMI Objects, ADO objects, and XML objects) whose members describe the data they contain.</span></span> <span data-ttu-id="e3325-112">不過，在腳本環境中，它是最有趣的資料，而不是包含資料的描述。</span><span class="sxs-lookup"><span data-stu-id="e3325-112">However, in a scripting environment it is the contained data that is most interesting, not the description of the contained data.</span></span> <span data-ttu-id="e3325-113">ETS 藉由引進介面卡概念來解決此問題，使基礎 .NET 物件能夠具有預期的預設語義。</span><span class="sxs-lookup"><span data-stu-id="e3325-113">ETS resolves this issue by introducing the notion of Adapters that adapt the underlying .NET object to have the expected default semantics.</span></span>
- <span data-ttu-id="e3325-114">有些 .NET 物件成員的名稱不一致，提供的公用成員集不足，或提供的功能不足。</span><span class="sxs-lookup"><span data-stu-id="e3325-114">Some .NET Object members are inconsistently named, provide an insufficient set of public members, or provide insufficient capability.</span></span> <span data-ttu-id="e3325-115">ETS 藉由引進擴充 .NET 物件與其他成員的功能來解決此問題。</span><span class="sxs-lookup"><span data-stu-id="e3325-115">ETS resolves this issue by introducing the ability to extend the .NET object with additional members.</span></span>

<span data-ttu-id="e3325-116">第二，PowerShell 腳本_語言是無類型的，因為_變數不需要宣告特定類型。</span><span class="sxs-lookup"><span data-stu-id="e3325-116">Second, the PowerShell scripting language is _typeless_ in that a variable does not need to be declared of a particular type.</span></span> <span data-ttu-id="e3325-117">也就是說，腳本開發人員所建立的_變數本質上_是無類型的。</span><span class="sxs-lookup"><span data-stu-id="e3325-117">That is, the variables a script developer creates are by nature _typeless_.</span></span> <span data-ttu-id="e3325-118">不過，PowerShell 系統是「型別導向」，因為它相依于針對基本作業（例如輸出結果或排序）操作型別名稱。</span><span class="sxs-lookup"><span data-stu-id="e3325-118">However, the PowerShell system is "type-driven" in that it depends on having a type name to operate against for basic operations such as outputting results or sorting.</span></span>

<span data-ttu-id="e3325-119">因此，腳本開發人員必須能夠陳述其中一個變數的型別，並建立自己的一組動態類型「物件」，其中包含屬性和方法，而且可以參與型別驅動系統。</span><span class="sxs-lookup"><span data-stu-id="e3325-119">Therefore a script developer must have the ability to state the type of one of their variables and build up their own set of dynamically typed "objects" that contain properties and methods and can participate in the type-driven system.</span></span> <span data-ttu-id="e3325-120">ETS 可解決這個問題，方法是提供指令碼語言的通用物件，讓它能夠動態地陳述其型別，以及動態新增成員。</span><span class="sxs-lookup"><span data-stu-id="e3325-120">ETS solves this problem by providing a common object for the scripting language that has the ability to state its type dynamically and to add members dynamically.</span></span>

<span data-ttu-id="e3325-121">基本上，ETS 會解決先前所述的問題，方法是提供**PSObject**物件，以作為所有從指令碼語言存取物件的基礎，並為 Cmdlet 開發人員提供標準的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="e3325-121">Fundamentally, ETS resolves the issue mentioned previously by providing the **PSObject** object, which acts as the basis of all object access from the scripting language and provides a standard abstraction for the cmdlet developer.</span></span>

### <a name="cmdlet-developers"></a><span data-ttu-id="e3325-122">Cmdlet 開發人員</span><span class="sxs-lookup"><span data-stu-id="e3325-122">Cmdlet Developers</span></span>

<span data-ttu-id="e3325-123">對於 Cmdlet 開發人員，ETS 提供下列支援：</span><span class="sxs-lookup"><span data-stu-id="e3325-123">For the cmdlet developers, ETS provides the following support:</span></span>

- <span data-ttu-id="e3325-124">使用**PSObject**物件以一般方式處理物件的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="e3325-124">The abstractions to work against objects in a generic way using the **PSObject** object.</span></span> <span data-ttu-id="e3325-125">ETS 也可讓您在必要時，深入探索這些抽象概念。</span><span class="sxs-lookup"><span data-stu-id="e3325-125">ETS also provides the ability to drill past these abstractions if required.</span></span>
- <span data-ttu-id="e3325-126">使用一組知名的擴充成員，為其物件類型的格式、排序、序列化和其他系統操作建立預設行為的機制。</span><span class="sxs-lookup"><span data-stu-id="e3325-126">The mechanisms to create a default behavior for formatting, sorting, serialization, and other system manipulations of their object type using a well-known set of extended members.</span></span>
- <span data-ttu-id="e3325-127">使用與使用 Languageprimitives.physicalequality 物件之指令碼語言相同的語義，針對任何物件操作的方式。</span><span class="sxs-lookup"><span data-stu-id="e3325-127">The means to operate against any object using the same semantics as the script language using a LanguagePrimitives object.</span></span>
- <span data-ttu-id="e3325-128">動態「輸入」雜湊表的方法，讓系統的其餘部分可以有效地對它進行操作。</span><span class="sxs-lookup"><span data-stu-id="e3325-128">The means to dynamically "type" a hash table so that the rest of the system can operate against it effectively.</span></span>

### <a name="script-developers"></a><span data-ttu-id="e3325-129">腳本開發人員</span><span class="sxs-lookup"><span data-stu-id="e3325-129">Script Developers</span></span>

<span data-ttu-id="e3325-130">針對腳本開發人員，ETS 提供下列支援：</span><span class="sxs-lookup"><span data-stu-id="e3325-130">For the script developers, ETS provides the following support:</span></span>

- <span data-ttu-id="e3325-131">使用相同的語法 () 來參考任何基礎物件類型的能力 `$a.x` 。</span><span class="sxs-lookup"><span data-stu-id="e3325-131">The ability to reference any underlying object type using the same syntax (`$a.x`).</span></span>
- <span data-ttu-id="e3325-132">存取不是**PSObject**物件所提供之抽象概念的能力 (例如僅存取調整的成員，或存取基底物件本身) 。</span><span class="sxs-lookup"><span data-stu-id="e3325-132">The ability to access beyond the abstraction provided by the **PSObject** object (such as accessing only adapted members, or accessing the base object itself).</span></span>
- <span data-ttu-id="e3325-133">能夠定義已知的成員，以控制物件實例或類型的格式設定、排序、序列化和其他操作。</span><span class="sxs-lookup"><span data-stu-id="e3325-133">The ability to define well-known members that control the formatting, sorting, serialization, and other manipulations of an object instance or type.</span></span>
- <span data-ttu-id="e3325-134">表示將物件命名為特定類型，進而控制其型別型成員的繼承。</span><span class="sxs-lookup"><span data-stu-id="e3325-134">The means to name an object as a specific type and thus control the inheritance of its type-based members.</span></span>
- <span data-ttu-id="e3325-135">新增、移除和修改擴充成員的能力。</span><span class="sxs-lookup"><span data-stu-id="e3325-135">The ability to add, remove, and modify extended members.</span></span>
- <span data-ttu-id="e3325-136">必要時操作**PSObject**物件本身的功能。</span><span class="sxs-lookup"><span data-stu-id="e3325-136">The ability to manipulate the **PSObject** object itself if required.</span></span>

## <a name="the-psobject-class"></a><span data-ttu-id="e3325-137">PSObject 類別</span><span class="sxs-lookup"><span data-stu-id="e3325-137">The PSObject class</span></span>

<span data-ttu-id="e3325-138">**PSObject**物件是所有從指令碼語言存取物件的基礎，並為 Cmdlet 開發人員提供標準的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="e3325-138">The **PSObject** object is the basis of all object access from the scripting language and provides a standard abstraction for the cmdlet developer.</span></span> <span data-ttu-id="e3325-139">它包含一個基底物件 (.NET 物件) 和任何實例成員 (成員（特別是擴充成員）存在於特定物件實例上，而不一定是相同類型) 的其他物件。</span><span class="sxs-lookup"><span data-stu-id="e3325-139">It contains a base-object (a .NET object) and any instance members (members, specifically extended members, that are present on a particular object instance while not necessarily on other objects of the same type).</span></span> <span data-ttu-id="e3325-140">根據基底物件的類型而定， **PSObject**物件也可能提供對調整成員的隱含和明確存取權，以及任何以類型為基礎的擴充成員。</span><span class="sxs-lookup"><span data-stu-id="e3325-140">Depending on the type of the base-object, the **PSObject** object might also provide implicit and explicit access to adapted members as well as any type-based extended members.</span></span>

<span data-ttu-id="e3325-141">**PSObject**物件提供下列機制：</span><span class="sxs-lookup"><span data-stu-id="e3325-141">The **PSObject** object provides the following mechanisms:</span></span>

- <span data-ttu-id="e3325-142">能夠在不使用基底物件的情況下，建立**PSObject** 。</span><span class="sxs-lookup"><span data-stu-id="e3325-142">The ability to construct an **PSObject** with or without a base-object.</span></span>
- <span data-ttu-id="e3325-143">透過一般查閱演算法存取每個已建立之**PSObject**物件的所有成員，以及在需要時覆寫該演算法的功能。</span><span class="sxs-lookup"><span data-stu-id="e3325-143">The ability to access of all members of each constructed **PSObject** object through a common lookup algorithm and the ability to override that algorithm when required.</span></span>
- <span data-ttu-id="e3325-144">能夠取得和設定所建立之**psobject**物件的型別名稱，讓腳本和 Cmdlet 可以根據相同的型別名稱來參考類似的**PSObject**物件，而不論其基底物件的型別為何。</span><span class="sxs-lookup"><span data-stu-id="e3325-144">The ability to get and set the type-names of the constructed **PSObject** objects so that scripts and cmdlets can reference similar **PSObject** objects by the same type-name, regardless of the type of their base-object.</span></span>

### <a name="how-to-construct-a-psobject"></a><span data-ttu-id="e3325-145">如何建立 PSObject</span><span class="sxs-lookup"><span data-stu-id="e3325-145">How to Construct a PSObject</span></span>

<span data-ttu-id="e3325-146">下列清單描述建立**PSObject**物件的方式：</span><span class="sxs-lookup"><span data-stu-id="e3325-146">The following list describes ways to create a **PSObject** object:</span></span>

- <span data-ttu-id="e3325-147">呼叫**PSObject** . #ctor 的函式會使用 PSCustomObject 的基底物件來建立新的**PSObject**物件。</span><span class="sxs-lookup"><span data-stu-id="e3325-147">Calling the **PSObject** .#ctor constructor creates a new **PSObject** object with a base-object of PSCustomObject.</span></span> <span data-ttu-id="e3325-148">這個類型的基底物件表示**PSObject**物件沒有有意義的基底物件。</span><span class="sxs-lookup"><span data-stu-id="e3325-148">A base-object of this type indicates that the **PSObject** object has no meaningful base-object.</span></span> <span data-ttu-id="e3325-149">不過，此類型為基底物件的**PSObject**物件確實提供了屬性包，Cmdlet 開發人員可以藉由新增擴充成員來尋找有用的功能。</span><span class="sxs-lookup"><span data-stu-id="e3325-149">However, a **PSObject** object with this type of base-object does provide a property bag that cmdlet developers can find helpful by adding extended-members.</span></span>

<span data-ttu-id="e3325-150">開發人員也可以指定物件類型名稱，讓這個物件可以與相同類型名稱的其他**PSObject**物件共用其擴充成員。</span><span class="sxs-lookup"><span data-stu-id="e3325-150">Developers can also specify the object type-name, which allows this object to share its extended-members with other **PSObject** objects of the same type-name.</span></span>

- <span data-ttu-id="e3325-151">呼叫**PSObject** . #ctor (system.object) 的函式會使用 system.object 類型的基底物件來建立新的**PSObject**物件。</span><span class="sxs-lookup"><span data-stu-id="e3325-151">Calling the **PSObject** .#ctor(System.Object) constructor creates a new **PSObject** object with a base-object of type System.Object.</span></span>

  <span data-ttu-id="e3325-152">在此情況下，所建立物件的類型名稱是基底物件之衍生階層的集合。</span><span class="sxs-lookup"><span data-stu-id="e3325-152">In this case, the type-name for the created object is a collection of the derivation hierarchy of the base-object.</span></span> <span data-ttu-id="e3325-153">例如，包含 ProcessInfo 基底物件之**PSObject**的類型名稱會包含下列名稱：</span><span class="sxs-lookup"><span data-stu-id="e3325-153">For example, the type-name for the **PSObject** that contains a ProcessInfo base-object would include the following names:</span></span>

  - <span data-ttu-id="e3325-154">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="e3325-154">System.Diagnostics.Process</span></span>
  - <span data-ttu-id="e3325-155">System.workflow.componentmodel.activity 元件</span><span class="sxs-lookup"><span data-stu-id="e3325-155">System.ComponentModel.Component</span></span>
  - <span data-ttu-id="e3325-156">System.MarshalByRefObject</span><span class="sxs-lookup"><span data-stu-id="e3325-156">System.MarshalByRefObject</span></span>
  - <span data-ttu-id="e3325-157">System.Object</span><span class="sxs-lookup"><span data-stu-id="e3325-157">System.Object</span></span>

- <span data-ttu-id="e3325-158">呼叫**PSObject** 。AsPSObject (System.object) 方法會根據提供的物件建立新的**PSObject**物件。</span><span class="sxs-lookup"><span data-stu-id="e3325-158">Calling the **PSObject** .AsPSObject(System.Object) method creates a new **PSObject** object based on a supplied object.</span></span>

  <span data-ttu-id="e3325-159">如果提供的物件為 System.object 類型，則會使用提供的物件做為新**PSObject**物件的基底物件。</span><span class="sxs-lookup"><span data-stu-id="e3325-159">If the supplied object is of type System.Object, the supplied object is used as the base-object for the new **PSObject** object.</span></span> <span data-ttu-id="e3325-160">如果提供的物件已經是**PSObject**物件，則提供的物件會以 is 的方式傳回。</span><span class="sxs-lookup"><span data-stu-id="e3325-160">If the supplied object is already an **PSObject** object, the supplied object is returned as is.</span></span>

### <a name="base-adapted-and-extended-members"></a><span data-ttu-id="e3325-161">Base、改編和擴充成員</span><span class="sxs-lookup"><span data-stu-id="e3325-161">Base, adapted, and extended members</span></span>

<span data-ttu-id="e3325-162">在概念上，ETS 會使用下列詞彙來顯示基底物件的原始成員與 PowerShell 新增的成員之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="e3325-162">Conceptually, ETS uses the following terms to show the relationship between the original members of the base-object and those members added by PowerShell.</span></span> <span data-ttu-id="e3325-163">如需**PSObject**物件所使用之特定成員類型的詳細資訊，請參閱[psobject 類別](/dotnet/api/system.management.automation.psobject)。</span><span class="sxs-lookup"><span data-stu-id="e3325-163">For more information about the specific types of members that are used by the **PSObject** object, see [PSObject class](/dotnet/api/system.management.automation.psobject).</span></span>

#### <a name="base-object-members"></a><span data-ttu-id="e3325-164">基底物件成員</span><span class="sxs-lookup"><span data-stu-id="e3325-164">Base-object members</span></span>

<span data-ttu-id="e3325-165">如果在建立**PSObject**物件時指定了基底物件，則會透過 members 屬性來提供基底物件的成員。</span><span class="sxs-lookup"><span data-stu-id="e3325-165">If the base-object is specified when constructing the **PSObject** objects, then the members of the base-object are made available through the Members property.</span></span>

#### <a name="adapted-members"></a><span data-ttu-id="e3325-166">改編的成員</span><span class="sxs-lookup"><span data-stu-id="e3325-166">Adapted members</span></span>

<span data-ttu-id="e3325-167">當基底物件是中繼物件時，其中一個會以一般的方式包含資料，而其屬性「描述」其包含的資料，ETS 會將這些物件調整為可透過調整的**PSObject**物件成員直接存取資料的視圖。</span><span class="sxs-lookup"><span data-stu-id="e3325-167">When a base-object is a meta-object, one that contains data in a generic fashion whose properties "describe" their contained data, ETS adapts those objects to a view that allows for direct access to the data through adapted members of the **PSObject** object.</span></span> <span data-ttu-id="e3325-168">調整的成員和基底物件成員是透過 Members 屬性來存取。</span><span class="sxs-lookup"><span data-stu-id="e3325-168">Adapted members and base-object members are accessed through the Members property.</span></span>

#### <a name="extended-members"></a><span data-ttu-id="e3325-169">擴充成員</span><span class="sxs-lookup"><span data-stu-id="e3325-169">Extended members</span></span>

<span data-ttu-id="e3325-170">除了從基底物件或由 PowerShell 所建立的調整成員所提供的成員之外， **PSObject**也可以定義擴充成員，以擴充原始的基底物件，以及在腳本環境中有用的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="e3325-170">In addition to the members made available from the base-object or those adapted members created by PowerShell, an **PSObject** may also define extended members that extend the original base-object with additional information that is useful in the scripting environment.</span></span>

<span data-ttu-id="e3325-171">例如，PowerShell 提供的所有核心 Cmdlet （例如 Get-Content 和 Set-Content Cmdlet）都會採用 path 參數。</span><span class="sxs-lookup"><span data-stu-id="e3325-171">For example, all the core cmdlets provided by PowerShell, such as the Get-Content and Set-Content cmdlets, take a path parameter.</span></span> <span data-ttu-id="e3325-172">為了確保這些指令程式和其他 Cmdlet 可以處理不同類型的物件，可以將路徑成員新增至這些物件，使其以一般方式將其資訊全部陳述。</span><span class="sxs-lookup"><span data-stu-id="e3325-172">To ensure that these cmdlets, and others, can work against objects of different types, a Path member can be added to those objects so that they all state their information in a common way.</span></span> <span data-ttu-id="e3325-173">這個擴充路徑成員可確保 Cmdlet 可以針對所有類型執行，即使基類可能沒有路徑成員也一樣。</span><span class="sxs-lookup"><span data-stu-id="e3325-173">This extended Path member ensures that the cmdlets can work against all those types even though there base class might not have a Path member.</span></span>

<span data-ttu-id="e3325-174">擴充的成員、調整的成員和基底物件成員都是透過 Members 屬性來存取。</span><span class="sxs-lookup"><span data-stu-id="e3325-174">Extended members, adapted members, and base-object members are all accessed through the Members property.</span></span>
