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
ms.openlocfilehash: a9204ca7b28fc5792ef9bd18f6b0b24964de7386
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859544"
---
# <a name="public-resource-schema"></a>公用資源結構描述

管理 OData 會使用 MOF，來定義資源和其屬性。 Management OData 實體的屬性直接對應到基礎的 cmdlet 所傳回之 managed 型別的屬性。

## <a name="defining-a-resource"></a>定義資源

每個資源會對應至 Windows PowerShell cmdlet 所傳回的物件。 在 publc 資源 MOF 檔案中，您可以定義資源所宣告的類別。 類別包含的屬性會對應至物件的屬性。 例如，在下列範例中， [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)類別由下列的 MOF。

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

每個屬性名稱會加上的資料類型。 在此範例中的資料類型對應至基本的 CLR 資料型別在.NET Framework 中，但屬性也可以是其他資源或兩者都稍後說明的複雜型別參考。

`Key`限定詞表示的屬性用來唯一識別資源執行個體。 資源可以有多個索引鍵。

`Required`限定詞表示的屬性是必要。 如果屬性會標示`Key`辨識符號，它會被視為必要的而`Required`限定詞不需要。

### <a name="complex-data-types"></a>複雜資料型別

實體的屬性可以有複雜資料型別。 複雜資料型別是組成其他類型，類似於以 C 程式設計語言的結構的型別。 複雜型別之 MOF 檔案中宣告為具有類別`ComplexType`限定詞，如下列範例所示。

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

若要宣告成複雜類型的實體屬性，您將它宣告為`string`型別與`EmbeddedInstance`辨識符號，包括複雜型別的名稱。 下列範例 hshows 屬性之宣告的`PswsTest_ProcessModule`在上述範例中宣告的型別。

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>相關聯的實體

您可以使用關聯與 AssocationClass 限定詞，將兩個實體產生關聯。 如需詳細資訊，請參閱 <<c0> [ 產生關聯的管理 OData 實體](./associating-management-odata-entities.md)。

### <a name="derived-types"></a>衍生型別

您可以從另一個型別衍生型別。 衍生的型別可繼承的所有屬性的型別從其衍生除了明確衍生的任何屬性。 下列範例會顯示型別宣告，然後是衍生自該類型的兩種類型的宣告。

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