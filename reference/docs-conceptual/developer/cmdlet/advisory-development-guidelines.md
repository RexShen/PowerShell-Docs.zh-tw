---
ms.date: 09/13/2016
ms.topic: reference
title: 建議性開發指導方針
description: 建議性開發指導方針
ms.openlocfilehash: 1ac18925bbc2506e6a03810d24f58c2f3113fd55
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668315"
---
# <a name="advisory-development-guidelines"></a>建議性開發指導方針

本節說明您應考慮的指導方針，以確保良好的開發和使用者體驗。 有時可能會套用，有時可能不會套用。

## <a name="design-guidelines"></a>設計方針

設計 Cmdlet 時，應考慮下列指導方針。 當您找到適用于您情況的設計指導方針時，請務必查看類似指導方針的程式碼指導方針。

### <a name="support-an-inputobject-parameter-ad01"></a> (AD01 支援 InputObject 參數) 

因為 Windows PowerShell 直接與 Microsoft .NET Framework 物件搭配運作，所以 .NET Framework 物件通常會完全符合使用者執行特定作業所需的型別。 `InputObject` 這是接受這類物件做為輸入之參數的標準名稱。 例如， [StopProc 教學](./stopproc-tutorial.md)課程中的範例 **Stop-Proc** Cmdlet `InputObject` 會定義型別流程的參數，以支援來自管線的輸入。 使用者可以取得一組處理常式物件、操控它們來選取要停止的確切物件，然後直接將它們傳遞給 **停止進程** Cmdlet。

### <a name="support-the-force-parameter-ad02"></a>支援 (AD02) 的 Force 參數

有時候，Cmdlet 需要保護使用者執行要求的操作。 `Force`如果使用者有權執行作業，這類 Cmdlet 應該支援參數，以允許使用者覆寫該保護。

例如，「 [移除專案](/powershell/module/microsoft.powershell.management/remove-item) 」 Cmdlet 通常不會移除唯讀檔案。 不過，這個 Cmdlet 支援 `Force` 參數，讓使用者可以強制移除唯讀檔案。 如果使用者已有修改唯讀屬性的許可權，而且使用者移除該檔案，則使用 `Force` 參數可簡化作業。 不過，如果使用者沒有移除檔案的許可權，則參數不會 `Force` 有任何作用。

### <a name="handle-credentials-through-windows-powershell-ad03"></a>透過 Windows PowerShell (AD03 處理認證) 

Cmdlet 應定義 `Credential` 代表認證的參數。 這個參數必須是 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 類型，而且必須使用 Credential 屬性宣告來定義。 這項支援會自動提示使用者輸入使用者名稱、密碼，或在未直接提供完整認證時提示使用者輸入密碼。 如需 Credential 屬性的詳細資訊，請參閱 [Credential attribute](./credential-attribute-declaration.md)宣告。

### <a name="support-encoding-parameters-ad04"></a>支援 (AD04) 的編碼參數

如果您的 Cmdlet 會從二進位格式讀取或寫入文字（例如寫入或讀取檔案系統中的檔案），則您的 Cmdlet 必須有編碼參數，以指定如何以二進位格式來編碼文字。

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>測試 Cmdlet 應傳回布林值 (AD05) 

針對其資源執行測試的 Cmdlet 應該會將 [system.string 型別](/dotnet/api/System.Boolean) 傳回給管線，以便在條件運算式中使用。

## <a name="code-guidelines"></a>程式碼指導方針

撰寫 Cmdlet 程式碼時，應考慮下列指導方針。 當您找到適用于您情況的指導方針時，請務必查看類似指導方針的設計指導方針。

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>遵循 Cmdlet 類別的命名慣例 (AC01) 

遵循標準命名慣例，讓您的 Cmdlet 更容易探索，並協助使用者瞭解 Cmdlet 的功能。 對於使用 Windows PowerShell 的其他開發人員而言，這種做法特別重要，因為 Cmdlet 是公用類型。

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>在正確的命名空間中定義 Cmdlet

您通常會在附加 "的 .NET Framework 命名空間中定義 Cmdlet 的類別。命令」表示 Cmdlet 執行所在之產品的命名空間。 例如，包含在 Windows PowerShell 中的 Cmdlet 會在 `Microsoft.PowerShell.Commands` 命名空間中定義。

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>將 Cmdlet 類別命名為符合 Cmdlet 名稱

