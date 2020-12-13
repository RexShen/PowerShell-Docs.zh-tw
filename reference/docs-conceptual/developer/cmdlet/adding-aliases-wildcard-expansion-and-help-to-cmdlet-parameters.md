---
ms.date: 09/13/2016
ms.topic: reference
title: 新增別名、萬用字元擴充與說明到 Cmdlet 參數
description: 新增別名、萬用字元擴充與說明到 Cmdlet 參數
ms.openlocfilehash: f0f07796370b4613b1ca0ad17b16c6598bfa438d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660636"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>新增別名、萬用字元擴充與說明到 Cmdlet 參數

本節說明如何將別名、萬用字元擴充和說明訊息新增至 Stop-Proc Cmdlet 的參數中， (在 [建立可修改系統](./creating-a-cmdlet-that-modifies-the-system.md)) 的 Cmdlet 中所述。

此 Stop-Proc 指令程式會嘗試停止使用 Get-Proc Cmdlet 抓取的處理常式， () [建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md) 中所述。

## <a name="defining-the-cmdlet"></a>定義 Cmdlet

Cmdlet 建立的第一個步驟，一律會命名 Cmdlet 並宣告可執行 Cmdlet 的 .NET 類別。 因為您要撰寫 Cmdlet 來變更系統，所以應該據此命名。 由於此 Cmdlet 會停止系統進程，因此它會使用 [Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) 類別所定義的動詞 "Stop"，並以名詞 "Proc" 表示進程。 如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱 [Cmdlet 動詞命令名稱](./approved-verbs-for-windows-powershell-commands.md)。

下列程式碼是此 Stop-Proc Cmdlet 的類別定義。

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>定義修改系統的參數

