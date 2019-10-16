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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366267"
---
# <a name="public-resource-schema"></a>公用資源結構描述

管理 OData 使用 MOF 來定義資源及其屬性。 管理 OData 實體的屬性會直接對應至基礎 Cmdlet 所傳回之 managed 類型的屬性。

## <a name="defining-a-resource"></a>定義資源

每個資源都會對應到 Windows PowerShell Cmdlet 所傳回的物件。 在公用資源 MOF 檔案中，您可以藉由宣告類別來定義資源。 類別是由對應至物件屬性的屬性所組成。 例如，在下列範例中，會以下列 MOF 表示[system.web](/dotnet/api/System.Diagnostics.Process)類別。

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

每個屬性名稱的前面都有一個資料類型。 這個範例中的資料類型會對應至 .NET Framework 中的基本 CLR 資料類型，但屬性也可以參考其他資源或複雜類型，這兩種方式都會在稍後說明。

@No__t-0 限定詞表示使用屬性來唯一識別資源實例。 一個資源可以有一個以上的索引鍵。

@No__t-0 限定詞表示需要屬性。 如果屬性標記為 `Key` 辨識符號，則會將它視為必要，而且不需要 `Required` 辨識符號。

### <a name="complex-data-types"></a>複雜資料類型

實體的屬性可以有複雜的資料類型。 複雜資料類型是由其他類型組成的類型，類似于 C 程式設計語言中的結構。 在 MOF 檔案中，會將複雜類型宣告為具有 `ComplexType` 限定詞的類別，如下列範例所示。

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

若要將實體屬性宣告為複雜型別，請將它宣告為具有 `EmbeddedInstance` 限定詞的 `string` 型別，包括複雜型別的名稱。 下列範例顯示在上一個範例中宣告的 `PswsTest_ProcessModule` 型別之屬性的宣告。

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>關聯實體

您可以使用 Association 和 AssociationClass 限定詞來建立兩個實體的關聯。 如需詳細資訊，請參閱建立[管理 OData 實體的關聯](./associating-management-odata-entities.md)。

### <a name="derived-types"></a>衍生類型

您可以從另一個型別衍生型別。 除了明確衍生的任何屬性之外，衍生的型別會繼承它所衍生之型別的所有屬性。 下列範例顯示類型宣告，然後是衍生自該類型的兩個類型的宣告。

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