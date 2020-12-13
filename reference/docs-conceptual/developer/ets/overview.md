---
ms.date: 07/09/2020
ms.topic: reference
title: 擴充類型系統總覽
description: 擴充類型系統總覽
ms.openlocfilehash: f4a789f779fa8a52f0fe524abff7ec3311e93b6c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655730"
---
# <a name="extended-type-system-overview"></a><span data-ttu-id="a5c0b-103">擴充類型系統總覽</span><span class="sxs-lookup"><span data-stu-id="a5c0b-103">Extended Type System Overview</span></span>

<span data-ttu-id="a5c0b-104">PowerShell 使用其 **PSObject** 物件以兩種方式擴充物件的類型。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-104">PowerShell uses its **PSObject** object to extend the types of objects in two ways.</span></span> <span data-ttu-id="a5c0b-105">首先， **PSObject** 物件會提供一種方式來顯示特定物件類型的不同視圖。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-105">First, the **PSObject** object provides a way to show different views of specific object types.</span></span> <span data-ttu-id="a5c0b-106">這稱為顯示物件的調整視圖。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-106">This is referred to as showing an adapted view of an object.</span></span> <span data-ttu-id="a5c0b-107">其次， **PSObject** 物件提供將成員新增至現有物件的方法。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-107">Second, the **PSObject** object provides a way to add members to existing object.</span></span> <span data-ttu-id="a5c0b-108">藉由包裝現有的物件（稱為基底物件）， **PSObject** 物件會提供擴充類型系統 (ETS) ，腳本和 Cmdlet 開發人員可以使用該介面來操作 shell 內的 .net 物件。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-108">Together, by wrapping an existing object, referred to as the base object, the **PSObject** object provides an extended type system (ETS) that script and cmdlet developers can use to manipulate .NET objects within the shell.</span></span>

## <a name="cmdlet-and-script-development-issues"></a><span data-ttu-id="a5c0b-109">Cmdlet 和腳本開發問題</span><span class="sxs-lookup"><span data-stu-id="a5c0b-109">Cmdlet and Script Development Issues</span></span>

<span data-ttu-id="a5c0b-110">ETS 可解決兩個基本問題：</span><span class="sxs-lookup"><span data-stu-id="a5c0b-110">ETS resolves two fundamental issues:</span></span>

<span data-ttu-id="a5c0b-111">首先，某些 .NET 物件沒有必要的預設行為，可作為 Cmdlet 之間的資料。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-111">First, some .NET Objects do not have the necessary default behavior for acting as the data between cmdlets.</span></span>

- <span data-ttu-id="a5c0b-112">某些 .NET 物件是 "meta" 物件 (例如： WMI 物件、ADO 物件和 XML 物件) 其成員描述其包含的資料。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-112">Some .NET objects are "meta" objects (for example: WMI Objects, ADO objects, and XML objects) whose members describe the data they contain.</span></span> <span data-ttu-id="a5c0b-113">不過，在腳本環境中，它是包含最重要的資料，而不是包含資料的描述。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-113">However, in a scripting environment it is the contained data that is most interesting, not the description of the contained data.</span></span> <span data-ttu-id="a5c0b-114">ETS 藉由引進調整基礎 .NET 物件以具有預期預設語義的介面卡概念來解決此問題。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-114">ETS resolves this issue by introducing the notion of Adapters that adapt the underlying .NET object to have the expected default semantics.</span></span>
- <span data-ttu-id="a5c0b-115">某些 .NET 物件成員的名稱不一致、提供的公用成員集不足，或提供的功能不足。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-115">Some .NET Object members are inconsistently named, provide an insufficient set of public members, or provide insufficient capability.</span></span> <span data-ttu-id="a5c0b-116">ETS 藉由引進擴充 .NET 物件與其他成員的功能來解決此問題。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-116">ETS resolves this issue by introducing the ability to extend the .NET object with additional members.</span></span>

