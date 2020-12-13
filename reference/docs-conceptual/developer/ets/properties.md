---
ms.date: 07/09/2020
ms.topic: reference
title: 擴充類型系統屬性
description: 擴充類型系統屬性
ms.openlocfilehash: cccd3c400a8822ee25c44e8e1625e35571420259
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646144"
---
# <a name="ets-properties"></a>ETS 屬性

屬性是可視為屬性的成員。 基本上，它們可以出現在運算式的左側。 可用的屬性包括別名、程式碼、附注和腳本屬性。

## <a name="alias-property"></a>Alias 屬性

別名屬性是參考 **PSObject** 物件所包含之另一個屬性的屬性。 它主要用來重新命名參考的屬性。 不過，它也可以用來將參考屬性的值轉換成另一種類型。 相對於 ETS，此類型的屬性一律為擴充成員，且由 [PSAliasProperty](/dotnet/api/system.management.automation.psaliasproperty) 類別定義。 類別包含下列屬性。

- **ConversionType** 屬性：用來轉換參考成員值的 CLR 型別。
- **IsGettable** 屬性：指出是否可以抓取參考屬性的值。
  藉由檢查所參考屬性的 **IsGettable** 屬性，可動態判斷這個屬性。
- **IsSettable** 屬性：指出是否可以設定參考屬性的值。 藉由檢查所參考屬性的 **IsSettable** 屬性，可動態判斷這個屬性。
- **MemberType** 屬性：將此屬性定義為別名屬性的 **AliasProperty** 列舉常數。
- **ReferencedMemberName** 屬性：此別名所參考之參考屬性的名稱。
- **TypeNameOfValue** 屬性：所參考屬性值之 CLR 類型的完整名稱。
- **Value** 屬性：參考屬性的值。

## <a name="code-property"></a>Code 屬性

程式碼屬性是一種屬性，它是以 CLR 語言定義的 getter 和 setter。 為了讓程式碼屬性可供使用，開發人員必須以某些 CLR 語言撰寫屬性、編譯和傳送結果元件。 此元件必須可在需要程式碼屬性的運行空間中使用。 相對於 ETS，此類型的屬性一律為擴充成員，且由 [PSCodeProperty](/dotnet/api/system.management.automation.pscodeproperty) 類別定義。 類別包含下列屬性。

- **GetterCodeReference** 屬性：用來取得程式碼屬性值的方法。
- **IsGettable** 屬性：指出是否可以取出 code 屬性的值，也就是 **SetterCodeReference** 屬性：用來設定 code 屬性值的方法。
- **IsSettable** 屬性：指出是否可以設定程式碼屬性的值， **SetterCodeReference** 屬性不是 null。
- **MemberType** 屬性：將此屬性定義為程式碼屬性的 **CodeProperty** 列舉常數。
- **SetterCodeReference** 屬性：用來取得程式碼屬性值的方法。
- **TypeNameOfValue** 屬性：屬性取得作業所傳回的程式碼屬性值的 CLR 型別。
- **Value** 屬性： code 屬性的值。 當抓取這個屬性時，會叫用 GetterCodeReference 屬性中的 getter 程式碼，傳遞目前的 **PSObject** 物件，並傳回檔用所傳回的值。 設定這個屬性時，會叫用 **SetterCodeReference** 屬性中的 setter 程式碼，並傳遞目前的 **PSObject** 物件做為第一個引數，以及用來將值設定為第二個引數的物件。

## <a name="note-property"></a>Note 屬性

附注屬性是具有名稱/值配對的屬性。 相對於 ETS，此類型的屬性一律為擴充成員，且由 [PSNoteProperty](/dotnet/api/system.management.automation.psnoteproperty) 類別定義。 類別包含下列屬性。

- **IsGettable** 屬性：指出是否可以取出 note 屬性的值。
- **IsSettable** 屬性：指出是否可以設定 note 屬性的值。
- **MemberType** 屬性：將此屬性定義為附注屬性的 **NoteProperty** 列舉常數。
- **TypeNameOfValue** 屬性： note 屬性的 get 作業所傳回之物件的完整型別名稱。
- **值**： note 屬性的值。

## <a name="powershell-property"></a>PowerShell 屬性

PowerShell 屬性是在基底物件上定義的屬性，或是透過介面卡提供的屬性。 它可以參考 CLR 欄位以及 CLR 屬性。 相對於 ETS，此類型的屬性可以是基底成員或介面卡成員，且是由 [PSProperty](/dotnet/api/system.management.automation.psproperty) 類別所定義。 類別包含下列屬性。

- **IsGettable** 屬性：指出是否可以抓取基底或調整屬性的值。
- **IsSettable** 屬性：指出是否可以設定基底或調整屬性的值。
- **MemberType** 屬性：將此屬性定義為 PowerShell 屬性的屬性列舉常數。
- **TypeNameOfValue** 屬性：屬性值類型的完整名稱。 例如，如果屬性的值是字串，其屬性值型 **別為 system.string。**
- **Value** 屬性：屬性的值。 如果在不支援該操作的屬性上呼叫 get 或 set 作業，則會擲回 **GetValueException** 或 **SetValueException** 例外狀況。

## <a name="powershell-script-property"></a>PowerShell 腳本屬性

腳本屬性是具有 getter 和 setter 腳本的屬性。 相對於 ETS，此類型的屬性一律為擴充成員，且由 [PSScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) 類別定義。 類別包含下列屬性。

- **GetterScript** 屬性：用來取得腳本屬性值的腳本。
- **IsGettable** 屬性：指出 **GetterScript** 屬性是否公開腳本區塊。
- **IsSettable** 屬性：指出 **SetterScript** 屬性是否公開腳本區塊。
- **MemberType** 屬性：將此屬性識別為腳本屬性的 ScriptProperty 列舉常數。
- **SetterScript** 屬性：用來設定腳本屬性值的腳本。
- **TypeNameOfValue** 屬性： getter 腳本所傳回之物件的完整型別名稱。 在此情況下，一律會傳回 **Object** 。
- **Value** 屬性： script 屬性的值。 Get 會叫用 getter 腳本，並傳回所提供的值。 Set 會叫用 setter 腳本。
