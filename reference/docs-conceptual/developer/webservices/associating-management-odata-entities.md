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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359807"
---
# <a name="associating-management-odata-entities"></a><span data-ttu-id="7482f-102">建立 Management OData 實體的關聯</span><span class="sxs-lookup"><span data-stu-id="7482f-102">Associating Management OData Entities</span></span>

<span data-ttu-id="7482f-103">在兩個不同的管理 OData 實體之間建立關聯通常會很有用。</span><span class="sxs-lookup"><span data-stu-id="7482f-103">It is often useful to create an association between two different Management OData entities.</span></span> <span data-ttu-id="7482f-104">例如，管理 OData 服務可能會有管理以類別組織之產品目錄的實體，並定義 `Product` 和 `Category` 的實體。</span><span class="sxs-lookup"><span data-stu-id="7482f-104">For example, a Management OData service could have entities that manage a catalogue of products that are organized in categories, and define the entities `Product` and `Category`.</span></span> <span data-ttu-id="7482f-105">藉由將這兩個實體產生關聯，用戶端就可以透過單一的 web 服務要求，取得類別中所有產品的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7482f-105">By associating these two entities, a client can get information about all of the products in a category with a single request to the web service.</span></span>

<span data-ttu-id="7482f-106">範例會示範如何在[關聯範例](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e)中下載實體之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="7482f-106">A sample that shows how to create associations between entities can be downloaded at [Association sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span></span>

## <a name="creating-the-association-in-the-resource-schema-file"></a><span data-ttu-id="7482f-107">在資源架構檔案中建立關聯</span><span class="sxs-lookup"><span data-stu-id="7482f-107">Creating the Association in the resource schema file</span></span>

<span data-ttu-id="7482f-108">下列 MOF 會定義兩個實體。</span><span class="sxs-lookup"><span data-stu-id="7482f-108">The following MOF defines two entities.</span></span> <span data-ttu-id="7482f-109">我們會建立它們之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="7482f-109">We will create an association between them.</span></span>

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

<span data-ttu-id="7482f-110">@No__t 0 類別定義的屬性是屬於該類別的產品名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="7482f-110">The `Category` class defines a property that is an array of the names of the products that belong to that category.</span></span>

<span data-ttu-id="7482f-111">若要建立兩個實體的關聯，您必須在服務的資源架構 MOF 檔案中，定義具有 `Association` 屬性的類別。</span><span class="sxs-lookup"><span data-stu-id="7482f-111">To associate two entities, you must define a class with the `Association` attribute in the resource schema MOF file for the service.</span></span> <span data-ttu-id="7482f-112">類別必須定義要關聯的兩個實體，稱為關聯的 @no__t 0。</span><span class="sxs-lookup"><span data-stu-id="7482f-112">The class must define the two entities to be associated, called `ends` of the association.</span></span> <span data-ttu-id="7482f-113">下列範例顯示類別的定義，其定義 Category 和 Products 實體之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="7482f-113">The following example shows a definition of a class that defines an association between the Category and Products entities.</span></span>

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

<span data-ttu-id="7482f-114">您也必須變更 Category 類別中 Products 屬性的宣告。</span><span class="sxs-lookup"><span data-stu-id="7482f-114">You must also change the declaration of the Products property in the Category class.</span></span> <span data-ttu-id="7482f-115">您可以使用 `AssociationClass` 關鍵字來指定屬性為關聯的一端。</span><span class="sxs-lookup"><span data-stu-id="7482f-115">You use the `AssociationClass` keyword to specify that the property is one end of the association.</span></span> <span data-ttu-id="7482f-116">屬性也必須定義為個別實體的參考，而不是字串陣列。</span><span class="sxs-lookup"><span data-stu-id="7482f-116">The property must also be defined as a reference to a separate entity, rather than an array of strings.</span></span> <span data-ttu-id="7482f-117">您可以使用 `ref` 關鍵字來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="7482f-117">You do this by using the `ref` keyword.</span></span> <span data-ttu-id="7482f-118">下列範例顯示關聯的屬性定義。</span><span class="sxs-lookup"><span data-stu-id="7482f-118">The following example shows the property definition for the association.</span></span>

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

<span data-ttu-id="7482f-119">最後，您必須將屬性定義加入至 `Product` 類別，以宣告關聯的另一端。</span><span class="sxs-lookup"><span data-stu-id="7482f-119">Finally, you must declare the other end of the association by adding a property definition to the `Product` class.</span></span> <span data-ttu-id="7482f-120">這是陣列或單一實體的參考。</span><span class="sxs-lookup"><span data-stu-id="7482f-120">This is a reference to either an array or to a single entity.</span></span> <span data-ttu-id="7482f-121">假設每個產品僅屬於一個類別，則定義會如下所示。</span><span class="sxs-lookup"><span data-stu-id="7482f-121">Assuming that each product belongs to only one category, the definition would be as follows.</span></span>

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

<span data-ttu-id="7482f-122">代表關聯兩端的屬性稱為導覽屬性。</span><span class="sxs-lookup"><span data-stu-id="7482f-122">The properties that represent the two ends of the association are called navigation properties.</span></span>

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a><span data-ttu-id="7482f-123">將實體與資源架構檔案產生關聯的步驟</span><span class="sxs-lookup"><span data-stu-id="7482f-123">Steps for associating entities in the resource schema file</span></span>

- <span data-ttu-id="7482f-124">使用 `Association` 關鍵字，將關聯定義為類別。</span><span class="sxs-lookup"><span data-stu-id="7482f-124">Define the association as a class by using the `Association` keyword.</span></span>

- <span data-ttu-id="7482f-125">使用 AssociationClass 關鍵字來限定關聯實體的屬性，以定義關聯的兩端。</span><span class="sxs-lookup"><span data-stu-id="7482f-125">Define the ends of the association by using the AssociationClass keyword to qualify properties of the associated entities.</span></span>

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a><span data-ttu-id="7482f-126">在資源對應 XML 檔案中建立關聯</span><span class="sxs-lookup"><span data-stu-id="7482f-126">Creating the association in the resource mapping XML file</span></span>

<span data-ttu-id="7482f-127">對應資源對應 XML 檔案中的關聯時，有三種不同的案例需要考慮。</span><span class="sxs-lookup"><span data-stu-id="7482f-127">There are three different cases to consider when mapping an association in the resource mapping XML file.</span></span>

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a><span data-ttu-id="7482f-128">決定如何在資源對應檔案中建立實體的關聯</span><span class="sxs-lookup"><span data-stu-id="7482f-128">Determining how to associate entities in the resource mapping file</span></span>

- <span data-ttu-id="7482f-129">如果基礎中有導覽屬性，則為。</span><span class="sxs-lookup"><span data-stu-id="7482f-129">If the navigation property is present in the underlying.</span></span> <span data-ttu-id="7482f-130">.NET Framework 類型，而且該屬性包含外鍵，則不需要明確對應。</span><span class="sxs-lookup"><span data-stu-id="7482f-130">.NET Framework type, and that property contains foreign keys, no explicit mapping is necessary.</span></span>

- <span data-ttu-id="7482f-131">如果流覽屬性不存在於基礎 .NET Framework 類型中，您必須指定可抓取相關聯實例索引鍵清單的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7482f-131">If the navigation property does not exist in the underlying .NET Framework type, you must specify a cmdlet that retrieves the list of keys of the associated instances.</span></span> <span data-ttu-id="7482f-132">若要這麼做，您可以加入以 `CmdletImplementation` 元素為 @no__t 的元素，並遵循針對其他 CRUD 命令定義 `cmdlets` 的元素。</span><span class="sxs-lookup"><span data-stu-id="7482f-132">You do this by adding an `Association` element nested under the `CmdletImplementation` element, following the elements that define the `cmdlets` for the other CRUD commands.</span></span>

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

- <span data-ttu-id="7482f-133">如果導覽屬性存在於基礎 .NET Framework 型別中，但是它包含物件實例，而不是外鍵，則您必須建立 Cmdlet （藉由撰寫 Windows PowerShell 函式或腳本）來取出外鍵。</span><span class="sxs-lookup"><span data-stu-id="7482f-133">If the navigation property does exist in the underlying .NET Framework type, but it contains object instances instead of foreign keys, then you must create a cmdlet (by writing a Windows PowerShell function or script) to retrieve the foreign keys.</span></span> <span data-ttu-id="7482f-134">接著，您可以在資源對應檔案中指定該 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7482f-134">You then specify that cmdlet in the resource mapping file.</span></span> <span data-ttu-id="7482f-135">例如，用來抓取金鑰的腳本看起來會像下面這樣。</span><span class="sxs-lookup"><span data-stu-id="7482f-135">For example, the script to retrieve the keys would look like the following.</span></span>

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  <span data-ttu-id="7482f-136">而資源對應檔案中的 XML 看起來會像下面這樣。</span><span class="sxs-lookup"><span data-stu-id="7482f-136">And the XML in the resource mapping file would look like the following.</span></span>

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

- <span data-ttu-id="7482f-137">除了指定 Cmdlet 來抓取相關聯的實體之外，您也可以指定 Cmdlet 來加入和移除集合中的參考。</span><span class="sxs-lookup"><span data-stu-id="7482f-137">In addition to specifying a cmdlet to retrieve the associated entities, you can also specify cmdlets to add and remove references from the collection.</span></span> <span data-ttu-id="7482f-138">下列範例假設 ProductToCategory 和 Remove-ProductFromCategory Cmdlet 存在（也可以在腳本或函式中定義，如上述範例所示）。</span><span class="sxs-lookup"><span data-stu-id="7482f-138">The following example assumes that the Add-ProductToCategory and Remove-ProductFromCategory cmdlets exist (they can also be defined in a script or function as in the previous example).</span></span>

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

## <a name="querying-associated-entities"></a><span data-ttu-id="7482f-139">查詢相關聯的實體</span><span class="sxs-lookup"><span data-stu-id="7482f-139">Querying associated entities</span></span>

<span data-ttu-id="7482f-140">用戶端可以藉由建立特定查詢來抓取與實體相關聯的實例清單。</span><span class="sxs-lookup"><span data-stu-id="7482f-140">The client can retrieve a list of the instances associated with an entity by creating specific queries.</span></span>

#### <a name="constructing-queries-for-associated-entities"></a><span data-ttu-id="7482f-141">為相關聯的實體建立查詢</span><span class="sxs-lookup"><span data-stu-id="7482f-141">Constructing queries for associated entities</span></span>

- <span data-ttu-id="7482f-142">用戶端可以要求類別的詳細資料，而不需要抓取其相關聯的產品。</span><span class="sxs-lookup"><span data-stu-id="7482f-142">A client can request the details of a category without retrieving its associated products.</span></span> <span data-ttu-id="7482f-143">例如，下列要求會取得 `food` 類別目錄的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7482f-143">For example, the following request gets details of the `food` category.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  <span data-ttu-id="7482f-144">若要取得類別的相關產品（但不是類別本身的詳細資料），用戶端會在要求中指定導覽屬性。</span><span class="sxs-lookup"><span data-stu-id="7482f-144">To get the associated products of the category (but not details of the category itself, the client specifies the navigation property in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- <span data-ttu-id="7482f-145">若只要取出產品的 Url，請在要求中使用 `$links` 辨識符號。</span><span class="sxs-lookup"><span data-stu-id="7482f-145">To retrieve only URLs of the products, use the `$links` qualifier in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- <span data-ttu-id="7482f-146">用戶端可以使用 `$expand` 辨識符號來取得類別目錄詳細資料和其相關聯的產品。</span><span class="sxs-lookup"><span data-stu-id="7482f-146">The client can get both the category details and its associated products by using the `$expand` qualifier.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a><span data-ttu-id="7482f-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7482f-147">See Also</span></span>

[<span data-ttu-id="7482f-148">建立 Management OData IIS 擴充功能 Web 服務</span><span class="sxs-lookup"><span data-stu-id="7482f-148">Creating a Management OData IIS Extension Web Service</span></span>](./creating-a-management-odata-web-service.md)