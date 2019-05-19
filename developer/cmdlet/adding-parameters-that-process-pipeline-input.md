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
ms.openlocfilehash: def0ac2ff98575beb29c3c2a7d91a5a5c53e648e
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854988"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>新增處理管道輸入的參數

其中一個的 cmdlet 來源是輸入的來自上游的 cmdlet 從管線上的物件。 本節說明如何將參數新增至 Get-proc cmdlet (中所述[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md))，讓此指令程式可以處理管線的物件。

此 Get-proc cmdlet 會使用`Name`接受來自管線的物件中，輸入的參數會從本機電腦，根據提供的名稱，擷取程序資訊，並接著會處理序的相關資訊顯示在命令列。

## <a name="defining-the-cmdlet-class"></a>定義在 Cmdlet 類別

Cmdlet 建立的第一個步驟一律命名 cmdlet，並實作指令程式的.NET 類別的宣告。 此 cmdlet 可擷取處理序資訊，因此在這裡選擇的指令動詞名稱是 「 Get 」。 （幾乎任何一種能夠擷取資訊的指令程式可以處理命令列輸入）。如需已核准的 cmdlet 動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)。

以下是此 Get-proc cmdlet 的定義。 會提供此定義的詳細資料[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)。

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a>定義從管線輸入

本章節描述如何定義從 cmdlet 管線的輸入。 此 Get-proc cmdlet 定義屬性，表示`Name`參數中所述[加入參數，該程序的命令列輸入](./adding-parameters-that-process-command-line-input.md)。 （請參閱該主題，以宣告參數的一般資訊）。

不過，當 cmdlet 需要處理管線的輸入，它必須具有其繫結至輸入值，Windows PowerShell 執行階段的參數。 若要這樣做，您必須新增`ValueFromPipeline`關鍵字或加入`ValueFromPipelineByProperty`關鍵字來[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性宣告。 指定`ValueFromPipeline`關鍵字，如果此指令程式會存取完整的輸入的物件。 指定`ValueFromPipelineByProperty`如果 cmdlet 會在存取物件的屬性。

以下是參數宣告`Name`接受管線輸入此 Get-proc cmdlet 的參數。

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

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

先前的宣告集`ValueFromPipeline`關鍵字來`true`，讓 Windows PowerShell 執行階段將參數繫結至連入物件的物件是否相同的型別，做為參數，或如果它可以強制轉型為相同的類型。 `ValueFromPipelineByPropertyName`關鍵字也會設定為`true`如此，Windows PowerShell 執行階段會檢查傳入物件`Name`屬性。 如果連入的物件會有這類屬性，執行階段會繫結`Name`參數來`Name`連入物件的屬性。

> [!NOTE]
> 設定`ValueFromPipeline`屬性 (attribute) 關鍵字參數的優先順序高於設定`ValueFromPipelineByPropertyName`關鍵字。

## <a name="overriding-an-input-processing-method"></a>覆寫輸入處理方法

如果您的 cmdlet 是處理管線輸入，它必須覆寫適當的輸入處理方法。 在中引進的基本輸入的處理方法[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)。

此 Get-proc cmdlet 會覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法來處理`Name`使用者或指令碼所提供的參數輸入。 如果未提供名稱，這個方法會取得每個要求的處理序名稱或所有處理程序的程序。 請注意，在[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)，來呼叫[System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29)是輸出機制，將輸出傳送到管線的物件。 此呼叫中，第二個參數`enumerateCollection`，設定為`true`告訴 Windows PowerShell 執行階段列舉的處理程序物件的陣列和一個處理序一次寫入命令列。

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

完整C#程式碼範例，請參閱 < [GetProcessSample03 範例](./getprocesssample03-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定義物件類型和格式設定

Windows PowerShell cmdlet 使用.Net 物件之間傳遞資訊。 因此，cmdlet 可能需要定義自己的類型，或可能需要擴充現有的類型提供的另一個 cmdlet 的 cmdlet。 如需定義新的型別或擴充現有類型的詳細資訊，請參閱[延伸的物件類型與格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-cmdlet"></a>建置此指令程式

在實作必須向 Windows PowerShell，透過 Windows PowerShell cmdlet 之後嵌入式管理單元。 如需有關如何註冊 cmdlet 的詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-cmdlet"></a>測試 Cmdlet

當尚未註冊 Windows PowerShell cmdlet 時，請執行命令列上測試。 例如，測試此範例指令程式的程式碼。 如需使用 cmdlet，從命令列的詳細資訊，請參閱[Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 在 Windows PowerShell 提示字元中，輸入下列命令來擷取在管線處理程序名稱。

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

- 輸入下列行以取得處理程序物件具有`Name`從程序，稱為 「 IEXPLORE"的屬性。 這個範例會使用`Get-Process`為上游的命令，以擷取 「 IEXPLORE"處理序 （Windows PowerShell 所提供） 的 cmdlet。

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

[加入處理命令列輸入的參數](./adding-parameters-that-process-command-line-input.md)

[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)

[擴充物件類型和格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell 參考](../windows-powershell-reference.md)

[Cmdlet 範例](./cmdlet-samples.md)
