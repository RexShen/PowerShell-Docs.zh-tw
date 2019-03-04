---
title: 將參數新增至 Cmdlet，設定 |Microsoft Docs
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
ms.openlocfilehash: b02a2e0d4b0a27c261b0bc05febda7826ad5276e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859264"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>新增參數集到 Cmdlet

本節說明如何新增參數集合停止處理序的指令程式 (中所述[建立 Cmdlet 會修改系統](./creating-a-cmdlet-that-modifies-the-system.md))。 類似於其他程式設計人員的指南中所述的停止程序 cmdlet，此 cmdlet 會嘗試停止處理程序會擷取使用 Get-proc cmdlet (中所述[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md))。

在本節中的主題包括下列各項：

- [若要了解參數集的項目](#Adding-Parameter-Sets-to-a-Cmdlet)

- [宣告 Cmdlet 類別](#Declaring-the-Cmdlet-Class)

- [宣告 Cmdlet 的參數](#Declaring-the-Parameters-of-the-Cmdlet)

- [覆寫輸入處理方法](#Overriding-an-Input-Processing-Method)

- [程式碼範例](#Declaring-the-Parameters-of-the-Cmdlet)

- [定義物件類型和格式設定](#Defining-Object-Types-and-Formatting)

- [建置此指令程式](#Building-the-Cmdlet)

- [測試 Cmdlet](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a>若要了解參數集的項目

Windows PowerShell 中定義的參數集的一組一起運作的參數。 群組 cmdlet 的參數，您可以建立單一的 cmdlet，可以變更其使用者所指定的哪一個群組的參數為基礎的功能。

指令程式會使用兩個參數集來定義不同的功能，例如`Get-EventLog`所提供的 Windows PowerShell cmdlet。 當使用者指定此 cmdlet 會傳回不同的資訊`List`或`LogName`參數。 如果`LogName`參數指定，則指令程式可傳回指定的事件記錄檔事件的相關資訊。 如果`List`參數指定，則此 cmdlet 會傳回檔案本身 （不包含事件資訊） 的記錄檔的相關資訊。 在此情況下，`List`和`LogName`參數會識別兩個不同的參數集。

兩個參數集時，必須注意的重要事項是，Windows PowerShell 執行階段會使用為特定的輸入，只有一個參數，而且每個參數集，必須具有至少一個參數，都是唯一的該參數集。

為了說明這個最後一點，此處理序停止外 cmdlet 會使用三個參數集： `ProcessName`， `ProcessId`，和`InputObject`。 每一參數集合具有一個參數不是在其他的參數集。 參數集可以共用其他的參數，但此 cmdlet 會使用唯一的參數`ProcessName`， `ProcessId`，和`InputObject`來識別哪些組 Windows PowerShell 執行階段應該使用的參數。

## <a name="declaring-the-cmdlet-class"></a>宣告 Cmdlet 類別

Cmdlet 建立的第一個步驟一律命名 cmdlet，並實作指令程式的.NET 類別的宣告。 此 cmdlet，因為此 cmdlet 會停止系統處理序，就會使用一個生命週期動詞"Stop"。 名詞 」 名稱"Proc"，因為 cmdlet 的運作方式的處理程序。 在下列宣告中，請注意 cmdlet 動詞和名詞名稱會反映在 cmdlet 類別的名稱。

> [!NOTE]
> 如需已核准的 cmdlet 動詞名稱的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)。

下列程式碼會為此停止程序 cmdlet 類別定義。

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

此 cmdlet 會定義做為指令程式 （這些參數也定義的參數集），輸入所需的三個參數，以及`Force`管理 cmdlet 的功能的參數和`PassThru`決定是否要傳送此 cmdlet 的參數透過管線的輸出物件。 根據預設，此 cmdlet 未通過管線的物件。 如需有關這些最後兩個參數的詳細資訊，請參閱 <<c0> [ 建立 Cmdlet 會修改系統](./creating-a-cmdlet-that-modifies-the-system.md)。

### <a name="declaring-the-name-parameter"></a>宣告名稱參數

此輸入的參數可讓使用者指定要停止的處理程序的名稱。 請注意，`ParameterSetName`屬性的關鍵字[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性會指定`ProcessName`參數設定為此參數。

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

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

也請注意 「 ProcessName"的別名指定給這個參數。

### <a name="declaring-the-id-parameter"></a>宣告的 Id 參數

此輸入的參數可讓使用者指定要停止的處理程序的識別碼。 請注意，`ParameterSetName`屬性的關鍵字[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性會指定`ProcessId`參數集。

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

請注意，也提供給這個參數的別名"ProcessId"。

### <a name="declaring-the-inputobject-parameter"></a>宣告 InputObject 參數

此輸入的參數可讓使用者指定輸入的物件，包含要停止處理序的相關資訊。 請注意，`ParameterSetName`屬性的關鍵字[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性會指定`InputObject`參數設定為此參數。

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

也請注意，此參數有沒有別名。

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>在多個參數集中宣告參數

雖然必須有唯一的參數，針對每個參數集，參數可以屬於一個以上的參數集。 在這些情況下，授與共用的參數[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性宣告，每個設定為此參數所屬。 如果參數是在所有的參數集，您只需要一次宣告的參數屬性，並不需要指定的參數集名稱。

## <a name="overriding-an-input-processing-method"></a>覆寫輸入處理方法

每個 cmdlet 必須覆寫輸入處理方法，這是最常[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。 此 cmdlet，在[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) ，讓此指令程式可以處理任意數目的處理程序，會覆寫方法。 它包含哪些參數集的使用者不同的方法以呼叫已指定 Select 陳述式。

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

Select 陳述式所呼叫的 Helper 方法不在這裡詳述，但您可以查看其完整的程式碼範例下, 一節中的實作。

## <a name="code-sample"></a>程式碼範例

完整C#程式碼範例，請參閱 < [StopProcessSample04 範例](./stopprocesssample04-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定義物件類型和格式設定

Windows PowerShell cmdlet 使用.NET 物件之間傳遞資訊。 因此，cmdlet 可能需要定義自己的類型，或可能需要擴充現有的類型提供的另一個 cmdlet 的 cmdlet。 如需定義新的型別或擴充現有類型的詳細資訊，請參閱[延伸的物件類型與格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-cmdlet"></a>建置此指令程式

在實作之後的 cmdlet，您必須向 Windows PowerShell 透過 Windows PowerShell 嵌入式管理單元。 如需有關如何註冊 cmdlet 的詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-cmdlet"></a>測試 Cmdlet

當尚未註冊 Windows PowerShell cmdlet 時，請執行命令列上測試。 以下是一些測試，顯示如何`ProcessId`和`InputObject`參數可用來測試其停止處理序的參數集。

- 啟動 Windows powershell 中，執行 停止處理序指令程式搭配`ProcessId`參數設定為停止處理程序根據其識別項。 在此情況下，使用此 cmdlet`ProcessId`參數設定為停止程序。

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- 啟動 Windows powershell 中，執行 停止處理序指令程式搭配`InputObject`參數設定為停止處理程序所擷取的 「 記事本 」 物件上`Get-Process`命令。

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>另請參閱

[建立 Cmdlet 會修改系統](./creating-a-cmdlet-that-modifies-the-system.md)

[如何建立 Windows PowerShell Cmdlet](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[擴充物件類型和格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)