<span data-ttu-id="a5c0b-117">其次，PowerShell 腳本 _語言是無型別，因為_ 變數不需要宣告特定型別。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-117">Second, the PowerShell scripting language is _typeless_ in that a variable does not need to be declared of a particular type.</span></span> <span data-ttu-id="a5c0b-118">也就是說，腳本開發人員所建立的變數 _是本質上_ 的類型。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-118">That is, the variables a script developer creates are by nature _typeless_.</span></span> <span data-ttu-id="a5c0b-119">不過，PowerShell 系統是「型別驅動」，因為它相依于具有可針對基本作業（例如輸出結果或排序）進行操作的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-119">However, the PowerShell system is "type-driven" in that it depends on having a type name to operate against for basic operations such as outputting results or sorting.</span></span>

<span data-ttu-id="a5c0b-120">因此，腳本開發人員必須能夠陳述其中一個變數的類型，並建立自己的一組動態類型「物件」，其中包含屬性和方法，而且可以參與型別驅動系統。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-120">Therefore a script developer must have the ability to state the type of one of their variables and build up their own set of dynamically typed "objects" that contain properties and methods and can participate in the type-driven system.</span></span> <span data-ttu-id="a5c0b-121">ETS 可解決這個問題，方法是提供指令碼語言的通用物件，讓它能夠動態地指出其型別並動態新增成員。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-121">ETS solves this problem by providing a common object for the scripting language that has the ability to state its type dynamically and to add members dynamically.</span></span>

<span data-ttu-id="a5c0b-122">基本上，ETS 會藉由提供 **PSObject** 物件來解決先前所述的問題，該物件會作為從指令碼語言存取所有物件的基礎，並為 Cmdlet 開發人員提供標準的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-122">Fundamentally, ETS resolves the issue mentioned previously by providing the **PSObject** object, which acts as the basis of all object access from the scripting language and provides a standard abstraction for the cmdlet developer.</span></span>

### <a name="cmdlet-developers"></a><span data-ttu-id="a5c0b-123">Cmdlet 開發人員</span><span class="sxs-lookup"><span data-stu-id="a5c0b-123">Cmdlet Developers</span></span>

<span data-ttu-id="a5c0b-124">針對 Cmdlet 開發人員，ETS 提供下列支援：</span><span class="sxs-lookup"><span data-stu-id="a5c0b-124">For the cmdlet developers, ETS provides the following support:</span></span>

- <span data-ttu-id="a5c0b-125">使用 **PSObject** 物件以一般方式處理物件的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-125">The abstractions to work against objects in a generic way using the **PSObject** object.</span></span> <span data-ttu-id="a5c0b-126">ETS 也可讓您視需要深入瞭解這些抽象概念。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-126">ETS also provides the ability to drill past these abstractions if required.</span></span>
- <span data-ttu-id="a5c0b-127">使用已知的擴充成員集合，為物件類型的格式設定、排序、序列化和其他系統操作建立預設行為的機制。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-127">The mechanisms to create a default behavior for formatting, sorting, serialization, and other system manipulations of their object type using a well-known set of extended members.</span></span>
- <span data-ttu-id="a5c0b-128">使用 Languageprimitives.physicalequality 物件，針對使用與指令碼語言相同之語義的任何物件進行操作的方法。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-128">The means to operate against any object using the same semantics as the script language using a LanguagePrimitives object.</span></span>
- <span data-ttu-id="a5c0b-129">以動態方式「輸入」雜湊表的方式，讓系統的其餘部分可以有效地操作。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-129">The means to dynamically "type" a hash table so that the rest of the system can operate against it effectively.</span></span>

### <a name="script-developers"></a><span data-ttu-id="a5c0b-130">腳本開發人員</span><span class="sxs-lookup"><span data-stu-id="a5c0b-130">Script Developers</span></span>

<span data-ttu-id="a5c0b-131">針對腳本開發人員，ETS 提供下列支援：</span><span class="sxs-lookup"><span data-stu-id="a5c0b-131">For the script developers, ETS provides the following support:</span></span>