當您將執行 Cmdlet 的 .NET Framework 類別命名時，請將類別命名為 " *\<Verb>**\<Noun>**\<Command>* "，您可以在此將 *\<Verb>* 和預留位置取代為 *\<Noun>* Cmdlet 名稱所使用的動詞和名詞。 例如， [取得進程](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 指令程式是由稱為的類別所執行 `GetProcessCommand` 。

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>如果沒有管線輸入覆寫 BeginProcessing 方法 (AC02) 

如果您的 Cmdlet 不接受來自管線的輸入，則應該在 [BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 方法中執行處理。 使用這個方法可讓 Windows PowerShell 維護 Cmdlet 之間的順序。 管線中的第一個 Cmdlet 一律會傳回其物件，管線中的其餘 Cmdlet 才有機會開始其處理。

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>若要處理停止要求， (AC03 覆寫 StopProcessing 方法) 

覆寫 [StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) 方法，讓您的 Cmdlet 可以處理停止信號。 某些 Cmdlet 需要很長的時間來完成其作業，而且它們可讓您在呼叫 Windows PowerShell 執行時間之間傳遞較長的時間，例如當 Cmdlet 在長時間執行的 RPC 呼叫中封鎖執行緒時。 這包括對 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 方法的呼叫，以及對 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 方法的呼叫，以及其他可能需要很長時間才能完成的意見反應機制的指令程式（Cmdlet）。 在這些情況下，使用者可能需要將停止信號傳送給這些 Cmdlet。

### <a name="implement-the-idisposable-interface-ac04"></a> (AC04) 執行 IDisposable 介面

如果您的 Cmdlet 具有未處置 (寫入 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法所) 之管線的物件，則您的 Cmdlet 可能需要額外的物件處置。 例如，如果您的 Cmdlet 會在 [BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 方法中開啟檔案控制代碼，並讓控制碼保持開啟，以供 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法使用，則必須在處理結束時關閉此控制碼。

Windows PowerShell 執行時間不一定會呼叫 system.string  [. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 方法。 例如，如果 Cmdlet 是在其作業中途取消，或 Cmdlet 的任何部分發生終止錯誤，則可能不會呼叫[system.string 方法。](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 因此，需要物件清除之 Cmdlet 的 .NET Framework 類別應該會執行完整的[IDisposable](/dotnet/api/System.IDisposable)介面模式（包括完成項），讓 Windows PowerShell 執行時間可以在處理結束時呼叫[IDisposable](/dotnet/api/System.IDisposable.Dispose)的介面和.. a [m.](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

### <a name="use-serialization-friendly-parameter-types-ac05"></a>使用 (AC05) 的序列化易記參數類型

若要支援在遠端電腦上執行 Cmdlet，請使用可在用戶端電腦上輕鬆序列化的類型，然後在伺服器電腦上解除凍結。 以下是可序列化的類型。

基本類型：

- Byte、SByte、Decimal、Single、Double、Int16、Int32、Int64、Uint16、UInt32 和 UInt64。

- Boolean、Guid、Byte []、TimeSpan、DateTime、Uri 和 Version。

- Char、String、Xml。

內建的 rehydratable 類型：

- PSPrimitiveDictionary

- SwitchParameter

- PSListModifier

- PSCredential

- IPAddress、MailAddress

- CultureInfo

- X509Certificate2、System.security.cryptography.x509certificates.x500distinguishedname

- System.security.accesscontrol.directorysecurity、System.security.accesscontrol.filesecurity、RegistrySecurity

其他類型：

- SecureString

- 容器 (上述類型的清單和字典) 

### <a name="use-securestring-for-sensitive-data-ac06"></a>將 SecureString 用於敏感性資料 (AC06) 

處理敏感性資料時，一律使用 [Securestring](/dotnet/api/System.Security.SecureString) 資料類型。 這可能包含參數的管線輸入，以及將機密資料傳回至管線。

## <a name="see-also"></a>另請參閱

[必要的開發指導方針](./required-development-guidelines.md)

[強烈建議使用的開發指導方針](./strongly-encouraged-development-guidelines.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
