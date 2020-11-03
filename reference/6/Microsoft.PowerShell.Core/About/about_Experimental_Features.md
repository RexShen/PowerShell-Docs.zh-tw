---
description: PowerShell 中的「實驗性功能」支援能提供一個機制，使實驗性功能可以與 PowerShell 或 PowerShell 模組中的現有穩定功能並存。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 關於實驗性功能
ms.openlocfilehash: 663b8bbd8659b972004499e0c8a247818b8ef311
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207123"
---
# <a name="experimental-features"></a>實驗性功能

PowerShell 中的「實驗性功能」支援能提供一個機制，使實驗性功能可以與 PowerShell 或 PowerShell 模組中的現有穩定功能並存。

實驗性功能是設計尚未完成的功能。 該功能可供使用者測試並提供意見反應。 在實驗性功能完成之後，設計變更便會成為中斷性變更。 實驗性功能並不適用於生產環境，因為允許對其進行中斷性變更。

實驗性功能預設為停用，且必須由系統的使用者或系統管理員明確地啟用。

啟用的實驗性功能會列在的檔案中，以 `powershell.config.json` `$PSHOME` 供特定使用者或使用者特定的設定檔使用。

> [!NOTE]
> 在使用者設定檔中啟用的實驗性功能優先于系統設定檔中所列的實驗性功能。

## <a name="the-experimental-attribute"></a>實驗性屬性

您 `Experimental` 可以使用屬性將某些程式碼宣告為實驗。

使用下列語法來宣告 `Experimental` 屬性（attribute），以提供實驗性功能的名稱，以及啟用實驗性功能時要採取的動作：

```csharp
[Experimental(NameOfExperimentalFeature, ExperimentAction)]
```

針對模組， `NameOfExperimentalFeature` 必須遵循的形式 `<modulename>.<experimentname>` 。 `ExperimentAction`必須指定參數，且唯一有效的值為：

- `Show` 表示在功能啟用時顯示此實驗性功能
- `Hide` 表示在啟用功能時隱藏此實驗性功能

### <a name="declaring-experimental-features-in-modules-written-in-c"></a>宣告以 C 撰寫的模組中的實驗性功能\#

想要使用實驗性功能旗標的模組作者，可以使用屬性將 Cmdlet 宣告為實驗性 `Experimental` 。

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }
```

### <a name="declaring-experimental-features-in-modules-written-in-powershell"></a>宣告以 PowerShell 撰寫的模組中的實驗性功能

以 PowerShell 撰寫的模組也可以使用 `Experimental` 屬性來宣告實驗性 Cmdlet：

```powershell
function Enable-SSHRemoting {
    [Experimental("MyRemoting.PSSSHRemoting", "Show")]
    [CmdletBinding()]
    param()
    ...
}
```

### <a name="mutually-exclusive-experimental-features"></a>相互專屬的實驗性功能

在某些情況下，實驗性功能無法與現有的功能並存並存，或另一個實驗性功能。

例如，您可以擁有可覆寫現有 Cmdlet 的實驗性 Cmdlet。 這兩個版本無法並存並存。 此 `ExperimentAction.Hide` 設定只允許一次啟用兩個 Cmdlet 的其中一個。

在此範例中，我們會建立新的實驗 `Invoke-WebRequest` Cmdlet。
`InvokeWebRequestCommand` 包含非實驗性的執行。
`InvokeWebRequestCommandV2` 包含 Cmdlet 的實驗版本。

使用時， `ExperimentAction.Hide` 只會允許一次啟用兩項功能的其中一個：

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }

[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Hide)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommand : WebCmdletBase { ... }
```

`MyWebCmdlets.PSWebCmdletV2`啟用實驗性功能時，將 `InvokeWebRequestCommand` 會隱藏現有的執行，並 `InvokeWebRequestCommandV2` 提供的實作為 `Invoke-WebRequest` 。

這可讓使用者試用新的 Cmdlet 並提供意見反應，然後在需要時還原為非實驗版本。

### <a name="experimental-parameters-in-cmdlets"></a>Cmdlet 中的實驗性參數

`Experimental`屬性也可以套用至個別參數。 這可讓您針對現有的 Cmdlet （而不是全新的 Cmdlet）建立一組實驗性的參數。

以下是 c # 中的範例：

```csharp
[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Show)]
[Parameter(ParameterSet = "NewCompilation")]
public CompilationParameters CompileParameters { ... }

[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Hide)]
[Parameter()]
public CodeDom CodeDom { ... }
```

以下是 PowerShell 腳本中的不同範例：

```powershell
param(
    [Experimental("MyModule.PSNewFeature", "Show")]
    [string] $NewName,

    [Experimental("MyModule.PSNewFeature", "Hide")]
    [string] $OldName
)
```

## <a name="checking-if-an-experimental-feature-is-enabled"></a>檢查是否已啟用實驗性功能

在您的程式碼中，您必須先檢查實驗性功能是否已啟用，然後再採取適當的動作。 您可以使用類別上的靜態方法，判斷是否已啟用實驗性功能 `IsEnabled()` `System.Management.Automation.ExperimentalFeature` 。

以下是 c # 中的範例：

```csharp
if (ExperimentalFeature.IsEnabled("MyModule.MyExperimentalFeature"))
{
   // code specific to the experimental feature
}
```

以下是 PowerShell 腳本中的範例：

```powershell
if ([ExperimentalFeature]::IsEnabled("MyModule.MyExperimentalFeature"))
{
  # code specific to the experimental feature
}
```

## <a name="see-also"></a>另請參閱

[Enable-ExperimentalFeature](xref:Microsoft.PowerShell.Core.Enable-ExperimentalFeature)

[Disable-ExperimentalFeature](xref:Microsoft.PowerShell.Core.Disable-ExperimentalFeature)

[Get-ExperimentalFeature](xref:Microsoft.PowerShell.Core.Get-ExperimentalFeature)
