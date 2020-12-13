---
ms.date: 09/13/2016
ms.topic: reference
title: 新增處理命令列輸入的參數
description: 新增處理命令列輸入的參數
ms.openlocfilehash: f20469d366330aa787fbc16e4f0a76e67fc7c6db
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "93354604"
---
# <a name="adding-parameters-that-process-command-line-input"></a>新增處理命令列輸入的參數

Cmdlet 的一個輸入來源是命令列。 本主題說明如何將參數新增至 Cmdlet， `Get-Proc` (在 [建立第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)) 中所述，讓 Cmdlet 可以根據傳遞給 Cmdlet 的明確物件，處理來自本機電腦的輸入。 `Get-Proc`此處所述的 Cmdlet 會根據其名稱抓取程式，然後在命令提示字元中顯示處理常式的相關資訊。

## <a name="defining-the-cmdlet-class"></a>定義 Cmdlet 類別

Cmdlet 建立的第一個步驟是 Cmdlet 的命名，以及用來執行 Cmdlet 之 .NET Framework 類別的宣告。 此 Cmdlet 會取出進程資訊，因此此處選擇的動詞名稱為 "Get"。  (幾乎任何能夠抓取資訊的 Cmdlet 都可以處理命令列輸入 ) 。如需已核准的 Cmdlet 動詞命令的詳細資訊，請參閱 [Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)。

以下是 Cmdlet 的類別宣告 `Get-Proc` 。 [建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)時，會提供有關此定義的詳細資料。

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a>宣告參數

Cmdlet 參數可讓使用者提供 Cmdlet 的輸入。 在下列範例中， `Get-Proc` 和 `Get-Member` 是管線 Cmdlet 的名稱，而 `MemberType` 是 Cmdlet 的參數 `Get-Member` 。 參數有 "property" 引數。

**PS> 的 get-proc; `get-member` -membertype 屬性**

若要宣告 Cmdlet 的參數，您必須先定義代表參數的屬性。 在 `Get-Proc` 此 Cmdlet 中，唯一的參數是 `Name` ，在此案例中代表要抓取 .NET Framework 進程物件的名稱。 因此，Cmdlet 類別會定義字串類型的屬性，以接受名稱陣列。

以下是 Cmdlet 參數的參數宣告 `Name` `Get-Proc` 。

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

