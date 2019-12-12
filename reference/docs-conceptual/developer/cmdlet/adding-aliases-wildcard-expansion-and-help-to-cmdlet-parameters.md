---
title: 將別名、萬用字元擴充和說明新增至 Cmdlet 參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: d210a852a90d94df2ab360dd86f0b83a396330e3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74415651"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>新增別名、萬用字元擴充與說明到 Cmdlet 參數

本節說明如何將別名、萬用字元擴充和說明訊息新增至 Stop-Proc Cmdlet 的參數（如[建立修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)中所述）。

這個停止進程指令程式會嘗試停止使用 Get-Proc Cmdlet 抓取的進程（如[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)所述）。

## <a name="defining-the-cmdlet"></a>定義 Cmdlet

Cmdlet 建立的第一個步驟一律為 Cmdlet 命名，並宣告可執行 Cmdlet 的 .NET 類別。 因為您要撰寫 Cmdlet 來變更系統，所以應該據以命名。 因為此 Cmdlet 會停止系統進程，所以會使用動詞 "Stop" （由[Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)類別所定義），並使用名詞 "Proc" 來表示進程。 如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)。

下列程式碼是這個停止進程 Cmdlet 的類別定義。

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>定義系統修改的參數

您的 Cmdlet 必須定義支援系統修改和使用者意見反應的參數。 Cmdlet 應定義 `Name` 參數或對等的，讓 Cmdlet 能夠以某種識別碼來修改系統。 此外，此 Cmdlet 應定義 `Force` 和 `PassThru` 參數。 如需這些參數的詳細資訊，請參閱[建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。

## <a name="defining-a-parameter-alias"></a>定義參數別名

參數別名可以是替代名稱或定義完善的1個字母或兩個字母的簡短名稱，以用於 Cmdlet 參數。 在這兩種情況下，使用別名的目標是要從命令列簡化使用者輸入。 Windows PowerShell 透過[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)屬性（使用宣告語法 [Alias （）]）支援參數別名。

下列程式碼顯示如何將別名新增至 `Name` 參數。

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

除了使用[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)屬性以外，Windows PowerShell 執行時間也會執行部分名稱比對，即使未指定別名也一樣。 例如，如果您的 Cmdlet 具有 `FileName` 參數，而且是以 `F`開頭的唯一參數，則使用者可以輸入 `Filename`、`Filenam`、`File`、`Fi`或 `F`，而且仍然會將專案辨識為 `FileName` 參數。

## <a name="creating-help-for-parameters"></a>建立參數的說明

Windows PowerShell 可讓您建立 Cmdlet 參數的說明。 請針對用於系統修改和使用者意見反應的任何參數執行此動作。 若要讓每個參數都支援說明，您可以在[Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性宣告中設定 `HelpMessage` 屬性關鍵字。 此關鍵字會定義要向使用者顯示的文字，以取得使用參數的協助。 您也可以設定 `HelpMessageBaseName` 關鍵字，以識別要用於訊息之資源的基底名稱。 如果您設定此關鍵字，則也必須設定 `HelpMessageResourceId` 關鍵字來指定資源識別碼。

這個 Stop-Proc Cmdlet 的下列程式碼會定義 `Name` 參數的 `HelpMessage` 屬性關鍵字。

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

您的 Cmdlet 必須覆寫輸入處理方法，這通常會是[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。 修改系統時，此 Cmdlet 應呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，以允許使用者在進行變更之前提供意見反應。（& i）..。 如需這些方法的詳細資訊，請參閱[建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。

## <a name="supporting-wildcard-expansion"></a>支援萬用字元展開

若要允許選取多個物件，您的 Cmdlet 可以使用[Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern)和[Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions)類別，為參數輸入提供萬用字元擴充支援。 萬用字元模式的範例包括 lsa *、\*.txt 和 [a-c]\*。 當模式包含應逐字使用的字元時，請使用後引號字元（'）做為換用字元。

檔案和路徑名稱的萬用字元擴充是常見案例的範例，當需要選取多個物件時，此 Cmdlet 可能會想要允許路徑輸入的支援。 常見的情況是在檔案系統中，使用者想要查看位於目前資料夾中的所有檔案。

您應該只需要很少的自訂萬用字元模式比對。 在此情況下，您的 Cmdlet 應支援萬用字元擴充的完整 POSIX 1003.2、3.13 規格，或下列簡化的子集：

- **問號（？）。** 符合指定位置的任何字元。

- **星號（\*）。** 符合從指定位置開始的零個或多個字元。

- **左括弧（[）。** 引進的模式括號運算式可以包含字元或字元範圍。 如果需要範圍，則會使用連字號（-）來表示範圍。

- **右括弧（]）。** 結束模式括號運算式。

- **後引號 escape 字元（'）。** 表示應該逐字採用下一個字元。 請注意，從命令列指定後置字元（而不是以程式設計方式指定）時，必須指定兩次後引號 escape 字元。

> [!NOTE]
> 如需萬用字元模式的詳細資訊，請參閱[在 Cmdlet 參數中支援萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)。

下列程式碼示範如何設定萬用字元選項，並定義用來解析此 Cmdlet 之 `Name` 參數的萬用字元模式。

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

下列程式碼顯示如何測試進程名稱是否符合定義的萬用字元模式。 請注意，在此情況下，如果進程名稱與模式不符，則 Cmdlet 會繼續進行，以取得下一個進程名稱。

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>範例程式碼

如需完整C#的範例程式碼，請參閱[StopProcessSample03 範例](./stopprocesssample03-sample.md)。

## <a name="define-object-types-and-formatting"></a>定義物件類型和格式

Windows PowerShell 會使用 .Net 物件在 Cmdlet 之間傳遞資訊。 因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。 如需定義新類型或擴充現有類型的詳細資訊，請參閱[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))。

## <a name="building-the-cmdlet"></a>建立 Cmdlet

在執行 Cmdlet 之後，必須透過 Windows PowerShell 嵌入式管理單元向 Windows PowerShell 註冊它。 如需註冊 Cmdlet 的詳細資訊，請參閱[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。

## <a name="testing-the-cmdlet"></a>測試 Cmdlet

當您的 Cmdlet 已向 Windows PowerShell 註冊時，您可以在命令列上執行它來進行測試。 讓我們來測試範例的 Stop-Proc Cmdlet。 如需從命令列使用 Cmdlet 的詳細資訊，請參閱[使用 Windows PowerShell 的消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 啟動 Windows PowerShell，並使用 `Name` 參數的 ProcessName 別名來停止進程。

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

- 在命令列上進行下列專案。 因為 Name 參數是必要的，所以系統會提示您輸入。 輸入 "！？" 顯示與參數相關聯的解說文字。

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

- 現在，請進行下列專案，以停止符合萬用字元模式 "* note\*" 的所有處理常式。 在您停止每個符合模式的處理常式之前，系統會先提示您。

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

[建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)

[如何建立 Windows PowerShell Cmdlet](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))

[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))

[在 Cmdlet 參數中支援萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
