---
title: 擴充類型系統屬性
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: 27da913b07dbc5f06ee46e5433208871168c36a5
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217918"
---
# <a name="ets-properties"></a>ETS 屬性

屬性是可視為屬性的成員。 基本上，它們可以出現在運算式的左側。 可用的屬性包括 [別名]、[程式碼]、[附注] 和 [腳本屬性]。

## <a name="alias-property"></a>Alias 屬性

Alias 屬性是參考**PSObject**物件包含之另一個屬性的屬性。 它主要是用來重新命名參考的屬性。 不過，它也可以用來將參考屬性的值轉換成另一種類型。 相對於 ETS，這種類型的屬性一律是擴充成員，並且是由[PSAliasProperty](/dotnet/api/system.management.automation.psaliasproperty)類別所定義。 類別包含下列屬性。

- **ConversionType**屬性：用來轉換參考成員值的 CLR 型別。
- **IsGettable**屬性：指出是否可以抓取參考屬性的值。
  此屬性是藉由檢查所參考屬性的**IsGettable**屬性來動態判斷。
- **IsSettable**屬性：指出是否可以設定參考屬性的值。 此屬性是藉由檢查所參考屬性的**IsSettable**屬性來動態判斷。
- **MemberType**屬性：將此屬性定義為別名屬性的**AliasProperty**列舉常數。
- **ReferencedMemberName**屬性：此別名所參考之參考屬性的名稱。
- **TypeNameOfValue**屬性：所參考屬性值之 CLR 類型的完整名稱。
- **Value**屬性：參考屬性的值。

## <a name="code-property"></a>Code 屬性

Code 屬性是一個屬性，它是以 CLR 語言定義的 getter 和 setter。 為了讓程式碼屬性變成可供使用，開發人員必須以某些 CLR 語言撰寫屬性、編譯和傳送結果元件。 這個元件必須可在需要程式碼屬性的運行時使用。 相對於 ETS，這種類型的屬性一律是擴充成員，並且是由[PSCodeProperty](/dotnet/api/system.management.automation.pscodeproperty)類別所定義。 類別包含下列屬性。

- **GetterCodeReference**屬性：用來取得程式碼屬性值的方法。
- **IsGettable**屬性：指出是否可以抓取程式碼屬性的值，也就是**SetterCodeReference**屬性：用來設定程式碼屬性值的方法。
- **IsSettable**屬性：指出是否可以設定程式碼屬性的值，而**SetterCodeReference**屬性不是 null。
- **MemberType**屬性：將此屬性定義為程式碼屬性的**CodeProperty**列舉常數。
- **SetterCodeReference**屬性：用來取得程式碼屬性值的方法。
- **TypeNameOfValue**屬性：屬性取得作業所傳回之程式碼屬性值的 CLR 型別。
- **Value**屬性： code 屬性的值。 抓取此屬性時，會叫用 GetterCodeReference 屬性中的 getter 程式碼，並傳遞目前的**PSObject**物件，並傳回檔用所傳回的值。 設定此屬性時，會叫用**SetterCodeReference**屬性中的 setter 程式碼，並傳遞目前的**PSObject**物件做為第一個引數，以及用來將值設定為第二個引數的物件。

## <a name="note-property"></a>Note 屬性

Note 屬性是具有名稱/值配對的屬性。 相對於 ETS，這種類型的屬性一律是擴充成員，並且是由[PSNoteProperty](/dotnet/api/system.management.automation.psnoteproperty)類別所定義。 類別包含下列屬性。

- **IsGettable**屬性：指出是否可以抓取 note 屬性的值。
- **IsSettable**屬性：指出是否可以設定 note 屬性的值。
- **MemberType**屬性：將此屬性定義為附注屬性的**NoteProperty**列舉常數。
- **TypeNameOfValue**屬性： note 屬性的 get 作業所傳回之物件的完整型別名稱。
- **值**： note 屬性的值。

## <a name="powershell-property"></a>PowerShell 屬性

PowerShell 屬性是在基底物件上定義的屬性，或可透過介面卡取得的屬性。 它可以參考 CLR 欄位和 CLR 屬性。 相對於 ETS，這種類型的屬性可以是基底成員或介面卡成員，而且是由[PSProperty](/dotnet/api/system.management.automation.psproperty)類別所定義。 類別包含下列屬性。

- **IsGettable**屬性：指出是否可以抓取基底或調整屬性的值。
- **IsSettable**屬性：指出是否可以設定基底或調整屬性的值。
- **MemberType**屬性：將此屬性定義為 PowerShell 屬性的屬性列舉常數。
- **TypeNameOfValue**屬性：屬性值類型的完整名稱。 例如，對於其值為字串的屬性，其屬性值類型為**system.string。**
- **Value**屬性：屬性的值。 如果在不支援該作業的屬性上呼叫 get 或 set 作業，則會擲回**GetValueException**或**SetValueException**例外狀況

## <a name="powershell-script-property"></a>PowerShell 腳本屬性

腳本屬性是具有 getter 和 setter 腳本的屬性。 相對於 ETS，這種類型的屬性一律是擴充成員，並且是由[PSScriptProperty](/dotnet/api/system.management.automation.psscriptproperty)類別所定義。 類別包含下列屬性。

- **GetterScript**屬性：用來捕獲腳本屬性值的腳本。
- **IsGettable**屬性：指出**GetterScript**屬性是否公開腳本區塊。
- **IsSettable**屬性：指出**SetterScript**屬性是否公開腳本區塊。
- **MemberType**屬性：將此屬性識別為腳本屬性的 ScriptProperty 列舉常數。
- **SetterScript**屬性：用來設定腳本屬性值的腳本。
- **TypeNameOfValue**屬性： getter 腳本所傳回之物件的完整型別名稱。 在此情況下，一律會傳回**system.object** 。
- **Value**屬性： Script 屬性的值。 Get 會叫用 getter 腳本，並傳回提供的值。 集合會叫用 setter 腳本。
