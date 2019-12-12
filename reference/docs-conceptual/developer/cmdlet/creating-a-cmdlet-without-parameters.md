---
title: 建立不含參數的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: af41c2c9855310d047404114a07b27180a7aa8fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74415664"
---
# <a name="creating-a-cmdlet-without-parameters"></a>建立不含參數的 Cmdlet

本節說明如何建立在不使用參數的情況下，從本機電腦抓取資訊的 Cmdlet，然後將資訊寫入管線。 這裡所述的 Cmdlet 是一個可抓取本機電腦處理常式相關資訊的 Get-Proc Cmdlet，然後在命令列中顯示該資訊。

> [!NOTE]
> 請注意，在撰寫 Cmdlet 時，Windows PowerShell®參考元件會下載到磁片上（預設為 C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0）。 它們不會安裝在全域組件快取（GAC）中。

## <a name="naming-the-cmdlet"></a>命名 Cmdlet

Cmdlet 名稱是由指示 Cmdlet 所採取之動作的動詞，以及表示此 Cmdlet 作用之專案的名詞所組成。 因為此範例的 Get 程式 Cmdlet 會抓取進程物件，所以它會使用動詞命令 "Get" （由[Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon)列舉所定義）和名詞 "Proc"，表示此 Cmdlet 適用于處理常式專案。

命名 Cmdlet 時，請勿使用下列任何字元： #、（） {} [] &-/\ $;： "' < > &#124;嗎？ @ ` .

### <a name="choosing-a-noun"></a>選擇名詞

您應該選擇特定的名詞。 最好是使用前面加上產品名稱之縮寫版本的單數名詞。 此類型的範例 Cmdlet 名稱是 "`Get-SQLServer`"。

### <a name="choosing-a-verb"></a>選擇動詞

您應該使用一組已核准的 Cmdlet 動詞名稱中的動詞。 如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)。

## <a name="defining-the-cmdlet-class"></a>定義 Cmdlet 類別

選擇 Cmdlet 名稱之後，請定義 .NET 類別來執行 Cmdlet。 以下是此範例 Get-Proc Cmdlet 的類別定義：

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

請注意，在類別定義之前，使用語法 `[Cmdlet(verb, noun, ...)]`的[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)屬性，是用來將此類別識別為 Cmdlet。 這是所有 Cmdlet 唯一必要的屬性，它可讓 Windows PowerShell 執行時間正確地呼叫它們。 您可以設定屬性關鍵字，以便在必要時進一步宣告類別。 請注意，我們的範例 GetProcCommand 類別的屬性宣告只會宣告 Get-help Cmdlet 的名詞和動詞名稱。

> [!NOTE]
> 對於所有的 Windows PowerShell 屬性類別，您可以設定的關鍵字會對應到屬性類別的屬性。

命名 Cmdlet 的類別時，最好是在類別名稱中反映 Cmdlet 名稱。 若要這麼做，請使用 "VerbNounCommand" 格式，並將 "Verb" 和 "名詞" 取代為 Cmdlet 名稱中使用的動詞和名詞。 如先前的類別定義中所示，範例 Get-Proc Cmdlet 會定義名為 GetProcCommand 的類別，其衍生自[system.object](/dotnet/api/System.Management.Automation.Cmdlet)基類。

> [!IMPORTANT]
> 如果您想要定義直接存取 Windows PowerShell 執行時間的 Cmdlet，您的 .NET 類別應該衍生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基類。 如需此類別的詳細資訊，請參閱[建立定義參數集的 Cmdlet](./adding-parameter-sets-to-a-cmdlet.md)。

> [!NOTE]
> Cmdlet 的類別必須明確標示為公用。 未標示為公用的類別會預設為內部，且不會由 Windows PowerShell 執行時間找到。

Windows PowerShell 會針對其 Cmdlet 類別使用[Microsoft. powershell. 命令](/dotnet/api/Microsoft.PowerShell.Commands)命名空間。 建議您將 Cmdlet 類別放在 API 命名空間的命令命名空間中，例如 xxx. PS. 命令。

## <a name="overriding-an-input-processing-method"></a>覆寫輸入處理方法

