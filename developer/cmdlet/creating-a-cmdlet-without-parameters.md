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
ms.openlocfilehash: c380b28570c955de6f41152fd617f5c1b0f9e4bd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068329"
---
# <a name="creating-a-cmdlet-without-parameters"></a>建立不含參數的 Cmdlet

本節說明如何建立 cmdlet 會從本機電腦，而不使用參數，擷取資訊，然後將資訊寫入管線。 此處所述的 cmdlet 是 Get-proc cmdlet 會擷取本機電腦的處理序的相關資訊，然後在命令列中顯示這些資訊。

在本節中的主題包括下列各項：

- [命名 Cmdlet](#Naming-the-Cmdlet)

- [定義在 Cmdlet 類別](#Defining-the-Cmdlet-Class)

- [覆寫輸入處理方法](#Overriding-an-Input-Processing-Method)

- [程式碼範例](#Code-Sample)

- [定義物件類型和格式設定](#Defining-Object-Types-and-Formatting)

- [建置此指令程式](#Building-the-Cmdlet)

- [測試 Cmdlet](#Testing-the-Cmdlet)

> [!NOTE]
> 請注意，在撰寫 cmdlet，Windows PowerShell® 參考組件預設會下載到磁碟上 （位於 C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0）。它們不會安裝在全域組件快取 (GAC) 中。

## <a name="naming-the-cmdlet"></a>命名 Cmdlet

Cmdlet 名稱是由，指出此 cmdlet 執行的動作動詞和名詞，指出此 cmdlet 作用的項目所組成。 由於此範例的 Get-proc cmdlet 擷取程序物件，它會使用動詞命令 「 取得 」，由[System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon)列舉和名詞"Proc"來表示此指令程式，適用於程序項目。

在命名 cmdlet 時，請勿使用任何下列字元: #，（） {} [] &-/ \ $;:"' <>&#124;嗎？ @ ` .

### <a name="choosing-a-noun"></a>選擇一個名詞

您應該選擇特定的名詞。 最好的方式是使用單數的名詞，加上一個精簡版本的產品名稱。 此類型的範例指令程式名稱是"`Get-SQLServer`」。

### <a name="choosing-a-verb"></a>選擇動詞命令

您應該使用的動詞命令，從一組核准的 cmdlet 動詞命令名稱。 如需已核准的 cmdlet 動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)。

## <a name="defining-the-cmdlet-class"></a>定義在 Cmdlet 類別

一旦您選擇的 cmdlet 名稱，定義.NET 類別來實作此 cmdlet。 以下是此範例的 Get-proc cmdlet 的類別定義：

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

請注意，類別定義之前[System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)屬性，且語法`[Cmdlet(verb, noun, ...)]`，用來識別此指令程式的類別。 這是唯一的必要的屬性，所有的 cmdlet，並可讓 Windows PowerShell 執行階段正確地呼叫它們。 您可以設定屬性的關鍵字，以進一步在必要時在類別宣告。 請注意，我們的範例 GetProcCommand 類別的屬性宣告會宣告只有名詞與動詞名稱 Get-proc cmdlet。

> [!NOTE]
> 針對所有的 Windows PowerShell 屬性類別，您可以設定的關鍵字會對應至屬性類別的屬性中。

在命名類別指令程式時，最好以反映 cmdlet 名稱中的類別名稱。 若要這樣做，請使用格式"VerbNounCommand"並取代 「 動詞 」 和 「 名詞 」 cmdlet 名稱中使用的名詞與動詞命令。 範例 Get-proc cmdlet 在先前的類別定義中所示定義一個叫做 GetProcCommand，衍生自類別[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)基底類別。

> [!IMPORTANT]
> 如果您想要定義直接存取 Windows PowerShell 執行階段的 cmdlet，您的.NET 類別應該衍生自[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基底類別。 如需有關這個類別的詳細資訊，請參閱 <<c0> [ 該定義的參數集建立 Cmdlet](./adding-parameter-sets-to-a-cmdlet.md)。

> [!NOTE]
> Cmdlet 類別必須明確標示為公用。 未標示為公用的類別會預設為內部，並且將找不到 Windows PowerShell 執行階段。

Windows PowerShell 會使用[Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands)其 cmdlet 類別的命名空間。 建議將您的 API 命名空間，例如 xxx.PS.Commands 命令命名空間中的 cmdlet 類別。

## <a name="overriding-an-input-processing-method"></a>覆寫輸入處理方法

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)類別提供三種主要的輸入的處理方法，至少一個 cmdlet 必須覆寫。 如需有關 Windows PowerShell 如何處理記錄的詳細資訊，請參閱 < [Windows PowerShell 的運作方式](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)。

針對所有類型的輸入，Windows PowerShell 執行階段會呼叫[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)以便處理。 如果您的 cmdlet 都必須執行某些前置處理或安裝程式，它可以執行這項操作藉由覆寫這個方法。

> [!NOTE]
> Windows PowerShell 會使用 「 記錄 」 這個詞彙來描述的一組 cmdlet 呼叫時提供的參數值。

如果您的 cmdlet 會接受管線輸入，則必須覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，並選擇性地[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。 比方說，cmdlet 可能會覆寫這兩種方法會收集所有的輸入使用如果[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)再作輸入為整體，而不是一個項目一次為`Sort-Object`cmdlet 會執行。

如果您的 cmdlet 不接受管線輸入，它應該覆寫[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。 請注意，這個方法經常用來取代[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)當 cmdlet 能用在上一個項目一次在此情況下，排序的 cmdlet。

此範例的 Get-proc cmdlet 必須接收管線輸入，因為它會覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，並使用的預設實作[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)並[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)。 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)覆寫擷取處理序，並將它們寫入命令列中使用[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。

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

#### <a name="things-to-remember-about-input-processing"></a>有關輸入處理的注意事項

- 輸入的預設來源是在命令列上使用者所提供的明確物件 （例如，字串）。 如需詳細資訊，請參閱 <<c0> [ 建立可處理命令列輸入的 Cmdlet](./adding-parameters-that-process-command-line-input.md)。

- 處理方法的輸入也可以接收來自管線上游 cmdlet 的輸出物件的輸入。 如需詳細資訊，請參閱 <<c0> [ 建立可處理程序管線輸入的 Cmdlet](./adding-parameters-that-process-pipeline-input.md)。 請注意您的指令程式可以接收來自命令列組合的輸入和管線的來源。

- 長的時間，或根本不可能不會傳回下游的 cmdlet。 基於這個理由的輸入處理方法，在您的 cmdlet 不應保留的鎖定期間呼叫[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)，特別是，範圍會延伸超出指令程式執行個體的鎖定。

> [!IMPORTANT]
> 指令程式應該永遠不會呼叫[System.Console.Writeline*](/dotnet/api/System.Console.WriteLine)或其對等項目。

- 您的 cmdlet 可能會有物件變數，以完成後清除處理 (例如，如果開啟檔案控制代碼，以[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法，並維持控制代碼，已開啟供[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord))。 請務必記住，Windows PowerShell 執行階段不會一律呼叫[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法，它應該執行物件的清除。

例如， [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)可能不會呼叫如果 cmdlet 會中途取消或終止錯誤發生在此指令程式的任何部分。 因此，需要物件清除 cmdlet 應該實作完整[System.IDisposable](/dotnet/api/System.IDisposable)模式，包括完成項，可讓執行階段呼叫兩者[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)並[System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose)結尾的處理。

## <a name="code-sample"></a>程式碼範例

完整C#程式碼範例，請參閱 < [GetProcessSample01 範例](./getprocesssample01-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定義物件類型和格式設定

Windows PowerShell cmdlet 使用.NET 物件之間傳遞資訊。 因此，cmdlet 可能需要定義自己的類型，或可能需要擴充現有的類型提供的另一個 cmdlet 的 cmdlet。 如需定義新的型別或擴充現有類型的詳細資訊，請參閱[延伸的物件類型與格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-cmdlet"></a>建置此指令程式

在實作之後的 cmdlet，您必須向 Windows PowerShell 透過 Windows PowerShell 嵌入式管理單元。 如需有關如何註冊 cmdlet 的詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-cmdlet"></a>測試 Cmdlet

當您的 cmdlet 已向 Windows PowerShell 時，您可以藉由在命令列上執行它來進行測試。 我們的範例 Get-proc cmdlet 的程式碼很小，但是它仍然會使用 Windows PowerShell 執行階段和現有的.NET 物件，這就足以讓有用。 讓我們來測試它，以深入了解 Get-proc 可以做什麼，以及如何使用它的輸出。 如需使用 cmdlet，從命令列的詳細資訊，請參閱[Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

1. 啟動 Windows PowerShell，並取得目前的處理程序在電腦上執行。

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

2. 變數指派給 cmdlet 的結果更容易操作。

    ```powershell
    $p=get-proc
    ```

3. 取得處理序數目。

    ```powershell
    $p.length
    ```

    下列輸出隨即出現。

    ```output
    63
    ```

4. 擷取特定的處理程序。

    ```powershell
    $p[6]
    ```

    下列輸出隨即出現。

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. 取得這個處理程序的開始時間。

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

6. 取得控制代碼計數會大於 500，處理程序和排序結果。

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

7. 使用`Get-Member`cmdlet 來列出每個處理序可用的屬性。

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

[建立可處理命令列輸入的 Cmdlet](./adding-parameters-that-process-command-line-input.md)

[建立可處理管線輸入的 Cmdlet](./adding-parameters-that-process-pipeline-input.md)

[如何建立 Windows PowerShell Cmdlet](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[擴充物件類型和格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Windows PowerShell 的運作方式](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[如何註冊 Cmdlet、 提供者，以及裝載應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell 參考](../windows-powershell-reference.md)

[Cmdlet 範例](./cmdlet-samples.md)