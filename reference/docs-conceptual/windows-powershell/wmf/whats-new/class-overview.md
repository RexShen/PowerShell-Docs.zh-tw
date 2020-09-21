---
ms.date: 07/29/2020
title: PowerShell 5.0 的新語言功能
ms.openlocfilehash: dada39c4121a810c7ce87a642f232934152104e5
ms.sourcegitcommit: 339e5fc8a4cc18b4ff6956fe5180343588e40e30
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87410167"
---
# <a name="new-language-features-in-powershell-50"></a>PowerShell 5.0 的新語言功能

PowerShell 5.0 新增了功能，可使用類似其他物件導向程式設計語言的正式語法和語意，來定義類別和其他使用者定義類型。 目標是要讓開發人員和 IT 專業人員能夠掌握更多面向的 PowerShell 使用案例、簡化 PowerShell 成品的開發 (例如 DSC 資源)，並擴大管理介面的涵蓋範圍。

PowerShell 5.0 會在 PowerShell 中引進下列新的語言元素︰

### <a name="class-keyword"></a>Class 關鍵字

`class` 關鍵字會定義新類別。 這是真的 .NET Framework 類型。 類別成員是公用的，但只在模組範圍內公用。 您不能將類型名稱當作字串來參考 (例如，`New-Object` 不會運作)，而且在這個版本中，您無法在類別定義所在的指令碼或模組檔案外部使用類型常值 (例如 `[MyClass]`)。

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a>Enum 關鍵字和列舉

已新增對 `enum` 關鍵字的支援，其會使用新行字元作為分隔符號。 您目前無法根據列舉本身來定義它。 不過，您可以根據另一個列舉來將某個列舉初始化，如下列範例所示。 此外，無法指定基底類型，它一律是 `[int]`。

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

列舉程式值必須是剖析時間常數。 您無法將它設定為所叫用命令的結果。

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Enum 支援算數運算，如下例所示。

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a>Import-DscResource

`Import-DscResource` 現在是真正的動態關鍵字。 PowerShell 會剖析所指定模組的根模組，其會搜尋包含 **DscResource** 屬性的類別。

### <a name="implementingassembly"></a>ImplementingAssembly

已將新欄位 **ImplementingAssembly** 新增至 **ModuleInfo**。 如果指令碼定義類別，它會設定成為指令碼模組所建立的動態組件，或二進位模組的載入組件。 若 **ModuleType** 為 **Manifest**，則不會設定它。

**ImplementingAssembly** 欄位的反映會探索模組中的資源。 這表示您可以探索以 PowerShell 或其他 Managed 語言撰寫的資源。

## <a name="further-reading"></a>進一步閱讀

- [about_Classes](/powershell/module/microsoft.powershell.core/about/about_classes)
- [about_Enum](/powershell/module/microsoft.powershell.core/about/about_enum)
- [about_Classes_and_DSC](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)
