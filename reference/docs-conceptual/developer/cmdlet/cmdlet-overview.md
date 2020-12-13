---
ms.date: 06/11/2020
ms.topic: reference
title: Cmdlet 概觀
description: Cmdlet 概觀
ms.openlocfilehash: ed3082e1a821bb9643ea2eef13b7348eb48488e4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653223"
---
# <a name="cmdlet-overview"></a>Cmdlet 概觀

Cmdlet 是在 PowerShell 環境中使用的輕量命令。 PowerShell 執行時間會在命令列所提供的自動化腳本內容中叫用這些 Cmdlet。 PowerShell 執行時間也會透過 PowerShell Api 以程式設計方式叫用它們。

## <a name="cmdlets"></a>指令程式

Cmdlet 會執行動作，通常會將 Microsoft .NET 物件傳回至管線中的下一個命令。 Cmdlet 是參與 PowerShell 管線語義的單一命令。
包含二進位 (C#) Cmdlet、進階指令碼函式、CDXML 以及工作流程。

此 SDK 檔說明如何建立以 c # 撰寫的二進位 Cmdlet。 如需以腳本為基礎之 Cmdlet 的詳細資訊，請參閱：

- [about_Functions_Advanced](/powershell/module/microsoft.powershell.core/about/about_functions_advanced)
- [about_Functions_CmdletBindingAttribute](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute)
- [about_Functions_Advanced_Methods](/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods)

若要建立二元指令程式，您必須執行一個衍生自兩個特製化 Cmdlet 基類之一的 Cmdlet 類別。 衍生的類別必須：

- 宣告一個屬性，將衍生類別識別為 Cmdlet。
- 定義公用屬性，這些屬性會以將公用屬性識別為 Cmdlet 參數的屬性裝飾。
- 覆寫一或多個輸入處理方法以處理記錄。

您可以使用 [import-module](/powershell/module/microsoft.powershell.core/import-module) Cmdlet 直接載入包含類別的元件，或者您可以使用 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API 建立裝載元件的主應用程式。 這兩種方法都可提供程式設計和命令列存取 Cmdlet 的功能。

## <a name="cmdlet-terms"></a>Cmdlet 條款

PowerShell Cmdlet 檔中經常使用下列詞彙：

### <a name="cmdlet-attribute"></a>Cmdlet 屬性

用來將 Cmdlet 類別宣告為 Cmdlet 的 .NET 屬性。 雖然 PowerShell 會使用其他幾個選擇性屬性，但需要 Cmdlet 屬性。 如需此屬性的詳細資訊，請參閱 [Cmdlet 屬性聲明](cmdlet-attribute-declaration.md)。

### <a name="cmdlet-parameter"></a>Cmdlet 參數

公用屬性，定義可供使用者或執行 Cmdlet 之應用程式使用的參數。 Cmdlet 可以有必要的、命名、位置和 *切換* 參數。 切換參數可讓您定義只有在呼叫中指定參數時，才會評估的參數。 如需不同類型參數的詳細資訊，請參閱 [Cmdlet 參數](cmdlet-parameters.md)。

### <a name="parameter-set"></a>參數集

可在相同命令中用來執行特定動作的一組參數。 Cmdlet 可以有多個參數集，但每個參數集至少必須有一個唯一的參數。 良好的 Cmdlet 設計強烈建議唯一的參數也是必要參數。
如需參數集的詳細資訊，請參閱 [Cmdlet 參數集](cmdlet-parameter-sets.md)。

### <a name="dynamic-parameter"></a>動態參數

在執行時間新增至 Cmdlet 的參數。 當另一個參數設定為特定值時，通常會將動態參數新增至 Cmdlet。 如需動態參數的詳細資訊，請參閱 [Cmdlet 動態參數](cmdlet-dynamic-parameters.md)。

### <a name="input-processing-methods"></a>輸入處理方法

System.servicemodel [類別會](/dotnet/api/System.Management.Automation.Cmdlet) 提供下列用來處理記錄的虛擬方法。 所有衍生的 Cmdlet 類別都必須覆寫前三個方法的一或多個：

- [BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)：用來為 Cmdlet 提供選用的一次性、預先處理的功能性功能。
- [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)：用來為指令程式提供記錄的處理功能，以供 Cmdlet 使用。 視 Cmdlet 的輸入而定， [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法可能會呼叫任意次數，或完全不會被呼叫。
- System.servicemodel：用來為指令程式提供選擇性的一次性、後置處理[功能。](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)
- [StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing)：用來在使用者以非同步方式停止 Cmdlet 時用來停止處理 (例如，按下<kbd>CTRL</kbd> + <kbd>C</kbd>) 。

如需這些方法的詳細資訊，請參閱 [Cmdlet 輸入處理方法](./cmdlet-input-processing-methods.md)。

當您執行 Cmdlet 時，您必須至少覆寫其中一個輸入處理方法。
一般而言， **ProcessRecord ( # B1** 是您覆寫的方法，因為它會針對 Cmdlet 所處理的每一筆記錄呼叫。 相反地， **BeginProcessing ( # B1** 方法和 **EndProcessing ( # B3** 方法會呼叫一次，以執行記錄的前置處理或後置處理。 如需這些方法的詳細資訊，請參閱 [輸入處理方法](cmdlet-input-processing-methods.md)。

### <a name="shouldprocess-feature"></a>ShouldProcess 功能

PowerShell 可讓您建立 Cmdlet，以在 Cmdlet 變更系統之前提示使用者提供意見反應。 若要使用這項功能，當您宣告 Cmdlet 屬性時，此 Cmdlet 必須宣告它支援該 `ShouldProcess` 功能，而此 Cmdlet 必須從輸入處理方法內呼叫 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 和 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法，才能使用此功能。 如需有關如何支援功能的詳細資訊 `ShouldProcess` ，請參閱 [要求確認](requesting-confirmation-from-cmdlets.md)。

### <a name="transaction"></a>交易

視為單一工作的命令邏輯群組。 如果群組中有任何命令失敗，而且使用者可以選擇接受或拒絕在交易內執行的動作，則工作會自動失敗。 若要參與交易，Cmdlet 必須在宣告 Cmdlet 屬性時宣告它支援交易。 Windows PowerShell 2.0 中引進了交易支援。 如需交易的詳細資訊，請參閱 [如何支援交易](how-to-support-transactions.md)。

## <a name="how-cmdlets-differ-from-commands"></a>Cmdlet 與命令有何不同

Cmdlet 與其他命令介面環境中的命令有下列不同之處：

- Cmdlet 是 .NET 類別的實例;它們並不是獨立的可執行檔。
- 您可以從短短幾行程式碼建立 Cmdlet。
- Cmdlet 通常不會進行自己的剖析、錯誤呈現或輸出格式。 PowerShell 執行時間會處理剖析、錯誤呈現和輸出格式。
- Cmdlet 會從管線處理輸入物件，而不是從文字資料流程處理，而 Cmdlet 通常會將物件當作輸出傳遞給管線。
- Cmdlet 是記錄導向的，因為它們會一次處理一個物件。

## <a name="cmdlet-base-classes"></a>Cmdlet 基類

Windows PowerShell 支援衍生自下列兩個基類的 Cmdlet。

- 大部分的 Cmdlet 都是以衍生自 system.string 基類的 .NET 類別[為基礎。](/dotnet/api/System.Management.Automation.Cmdlet)
  衍生自這個類別可讓 Cmdlet 使用 Windows PowerShell 執行時間的最小相依性集合。 這樣有兩個優點。 第一個優點是 Cmdlet 物件較小，而您較不可能受 PowerShell 執行時間的變更影響。 第二個優點是，如果您需要，您可以直接建立 Cmdlet 物件的實例，然後直接叫用它，而不是透過 PowerShell 執行時間叫用它。

- 更複雜的 Cmdlet 是以衍生自 [PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 基類的 .net 類別為基礎。 衍生自這個類別可讓您更容易存取 PowerShell 執行時間。 這種存取權可讓您的 Cmdlet 呼叫腳本、存取提供者，以及存取目前的會話狀態。
   (存取目前的會話狀態時，您會取得並設定會話變數和喜好設定。 ) 不過，從此類別衍生的會增加 Cmdlet 物件的大小，這表示您的 Cmdlet 會更緊密地與目前的 PowerShell 執行時間版本結合。

一般情況下，除非您需要對 PowerShell 執行時間進行延伸存取，否則您應該從 [system.object](/dotnet/api/System.Management.Automation.Cmdlet) 類別衍生。
不過，PowerShell 執行時間有大量的記錄功能可執行 Cmdlet。 如果您的審核模型相依于此記錄，您可以從 [PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 類別衍生，以防止在另一個 Cmdlet 內執行您的 Cmdlet。

## <a name="cmdlet-attributes"></a>Cmdlet 屬性

PowerShell 定義數個用來管理 Cmdlet 的 .NET 屬性，並指定 PowerShell 提供的一般功能，以及指令程式可能需要的功能。 例如，屬性是用來將類別指定為 Cmdlet、指定 Cmdlet 的參數，以及要求驗證輸入，讓 Cmdlet 開發人員不需要在其 Cmdlet 程式碼中執行該功能。 如需屬性的詳細資訊，請參閱 [PowerShell 屬性](./cmdlet-attributes.md)。

## <a name="cmdlet-names"></a>Cmdlet 名稱

PowerShell 會使用動詞和名詞名稱組來命名 Cmdlet。 例如， `Get-Command` PowerShell 中包含的 Cmdlet 是用來取得命令 shell 中註冊的所有 Cmdlet。 指令動詞會識別 Cmdlet 執行的動作，而名詞會識別 Cmdlet 執行其動作的資源。

當 .NET 類別宣告為 Cmdlet 時，會指定這些名稱。 如需如何將 .NET 類別宣告為 Cmdlet 的詳細資訊，請參閱 [Cmdlet 屬性聲明](./cmdlet-class-declaration.md)。

## <a name="writing-cmdlet-code"></a>撰寫 Cmdlet 程式碼

本檔提供兩種方式來探索如何撰寫 Cmdlet 程式碼。 如果您想要查看程式碼，而不需要進行太多說明，請參閱 [Cmdlet 程式碼範例](./examples-of-cmdlet-code.md)。 如果您想要更多有關程式碼的說明，請參閱 [GetProc 教學](./getproc-tutorial.md)課程、 [StopProc 教學](./stopproc-tutorial.md)課程或 [SelectStr 教學](./selectstr-tutorial.md) 課程主題。

如需撰寫 Cmdlet 之指導方針的詳細資訊，請參閱 [Cmdlet 開發指導方針](./cmdlet-development-guidelines.md)。

## <a name="see-also"></a>另請參閱

[PowerShell Cmdlet 概念](./windows-powershell-cmdlet-concepts.md)

[撰寫 PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[PowerShell SDK](../windows-powershell-reference.md)