- <span data-ttu-id="a5c0b-132">使用相同語法 () 來參考任何基礎物件類型的能力 `$a.x` 。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-132">The ability to reference any underlying object type using the same syntax (`$a.x`).</span></span>
- <span data-ttu-id="a5c0b-133">存取 **PSObject** 物件所提供之抽象概念以外的能力 (例如只存取調整的成員，或存取基底物件本身) 。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-133">The ability to access beyond the abstraction provided by the **PSObject** object (such as accessing only adapted members, or accessing the base object itself).</span></span>
- <span data-ttu-id="a5c0b-134">能夠定義知名的成員，以控制物件實例或型別的格式化、排序、序列化和其他操作。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-134">The ability to define well-known members that control the formatting, sorting, serialization, and other manipulations of an object instance or type.</span></span>
- <span data-ttu-id="a5c0b-135">將物件命名為特定類型，進而控制其型別型成員繼承的方法。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-135">The means to name an object as a specific type and thus control the inheritance of its type-based members.</span></span>
- <span data-ttu-id="a5c0b-136">新增、移除和修改擴充成員的能力。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-136">The ability to add, remove, and modify extended members.</span></span>
- <span data-ttu-id="a5c0b-137">必要時操作 **PSObject** 物件本身的能力。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-137">The ability to manipulate the **PSObject** object itself if required.</span></span>

## <a name="the-psobject-class"></a><span data-ttu-id="a5c0b-138">PSObject 類別</span><span class="sxs-lookup"><span data-stu-id="a5c0b-138">The PSObject class</span></span>

<span data-ttu-id="a5c0b-139">**PSObject** 物件是從指令碼語言存取所有物件的基礎，並且為 Cmdlet 開發人員提供標準的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-139">The **PSObject** object is the basis of all object access from the scripting language and provides a standard abstraction for the cmdlet developer.</span></span> <span data-ttu-id="a5c0b-140">它包含一個基底物件， (.NET 物件) ，以及在特定物件實例上的任何實例成員 (成員（特別是擴充成員），而不一定會出現在相同類型) 的其他物件上。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-140">It contains a base-object (a .NET object) and any instance members (members, specifically extended members, that are present on a particular object instance while not necessarily on other objects of the same type).</span></span> <span data-ttu-id="a5c0b-141">根據基底物件的類型而定， **PSObject** 物件也可能會對調整的成員以及任何以類型為基礎的擴充成員提供隱含且明確的存取權。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-141">Depending on the type of the base-object, the **PSObject** object might also provide implicit and explicit access to adapted members as well as any type-based extended members.</span></span>

<span data-ttu-id="a5c0b-142">**PSObject** 物件提供下列機制：</span><span class="sxs-lookup"><span data-stu-id="a5c0b-142">The **PSObject** object provides the following mechanisms:</span></span>

- <span data-ttu-id="a5c0b-143">使用或不含基底物件來建立 **PSObject** 的能力。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-143">The ability to construct an **PSObject** with or without a base-object.</span></span>
- <span data-ttu-id="a5c0b-144">透過一般查閱演算法來存取每個已建立之 **PSObject** 物件的所有成員，以及在必要時覆寫該演算法的能力。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-144">The ability to access of all members of each constructed **PSObject** object through a common lookup algorithm and the ability to override that algorithm when required.</span></span>
- <span data-ttu-id="a5c0b-145">取得和設定所建立之 **psobject** 物件的型別名稱的能力，讓腳本和 Cmdlet 可以參考相同型別名稱的類似 **PSObject** 物件，不論其基底物件的型別為何。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-145">The ability to get and set the type-names of the constructed **PSObject** objects so that scripts and cmdlets can reference similar **PSObject** objects by the same type-name, regardless of the type of their base-object.</span></span>

### <a name="how-to-construct-a-psobject"></a><span data-ttu-id="a5c0b-146">如何建立 PSObject</span><span class="sxs-lookup"><span data-stu-id="a5c0b-146">How to Construct a PSObject</span></span>

