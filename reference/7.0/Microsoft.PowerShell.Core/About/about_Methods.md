---
description: 說明如何使用方法，在 PowerShell 中的物件上執行動作。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_methods?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Methods
ms.openlocfilehash: 25056ff8b3c0bc8828be1426463b2d087e23a131
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390995"
---
# <a name="about-methods"></a>關於方法

## <a name="short-description"></a>簡短描述
說明如何使用方法，在 PowerShell 中的物件上執行動作。

## <a name="long-description"></a>完整描述

PowerShell 會使用物件來代表資料存放區中的專案或電腦的狀態。 例如，FileInfo 物件代表檔案系統磁碟機中的檔案，ProcessInfo 物件代表電腦上的處理程序。

物件具有屬性，可儲存關於物件的相關資料，以及可讓您變更物件的方法。

「方法」是一組指示，指定可對物件執行的動作。 例如， `FileInfo` 物件包含複製物件所代表之檔案的 `CopyTo` 方法 `FileInfo` 。

若要取得任何物件的方法，請使用 `Get-Member` Cmdlet。 使用其 **MemberType** 屬性，其值為 "Method"。 下列命令會取得處理程序物件的方法。

```powershell
Get-Process | Get-Member -MemberType Method
```

```Output
TypeName: System.Diagnostics.Process

Name                      MemberType Definition
----                      ---------- ----------
BeginErrorReadLine        Method     System.Void BeginErrorReadLine()
BeginOutputReadLine       Method     System.Void BeginOutputReadLine()
...
Kill                      Method     System.Void Kill()
Refresh                   Method     System.Void Refresh()
Start                     Method     bool Start()
ToString                  Method     string ToString()
WaitForExit               Method     bool WaitForExit(int milliseconds), ...
WaitForInputIdle          Method     bool WaitForInputIdle(int millisecon...
```

若要執行或「叫用」物件的方法，請輸入點 (.)、方法名稱及一組括號 "()"。 如果方法包含引數，請將引數值包含在括號內。 即使沒有引數，每個方法呼叫仍需要括號。 如果方法接受多個引數，它們應該以逗號分隔。

例如，下列命令會叫用處理程序的 Kill 方法，以結束電腦上的 [記事本] 處理程序。

```powershell
$notepad = Get-Process notepad
$notepad.Kill()
```

您可以藉由結合上述語句來縮短此範例。

```powershell
(Get-Process Notepad).Kill()
```

此 `Get-Process` 命令會以括弧括住，以確保它會在叫用 Kill 方法之前執行。 `Kill`然後，會在傳回的物件上叫用方法 `Process` 。

另一個非常實用的方法是 `Replace` 字串的方法。 `Replace`方法會取代字串中的文字。 在下列範例中，點 (. ) 可以緊接在字串的結尾引號之後。

```powershell
'this is rocket science'.Replace('rocket', 'rock')
```

```Output
this is rock science
```

如先前的範例所示，您可以使用命令、變數中的物件或任何產生物件 (（例如引號中的字串) ）來叫用物件上的方法。

從 PowerShell 4.0 開始，支援使用動態方法名稱來叫用方法。

### <a name="learning-about-methods"></a>瞭解方法

