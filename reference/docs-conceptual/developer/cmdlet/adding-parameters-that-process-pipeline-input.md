---
title: 加入處理管線輸入的參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: 9ecb73a4138a5853fa5fb378874da2d81c5dbdba
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364597"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>新增處理管道輸入的參數

Cmdlet 的其中一個輸入來源是管線上源自上游 Cmdlet 的物件。 本節說明如何將參數新增至 Get-help Cmdlet （如[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)所述），讓 Cmdlet 可以處理管線物件。

這個程式碼指令程式會使用接受管線物件輸入的 `Name` 參數，根據提供的名稱從本機電腦抓取處理資訊，然後在命令列中顯示進程的相關資訊。

## <a name="defining-the-cmdlet-class"></a>定義 Cmdlet 類別

Cmdlet 建立的第一個步驟一律為 Cmdlet 命名，並宣告可執行 Cmdlet 的 .NET 類別。 此 Cmdlet 會抓取處理常式資訊，因此此處選擇的動詞名稱是 "Get"。 （幾乎任何能夠抓取資訊的 Cmdlet 都可以處理命令列輸入）。如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)。

以下是這個 Get-Proc Cmdlet 的定義。 [建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)會提供此定義的詳細資料。

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a>從管線定義輸入

本節說明如何從管線定義 Cmdlet 的輸入。 此 Proc Cmdlet 會定義代表 `Name` 參數的屬性，如[新增處理命令列輸入的參數](./adding-parameters-that-process-command-line-input.md)中所述。 （如需宣告參數的一般資訊，請參閱該主題）。

不過，當 Cmdlet 需要處理管線輸入時，Windows PowerShell 執行時間必須將其參數系結至輸入值。 若要這樣做，您必須加入 `ValueFromPipeline` 關鍵字，或將 `ValueFromPipelineByProperty` 關鍵字加入[Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性宣告中。 如果 Cmdlet 存取完整的輸入物件，請指定 `ValueFromPipeline` 關鍵字。 如果 Cmdlet 只存取物件的屬性，請指定 `ValueFromPipelineByProperty`。

以下是接受管線輸入之這個 Get-Proc Cmdlet 的 `Name` 參數的參數宣告。

[!code-csharp[GetProcessSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

先前的宣告會將 `ValueFromPipeline` 關鍵字設定為 `true`，如此一來，如果物件的類型與參數相同，或者可以強制轉型為相同的類型，Windows PowerShell 執行時間就會將參數系結至傳入的物件。 @No__t-0 關鍵字也設定為 `true`，因此 Windows PowerShell 執行時間會檢查 @no__t 2 屬性的傳入物件。 如果傳入的物件具有這類屬性，則執行時間會將 `Name` 參數系結至傳入物件的 `Name` 屬性。

> [!NOTE]
> 參數的 `ValueFromPipeline` 屬性關鍵字設定會優先于 `ValueFromPipelineByPropertyName` 關鍵字的設定。

## <a name="overriding-an-input-processing-method"></a>覆寫輸入處理方法

如果您的 Cmdlet 是用來處理管線輸入，它必須覆寫適當的輸入處理方法。 基本輸入處理方法會在[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)中引進。

此 Proc 指令程式會覆寫[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，以處理使用者或腳本所提供的 @no__t 1 參數輸入。 如果未提供任何名稱，這個方法會取得每個要求的進程名稱或所有進程的進程。 請注意，在[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)中，對[WriteObject （system.object，system.string）](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)的呼叫是將輸出物件傳送至管線的輸出機制。 這個呼叫的第二個參數 `enumerateCollection`，會設定為 `true`，告訴 Windows PowerShell 執行時間列舉進程物件的陣列，並一次將一個進程寫入命令列。

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
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>程式碼範例

如需完整C#的範例程式碼，請參閱[GetProcessSample03 範例](./getprocesssample03-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定義物件類型和格式

Windows PowerShell 會使用 .Net 物件在 Cmdlet 之間傳遞資訊。 因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。 如需定義新類型或擴充現有類型的詳細資訊，請參閱[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))。

## <a name="building-the-cmdlet"></a>建立 Cmdlet

在執行 Cmdlet 之後，必須透過 Windows PowerShell 嵌入式管理單元向 Windows PowerShell 註冊它。 如需註冊 Cmdlet 的詳細資訊，請參閱[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。

## <a name="testing-the-cmdlet"></a>測試 Cmdlet

當您的 Cmdlet 已向 Windows PowerShell 註冊時，請在命令列上執行它來進行測試。 例如，測試範例 Cmdlet 的程式碼。 如需從命令列使用 Cmdlet 的詳細資訊，請參閱[使用 Windows PowerShell 的消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 在 Windows PowerShell 提示字元中，輸入下列命令以透過管線抓取進程名稱。

    ```powershell
    PS> type ProcessNames | get-proc
    ```

下列輸出隨即出現。

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- 輸入下列幾行，從名為 "IEXPLORE.EXE" 的進程取得具有 @no__t 0 屬性的處理常式物件。 這個範例使用 `Get-Process` 指令程式（由 Windows PowerShell 提供）作為上游命令來抓取 "IEXPLORE.EXE" 進程。

    ```powershell
    PS> get-process iexplore | get-proc
    ```

下列輸出隨即出現。

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a>另請參閱

[新增處理命令列輸入的參數](./adding-parameters-that-process-command-line-input.md)

[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)

[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))

[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell 參考](../windows-powershell-reference.md)

[Cmdlet 範例](./cmdlet-samples.md)
