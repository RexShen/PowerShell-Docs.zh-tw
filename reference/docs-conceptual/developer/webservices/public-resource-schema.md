---
title: 公用資源架構 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366267"
---
# <a name="public-resource-schema"></a><span data-ttu-id="348cc-102">公用資源結構描述</span><span class="sxs-lookup"><span data-stu-id="348cc-102">Public Resource Schema</span></span>

<span data-ttu-id="348cc-103">管理 OData 使用 MOF 來定義資源及其屬性。</span><span class="sxs-lookup"><span data-stu-id="348cc-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="348cc-104">管理 OData 實體的屬性會直接對應至基礎 Cmdlet 所傳回之 managed 類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="348cc-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="348cc-105">定義資源</span><span class="sxs-lookup"><span data-stu-id="348cc-105">Defining a resource</span></span>

<span data-ttu-id="348cc-106">每個資源都會對應到 Windows PowerShell Cmdlet 所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="348cc-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="348cc-107">在公用資源 MOF 檔案中，您可以藉由宣告類別來定義資源。</span><span class="sxs-lookup"><span data-stu-id="348cc-107">In the public resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="348cc-108">類別是由對應至物件屬性的屬性所組成。</span><span class="sxs-lookup"><span data-stu-id="348cc-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="348cc-109">例如，在下列範例中，會以下列 MOF 表示[system.web](/dotnet/api/System.Diagnostics.Process)類別。</span><span class="sxs-lookup"><span data-stu-id="348cc-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

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

<span data-ttu-id="348cc-110">每個屬性名稱的前面都有一個資料類型。</span><span class="sxs-lookup"><span data-stu-id="348cc-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="348cc-111">這個範例中的資料類型會對應至 .NET Framework 中的基本 CLR 資料類型，但屬性也可以參考其他資源或複雜類型，這兩種方式都會在稍後說明。</span><span class="sxs-lookup"><span data-stu-id="348cc-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="348cc-112">`Key` 限定詞表示會使用屬性來唯一識別資源實例。</span><span class="sxs-lookup"><span data-stu-id="348cc-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="348cc-113">一個資源可以有一個以上的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="348cc-113">A resource can have more than one key.</span></span>

<span data-ttu-id="348cc-114">`Required` 限定詞表示此為必要屬性。</span><span class="sxs-lookup"><span data-stu-id="348cc-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="348cc-115">如果屬性是以 `Key` 限定詞標示，則會將它視為必要，而且不需要 `Required` 限定詞。</span><span class="sxs-lookup"><span data-stu-id="348cc-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="348cc-116">複雜資料類型</span><span class="sxs-lookup"><span data-stu-id="348cc-116">Complex data types</span></span>

<span data-ttu-id="348cc-117">實體的屬性可以有複雜的資料類型。</span><span class="sxs-lookup"><span data-stu-id="348cc-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="348cc-118">複雜資料類型是由其他類型組成的類型，類似于 C 程式設計語言中的結構。</span><span class="sxs-lookup"><span data-stu-id="348cc-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="348cc-119">在 MOF 檔案中，會將複雜類型宣告為具有 `ComplexType` 限定詞的類別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="348cc-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="348cc-120">若要將實體屬性宣告為複雜型別，請將它宣告為具有 `EmbeddedInstance` 限定詞的 `string` 型別，包括複雜型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="348cc-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="348cc-121">下列範例顯示在上一個範例中宣告之 `PswsTest_ProcessModule` 類型的屬性宣告。</span><span class="sxs-lookup"><span data-stu-id="348cc-121">The following example shows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="348cc-122">關聯實體</span><span class="sxs-lookup"><span data-stu-id="348cc-122">Associating entities</span></span>

<span data-ttu-id="348cc-123">您可以使用 Association 和 AssociationClass 限定詞來建立兩個實體的關聯。</span><span class="sxs-lookup"><span data-stu-id="348cc-123">You can associate two entities by using the Association and AssociationClass qualifiers.</span></span> <span data-ttu-id="348cc-124">如需詳細資訊，請參閱建立[管理 OData 實體的關聯](./associating-management-odata-entities.md)。</span><span class="sxs-lookup"><span data-stu-id="348cc-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="348cc-125">衍生類型</span><span class="sxs-lookup"><span data-stu-id="348cc-125">Derived types</span></span>

<span data-ttu-id="348cc-126">您可以從另一個型別衍生型別。</span><span class="sxs-lookup"><span data-stu-id="348cc-126">You can derive a type from another type.</span></span> <span data-ttu-id="348cc-127">除了明確衍生的任何屬性之外，衍生的型別會繼承它所衍生之型別的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="348cc-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="348cc-128">下列範例顯示類型宣告，然後是衍生自該類型的兩個類型的宣告。</span><span class="sxs-lookup"><span data-stu-id="348cc-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

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