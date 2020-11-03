---
description: 描述指定屬性的函式如何 `CmdletBinding` 使用可用於已編譯 Cmdlet 的方法和屬性。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Methods
ms.openlocfilehash: 0da0efdacdf76fca590e338dce7d4f41dc9c5026
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206620"
---
# <a name="about-functions-advanced-methods"></a>關於函數的 Advanced 方法

## <a name="short-description"></a>簡短描述

描述指定屬性的函式如何 `CmdletBinding` 使用可用於已編譯 Cmdlet 的方法和屬性。

## <a name="long-description"></a>完整描述

指定屬性的函式 `CmdletBinding` 可以透過變數存取許多方法和屬性 `$PSCmdlet` 。 這些方法包括下列方法：

- 編譯 Cmdlet 用來執行其工作的輸入處理方法。
- `ShouldProcess` `ShouldContinue` 用來在執行動作之前取得使用者意見反應的和方法。
- `ThrowTerminatingError`產生錯誤記錄的方法。
- 傳回 `Write` 不同輸出類型的數個方法。

**PSCmdlet** 類別的所有方法和屬性都可用於 advanced 函數。 如需詳細資訊，請參閱 [PSCmdlet](/dotnet/api/system.management.automation.pscmdlet)。

如需屬性的詳細資訊 `CmdletBinding` ，請參閱 [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)。
如需 **CmdletBindingAttribute** 類別，請參閱 [CmdletBindingAttribute](/dotnet/api/system.management.automation.cmdletbindingattribute)。

### <a name="input-processing-methods"></a>輸入處理方法

本節所述的方法稱為輸入處理方法。 針對函式，這三種方法是由函式的 `Begin` 、 `Process` 和區塊所表示 `End` 。 您不需要在函式中使用任何這些區塊。

> [!NOTE]
> 這些區塊也適用于未使用屬性的函式 `CmdletBinding` 。

#### <a name="begin"></a>開始

此區塊會用來為函式提供選擇性的一次性前置處理。
PowerShell 執行時間會針對管線中的每個函式實例，使用這個區塊中的程式碼一次。

#### <a name="process"></a>程序

此區塊用來提供函數的記錄記錄處理。 您可以使用 `Process` 區塊，而不需要定義其他區塊。 `Process`區塊執行數目取決於您使用函式的方式，以及函式接收的輸入。

自動變數 `$_` 或 `$PSItem` 包含管線中的目前物件，以便在區塊中使用 `Process` 。 `$input`自動變數包含僅適用于函式和腳本區塊的列舉值。
如需詳細資訊，請參閱 [about_Automatic_Variables](about_Automatic_Variables.md)。

- 在管線的開頭或外部呼叫函式，會執行 `Process` 一次區塊。
- 在管線中， `Process` 區塊會針對到達函式的每個輸入物件執行一次。
- 如果到達函式的管線輸入是空的，則 `Process` **不會** 執行區塊。
  - `Begin`和 `End` 區塊仍會執行。

> [!IMPORTANT]
> 如果函式參數設定為接受管線輸入，而且 `Process` 未定義區塊，則依記錄處理的記錄將會失敗。 在此情況下，您的函式只會執行一次，不論輸入為何。

#### <a name="end"></a>結束

此區塊會用來為函式提供選擇性的一次性後續處理。

下列範例會顯示函式的外框，其中包含一次性前置處理的 `Begin` 區塊、多筆 `Process` 記錄處理的區塊，以及 `End` 一次性後處理的區塊。