若要尋找物件之方法的定義，請移至 [物件類型] 的 [說明] 主題，並尋找其 [方法] 頁面。 例如，下列頁面描述進程物件的方法：處理 [程式](/dotnet/api/system.diagnostics.process#methods)。

若要判斷方法的引數，請檢查方法定義，這就像是 PowerShell Cmdlet 的語法圖。

方法定義可能會有一或多個方法簽章，就像是 PowerShell Cmdlet 的參數集。 簽章會顯示叫用方法的所有有效命令格式。

例如，類別的 `CopyTo` 方法 `FileInfo` 包含下列兩個方法簽章：

```
    CopyTo(String destFileName)
    CopyTo(String destFileName, Boolean overwrite)
```

第一個方法簽章採用目的地檔案名稱 (和路徑)。 下列範例會使用第一個 `CopyTo` 方法，將檔案複製 `Final.txt` 到 `C:\Bin` 目錄。

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt")
```

> [!NOTE]
> 與 PowerShell 的 _引數_ 模式不同的是，物件方法會以 _運算式_ 模式執行，這是傳遞至 PowerShell 建立所在的 .net framework。 在 _運算式_ 模式中 **bareword** 引數 (不具引號的字串) 是不允許的。 使用路徑作為參數時，您可以看到此差異，而將路徑視為引數。 您可以在[about_Parsing](about_Parsing.md)中閱讀剖析模式的詳細資訊。

第二個方法簽章會採用目的地檔案名和布林值，判斷是否應該覆寫目的地檔案（如果已經存在的話）。

下列範例會使用第二 `CopyTo` 種方法將檔案複製 `Final.txt` 到 `C:\Bin` 目錄，並覆寫現有的檔案。

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt", $true)
```

### <a name="methods-of-scalar-objects-and-collections"></a>純量物件和集合的方法

特定類型的單一 (「純量」) 物件方法通常不同於同類型物件集合的方法。

例如，每個進程都有一個 `Kill` 方法，但是進程的集合沒有 Kill 方法。

從 PowerShell 3.0 開始，PowerShell 會嘗試避免因為純量物件和集合的不同方法所產生的腳本錯誤。

如果您提交集合，但要求的方法僅存在單一 ( 「純量」 ) 物件上，則 PowerShell 會在集合中的每個物件上叫用方法。

如果方法存在於個別的物件和集合上，則只會叫用集合的方法。

這項功能也適用於純量物件和集合的屬性。 如需詳細資訊，請參閱 [about_Properties](about_Properties.md)。

### <a name="examples"></a>範例

下列範例會在物件集合中執行個別進程物件的 **Kill** 方法。

第一個命令會啟動「記事本」處理程序的三個執行個體。 `Get-Process` 取得「記事本」處理常式的所有三個實例，並將它們儲存在 `$p` 變數中。

```powershell
Notepad; Notepad; Notepad
$p = Get-Process Notepad
$p.Count
```

```Output
3
```

下一個命令會在變數中的所有三個進程上執行 **Kill** 方法 `$p` 。 即使處理常式集合沒有方法，此命令仍可運作 `Kill` 。

```powershell
$p.Kill()
Get-Process Notepad
```

此 `Get-Process` 命令會確認 `Kill` 方法是否正常運作。

```Output
Get-Process : Cannot find a process with the name "notepad". Verify the proc
ess name and call the cmdlet again.
At line:1 char:12
+ Get-Process <<<<  notepad
    + CategoryInfo          : ObjectNotFound: (notepad:String) [Get-Process]
, ProcessCommandException
    + FullyQualifiedErrorId : NoProcessFoundForGivenName,Microsoft.PowerShel
l.Commands.GetProcessCommand
```

這個範例在功能上相當於使用指令程式 `Foreach-Object` 在集合中的每個物件上執行方法。

```powershell
$p | ForEach-Object {$_.Kill()}
```

### <a name="foreach-and-where-methods"></a>ForEach 和 Where 方法

從 PowerShell 4.0 開始，支援使用方法語法進行集合篩選。 這可讓您在處理集合和時使用兩個新的方法 `ForEach` `Where` 。

您可以在 [about_arrays](about_arrays.md) 中深入閱讀這些方法

### <a name="calling-a-specific-method-when-multiple-overloads-exist"></a>有多個多載存在時呼叫特定的方法

呼叫 .NET 方法時，請考慮下列案例。 如果方法接受物件，但透過介面採用更明確的類型來進行多載，則 PowerShell 會選擇接受物件的方法，除非您明確地將它轉換成該介面。

```powershell
Add-Type -TypeDefinition @'

   // Interface
   public interface IFoo {
     string Bar(int p);
   }

   // Type that implements the interface
   public class Foo : IFoo {

   // Direct member method named 'Bar'
   public string Bar(object p) { return $"object: {p}"; }

   // *Explicit* implementation of IFoo's 'Bar' method().
   string IFoo.Bar(int p) {
       return $"int: {p}";
   }

}
'@
```

在此範例中， `object` 已選擇 **橫條** 方法的較不特定多載。

```powershell
[Foo]::new().Bar(1)
```

```Output
object: 1
```

在此範例中，我們會將方法轉換為介面 **IFoo** ，以選取更明確的 **Bar** 方法多載。

```powershell
([IFoo] [Foo]::new()).Bar(1)
```

```Output
int: 1
```

## <a name="see-also"></a>另請參閱

[about_Objects](about_Objects.md)

[about_Properties](about_Properties.md)

[Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member)
