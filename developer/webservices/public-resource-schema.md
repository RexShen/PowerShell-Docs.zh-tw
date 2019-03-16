---
title: 公用資源結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057241"
---
# <a name="public-resource-schema"></a><span data-ttu-id="900e5-102">公用資源結構描述</span><span class="sxs-lookup"><span data-stu-id="900e5-102">Public Resource Schema</span></span>

<span data-ttu-id="900e5-103">管理 OData 會使用 MOF，來定義資源和其屬性。</span><span class="sxs-lookup"><span data-stu-id="900e5-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="900e5-104">Management OData 實體的屬性直接對應到基礎的 cmdlet 所傳回之 managed 型別的屬性。</span><span class="sxs-lookup"><span data-stu-id="900e5-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="900e5-105">定義資源</span><span class="sxs-lookup"><span data-stu-id="900e5-105">Defining a resource</span></span>

<span data-ttu-id="900e5-106">每個資源會對應至 Windows PowerShell cmdlet 所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="900e5-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="900e5-107">在公用資源的 MOF 檔案中，您可以定義資源所宣告的類別。</span><span class="sxs-lookup"><span data-stu-id="900e5-107">In the public resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="900e5-108">類別包含的屬性會對應至物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="900e5-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="900e5-109">例如，在下列範例中， [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)類別由下列的 MOF。</span><span class="sxs-lookup"><span data-stu-id="900e5-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

```csharp
class PswsTest_Process
{
    [Key] SInt32 Id;
    [Required] SInt32 BasePriority;
    [Required] SInt32 HandleCount;
    [Required] string MachineName;
    [Required] SInt32 MainWindowHandle;

    ...
};
```

<span data-ttu-id="900e5-110">每個屬性名稱會加上的資料類型。</span><span class="sxs-lookup"><span data-stu-id="900e5-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="900e5-111">在此範例中的資料類型對應至基本的 CLR 資料型別在.NET Framework 中，但屬性也可以是其他資源或兩者都稍後說明的複雜型別參考。</span><span class="sxs-lookup"><span data-stu-id="900e5-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="900e5-112">`Key`限定詞表示的屬性用來唯一識別資源執行個體。</span><span class="sxs-lookup"><span data-stu-id="900e5-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="900e5-113">資源可以有多個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="900e5-113">A resource can have more than one key.</span></span>

<span data-ttu-id="900e5-114">`Required`限定詞表示的屬性是必要。</span><span class="sxs-lookup"><span data-stu-id="900e5-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="900e5-115">如果屬性會標示`Key`辨識符號，它會被視為必要的而`Required`限定詞不需要。</span><span class="sxs-lookup"><span data-stu-id="900e5-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="900e5-116">複雜資料型別</span><span class="sxs-lookup"><span data-stu-id="900e5-116">Complex data types</span></span>

<span data-ttu-id="900e5-117">實體的屬性可以有複雜資料型別。</span><span class="sxs-lookup"><span data-stu-id="900e5-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="900e5-118">複雜資料型別是組成其他類型，類似於以 C 程式設計語言的結構的型別。</span><span class="sxs-lookup"><span data-stu-id="900e5-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="900e5-119">複雜型別之 MOF 檔案中宣告為具有類別`ComplexType`限定詞，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="900e5-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="900e5-120">若要宣告成複雜類型的實體屬性，您將它宣告為`string`型別與`EmbeddedInstance`辨識符號，包括複雜型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="900e5-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="900e5-121">下列範例顯示的屬性宣告`PswsTest_ProcessModule`在上述範例中宣告的型別。</span><span class="sxs-lookup"><span data-stu-id="900e5-121">The following example shows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="900e5-122">相關聯的實體</span><span class="sxs-lookup"><span data-stu-id="900e5-122">Associating entities</span></span>

<span data-ttu-id="900e5-123">您可以使用關聯與 AssociationClass 限定詞，將兩個實體產生關聯。</span><span class="sxs-lookup"><span data-stu-id="900e5-123">You can associate two entities by using the Association and AssociationClass qualifiers.</span></span> <span data-ttu-id="900e5-124">如需詳細資訊，請參閱 <<c0> [ 產生關聯的管理 OData 實體](./associating-management-odata-entities.md)。</span><span class="sxs-lookup"><span data-stu-id="900e5-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="900e5-125">衍生型別</span><span class="sxs-lookup"><span data-stu-id="900e5-125">Derived types</span></span>

<span data-ttu-id="900e5-126">您可以從另一個型別衍生型別。</span><span class="sxs-lookup"><span data-stu-id="900e5-126">You can derive a type from another type.</span></span> <span data-ttu-id="900e5-127">衍生的型別可繼承的所有屬性的型別從其衍生除了明確衍生的任何屬性。</span><span class="sxs-lookup"><span data-stu-id="900e5-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="900e5-128">下列範例會顯示型別宣告，然後是衍生自該類型的兩種類型的宣告。</span><span class="sxs-lookup"><span data-stu-id="900e5-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

```csharp
Class Product {

    [Key] String ProductName;

};

Class DairyProduct : Product {

    Uint16 PercentFat;
};
Class POPProduct : Product {

    Boolean IsCarbonated;
};
```