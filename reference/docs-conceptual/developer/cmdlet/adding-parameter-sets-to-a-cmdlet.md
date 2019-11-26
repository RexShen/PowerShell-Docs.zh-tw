---
title: 將參數集新增至 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: c9c0b9a7a587e856efc82b4d277cee373e3f8b38
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416319"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>新增參數集到 Cmdlet

## <a name="things-to-know-about-parameter-sets"></a>有關參數集的須知事項

Windows PowerShell 會將參數集定義為一起運作的一組參數。 藉由將 Cmdlet 的參數分組，您可以建立單一 Cmdlet，根據使用者指定的參數群組來變更其功能。

Windows PowerShell 所提供的 `Get-EventLog` Cmdlet，是使用兩個參數集來定義不同功能的 Cmdlet 範例。 當使用者指定 `List` 或 `LogName` 參數時，此 Cmdlet 會傳回不同的資訊。 如果指定了 `LogName` 參數，此 Cmdlet 會傳回指定事件記錄檔中事件的相關資訊。 如果指定了 `List` 參數，Cmdlet 會傳回記錄檔本身的相關資訊（而不是其包含的事件資訊）。 在此情況下，`List` 和 `LogName` 參數會識別兩個不同的參數集。

有關參數集的兩個重要事項，就是 Windows PowerShell 執行時間只會針對特定輸入使用一個參數集，而且每個參數集必須至少有一個參數是該參數集唯一的。

為了說明最後一點，此停止程式 Cmdlet 會使用三個參數集： `ProcessName`、`ProcessId`和 `InputObject`。 每個參數集都有一個不在其他參數集內的參數。 參數集可以共用其他參數，但此 Cmdlet 會使用 `ProcessName`、`ProcessId`和 `InputObject` 的唯一參數，以識別 Windows PowerShell 執行時間應該使用的參數集。

## <a name="declaring-the-cmdlet-class"></a>宣告 Cmdlet 類別

Cmdlet 建立的第一個步驟一律為 Cmdlet 命名，並宣告可執行 Cmdlet 的 .NET 類別。 針對此 Cmdlet，會使用生命週期動詞 "Stop"，因為此 Cmdlet 會停止系統進程。 使用名詞名稱 "Proc"，因為 Cmdlet 會在進程上運作。 在下面的宣告中，請注意 Cmdlet 動詞和名詞名稱會反映在 Cmdlet 類別的名稱中。

> [!NOTE]
> 如需已核准 Cmdlet 動詞命令名稱的詳細資訊，請參閱[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)。

下列程式碼是這個停止進程 Cmdlet 的類別定義。

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a>宣告 Cmdlet 的參數

此 Cmdlet 會定義三個參數，做為 Cmdlet 的輸入（這些參數也會定義參數集），以及管理 Cmdlet 所執行之工作的 `Force` 參數，以及可判斷 Cmdlet 是否透過管線傳送輸出物件的 `PassThru` 參數。 根據預設，此 Cmdlet 不會透過管線傳遞物件。 如需最後兩個參數的詳細資訊，請參閱[建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。

### <a name="declaring-the-name-parameter"></a>宣告 Name 參數

此輸入參數可讓使用者指定要停止的處理常式名稱。 請注意， [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性的 `ParameterSetName` 屬性關鍵字會指定為此參數設定的 `ProcessName` 參數。

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

另請注意，別名 "ProcessName" 也會提供給此參數。

### <a name="declaring-the-id-parameter"></a>宣告 Id 參數

此輸入參數可讓使用者指定要停止之處理常式的識別碼。 請注意， [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性的 `ParameterSetName` 屬性關鍵字會指定 `ProcessId` 參數集。

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

另請注意，別名 "ProcessId" 也會提供給此參數。

### <a name="declaring-the-inputobject-parameter"></a>宣告 InputObject 參數

此輸入參數可讓使用者指定輸入物件，其中包含要停止之處理常式的相關資訊。 請注意， [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性的 `ParameterSetName` 屬性關鍵字會指定為此參數設定的 `InputObject` 參數。

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

另請注意，此參數沒有別名。

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>宣告多個參數集合中的參數

雖然每個參數集都必須有唯一的參數，但參數可以屬於一個以上的參數集。 在這些情況下，請為此參數所屬的每個集合，提供[Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性宣告給 shared 參數。 如果參數是在所有參數集中，您只需要宣告參數屬性一次，而不需要指定參數集名稱。

## <a name="overriding-an-input-processing-method"></a>覆寫輸入處理方法

每個 Cmdlet 都必須覆寫輸入處理方法，這通常會是[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。 在此 Cmdlet 中，會覆寫[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，讓 Cmdlet 可以處理任何數目的進程。 它包含一個 Select 語句，它會根據使用者指定的參數集來呼叫不同的方法。

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

這裡不會說明 Select 語句所呼叫的 Helper 方法，但您可以在下一節的完整程式碼範例中看到其實作為。

## <a name="code-sample"></a>程式碼範例

如需完整C#的範例程式碼，請參閱[StopProcessSample04 範例](./stopprocesssample04-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定義物件類型和格式

Windows PowerShell 會使用 .NET 物件在 Cmdlet 之間傳遞資訊。 因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。 如需定義新類型或擴充現有類型的詳細資訊，請參閱[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))。

## <a name="building-the-cmdlet"></a>建立 Cmdlet

在執行 Cmdlet 之後，您必須透過 Windows powershell 嵌入式管理單元向 Windows PowerShell 註冊它。 如需註冊 Cmdlet 的詳細資訊，請參閱[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。

## <a name="testing-the-cmdlet"></a>測試 Cmdlet

當您的 Cmdlet 已向 Windows PowerShell 註冊時，請在命令列上執行它來進行測試。 以下是一些測試，說明如何使用 `ProcessId` 和 `InputObject` 參數來測試其參數集以停止進程。

- 啟動 Windows PowerShell 之後，請執行 `ProcessId` 參數集的 Stop-Proc Cmdlet，以根據其識別碼停止進程。 在此情況下，Cmdlet 會使用 `ProcessId` 參數集來停止進程。

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- 當 Windows PowerShell 啟動時，請執行 `InputObject` 參數集的 Stop-Proc Cmdlet，以停止 `Get-Process` 命令所抓取之記事本物件上的進程。

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>另請參閱

[建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)

[如何建立 Windows PowerShell Cmdlet](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))

[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
