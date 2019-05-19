---
title: 新增萬用字元展開的別名和 Cmdlet 參數的協助 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: 946b71e4480a47ac6ccd6930be445d7efb4fb62d
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854901"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>新增別名、萬用字元擴充與說明到 Cmdlet 參數

本節說明如何新增萬用字元展開的別名，並說明郵件停止程序 cmdlet 的參數 (中所述[建立 Cmdlet 會修改系統](./creating-a-cmdlet-that-modifies-the-system.md))。

此停止程序 cmdlet 會嘗試停止處理程序會擷取使用 Get-proc cmdlet (中所述[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md))。

## <a name="defining-the-cmdlet"></a>定義此指令程式

Cmdlet 建立的第一個步驟一律命名 cmdlet，並實作指令程式的.NET 類別的宣告。 因為您正在撰寫的 cmdlet，來變更系統，它應該命名。 由於此 cmdlet 會停止系統處理序，它會使用所定義的 「 停止 」，動詞[System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)類別，和名詞"Proc"來指出程序。 如需已核准的 cmdlet 動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)。

下列程式碼會為此停止程序 cmdlet 類別定義。

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>修改系統定義的參數

您的指令程式必須定義參數，該修改支援系統和使用者意見反應。 此 cmdlet 應該定義`Name`參數或同等權限，讓此指令程式將能夠某種形式的識別項來修改系統。 此外，此 cmdlet 應該定義`Force`和`PassThru`參數。 如需有關這些參數的詳細資訊，請參閱 <<c0> [ 建立 Cmdlet 會修改系統](./creating-a-cmdlet-that-modifies-the-system.md)。

## <a name="defining-a-parameter-alias"></a>定義參數別名

參數別名可以是替代的名稱或針對 cmdlet 參數定義完善字母 1 或 2 個字母簡短名稱。 在這兩種情況下，使用別名的目標是簡化從命令列的使用者項目。 Windows PowerShell 支援透過參數別名[System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)屬性，它會使用宣告語法 [Alias()]。

下列程式碼會示範如何將別名加入至`Name`參數。

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

除了使用[System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)屬性，Windows PowerShell 執行階段執行的部分名稱比對，即使已指定任何別名。 例如，如果您的 cmdlet 已`FileName`參數，也就是開頭的唯一參數`F`，使用者可以輸入`Filename`， `Filenam`， `File`， `Fi`，或`F`，仍會辨識項目標示為`FileName`參數。

## <a name="creating-help-for-parameters"></a>建立參數的說明

Windows PowerShell 可讓您建立的 cmdlet 參數的說明。 用於系統修改和使用者意見反應的任何參數執行這項操作。 對於支援說明每個參數，您可以設定`HelpMessage`屬性中的關鍵字[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性宣告。 這個關鍵字會定義要有關使用參數使用者顯示的文字。 您也可以設定`HelpMessageBaseName`關鍵字來識別資源以用於訊息的基底名稱。 如果您設定此關鍵字，您也必須設定`HelpMessageResourceId`關鍵字來指定資源識別項。

下列程式碼，從這個停止程序 cmdlet 定義`HelpMessage`屬性的關鍵字`Name`參數。

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a>覆寫輸入處理方法

您的 cmdlet 必須覆寫輸入處理方法，這是最常[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。 此 cmdlet 時修改系統，應該呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)並[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，可讓使用者若要進行變更之前，請提供意見反應。 如需這些方法的詳細資訊，請參閱[建立 Cmdlet 會修改系統](./creating-a-cmdlet-that-modifies-the-system.md)。

## <a name="supporting-wildcard-expansion"></a>支援的萬用字元展開

若要允許選取多個物件，可以使用您的 cmdlet [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern)並[System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions)類別提供萬用字元展開支援輸入的參數。 萬用字元模式的範例包括 lsa * \*.txt 和 [a-c]\*。 模式所包含的字元應該解譯為常值使用時，則您可以做為逸出字元後引號字元 （'）。

萬用字元展開的檔案和路徑的名稱是此 cmdlet 可能要允許的路徑輸入支援，需要選取多個物件時的常見案例的範例。 常見的案例是在檔案系統中，使用者想要查看位於目前的資料夾中的所有檔案的位置。

您應該很少需要自訂的萬用字元模式比對實作。 在此情況下，您的指令程式應該支援完整的 POSIX 1003.2、 3.13 萬用字元展開規格或以下的簡化的子集：

- **問號 （？）。** 比對任何字元，在指定的位置。

- **星號 (\*)。** 比對零或多個字元的指定位置開始。

- **左括號 ([])。** 引進模式括號運算式可以包含字元範圍。 如果範圍為必要項目，是連字號 （-） 用來表示範圍。

- **右括號 (])。** 結束模式括號運算式。

- **後引號逸出字元 （'）。** 表示下一個字元應該解譯為常值帶。 請注意，當指定時從命令列 （而不是以程式設計方式指定） 的後引號字元後, 引號逸出字元必須指定兩次。

> [!NOTE]
> 如需萬用字元模式的詳細資訊，請參閱[在 Cmdlet 參數中的 支援使用萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)。

下列程式碼示範如何設定萬用字元選項，並定義用來解析萬用字元模式`Name`此 cmdlet 的參數。

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

下列程式碼會示範如何測試處理序名稱是否符合已定義的萬用字元模式。 請注意，在此情況下，是否處理序名稱與模式不符，此 cmdlet 會繼續上取得下一個程序名稱。

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>程式碼範例

完整C#程式碼範例，請參閱 < [StopProcessSample03 範例](./stopprocesssample03-sample.md)。

## <a name="define-object-types-and-formatting"></a>定義物件類型和格式設定

Windows PowerShell cmdlet 使用.Net 物件之間傳遞資訊。 因此，cmdlet 可能需要定義自己的類型，或可能需要擴充現有的類型提供的另一個 cmdlet 的 cmdlet。 如需定義新的型別或擴充現有類型的詳細資訊，請參閱[延伸的物件類型與格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-cmdlet"></a>建置此指令程式

在實作之後的 cmdlet，它必須向 Windows PowerShell 透過 Windows PowerShell 嵌入式管理單元。 如需有關如何註冊 cmdlet 的詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-cmdlet"></a>測試 Cmdlet

當您的 cmdlet 已向 Windows PowerShell 時，您可以藉由在命令列上執行它來進行測試。 我們來測試範例停止程序 cmdlet。 如需使用 cmdlet，從命令列的詳細資訊，請參閱[Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 啟動 Windows PowerShell 並使用停止程序，停止處理序使用的 ProcessName 別名`Name`參數。

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

下列輸出隨即出現。

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- 請在命令列上的下列項目。 Name 參數是必要的因為它會提示您。 輸入 「 ！？" 會顯示與參數關聯的說明文字。

    ```powershell
    PS> stop-proc
    ```

下列輸出隨即出現。

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- 現在請停止所有符合萬用字元模式的處理序的下列項目 」 * 注意\*"。 系統會提示您停止每個符合模式的處理序之前。

    ```powershell
    PS> stop-proc -Name *note*
    ```

下列輸出隨即出現。

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

下列輸出隨即出現。

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

下列輸出隨即出現。

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>另請參閱

[建立修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)

[如何建立 Windows PowerShell Cmdlet](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[擴充物件類型和格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[如何註冊 Cmdlet、 提供者，以及裝載應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[在 Cmdlet 參數支援萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
