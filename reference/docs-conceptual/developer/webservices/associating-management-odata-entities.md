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
ms.openlocfilehash: 4849735bf412497f5590b109c67760b6a197cb2b
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561722"
---
# <a name="associating-management-odata-entities"></a>建立 Management OData 實體的關聯

在兩個不同的管理 OData 實體之間建立關聯通常會很有用。 例如，管理 OData 服務可能會有管理以類別組織之產品目錄的實體，以及定義實體 `Product` 和 `Category` 。 藉由將這兩個實體產生關聯，用戶端就可以透過單一的 web 服務要求，取得類別中所有產品的相關資訊。

範例會示範如何在[關聯範例](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e)中下載實體之間的關聯。

## <a name="creating-the-association-in-the-resource-schema-file"></a>在資源架構檔案中建立關聯

下列 MOF 會定義兩個實體。 我們會建立它們之間的關聯。

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

`Category`類別會定義屬性，這是屬於該類別的產品名稱陣列。

若要建立兩個實體的關聯，您必須 `Association` 在服務的資源架構 MOF 檔案中定義具有屬性的類別。 類別必須定義要關聯的兩個實體，稱為 `ends` 關聯。 下列範例顯示類別的定義，其定義 Category 和 Products 實體之間的關聯。

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

您也必須變更 Category 類別中 Products 屬性的宣告。 您可以使用 `AssociationClass` 關鍵字，將屬性指定為關聯的一端。 屬性也必須定義為個別實體的參考，而不是字串陣列。 您可以使用關鍵字來執行這項操作 `ref` 。 下列範例顯示關聯的屬性定義。

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

最後，您必須將屬性定義加入至類別，以宣告關聯的另一端 `Product` 。 這是陣列或單一實體的參考。 假設每個產品僅屬於一個類別，則定義會如下所示。

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

代表關聯兩端的屬性稱為導覽屬性。

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>將實體與資源架構檔案產生關聯的步驟

- 使用關鍵字，將關聯定義為類別 `Association` 。

- 使用 AssociationClass 關鍵字來限定關聯實體的屬性，以定義關聯的兩端。

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>在資源對應 XML 檔案中建立關聯

對應資源對應 XML 檔案中的關聯時，有三種不同的案例需要考慮。

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>決定如何在資源對應檔案中建立實體的關聯

- 如果基礎中有導覽屬性，則為。 .NET Framework 類型，而且該屬性包含外鍵，則不需要明確對應。

- 如果流覽屬性不存在於基礎 .NET Framework 類型中，您必須指定可抓取相關聯實例索引鍵清單的 Cmdlet。 若要這麼做，您可以在專案底下加入嵌套的專案 `Association` `CmdletImplementation` ，並遵循 `cmdlets` 針對其他 CRUD 命令定義的元素。

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

- 如果導覽屬性存在於基礎 .NET Framework 型別中，但是它包含物件實例，而不是外鍵，則您必須建立 Cmdlet （藉由撰寫 Windows PowerShell 函式或腳本）來取出外鍵。 接著，您可以在資源對應檔案中指定該 Cmdlet。 例如，用來抓取金鑰的腳本看起來會像下面這樣。

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  而資源對應檔案中的 XML 看起來會像下面這樣。

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

- 除了指定 Cmdlet 來抓取相關聯的實體之外，您也可以指定 Cmdlet 來加入和移除集合中的參考。 下列範例假設 ProductToCategory 和 Remove-ProductFromCategory Cmdlet 存在（也可以在腳本或函式中定義，如上述範例所示）。

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

## <a name="querying-associated-entities"></a>查詢相關聯的實體

用戶端可以藉由建立特定查詢來抓取與實體相關聯的實例清單。

#### <a name="constructing-queries-for-associated-entities"></a>為相關聯的實體建立查詢

- 用戶端可以要求類別的詳細資料，而不需要抓取其相關聯的產品。 例如，下列要求會取得類別目錄的詳細資料 `food` 。

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  若要取得類別的相關產品（但不是類別本身的詳細資料），用戶端會在要求中指定導覽屬性。

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- 若只要取出產品的 Url，請 `$links` 在要求中使用限定詞。

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- 用戶端可以使用辨識符號來取得類別目錄詳細資料及其相關聯的產品 `$expand` 。

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>另請參閱

[建立 Management OData IIS 擴充功能 Web 服務](./creating-a-management-odata-web-service.md)
