---
ms.date: 07/09/2020
ms.topic: reference
title: 擴充類型系統類別成員
description: 擴充類型系統類別成員
ms.openlocfilehash: 06488ce423f363a285ab53b21ab45989654346dc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666836"
---
# <a name="extended-type-system-class-members"></a>擴充類型系統類別成員

ETS 指的是許多不同類型的成員，而其類型是由 **psmembertypes** 列舉所定義。 這些成員類型包括屬性、方法、成員和成員集，這些都是由自己的 CLR 類型所定義。 例如， **NoteProperty** 是由它自己的 **PSNoteProperty** 型別所定義。 這些個別的 CLR 類型都有自己的唯一屬性，以及繼承自 [PSMemberInfo 類別](/dotnet/api/system.management.automation.psmemberinfo)的通用屬性。

## <a name="the-psmemberinfo-class"></a>PSMemberInfo 類別

**PSMemberInfo** 類別會作為所有 ETS 成員類型的基類。 這個類別會將下列基底屬性提供給所有成員 CLR 類型。

- **Name** 屬性：成員的名稱。 此名稱可由基底物件定義，或在公開調整成員或擴充成員時由 PowerShell 定義。
- **Value** 屬性：從特定成員傳回的值。 每個成員類型都會定義其成員值的處理方式。
- **TypeNameOfValue** 屬性：這是 value 屬性所傳回之值的 CLR 型別名稱。

## <a name="accessing-members"></a>存取成員

您可以透過 **PSObject** 物件的 **成員**、**方法** 和 **屬性** 屬性來存取成員集合。

## <a name="ets-properties"></a>ETS 屬性

ETS 屬性是可視為屬性的成員。 基本上，它們可以出現在運算式的左側。 它們包括別名屬性、程式碼屬性、PowerShell 屬性、附注屬性，以及腳本屬性。 如需這些屬性類型的詳細資訊，請參閱 [ETS 屬性](properties.md)。

## <a name="ets-methods"></a>ETS 方法

ETS 方法是可採用引數、可能會傳回結果，且不能出現在運算式左側的成員。 它們包含程式碼方法、PowerShell 方法和腳本方法。
如需這些類型之方法的詳細資訊，請參閱 [ETS 方法](methods.md)。