[System.web](/dotnet/api/System.Management.Automation.Cmdlet)類別提供三種主要的輸入處理方法，其中至少有一個 Cmdlet 必須覆寫。 如需 Windows PowerShell 如何處理記錄的詳細資訊，請參閱[Windows powershell 的運作方式](/previous-versions//ms714658(v=vs.85))。

針對所有類型的輸入，Windows PowerShell 執行時間會呼叫[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)以啟用處理。 如果您的 Cmdlet 必須執行一些前置處理或設定，可以藉由覆寫此方法來執行此動作。

> [!NOTE]
> Windows PowerShell 使用「記錄」一詞來描述呼叫 Cmdlet 時所提供的參數值集。

如果您的 Cmdlet 接受管線輸入，它就必須覆寫[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，並選擇性地覆寫[system.servicemodel 方法和。](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 例如，Cmdlet 可能會覆寫這兩個方法（如果它會使用[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)來收集所有輸入），然後一次在輸入上當做整體而不是一個元素來操作，如同 `Sort-Object` Cmdlet 一樣。

如果您的 Cmdlet 不接受管線輸入，它應該覆寫[system.web](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。 請注意，當 Cmdlet 一次無法在一個專案上操作時，通常會使用這個方法來取代[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) ，這就是排序 Cmdlet 的情況。

因為此範例過程指令程式必須接收管線輸入，所以它會覆寫[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，並使用 BeginProcessing 和[system.web](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)的預設實作為檔案的管理[元件](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)（可能為系統管理）。 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)覆寫會抓取進程，並使用[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法將它們寫入至命令列中的程式碼。

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a>輸入處理需要注意的事項

- 輸入的預設來源是使用者在命令列上提供的明確物件（例如字串）。 如需詳細資訊，請參閱[建立 Cmdlet 來處理命令列輸入](./adding-parameters-that-process-command-line-input.md)。

- 輸入處理方法也可以從管線上上游 Cmdlet 的輸出物件接收輸入。 如需詳細資訊，請參閱[建立 Cmdlet 來處理管線輸入](./adding-parameters-that-process-pipeline-input.md)。 請注意，您的 Cmdlet 可以從命令列和管線來源的組合接收輸入。

- 下游 Cmdlet 可能不會傳回長時間，或根本不會傳回。 基於這個理由，您 Cmdlet 中的輸入處理方法不應在呼叫[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)時保留鎖定，尤其是範圍延伸超過 Cmdlet 實例的鎖定。

> [!IMPORTANT]
> Cmdlet 絕對不應呼叫[system.object *](/dotnet/api/System.Console.WriteLine)或其對等的。

- 當程式完成處理時，您的 Cmdlet 可能會有要清除的物件變數（例如，如果它在[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法中開啟檔案控制代碼，並讓控制碼保持開啟以供[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)使用）。 請務必記住，Windows PowerShell 執行時間不一定會呼叫[system.web](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法，這應該會執行物件清除。

例如，如果指令程式中途取消，或 Cmdlet 的任何部分發生終止錯誤，則可能不會呼叫[system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 。 因此，需要物件清理的 Cmdlet 應該會執行完整的[System.IDisposable](/dotnet/api/System.IDisposable)模式，包括完成項，讓執行時間可以同時呼叫[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)和處理結束時的 [IDisposable](/dotnet/api/System.IDisposable.Dispose)。

## <a name="code-sample"></a>範例程式碼

如需完整C#的範例程式碼，請參閱[GetProcessSample01 範例](./getprocesssample01-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定義物件類型和格式

Windows PowerShell 會使用 .NET 物件在 Cmdlet 之間傳遞資訊。 因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。 如需定義新類型或擴充現有類型的詳細資訊，請參閱[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))。

## <a name="building-the-cmdlet"></a>建立 Cmdlet

在執行 Cmdlet 之後，您必須透過 Windows powershell 嵌入式管理單元向 Windows PowerShell 註冊它。 如需註冊 Cmdlet 的詳細資訊，請參閱[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。

## <a name="testing-the-cmdlet"></a>測試 Cmdlet

當您的 Cmdlet 已向 Windows PowerShell 註冊時，您可以在命令列上執行它來進行測試。 範例 Proc Cmdlet 的程式碼很小，但它仍會使用 Windows PowerShell 執行時間和現有的 .NET 物件，這足以讓它發揮作用。 讓我們來測試它，以進一步瞭解有哪些程式可執行，以及如何使用其輸出。 如需從命令列使用 Cmdlet 的詳細資訊，請參閱[使用 Windows PowerShell 的消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

1. 啟動 Windows PowerShell，並取得電腦上正在執行的目前進程。

    ```powershell
    get-proc
    ```

    下列輸出隨即出現。

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. 將變數指派給 Cmdlet 結果，以方便操作。

    ```powershell
    $p=get-proc
    ```

3. 取得進程的數目。

    ```powershell
    $p.length
    ```

    下列輸出隨即出現。

    ```output
    63
    ```

4. 取出特定的進程。

    ```powershell
    $p[6]
    ```

    下列輸出隨即出現。

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. 取得此程式的開始時間。

    ```powershell
    $p[6].starttime
    ```

    下列輸出隨即出現。

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. 取得控制碼計數大於500的進程，並將結果排序。

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    下列輸出隨即出現。

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. 使用 `Get-Member` Cmdlet 來列出每個進程可用的屬性。

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    下列輸出隨即出現。

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a>另請參閱

[建立 Cmdlet 來處理命令列輸入](./adding-parameters-that-process-command-line-input.md)

[建立 Cmdlet 來處理管線輸入](./adding-parameters-that-process-pipeline-input.md)

[如何建立 Windows PowerShell Cmdlet](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))

[Windows PowerShell 的運作方式](/previous-versions//ms714658(v=vs.85))

[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell 參考](../windows-powershell-reference.md)

[Cmdlet 範例](./cmdlet-samples.md)