```powershell
Function Test-ScriptCmdlet
{
[CmdletBinding(SupportsShouldProcess=$True)]
    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

> [!NOTE]
> 使用 `Begin` 或 `End` 區塊需要您定義全部三個區塊。 使用全部三個區塊時，所有的 PowerShell 程式碼都必須在其中一個區塊內。

### <a name="confirmation-methods"></a>確認方法

#### <a name="shouldprocess"></a>ShouldProcess

在函式執行會變更系統的動作之前，會呼叫這個方法來要求使用者確認。 函數可以根據方法所傳回的布林值繼續進行。 只有從函式的區塊內才能呼叫這個方法 `Process{}` 。 `CmdletBinding`屬性也必須宣告函數支援 `ShouldProcess` (，如先前的範例) 所示。

如需此方法的詳細資訊，請參閱 [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess)。

如需如何要求確認的詳細資訊，請參閱 [要求確認](/powershell/scripting/developer/cmdlet/requesting-confirmation)。

#### <a name="shouldcontinue"></a>ShouldContinue

呼叫這個方法來要求第二次確認訊息。 它應該在方法傳回時呼叫 `ShouldProcess` `$true` 。 如需此方法的詳細資訊，請參閱 [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue)。

### <a name="error-methods"></a>Error 方法

函數可以在發生錯誤時呼叫兩種不同的方法。 當非終止錯誤發生時，函式應該呼叫 `WriteError` 方法，如方法一節中所述 `Write` 。 當發生終止錯誤且函式無法繼續時，它應該呼叫 `ThrowTerminatingError` 方法。 您也可以使用 `Throw` 語句來終止錯誤，並使用非終止錯誤的 [寫入錯誤](xref:Microsoft.PowerShell.Utility.Write-Error) Cmdlet。

如需詳細資訊，請參閱 [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror)。

### <a name="write-methods"></a>Write 方法

函數可以呼叫下列方法，以傳回不同類型的輸出。
請注意，並非所有輸出都會移至管線中的下一個命令。 您也可以使用各種 `Write` Cmdlet，例如 `Write-Error` 。

#### <a name="writecommanddetail"></a>WriteCommandDetail

如需方法的詳細資訊 `WriteCommandDetails` ，請參閱 [WriteCommandDetail](/dotnet/api/system.management.automation.cmdlet.writecommanddetail)。

#### <a name="writedebug"></a>WriteDebug

若要提供可用來對函式進行疑難排解的資訊，請讓函數呼叫 `WriteDebug` 方法。 `WriteDebug`方法會向使用者顯示 debug 訊息。 如需詳細資訊，請參閱 [WriteDebug](/dotnet/api/system.management.automation.cmdlet.writedebug)。

#### <a name="writeerror"></a>WriteError

當非終止錯誤發生時，函式應該呼叫這個方法，而函式則是設計來繼續處理記錄。 如需詳細資訊，請參閱 [WriteError](/dotnet/api/system.management.automation.cmdlet.writeerror)。

> [!NOTE]
> 如果發生終止錯誤，函式應該呼叫 [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror) 方法。

#### <a name="writeobject"></a>WriteObject

`WriteObject`方法可讓函數將物件傳送至管線中的下一個命令。 在大部分情況下， `WriteObject` 是函數傳回資料時所要使用的方法。 如需詳細資訊，請參閱 [PSCmdlet. WriteObject](/dotnet/api/system.management.automation.cmdlet.writeobject)。

#### <a name="writeprogress"></a>WriteProgress

對於具有需要很長時間才能完成之動作的函式，這個方法可讓函式呼叫 `WriteProgress` 方法，以顯示進度資訊。 例如，您可以顯示已完成的百分比。
如需詳細資訊，請參閱 [PSCmdlet. WriteProgress](/dotnet/api/system.management.automation.cmdlet.writeprogress)。

#### <a name="writeverbose"></a>WriteVerbose

若要提供函式運作方式的詳細資訊，請讓函數呼叫 `WriteVerbose` 方法，以向使用者顯示詳細訊息。 依預設不會顯示詳細訊息。 如需詳細資訊，請參閱 [PSCmdlet. WriteVerbose](/dotnet/api/system.management.automation.cmdlet.writeverbose)。

#### <a name="writewarning"></a>WriteWarning

若要提供可能導致非預期結果的狀況相關資訊，請將函數呼叫 WriteWarning 方法，以向使用者顯示警告訊息。 根據預設，會顯示警告訊息。 如需詳細資訊，請參閱 [PSCmdlet. WriteWarning](/dotnet/api/system.management.automation.cmdlet.writewarning)。

> [!NOTE]
> 您也可以藉由設定 `$WarningPreference` 變數，或使用 `Verbose` 和 `Debug` 命令列選項來顯示警告訊息。 如需變數的詳細資訊 `$WarningPreference` ，請參閱 [about_Preference_Variables](about_Preference_Variables.md)。

### <a name="other-methods-and-properties"></a>其他方法和屬性

如需可透過變數存取之其他方法和屬性的詳細資訊 `$PSCmdlet` ，請參閱 [PSCmdlet](/dotnet/api/system.management.automation.pscmdlet)。

例如， [ParameterSetName](/dotnet/api/system.management.automation.pscmdlet.parametersetname) 屬性可讓您查看正在使用的參數集。 參數集可讓您建立一個函式，該函式會根據執行函數時所指定的參數來執行不同的工作。

## <a name="see-also"></a>另請參閱

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

[about_Preference_Variables](about_Preference_Variables.md)
