---
title: 擴充類型系統成員集
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: 11e1e7819efecc1f1d8164ef32fb97cda978e748
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217944"
---
# <a name="ets-member-sets"></a>ETS 成員集

成員集可讓您將**PSObject**物件的成員分割成兩個子集，讓子集的成員可以透過其子集名稱加以參考。 這兩個子集類型包含屬性集和成員集。 例如，PowerShell 如何使用成員集，會有一個名為**DefaultDisplayPropertySet**的特定屬性集，可在執行時間用來判斷要針對指定的**PSObject**物件顯示哪些屬性。

## <a name="property-sets"></a>屬性集

屬性集可以包含**PSObject**類型的任意數目屬性。 一般來說，每當需要) 相同類型 (屬性集合時，就可以使用屬性集。 藉由呼叫 `PSPropertySet(System.String,System.Collections.Generic.IEnumerable{System.String})` 具有屬性集名稱和參考屬性名稱的函式，即可建立屬性集。 然後，建立的**PSPropertySet**物件可以用來當做指向集合中屬性的別名。 [PSPropertySet](/dotnet/api/system.management.automation.pspropertyset)類別具有下列屬性和方法。

- **IsInstance**屬性：取得**布林**值，指出屬性的來源。
- **MemberType**屬性：取得屬性集內的屬性類型。
- **Name**屬性：取得屬性集的名稱。
- **ReferencedPropertyNames**屬性：取得屬性集內的屬性名稱。
- **TypeNameOfValue**屬性：取得將此集合定義為屬性集的**PropertySet**列舉常數。
- **Value**屬性：取得或設定**PSPropertySet**物件。
- `PSPropertySet.Copy`method：建立**PSPropertySet**物件的完全相同複本。
- `PSMemberSet.ToString`method：將**PSPropertySet**物件轉換為字串。

## <a name="member-sets"></a>成員集

成員集可以包含任何類型的任意數目的擴充成員。 成員集的建立方式是呼叫`PSMemberSet(System.String,System.Collections.Generic.IEnumerable{System.Management.Automation.PSMemberInfo})`
具有成員集名稱和參考成員名稱的函式。 然後，建立的**PSPropertySet**物件可以用來當做指向集合中成員的別名。 [PSMemberSet](/dotnet/api/system.management.automation.psmemberset)類別具有下列屬性和方法。

- **IsInstance**屬性：取得指出成員來源的**布林**值。
- **Members**屬性：取得成員集的所有成員。
- **MemberType**屬性：取得將此集合定義為成員集的**成員**集列舉常數。
- **方法**屬性：取得成員集合中包含的方法。
- **Properties**屬性：取得成員集合中包含的屬性。
- **TypeNameOfValue**屬性：取得將此集合定義為成員集的**成員**集列舉常數。
- **Value**屬性：取得**PSMemberSet**物件。
- `PSMemberSet.Copy`method：建立**PSMemberSet**物件的完全相同複本。
- `PSMemberSet.ToString`method：將**PSMemberSet**物件轉換為字串。