<span data-ttu-id="a5c0b-147">下列清單描述建立 **PSObject** 物件的方式：</span><span class="sxs-lookup"><span data-stu-id="a5c0b-147">The following list describes ways to create a **PSObject** object:</span></span>

- <span data-ttu-id="a5c0b-148">呼叫 **PSObject** . #ctor 的函式會使用 PSCustomObject 的基底物件來建立新的 **PSObject** 物件。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-148">Calling the **PSObject** .#ctor constructor creates a new **PSObject** object with a base-object of PSCustomObject.</span></span> <span data-ttu-id="a5c0b-149">這個型別的基底物件表示 **PSObject** 物件沒有有意義的基底物件。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-149">A base-object of this type indicates that the **PSObject** object has no meaningful base-object.</span></span> <span data-ttu-id="a5c0b-150">不過，具有這種類型之基底物件的 **PSObject** 物件確實提供了一個屬性包，讓指令程式開發人員可以藉由新增擴充成員找到實用的功能。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-150">However, a **PSObject** object with this type of base-object does provide a property bag that cmdlet developers can find helpful by adding extended-members.</span></span>

<span data-ttu-id="a5c0b-151">開發人員也可以指定物件類型名稱，以允許此物件與相同類型名稱的其他 **PSObject** 物件共用其擴充成員。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-151">Developers can also specify the object type-name, which allows this object to share its extended-members with other **PSObject** objects of the same type-name.</span></span>

- <span data-ttu-id="a5c0b-152">呼叫 **PSObject** . #ctor (system.string) 的函式會建立一個新的 **PSObject** 物件，其基底物件為 system.object 類型。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-152">Calling the **PSObject** .#ctor(System.Object) constructor creates a new **PSObject** object with a base-object of type System.Object.</span></span>

  <span data-ttu-id="a5c0b-153">在此情況下，所建立物件的型別名稱就是基底物件之衍生階層的集合。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-153">In this case, the type-name for the created object is a collection of the derivation hierarchy of the base-object.</span></span> <span data-ttu-id="a5c0b-154">例如，包含 ProcessInfo 基底物件之 **PSObject** 的類型名稱會包含下列名稱：</span><span class="sxs-lookup"><span data-stu-id="a5c0b-154">For example, the type-name for the **PSObject** that contains a ProcessInfo base-object would include the following names:</span></span>

  - <span data-ttu-id="a5c0b-155">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="a5c0b-155">System.Diagnostics.Process</span></span>
  - <span data-ttu-id="a5c0b-156">ComponentModel 元件</span><span class="sxs-lookup"><span data-stu-id="a5c0b-156">System.ComponentModel.Component</span></span>
  - <span data-ttu-id="a5c0b-157">System.MarshalByRefObject</span><span class="sxs-lookup"><span data-stu-id="a5c0b-157">System.MarshalByRefObject</span></span>
  - <span data-ttu-id="a5c0b-158">System.Object</span><span class="sxs-lookup"><span data-stu-id="a5c0b-158">System.Object</span></span>

- <span data-ttu-id="a5c0b-159">呼叫 **PSObject** 。AsPSObject (System.object) 方法會根據提供的物件建立新的 **PSObject** 物件。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-159">Calling the **PSObject** .AsPSObject(System.Object) method creates a new **PSObject** object based on a supplied object.</span></span>

  <span data-ttu-id="a5c0b-160">如果提供的物件為 system.string 類型，則會使用提供的物件做為新 **PSObject** 物件的基底物件。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-160">If the supplied object is of type System.Object, the supplied object is used as the base-object for the new **PSObject** object.</span></span> <span data-ttu-id="a5c0b-161">如果提供的物件已經是 **PSObject** 物件，則會以原樣傳回提供的物件。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-161">If the supplied object is already an **PSObject** object, the supplied object is returned as is.</span></span>

### <a name="base-adapted-and-extended-members"></a><span data-ttu-id="a5c0b-162">基底、調整及擴充成員</span><span class="sxs-lookup"><span data-stu-id="a5c0b-162">Base, adapted, and extended members</span></span>

