---
ms.date: 07/09/2020
ms.topic: reference
title: 擴充類型系統類型轉換器
description: 擴充類型系統類型轉換器
ms.openlocfilehash: 0774e9eaae1187162b3d55cc45b902f7411a1f18
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648428"
---
# <a name="ets-type-converters"></a>ETS 類型轉換器

當對方法進行呼叫時，ETS 會使用兩種基本類型的類型轉換器 `LanguagePrimitives.ConvertTo(System.Object, System.Type)` 。 當呼叫這個方法時，PowerShell 會嘗試使用其標準的 PowerShell 語言轉換器或自訂轉換器來執行類型轉換。 如果 PowerShell 無法執行轉換，則會擲回 **PSInvalidCastException** 例外狀況。

## <a name="standard-windows-powershell-language-converters"></a>標準 Windows PowerShell 語言轉換器

系統會先檢查這些標準轉換，再進行任何自訂轉換，而且無法覆寫。 下表列出呼叫方法時，PowerShell 所執行的型別轉換 `ConvertTo(System.Object, System.Type)` 。 請注意， **valueToConvert** 和 **resultType** 參數的參考會參考方法的參數 `ConvertTo(System.Object,System.Type)` 。

| 從 (valueToConvert)  |  若要 (resultType)   |                                                                               傳回                                                                               |
| --------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Null                  | 字串            | ""                                                                                                                                                                  |
| Null                  | Char              | '\0'                                                                                                                                                                |
| Null                  | 數字           | `0` 在 **resultType** 參數中指定之類型的。                                                                                                          |
| Null                  | Boolean           | 呼叫方法的結果 `IsTrue(System.Object)(Null)` 。                                                                                                        |
| Null                  | PSObject          | **PSObject** 類型的新物件。                                                                                                                                    |
| Null                  | 非實數值型別    | Null。                                                                                                                                                               |
| Null                  | 可為 null &lt; T&gt; | Null。                                                                                                                                                               |
| 衍生類別         | 基底類別        | **valueToConvert**                                                                                                                                                  |
| 什麼              | Void              | **Automationnull.value 之。值**                                                                                                                                            |
| 什麼              | 字串            | 呼叫 `ToString` 機制。                                                                                                                                         |
| 什麼              | Boolean           | `IsTrue(System.Object) (valueToConvert)`                                                                                                                            |
| 什麼              | PSObject          | 呼叫方法的結果 `AsPSObject(System.Object) (valueToConvert)` 。                                                                                         |
| 什麼              | Xml 檔      | 將 **valueToConvert** 轉換成字串，然後 **呼叫函數** 調用。                                                                                      |
| Array                 | Array             | 嘗試轉換陣列的每個元素。                                                                                                                      |
| 單一             | Array             | `Array[0]` 等於 **valueToConvert** ，它會轉換成陣列的元素類型。                                                                            |
| IDictionary           | 雜湊表        | 呼叫 Hashtable (valueToConvert) 的結果。                                                                                                                       |
| String                | Char[]            | `valueToConvert.ToCharArray`                                                                                                                                        |
| 字串                | Regex             | 呼叫的結果 `Regx(valueToConvert)` 。                                                                                                                          |
| 字串                | 類型              | 使用 **valueToConvert** 參數來搜尋 **RunspaceConfiguration**，以傳回適當的類型。                                                 |
| String                | 數值           | 如果 **valueToConvert** 是 ""，則傳回 `0` **resultType** 的。 否則會使用文化特性「文化特性」來產生數值。                       |
| 整數               | System.Enum       | 如果整數是由列舉所定義，則將整數轉換成常數。 如果未定義整數，則會擲回 **PSInvalidCastException** 例外狀況。 |

## <a name="custom-conversions"></a>自訂轉換

如果 PowerShell 無法使用標準的 PowerShell 語言轉換器來轉換型別，則會檢查是否有自訂的轉換器。 PowerShell 會依照本節所述的順序，尋找數種類型的自訂轉換器。 請注意， **valueToConvert** 和 **resultType** 參數的參考會參考方法的參數 `ConvertTo(System.Object, System.Type)` 。 如果自訂轉換器擲回例外狀況，則不會進一步嘗試轉換物件，而該例外狀況會包裝在 **PSInvalidCastException** 例外狀況中，然後會擲回該例外狀況。

## <a name="powershell-type-converter"></a>PowerShell 類型轉換器

PowerShell 類型轉換器可用來轉換單一類型或類型系列，例如衍生自 **system.string 類別的** 所有類型。 若要建立 PowerShell 類型轉換器，您必須執行 >pstypeconverter 類別，並將該執行與目標類別產生關聯。 有兩種方式可以將 PowerShell 類型轉換器與其目標類別產生關聯。

- 透過類型設定檔
- 藉由將 **system.componentmodel.typeconverterattribute> 套用** 屬性套用至目標類別

PowerShell 類型轉換器（衍生自 [>pstypeconverter](/dotnet/api/system.management.automation.pstypeconverter) 抽象類別）提供將物件轉換為特定類型或從特定類型轉換成特定類型的方法。 如果 **valueToConvert** 參數包含的物件具有與其相關聯的 PowerShell 類型轉換器，則 powershell 會呼叫 `PSTypeConverter.ConvertTo(System.Object, System.Type,System.IFormatProvider, System.Boolean)`
相關聯的轉換器的方法，將物件轉換為 **resultType** 參數所指定的型別。 如果 **resultType** 參數參考的類型具有與其相關聯的 PowerShell 類型轉換器，則 powershell 會呼叫 `PSTypeConverter.ConvertFrom(System.Object,System.Type, System.IFormatProvider, System.Boolean)`
相關聯轉換器的方法，可從 **resultType** 參數所指定的型別轉換物件。

## <a name="system-type-converter"></a>系統類型轉換器

系統類型轉換器可用來轉換特定的目標類別。 這種類型的轉換器不能用來轉換類別的系列。 若要建立系統類型轉換器，您必須執行 [TypeConverter](/dotnet/api/system.management.automation.runspaces.typedata.typeconverter#System_Management_Automation_Runspaces_TypeData_TypeConverter) 類別，並將該執行與目標類別產生關聯。 有兩種方式可以將系統類型轉換器與其目標類別產生關聯。

- 透過類型設定檔
- 藉由將 System.componentmodel.typeconverterattribute> 套用屬性套用至目標類別

## <a name="parse-converter"></a>剖析轉換器

如果 **valueToConvert** 參數是字串，而且 **resultType** 參數的物件類型具有 `Parse` 方法，則 `Parse` 會呼叫方法來轉換字串。

## <a name="constructor-converter"></a>函數轉換器

如果 **resultType** 參數的物件類型具有單一參數的函式，其類型與 **valueToConvert** 參數的物件相同，則會呼叫此函式。

## <a name="implicit-cast-operator-converter"></a>隱含轉換運算子轉換子

如果 **valueToConvert** 參數具有轉換成 **resultType** 的隱含轉換運算子，則會呼叫其轉換運算子。 如果 **resultType** 參數有從 **valueToConvert** 轉換的隱含轉換運算子，則會呼叫其轉換運算子。

## <a name="explicit-cast-operator-converter"></a>明確轉換運算子轉換子

如果 **valueToConvert** 參數具有轉換成 **resultType** 的明確轉換運算子，則會呼叫其轉換運算子。 如果 **resultType** 參數有從 **valueToConvert** 轉換的明確轉換運算子，則會呼叫其轉換運算子。
