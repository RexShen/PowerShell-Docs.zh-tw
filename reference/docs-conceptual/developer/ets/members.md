---
title: 擴充類型系統類別成員
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: c066bd69c0ab20cceff96aa789654e80443758e5
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217947"
---
# <a name="extended-type-system-class-members"></a>擴充類型系統類別成員

ETS 是指** psmembertypes**列舉所定義的各種不同類型的成員。 這些成員類型包括屬性、方法、成員和成員集，這些都是由自己的 CLR 類型所定義。 例如， **NoteProperty**是由自己的**PSNoteProperty**類型所定義。 這些個別的 CLR 型別都有自己唯一的屬性，以及繼承自[PSMemberInfo 類別](/dotnet/api/system.management.automation.psmemberinfo)的通用屬性。

## <a name="the-psmemberinfo-class"></a>PSMemberInfo 類別

**PSMemberInfo**類別可做為所有 ETS 成員類型的基類。 這個類別會將下列基底屬性提供給所有成員 CLR 類型。

- **Name**屬性：成員的名稱。 此名稱可由基底物件定義，或在公開調整成員或擴充成員時由 PowerShell 定義。
- **Value**屬性：從特定成員傳回的值。 每個成員類型都會定義它如何處理其成員值。
- **TypeNameOfValue**屬性：這是 value 屬性所傳回之值的 CLR 型別名稱。

## <a name="accessing-members"></a>存取成員

成員集合可以透過**PSObject**物件的**members**、**方法**和**properties**屬性來存取。

## <a name="ets-properties"></a>ETS 屬性

ETS 屬性是可視為屬性的成員。 基本上，它們可以出現在運算式的左側。 其中包括別名屬性、程式碼屬性、PowerShell 屬性、附注屬性和腳本屬性。 如需這些屬性類型的詳細資訊，請參閱[ETS 屬性](properties.md)。

## <a name="ets-methods"></a>ETS 方法

ETS 方法是可以接受引數、可能會傳回結果，而且不能出現在運算式左側的成員。 其中包括程式碼方法、PowerShell 方法和腳本方法。
如需這些類型之方法的詳細資訊，請參閱[ETS 方法](methods.md)。