您的 Cmdlet 必須定義支援系統修改和使用者意見反應的參數。 Cmdlet 應定義 `Name` 參數或對等專案，讓 Cmdlet 能夠以某種識別碼來修改系統。 此外，此 Cmdlet 也應定義 `Force` 和 `PassThru` 參數。 如需這些參數的詳細資訊，請參閱 [建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。

## <a name="defining-a-parameter-alias"></a>定義參數別名

參數別名可以是 Cmdlet 參數的替代名稱或定義完善的1個字母或2個字母的簡短名稱。 在這兩種情況下，使用別名的目標是要從命令列簡化使用者輸入。 Windows PowerShell 透過 [Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 屬性支援參數別名，其使用宣告語法 [Alias ( # A1]。

下列程式碼顯示如何將別名加入至 `Name` 參數。

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

除了使用 [Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 屬性以外，Windows PowerShell 執行時間也會執行部分名稱比對，即使未指定別名也一樣。 例如，如果您的 Cmdlet 有一個 `FileName` 參數，而且這是以開頭的唯一參數 `F` ，則使用者可以輸入 `Filename` 、、、 `Filenam` 或， `File` `Fi` `F` 並且仍將專案辨識為 `FileName` 參數。

## <a name="creating-help-for-parameters"></a>建立參數的說明

Windows PowerShell 可讓您建立 Cmdlet 參數的說明。 針對用於系統修改和使用者意見反應的任何參數，請這麼做。 針對每個支援協助的參數，您可以 `HelpMessage` 在 [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 屬性宣告中設定 attribute 關鍵字。 此關鍵字會定義要顯示給使用者的文字，以取得使用參數的協助。 您也可以設定 `HelpMessageBaseName` 關鍵字，以識別要用於訊息的資源基底名稱。 如果設定此關鍵字，您也必須設定 `HelpMessageResourceId` 關鍵字來指定資源識別碼。

此 Stop-Proc Cmdlet 中的下列程式碼會定義 `HelpMessage` 參數的 attribute 關鍵字 `Name` 。

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

您的 Cmdlet 必須覆寫輸入處理方法，最常見的方法是 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。 修改系統時，此 Cmdlet 應該呼叫 ShouldProcess 和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，以允許使用者在進行變更之前提供意見反應。」」（system [.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ）。 如需這些方法的詳細資訊，請參閱 [建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。

## <a name="supporting-wildcard-expansion"></a>支援萬用字元展開

若要允許選取多個物件，您的 Cmdlet 可以使用 [Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) 和 [Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) 類別來提供參數輸入的萬用字元擴充支援。 萬用字元模式的範例有 lsa *、 \* .txt 和 [a-c] \* 。 當模式包含應逐字使用的字元時，請使用後引號字元 (') 作為 escape 字元。

檔案和路徑名稱的萬用字元擴充是常見案例的範例，在需要選取多個物件時，此 Cmdlet 可能會想要允許路徑輸入的支援。 常見的案例是在檔案系統中，使用者想要查看目前資料夾中的所有檔案。

您只需要很少的自訂萬用字元模式比對。 在此情況下，您的 Cmdlet 應該支援萬用字元擴充的完整 POSIX 1003.2、3.13 規格或下列簡化子集：

- **問號 (？ ) 。** 符合指定位置的任何字元。

- **星號 (\*) 。** 符合從指定位置開始的零或多個字元。

- **左括弧 ( [) ]。** 引進可包含字元或字元範圍的模式括號運算式。 如果需要範圍，則會使用連字號 (-) 來指出範圍。

- **右括弧 (] ) 。** 結束模式括號運算式。

- **反向引號 escape 字元 (') 。** 表示應以文字形式取得下一個字元。 請注意，從命令列指定後引號字元 (與以程式設計的方式指定時，不是以程式設計的方式) ，就必須指定後引號 escape 字元兩次。

> [!NOTE]
> 如需萬用字元模式的詳細資訊，請參閱 [在 Cmdlet 參數中支援萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)。

下列程式碼示範如何設定萬用字元選項，並定義用來解析此 Cmdlet 之參數的萬用字元模式 `Name` 。

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

下列程式碼示範如何測試進程名稱是否符合已定義的萬用字元模式。 請注意，在此情況下，如果處理常式名稱不符合模式，Cmdlet 會繼續進行，以取得下一個進程名稱。

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>程式碼範例

如需完整的 c # 範例程式碼，請參閱 [StopProcessSample03 範例](./stopprocesssample03-sample.md)。

## <a name="define-object-types-and-formatting"></a>定義物件類型和格式

Windows PowerShell 使用 .Net 物件在 Cmdlet 之間傳遞資訊。 因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。 如需定義新型別或擴充現有類型的詳細資訊，請參閱 [擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))。

## <a name="building-the-cmdlet"></a>建立 Cmdlet

在執行 Cmdlet 之後，必須透過 Windows PowerShell 嵌入式管理單元向 Windows PowerShell 註冊。 如需註冊 Cmdlet 的詳細資訊，請參閱 [如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。

## <a name="testing-the-cmdlet"></a>測試 Cmdlet

當您的 Cmdlet 註冊 Windows PowerShell 時，您可以在命令列上執行它來進行測試。 讓我們測試範例 Stop-Proc Cmdlet。 如需從命令列使用 Cmdlet 的詳細資訊，請參閱 [Windows PowerShell 的消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 啟動 Windows PowerShell，並使用 Stop-Proc 來停止使用參數 ProcessName 別名的進程 `Name` 。

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

    即會出現下列輸出。

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

    即會出現下列輸出。

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- 現在，請輸入下列專案，以停止所有符合萬用字元模式 "* note" 的處理常式 \* 。 在停止符合模式的每個處理常式之前，系統會提示您。

    ```powershell
    PS> stop-proc -Name *note*
    ```

    即會出現下列輸出。

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

    即會出現下列輸出。

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

    即會出現下列輸出。

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>另請參閱

[建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)

[如何建立 Windows PowerShell Cmdlet](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[擴充物件類型和格式化](/previous-versions//ms714665(v=vs.85))

[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))

[在 Cmdlet 參數中支援萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