<span data-ttu-id="a5c0b-163">就概念而言，ETS 會使用下列詞彙來顯示基底物件的原始成員與 PowerShell 新增的成員之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-163">Conceptually, ETS uses the following terms to show the relationship between the original members of the base-object and those members added by PowerShell.</span></span> <span data-ttu-id="a5c0b-164">如需 **psobject** 物件所使用之特定類型成員的詳細資訊，請參閱 [psobject 類別](/dotnet/api/system.management.automation.psobject)。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-164">For more information about the specific types of members that are used by the **PSObject** object, see [PSObject class](/dotnet/api/system.management.automation.psobject).</span></span>

#### <a name="base-object-members"></a><span data-ttu-id="a5c0b-165">基底物件成員</span><span class="sxs-lookup"><span data-stu-id="a5c0b-165">Base-object members</span></span>

<span data-ttu-id="a5c0b-166">如果在建立 **PSObject** 物件時指定了基底物件，則基底物件的成員可透過 members 屬性取得。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-166">If the base-object is specified when constructing the **PSObject** objects, then the members of the base-object are made available through the Members property.</span></span>

#### <a name="adapted-members"></a><span data-ttu-id="a5c0b-167">改編的成員</span><span class="sxs-lookup"><span data-stu-id="a5c0b-167">Adapted members</span></span>

<span data-ttu-id="a5c0b-168">當基底物件是中繼物件時，其中一個物件會以一般方式（其屬性「描述」其包含的資料）來包含資料，ETS 會將這些物件調整為可讓您透過調整的 **PSObject** 物件成員直接存取資料的視圖。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-168">When a base-object is a meta-object, one that contains data in a generic fashion whose properties "describe" their contained data, ETS adapts those objects to a view that allows for direct access to the data through adapted members of the **PSObject** object.</span></span> <span data-ttu-id="a5c0b-169">您可以透過 Members 屬性來存取調整的成員和基底物件成員。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-169">Adapted members and base-object members are accessed through the Members property.</span></span>

#### <a name="extended-members"></a><span data-ttu-id="a5c0b-170">擴充成員</span><span class="sxs-lookup"><span data-stu-id="a5c0b-170">Extended members</span></span>

<span data-ttu-id="a5c0b-171">除了從基底物件或由 PowerShell 所建立的調整成員中提供的成員之外， **PSObject** 也可以定義擴充成員，以擴充原始的基底物件與腳本環境中有用的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-171">In addition to the members made available from the base-object or those adapted members created by PowerShell, an **PSObject** may also define extended members that extend the original base-object with additional information that is useful in the scripting environment.</span></span>

<span data-ttu-id="a5c0b-172">例如，PowerShell 提供的所有核心 Cmdlet （例如 Get-Content 和 Set-Content Cmdlet）都會採用 path 參數。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-172">For example, all the core cmdlets provided by PowerShell, such as the Get-Content and Set-Content cmdlets, take a path parameter.</span></span> <span data-ttu-id="a5c0b-173">為了確保這些 Cmdlet 和其他 Cmdlet 可以針對不同類型的物件來工作，您可以將路徑成員新增至這些物件，讓它們都能以一般方式來陳述其資訊。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-173">To ensure that these cmdlets, and others, can work against objects of different types, a Path member can be added to those objects so that they all state their information in a common way.</span></span> <span data-ttu-id="a5c0b-174">這個擴充路徑成員可以確保 Cmdlet 可以針對所有這些類型運作，即使基類可能沒有路徑成員也一樣。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-174">This extended Path member ensures that the cmdlets can work against all those types even though there base class might not have a Path member.</span></span>

<span data-ttu-id="a5c0b-175">擴充的成員、調整的成員和基底物件成員都是透過 Members 屬性來存取。</span><span class="sxs-lookup"><span data-stu-id="a5c0b-175">Extended members, adapted members, and base-object members are all accessed through the Members property.</span></span>
