---
ms.date: 07/09/2020
ms.topic: reference
title: 擴充類型系統成員集合
description: 擴充類型系統成員集合
ms.openlocfilehash: b04d2618dc4bcf302d2e683d50c351ad3aa076ac
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650086"
---
# <a name="ets-member-sets"></a>ETS 成員集

成員集可讓您將 **PSObject** 物件的成員分割成兩個子集，讓子集的成員可以透過其子集名稱加以參考。 這兩種類型的子集包括屬性集和成員集。 例如，PowerShell 如何使用成員集，會有一個名為 **DefaultDisplayPropertySet** 的特定屬性集，用來決定在執行時間，要針對指定的 **PSObject** 物件顯示哪些屬性。

## <a name="property-sets"></a>屬性集

屬性集可以包含 **PSObject** 型別的任意數目屬性。 一般情況下，每當需要相同) 類型 (的屬性集合時，就可以使用屬性集。 您可以 `PSPropertySet(System.String,System.Collections.Generic.IEnumerable{System.String})` 使用屬性集的名稱和參考屬性的名稱來呼叫該函式，以建立屬性集。 然後，您可以使用建立的 **PSPropertySet** 物件做為指向集合中屬性的別名。 [PSPropertySet](/dotnet/api/system.management.automation.pspropertyset)類別具有下列屬性和方法。

- **IsInstance** 屬性：取得 **布林** 值，這個值表示屬性的來源。
- **MemberType** 屬性：取得屬性集內的屬性類型。
- **Name** 屬性：取得屬性集的名稱。
- **ReferencedPropertyNames** 屬性：取得屬性集內屬性的名稱。
- **TypeNameOfValue** 屬性：取得將此集合定義為屬性集的 **PropertySet** 列舉常數。
- **Value** 屬性：取得或設定 **PSPropertySet** 物件。
- `PSPropertySet.Copy` 方法：建立 **PSPropertySet** 物件的完整複本。
- `PSMemberSet.ToString` 方法：將 **PSPropertySet** 物件轉換為字串。

## <a name="member-sets"></a>成員集

成員集可包含任何類型的任意數目的擴充成員。 成員集的建立方式是呼叫 `PSMemberSet(System.String,System.Collections.Generic.IEnumerable{System.Management.Automation.PSMemberInfo})`
具有成員集名稱的函式和參考成員名稱的函式。 然後，您可以使用建立的 **PSPropertySet** 物件做為指向集合中成員的別名。 [PSMemberSet](/dotnet/api/system.management.automation.psmemberset)類別具有下列屬性和方法。

- **IsInstance** 屬性：取得指出成員來源的 **布林** 值。
- **Members** 屬性：取得成員集合的所有成員。
- **MemberType** 屬性：取得將此集合定義為成員集的成員 **集列舉常數** 。
- **方法** 屬性：取得成員集合中包含的方法。
- **Properties** 屬性：取得成員集合中包含的屬性。
- **TypeNameOfValue** 屬性：取得將此集合定義為成員集的成員 **集列舉常數** 。
- **Value** 屬性：取得 **PSMemberSet** 物件。
- `PSMemberSet.Copy` 方法：建立 **PSMemberSet** 物件的完整複本。
- `PSMemberSet.ToString` 方法：將 **PSMemberSet** 物件轉換為字串。
