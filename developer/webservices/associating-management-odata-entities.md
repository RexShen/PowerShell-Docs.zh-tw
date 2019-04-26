---
title: 建立管理 OData 實體的關聯 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080742"
---
# <a name="associating-management-odata-entities"></a><span data-ttu-id="f6938-102">建立 Management OData 實體的關聯</span><span class="sxs-lookup"><span data-stu-id="f6938-102">Associating Management OData Entities</span></span>

<span data-ttu-id="f6938-103">通常很有用來建立兩個不同的管理 OData 實體之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="f6938-103">It is often useful to create an association between two different Management OData entities.</span></span> <span data-ttu-id="f6938-104">比方說，管理 OData 服務可以管理組織之分類的產品目錄的實體，並且定義實體`Product`和`Category`。</span><span class="sxs-lookup"><span data-stu-id="f6938-104">For example, a Management OData service could have entities that manage a catalogue of products that are organized in categories, and define the entities `Product` and `Category`.</span></span> <span data-ttu-id="f6938-105">這兩個實體建立關聯之後，用戶端可以取得某個類別目錄 web 服務的單一要求中的所有產品的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f6938-105">By associating these two entities, a client can get information about all of the products in a category with a single request to the web service.</span></span>

<span data-ttu-id="f6938-106">此範例示範如何建立實體之間的關聯，請下載位置[關聯範例](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e)。</span><span class="sxs-lookup"><span data-stu-id="f6938-106">A sample that shows how to create associations between entities can be downloaded at [Association sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span></span>

## <a name="creating-the-association-in-the-resource-schema-file"></a><span data-ttu-id="f6938-107">資源檔中的結構描述建立關聯</span><span class="sxs-lookup"><span data-stu-id="f6938-107">Creating the Association in the resource schema file</span></span>

<span data-ttu-id="f6938-108">下列的 MOF 定義兩個實體。</span><span class="sxs-lookup"><span data-stu-id="f6938-108">The following MOF defines two entities.</span></span> <span data-ttu-id="f6938-109">我們將建立它們之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="f6938-109">We will create an association between them.</span></span>

```csharp
class Product {

[key] string ProductName;

// other fields ...
};

class Category {

[key] string CategoryName;

string Products[];

// other fields
}
```

<span data-ttu-id="f6938-110">`Category`類別定義的屬性隸屬於該類別的產品名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="f6938-110">The `Category` class defines a property that is an array of the names of the products that belong to that category.</span></span>

<span data-ttu-id="f6938-111">若要建立兩個實體的關聯，您必須定義類別`Association`服務的資源結構描述 MOF 檔案中的屬性。</span><span class="sxs-lookup"><span data-stu-id="f6938-111">To associate two entities, you must define a class with the `Association` attribute in the resource schema MOF file for the service.</span></span> <span data-ttu-id="f6938-112">此類別必須定義兩個實體相關聯，請呼叫`ends`的關聯。</span><span class="sxs-lookup"><span data-stu-id="f6938-112">The class must define the two entities to be associated, called `ends` of the association.</span></span> <span data-ttu-id="f6938-113">下列範例顯示定義的分類和產品實體之間的關聯的類別定義。</span><span class="sxs-lookup"><span data-stu-id="f6938-113">The following example shows a definition of a class that defines an association between the Category and Products entities.</span></span>

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

<span data-ttu-id="f6938-114">您也必須變更類別目錄類別中的 Products 屬性的宣告。</span><span class="sxs-lookup"><span data-stu-id="f6938-114">You must also change the declaration of the Products property in the Category class.</span></span> <span data-ttu-id="f6938-115">您使用`AssociationClass`關鍵字來指定此屬性是關聯的一端。</span><span class="sxs-lookup"><span data-stu-id="f6938-115">You use the `AssociationClass` keyword to specify that the property is one end of the association.</span></span> <span data-ttu-id="f6938-116">屬性也必須定義成個別的實體，而不是字串陣列的參考。</span><span class="sxs-lookup"><span data-stu-id="f6938-116">The property must also be defined as a reference to a separate entity, rather than an array of strings.</span></span> <span data-ttu-id="f6938-117">您可以使用`ref`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f6938-117">You do this by using the `ref` keyword.</span></span> <span data-ttu-id="f6938-118">下列範例會顯示關聯的屬性定義。</span><span class="sxs-lookup"><span data-stu-id="f6938-118">The following example shows the property definition for the association.</span></span>

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

<span data-ttu-id="f6938-119">最後，您必須宣告關聯另一端，藉由新增一個屬性定義`Product`類別。</span><span class="sxs-lookup"><span data-stu-id="f6938-119">Finally, you must declare the other end of the association by adding a property definition to the `Product` class.</span></span> <span data-ttu-id="f6938-120">這是陣列或單一實體的參考。</span><span class="sxs-lookup"><span data-stu-id="f6938-120">This is a reference to either an array or to a single entity.</span></span> <span data-ttu-id="f6938-121">假設每個產品都屬於一種類別，定義是，如下所示。</span><span class="sxs-lookup"><span data-stu-id="f6938-121">Assuming that each product belongs to only one category, the definition would be as follows.</span></span>

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

<span data-ttu-id="f6938-122">代表關聯的兩端的屬性稱為導覽屬性。</span><span class="sxs-lookup"><span data-stu-id="f6938-122">The properties that represent the two ends of the association are called navigation properties.</span></span>

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a><span data-ttu-id="f6938-123">將資源檔中的結構描述的實體產生關聯的步驟</span><span class="sxs-lookup"><span data-stu-id="f6938-123">Steps for associating entities in the resource schema file</span></span>

- <span data-ttu-id="f6938-124">做為類別定義的關聯，藉由使用`Association`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f6938-124">Define the association as a class by using the `Association` keyword.</span></span>

- <span data-ttu-id="f6938-125">使用 AssociationClass 關鍵字來限定，相關聯的實體的屬性，以定義此關聯各端。</span><span class="sxs-lookup"><span data-stu-id="f6938-125">Define the ends of the association by using the AssociationClass keyword to qualify properties of the associated entities.</span></span>

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a><span data-ttu-id="f6938-126">建立資源的對應 XML 檔案中的關聯</span><span class="sxs-lookup"><span data-stu-id="f6938-126">Creating the association in the resource mapping XML file</span></span>

<span data-ttu-id="f6938-127">有三種不同的案例，來對應資源對應 XML 檔案中的關聯時，請考慮。</span><span class="sxs-lookup"><span data-stu-id="f6938-127">There are three different cases to consider when mapping an association in the resource mapping XML file.</span></span>

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a><span data-ttu-id="f6938-128">決定如何將資源對應檔案中的實體產生關聯</span><span class="sxs-lookup"><span data-stu-id="f6938-128">Determining how to associate entities in the resource mapping file</span></span>

- <span data-ttu-id="f6938-129">如果有在基礎的導覽屬性。</span><span class="sxs-lookup"><span data-stu-id="f6938-129">If the navigation property is present in the underlying.</span></span> <span data-ttu-id="f6938-130">.NET framework 型別，以及該屬性包含外部索引鍵，不需要任何明確的對應。</span><span class="sxs-lookup"><span data-stu-id="f6938-130">.NET Framework type, and that property contains foreign keys, no explicit mapping is necessary.</span></span>

- <span data-ttu-id="f6938-131">如果導覽屬性不存在於基礎的.NET Framework 型別中，您必須指定指令程式來擷取索引鍵相關聯的執行個體的清單。</span><span class="sxs-lookup"><span data-stu-id="f6938-131">If the navigation property does not exist in the underlying .NET Framework type, you must specify a cmdlet that retrieves the list of keys of the associated instances.</span></span> <span data-ttu-id="f6938-132">您可以加入`Association`項目之下巢狀`CmdletImplementation`項目，遵循這些元素會定義`cmdlets`CRUD 命令。</span><span class="sxs-lookup"><span data-stu-id="f6938-132">You do this by adding an `Association` element nested under the `CmdletImplementation` element, following the elements that define the `cmdlets` for the other CRUD commands.</span></span>

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- <span data-ttu-id="f6938-133">如果導覽屬性存在於基礎的.NET Framework 型別，但它包含的物件執行個體，而不是外部索引鍵，則您必須建立一個 cmdlet （藉由撰寫 Windows PowerShell 函式或指令碼） 來擷取外部索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f6938-133">If the navigation property does exist in the underlying .NET Framework type, but it contains object instances instead of foreign keys, then you must create a cmdlet (by writing a Windows PowerShell function or script) to retrieve the foreign keys.</span></span> <span data-ttu-id="f6938-134">然後，您會指定該 cmdlet 在資源的對應檔案。</span><span class="sxs-lookup"><span data-stu-id="f6938-134">You then specify that cmdlet in the resource mapping file.</span></span> <span data-ttu-id="f6938-135">比方說，要擷取索引鍵的指令碼看起來會如下所示。</span><span class="sxs-lookup"><span data-stu-id="f6938-135">For example, the script to retrieve the keys would look like the following.</span></span>

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  <span data-ttu-id="f6938-136">與資源對應檔案中的 XML 看起來如下所示。</span><span class="sxs-lookup"><span data-stu-id="f6938-136">And the XML in the resource mapping file would look like the following.</span></span>

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory.ps1</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- <span data-ttu-id="f6938-137">除了指定的 cmdlet 來擷取相關聯的實體，您也可以指定指令程式來新增和移除集合中的參考。</span><span class="sxs-lookup"><span data-stu-id="f6938-137">In addition to specifying a cmdlet to retrieve the associated entities, you can also specify cmdlets to add and remove references from the collection.</span></span> <span data-ttu-id="f6938-138">下列範例假設的新增 ProductToCategory 和移除 ProductFromCategory cmdlet 存在於 （他們也可以定義在指令碼或函式，如先前範例所示）。</span><span class="sxs-lookup"><span data-stu-id="f6938-138">The following example assumes that the Add-ProductToCategory and Remove-ProductFromCategory cmdlets exist (they can also be defined in a script or function as in the previous example).</span></span>

  ```xml
  Class Name="Sample.Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
  ...
              </GetReference>
        <AddReference>
     <CmdletName>"Add-ProductToCategory"</>
     <ParameterForThisObject>"Product"</>
     <ParameterForReferredObject>"Category"</>
        </AddReference>
        <RemoveReference>
     <CmdletName="Remove-ProductFromCategory"/>
     <ParameterForThisObject >"Product"</>
     <ParameterForReferredObject >"Category"</>
        </RemoveReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

## <a name="querying-associated-entities"></a><span data-ttu-id="f6938-139">查詢相關聯的實體</span><span class="sxs-lookup"><span data-stu-id="f6938-139">Querying associated entities</span></span>

<span data-ttu-id="f6938-140">用戶端可以擷取與實體相關聯，藉由建立特定查詢的執行個體清單。</span><span class="sxs-lookup"><span data-stu-id="f6938-140">The client can retrieve a list of the instances associated with an entity by creating specific queries.</span></span>

#### <a name="constructing-queries-for-associated-entities"></a><span data-ttu-id="f6938-141">建構相關聯的實體的查詢</span><span class="sxs-lookup"><span data-stu-id="f6938-141">Constructing queries for associated entities</span></span>

- <span data-ttu-id="f6938-142">用戶端可以要求類別目錄的詳細資料，而未擷取其相關聯的產品。</span><span class="sxs-lookup"><span data-stu-id="f6938-142">A client can request the details of a category without retrieving its associated products.</span></span> <span data-ttu-id="f6938-143">例如，下列要求會取得一份訂單`food`類別目錄。</span><span class="sxs-lookup"><span data-stu-id="f6938-143">For example, the following request gets details of the `food` category.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  <span data-ttu-id="f6938-144">若要取得相關聯的產品類別目錄的 （但未詳細資料的分類，用戶端的要求中指定的導覽屬性。</span><span class="sxs-lookup"><span data-stu-id="f6938-144">To get the associated products of the category (but not details of the category itself, the client specifies the navigation property in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- <span data-ttu-id="f6938-145">若要擷取的產品的 Url，請使用`$links`要求中的限定詞。</span><span class="sxs-lookup"><span data-stu-id="f6938-145">To retrieve only URLs of the products, use the `$links` qualifier in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- <span data-ttu-id="f6938-146">用戶端可以取得分類的詳細資料和其相關聯的產品使用`$expand`限定詞。</span><span class="sxs-lookup"><span data-stu-id="f6938-146">The client can get both the category details and its associated products by using the `$expand` qualifier.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a><span data-ttu-id="f6938-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6938-147">See Also</span></span>

[<span data-ttu-id="f6938-148">建立管理 OData IIS 擴充功能的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="f6938-148">Creating a Management OData IIS Extension Web Service</span></span>](./creating-a-management-odata-web-service.md)