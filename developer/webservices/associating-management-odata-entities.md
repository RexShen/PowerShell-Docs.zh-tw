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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860824"
---
# <a name="associating-management-odata-entities"></a>建立 Management OData 實體的關聯

通常很有用來建立兩個不同的管理 OData 實體之間的關聯。 比方說，管理 OData 服務可以管理組織之分類的產品目錄的實體，並且定義實體`Product`和`Category`。 這兩個實體建立關聯之後，用戶端可以取得某個類別目錄 web 服務的單一要求中的所有產品的相關資訊。

此範例示範如何建立實體之間的關聯，請下載位置[關聯範例](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e)。

## <a name="creating-the-association-in-the-resource-schema-file"></a>資源檔中的結構描述建立關聯

下列的 MOF 定義兩個實體。 我們將建立它們之間的關聯。

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

`Category`類別定義的屬性隸屬於該類別的產品名稱的陣列。

若要建立兩個實體的關聯，您必須定義類別`Association`服務的資源結構描述 MOF 檔案中的屬性。 此類別必須定義兩個實體相關聯，請呼叫`ends`的關聯。 下列範例顯示定義的分類和產品實體之間的關聯的類別定義。

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

您也必須變更類別目錄類別中的 Products 屬性的宣告。 您使用`AssociationClass`關鍵字來指定此屬性是關聯的一端。 屬性也必須定義成個別的實體，而不是字串陣列的參考。 您可以使用`ref`關鍵字。 下列範例會顯示關聯的屬性定義。

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

最後，您必須宣告關聯另一端，藉由新增一個屬性定義`Product`類別。 這是陣列或單一實體的參考。 假設每個產品都屬於一種類別，定義是，如下所示。

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

代表關聯的兩端的屬性稱為導覽屬性。

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>將資源檔中的結構描述的實體產生關聯的步驟

- 做為類別定義的關聯，藉由使用`Association`關鍵字。

- 使用 AssociationClass 關鍵字來限定，相關聯的實體的屬性，以定義此關聯各端。

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>建立資源的對應 XML 檔案中的關聯

有三種不同的案例，來對應資源對應 XML 檔案中的關聯時，請考慮。

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>決定如何將資源對應檔案中的實體產生關聯

- 如果有在基礎的導覽屬性。 .NET framework 型別，以及該屬性包含外部索引鍵，不需要任何明確的對應。

- 如果導覽屬性不存在於基礎的.NET Framework 型別中，您必須指定指令程式來擷取索引鍵相關聯的執行個體的清單。 您可以加入`Association`項目之下巢狀`CmdletImplementation`項目，遵循這些元素會定義`cmdlets`CRUD 命令。

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

- 如果導覽屬性存在於基礎的.NET Framework 型別，但它包含的物件執行個體，而不是外部索引鍵，則您必須建立一個 cmdlet （藉由撰寫 Windows PowerShell 函式或指令碼） 來擷取外部索引鍵。 然後，您會指定該 cmdlet 在資源的對應檔案。 比方說，要擷取索引鍵的指令碼看起來會如下所示。

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  與資源對應檔案中的 XML 看起來如下所示。

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

- 除了指定的 cmdlet 來擷取相關聯的實體，您也可以指定指令程式來新增和移除集合中的參考。 下列範例假設的新增 ProductToCategory 和移除 ProductFromCategory cmdlet 存在於 （他們也可以定義在指令碼或函式，如先前範例所示）。

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

用戶端可以擷取與實體相關聯，藉由建立特定查詢的執行個體清單。

#### <a name="constructing-queries-for-associated-entities"></a>建構相關聯的實體的查詢

- 用戶端可以要求類別目錄的詳細資料，而未擷取其相關聯的產品。 例如，下列要求會取得一份訂單`food`類別目錄。

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  若要取得相關聯的產品類別目錄的 （但未詳細資料的分類，用戶端的要求中指定的導覽屬性。

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- 若要擷取的產品的 Url，請使用`$links`要求中的限定詞。

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- 用戶端可以取得分類的詳細資料和其相關聯的產品使用`$expand`限定詞。

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>另請參閱

[建立管理 OData IIS 擴充功能的 Web 服務](./creating-a-management-odata-web-service.md)