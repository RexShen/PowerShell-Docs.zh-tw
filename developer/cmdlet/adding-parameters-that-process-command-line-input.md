---
title: 將處理命令列輸入的參數加入 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: fb113086ce89e4becff9bcaf3232905fde2bf610
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055915"
---
# <a name="adding-parameters-that-process-command-line-input"></a>新增處理命令列輸入的參數

其中一個的 cmdlet 來源是輸入的命令列。 本主題描述如何將參數加入**Get-proc** cmdlet (見[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md))，讓此指令程式可以處理從明確為基礎的本機電腦的輸入物件會傳遞至 cmdlet。 **Get-proc**這裡擷取其名稱為基礎的處理序所述的 cmdlet，並接著會處理序的相關資訊顯示在命令提示字元。

本主題中，為下列各節：

- [定義在 Cmdlet 類別](#Defining-the-Cmdlet-Class)

- [宣告參數](#Declaring-Parameters)

- [支援的參數驗證](#Supporting-Parameter-Validation)

- [覆寫輸入處理方法](#Overriding-an-Input-Processing-Method)

- [程式碼範例](#Code-Sample)

- [定義物件類型和格式設定](#Defining-Object-Types-and-Formatting)

- [建置此指令程式](#Building-the-Cmdlet)

- [測試 Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>定義在 Cmdlet 類別

Cmdlet 建立的第一個步驟是，cmdlet 命名並實作指令程式的.NET Framework 類別的宣告。 此 cmdlet 可擷取處理序資訊，所以在這裡選擇的指令動詞名稱是 「 取得 」。 （幾乎任何一種能夠擷取資訊的指令程式可以處理命令列輸入）。如需已核准的 cmdlet 動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)。

以下是類別宣告**Get-proc** cmdlet。 將提供關於此定義的詳細資料[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)。

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

Cmdlet 參數可讓使用者提供 cmdlet 的輸入。 在下列範例中， **Get-proc**並`Get-Member`是導送 cmdlet 的名稱並`MemberType`是參數`Get-Member`cmdlet。 參數的引數"property"。

**PS > 取得跨處理序;`get-member` -membertype 屬性**

若要宣告 cmdlet 的參數，您必須先定義代表參數的屬性。 在  **Get-proc** cmdlet，唯一的參數是`Name`，在此情況下代表要擷取之.NET Framework 程序物件的名稱。 因此，在 cmdlet 類別定義接受名稱的陣列的字串類型屬性。

以下是參數宣告`Name`的參數**Get-proc** cmdlet。

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

若要通知，這個值，Windows PowerShell 執行階段`Name`參數， [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性加入至屬性定義。 宣告這個屬性的基本語法是`[Parameter()]`。

> [!NOTE]
> 參數必須明確標示為公用。 未標示為公用的預設值為 internal，和 Windows PowerShell 執行階段找不到的參數。

此 cmdlet 會使用字串的陣列`Name`參數。 可能的話，您的 cmdlet 也應該定義參數陣列，因為這可讓 cmdlet 接受一個以上的項目。

#### <a name="things-to-remember-about-parameter-definitions"></a>參數定義時，必須注意的事項

- 預先定義的 Windows PowerShell 參數名稱和資料類型應該重複使用盡量確保您的 cmdlet 與 Windows PowerShell cmdlet 相容。 例如，如果使用預先定義的所有 cmdlet`Id`參數名稱來識別資源，使用者可輕鬆地了解參數，無論他們使用何種 cmdlet 的意義。 基本上，參數名稱會遵循相同的規則所使用的 common language runtime (CLR) 中的變數名稱。 如需參數命名的詳細資訊，請參閱[Cmdlet 的參數名稱](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb)。

- Windows PowerShell 會保留幾個參數名稱，以提供一致的使用者體驗。 請勿使用這些參數名稱： `WhatIf`， `Confirm`， `Verbose`， `Debug`， `Warn`， `ErrorAction`， `ErrorVariable`， `OutVariable`，和`OutBuffer`。 此外，保留了這些參數名稱的下列別名： `vb`， `db`， `ea`， `ev`， `ov`，和`ob`。

- `Name` 是簡單且常見的參數名稱，建議在您的 cmdlet 中使用。 您最好選擇比特定指令程式所特有而且難以記住複雜名稱如下的參數名稱。

- 參數是在 Windows PowerShell 中，不區分大小寫的雖然預設殼層會保留大小寫。 引數的區分大小寫取決於此指令程式的作業。 引數會指定在命令列傳遞至參數。

- 如需其他的參數宣告的範例，請參閱[Cmdlet 參數](./cmdlet-parameters.md)。

## <a name="declaring-parameters-as-positional-or-named"></a>宣告為位置或具名的參數

指令程式必須設定每個參數為位置或具名參數。 這兩種參數接受單一引數，並以逗號和布林設定分隔的多個引數。 布林值的參數，也稱為*切換*，處理，則為 True 的設定。 參數用來判斷參數存在。 建議的預設值是`false`。

此範例**Get-proc** cmdlet 定義`Name`參數做為位置參數，以位置為 0。 這表示使用者輸入的命令列的第一個引數會自動插入這個參數。 如果您想要定義具名的參數，使用者必須指定參數名稱從命令列中，將保留`Position`從屬性宣告的關鍵字。

> [!NOTE]
> 除非必須命名參數，否則我們建議您最常使用的參數位置，讓使用者不需要輸入參數名稱。

## <a name="declaring-parameters-as-mandatory-or-optional"></a>宣告為強制或選擇性的參數

指令程式必須設定每個參數為選擇性或必要的參數。 在此範例中**Get-proc** cmdlet，此 cmdlet`Name`參數會定義為選擇性，因為`Mandatory`屬性宣告中未設定關鍵字。

## <a name="supporting-parameter-validation"></a>支援的參數驗證

此範例**Get-proc** cmdlet 會將輸入的驗證屬性 (attribute) [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute)至`Name`參數，以啟用驗證，既不是輸入`null`或空白。 這個屬性是其中一個 Windows PowerShell 所提供的數個驗證屬性。 如需其他的驗證屬性的範例，請參閱[驗證參數輸入](./validating-parameter-input.md)。

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>覆寫輸入處理方法

如果您的指令程式來處理命令列輸入，它必須覆寫適當的輸入處理方法。 在中引進的基本輸入的處理方法[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)。

**Get-proc** cmdlet 會覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，以處理`Name`使用者或指令碼所提供的參數輸入。 如果未提供名稱，這個方法會取得每個要求的處理序名稱，或所有處理序的處理程序。 請注意，在[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)，來呼叫[System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)是輸出機制，將輸出傳送到管線的物件。 此呼叫中，第二個參數`enumerateCollection`，設定為`true`告知 Windows PowerShell 執行階段列舉的處理程序物件的輸出陣列和一個處理序一次寫入命令列。

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

完整C#程式碼範例，請參閱 < [GetProcessSample02 範例](./getprocesssample02-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定義物件類型和格式設定

Windows PowerShell cmdlet，使用.NET Framework 物件之間傳遞資訊。 因此，cmdlet 可能需要定義自己的類型，或可能需要擴充現有的類型提供的另一個 cmdlet 的 cmdlet。 如需定義新的型別或擴充現有類型的詳細資訊，請參閱[延伸的物件類型與格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-cmdlet"></a>建置此指令程式

您實作的 cmdlet 之後，您必須使用 Windows PowerShell 註冊使用 Windows PowerShell 嵌入式管理單元。 如需有關如何註冊 cmdlet 的詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-cmdlet"></a>測試 Cmdlet

使用 Windows PowerShell 註冊您的 cmdlet 時，您可以藉由在命令列上執行它來進行測試。 以下是兩種方式可以測試此範例指令程式的程式碼。 如需使用 cmdlet，從命令列的詳細資訊，請參閱[Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 在 Windows PowerShell 提示字元中，使用下列命令來列出 Internet Explorer 的程序，名為"IEXPLORE。 」

    ```powershell
    PS> get-proc -name iexplore
    ```

下列輸出隨即出現。

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- 若要列出的 Internet Explorer、 Outlook 和 「 記事本 」 處理程序名為"IEXPLORE"，"OUTLOOK"和"NOTEPAD，"使用下列命令。 如果有多個處理序，其中會顯示所有。

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

下列輸出隨即出現。

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a>另請參閱

[新增處理程序管線輸入的參數](./adding-parameters-that-process-pipeline-input.md)

[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)

[擴充物件類型和格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell 參考](../windows-powershell-reference.md)

[Cmdlet 範例](./cmdlet-samples.md)