若要通知 Windows PowerShell 執行時間這個屬性是 `Name` 參數， [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 屬性會加入至屬性定義。 宣告這個屬性的基本語法為 `[Parameter()]` 。

> [!NOTE]
> 參數必須明確標記為公用。 未標記為 public 的參數預設為內部，且 Windows PowerShell 執行時間找不到這些參數。

此 Cmdlet 會使用參數的字串陣列 `Name` 。 可能的話，您的 Cmdlet 也應該將參數定義為數組，因為這可讓 Cmdlet 接受一個以上的專案。

#### <a name="things-to-remember-about-parameter-definitions"></a>有關參數定義的注意事項

- 預先定義的 Windows PowerShell 參數名稱和資料類型應盡可能重複使用，以確保您的 Cmdlet 與 Windows PowerShell Cmdlet 相容。 例如，如果所有 Cmdlet 都使用預先定義的 `Id` 參數名稱來識別資源，則不論使用哪一個 Cmdlet，使用者都可以輕鬆地瞭解參數的意義。 基本上，參數名稱會遵循與在 common language runtime (CLR) 中用於變數名稱相同的規則。 如需參數命名的詳細資訊，請參閱 [Cmdlet 參數名稱](/previous-versions/ms714468(v=vs.85))。

- Windows PowerShell 會保留幾個參數名稱，以提供一致的使用者體驗。 請勿使用這些參數名稱： `WhatIf` 、 `Confirm` 、 `Verbose` 、 `Debug` 、 `Warn` 、、、 `ErrorAction` `ErrorVariable` `OutVariable` 和 `OutBuffer` 。 此外，這些參數名稱的下列別名會保留： `vb` 、 `db` 、 `ea` 、 `ev` 、 `ov` 和 `ob` 。

- `Name` 是簡單且一般的參數名稱，建議在您的 Cmdlet 中使用。 最好是選擇參數名稱，就像是特定 Cmdlet 唯一的複雜名稱一樣，而且難以記住。

- Windows PowerShell 中的參數不區分大小寫，但根據預設，shell 會保留大小寫。 引數的區分大小寫取決於 Cmdlet 的操作。 引數會傳遞至命令列中指定的參數。

- 如需其他參數聲明的範例，請參閱 [Cmdlet 參數](./cmdlet-parameters.md)。

## <a name="declaring-parameters-as-positional-or-named"></a>將參數宣告為位置或命名

Cmdlet 必須將每個參數都設定為位置或具名引數。 這兩種參數都接受單一引數、多個以逗號分隔的引數，以及布林值設定。 布林值參數也稱為 *參數，只* 會處理布林值設定。 參數是用來判斷參數是否存在。 建議的預設值為 `false` 。

範例 Cmdlet 會將 `Get-Proc` `Name` 參數定義為位置參數，並使用位置參數
0. 這表示，系統會自動為此參數插入使用者在命令列上輸入的第一個引數。 如果您想要定義一個具名引數，讓使用者必須從命令列指定參數名稱，請將 `Position` 關鍵字保留在屬性宣告之外。

> [!NOTE]
> 除非參數必須命名，否則建議您將最常使用的參數設為位置，讓使用者不需要輸入參數名稱。

## <a name="declaring-parameters-as-mandatory-or-optional"></a>將參數宣告為強制性或選擇性

Cmdlet 必須將每個參數設定為選擇性或強制參數。 在範例 `Get-Proc` Cmdlet 中， `Name` 參數定義為選擇性，因為屬性宣告 `Mandatory` 中未設定關鍵字。

## <a name="supporting-parameter-validation"></a>支援參數驗證

範例 `Get-Proc` Cmdlet 會將輸入驗證屬性 [Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute)新增至 `Name` 參數，以啟用輸入不是 `null` 或空白的驗證。 這個屬性是 Windows PowerShell 所提供的數個驗證屬性之一。 如需其他驗證屬性的範例，請參閱 [驗證參數輸入](./validating-parameter-input.md)。

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>覆寫輸入處理方法

如果您的 Cmdlet 是用來處理命令列輸入，則必須覆寫適當的輸入處理方法。 基本輸入處理方法是在 [建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)時引進。

此 `Get-Proc` Cmdlet 會覆寫 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法，以處理 `Name` 使用者或腳本提供的參數輸入。 這個方法會取得每個要求之進程名稱的處理常式，如果未提供任何名稱，則會取得所有的進程。 請注意，在 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)中，呼叫 [WriteObject% 28system.string 29> .%. 布林值 %29](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 是將輸出物件傳送至管線的輸出機制。（& a） 這個呼叫的第二個參數 `enumerateCollection` 會設為， `true` 以通知 Windows PowerShell 執行時間列舉處理常式物件的輸出陣列，並一次將一個進程寫入命令列。

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
    // Write the processes to the pipeline making them available
    // to the next cmdlet. The second argument of this call tells
    // PowerShell to enumerate the array, and send one process at a
    // time to the pipeline.
    WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>程式碼範例

如需完整的 c # 範例程式碼，請參閱 [>getprocesssample02 範例](./getprocesssample02-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定義物件類型和格式

Windows PowerShell 使用 .NET Framework 物件，在 Cmdlet 之間傳遞資訊。 因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。 如需定義新型別或擴充現有類型的詳細資訊，請參閱 [擴充物件類型和格式](/previous-versions/ms714665(v=vs.85))。

## <a name="building-the-cmdlet"></a>建立 Cmdlet

在執行 Cmdlet 之後，您必須使用 Windows PowerShell 嵌入式管理單元向 Windows PowerShell 註冊。 如需註冊 Cmdlet 的詳細資訊，請參閱 [如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))。

## <a name="testing-the-cmdlet"></a>測試 Cmdlet

當您的 Cmdlet 註冊 Windows PowerShell 時，您可以在命令列上執行它來進行測試。 以下是兩種測試範例 Cmdlet 程式碼的方式。 如需從命令列使用 Cmdlet 的詳細資訊，請參閱 [消費者入門與 Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 在 Windows PowerShell 提示字元中，使用下列命令來列出名為 "IEXPLORE.EXE" 的 Internet Explorer 進程。

  ```powershell
  get-proc -name iexplore
  ```

  即會出現下列輸出。

  ```Output
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
  -------  ------  -----   -----  -----   ------ --   -----------
      354      11  10036   18992    85   0.67   3284   iexplore
  ```

- 若要列出名稱為 "IEXPLORE.EXE"、"OUTLOOK" 和 "NOTEPAD" 的 Internet Explorer、Outlook 和 Notepad 進程，請使用下列命令。 如果有多個處理常式，則會顯示它們。

  ```powershell
  get-proc -name iexplore, outlook, notepad
  ```

  即會出現下列輸出。

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
  -------  ------  -----   -----  -----  ------   --   -----------
      732      21  24696    5000    138   2.25  2288   iexplore
      715      19  20556   14116    136   1.78  3860   iexplore
     3917      62  74096   58112    468 191.56  1848   OUTLOOK
       39       2   1024    3280     30   0.09  1444   notepad
       39       2   1024     356     30   0.08  3396   notepad
  ```

## <a name="see-also"></a>另請參閱

[新增處理管道輸入的參數](./adding-parameters-that-process-pipeline-input.md)

[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)

[擴充物件類型和格式化](/previous-versions/ms714665(v=vs.85))

[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell 參考](../windows-powershell-reference.md)

[Cmdlet 範例](./cmdlet-samples.md)
