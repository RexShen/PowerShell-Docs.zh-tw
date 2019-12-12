---
title: 諮詢開發指導方針 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 980b488800587e31286e2ca2ece924e07f8af3f3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72370037"
---
# <a name="advisory-development-guidelines"></a>建議性開發指導方針

本節說明您應考慮的指導方針，以確保良好的開發和使用者體驗。 有時候可能會套用，有時可能不會套用。

## <a name="design-guidelines"></a>設計指導方針

設計 Cmdlet 時，應該考慮下列指導方針。 當您找到適用于您情況的設計指導方針時，請務必查看類似方針的程式碼方針。

### <a name="support-an-inputobject-parameter-ad01"></a>支援 InputObject 參數（AD01）

由於 Windows PowerShell 會直接與 Microsoft .NET Framework 物件搭配運作，因此通常會提供 .NET Framework 物件，完全符合使用者執行特定作業所需的類型。 `InputObject` 是接受這類物件做為輸入之參數的標準名稱。 例如， [StopProc 教學](./stopproc-tutorial.md)課程中的範例**停止程式**Cmdlet 會定義支援管線輸入之 Process 類型的 `InputObject` 參數。 使用者可以取得一組處理常式物件，操控它們以選取要停止的確切物件，然後直接將它們傳遞給**停止程式**Cmdlet。

### <a name="support-the-force-parameter-ad02"></a>支援 Force 參數（AD02）

有時候，Cmdlet 必須保護使用者，使其無法執行要求的操作。 這類 Cmdlet 應該支援 `Force` 參數，以允許使用者在有權執行作業時覆寫該保護。

例如，[移除專案](/powershell/module/microsoft.powershell.management/remove-item)Cmdlet 通常不會移除唯讀檔案。 不過，此 Cmdlet 支援 `Force` 參數，讓使用者可以強制移除唯讀檔案。 如果使用者已經有修改唯讀屬性的許可權，而且使用者移除該檔案，使用 `Force` 參數可簡化作業。 不過，如果使用者沒有移除檔案的許可權，`Force` 參數就不會有任何作用。

### <a name="handle-credentials-through-windows-powershell-ad03"></a>透過 Windows PowerShell 處理認證（AD03）

Cmdlet 應定義 `Credential` 參數來代表認證。 這個參數的類型必須是[system.web](/dotnet/api/System.Management.Automation.PSCredential) ，而且必須使用 Credential 屬性宣告來定義。 當未直接提供完整認證時，這項支援會自動提示使用者輸入使用者名稱、密碼或兩者。 如需認證屬性的詳細資訊，請參閱[Credential 屬性](./credential-attribute-declaration.md)宣告。

### <a name="support-encoding-parameters-ad04"></a>支援編碼參數（AD04）

如果您的 Cmdlet 會讀取或寫入二進位格式的文字（例如寫入或讀取檔案系統中的檔案），則您的 Cmdlet 必須具有編碼參數，以指定二進位格式的文字編碼方式。

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>測試 Cmdlet 應傳回布林值（AD05）

對其資源執行測試的 Cmdlet 應該[會將 system.string 類型傳回](/dotnet/api/System.Boolean)給管線，以便在條件運算式中使用。

## <a name="code-guidelines"></a>程式碼方針

撰寫 Cmdlet 程式碼時，應考慮下列指導方針。 當您找到適用于您情況的指導方針時，請務必查看類似指導方針的設計方針。

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>遵循 Cmdlet 類別命名慣例（AC01）

藉由遵循標準命名慣例，您可以讓 Cmdlet 更容易找到，並協助使用者瞭解 Cmdlet 的作用。 這種作法對於使用 Windows PowerShell 的其他開發人員而言特別重要，因為 Cmdlet 是公用類型。

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>在正確的命名空間中定義 Cmdlet

您通常會在附加 "的 .NET Framework 命名空間中，定義 Cmdlet 的類別。命令，代表 Cmdlet 執行所在產品的命名空間。 例如，Windows PowerShell 隨附的 Cmdlet 會定義在 `Microsoft.PowerShell.Commands` 命名空間中。

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>將 Cmdlet 類別命名為符合 Cmdlet 名稱

當您命名執行 Cmdlet 的 .NET Framework 類別時，請將類別命名為「 *\<動詞 > **\<名詞 >** \<命令 >* 」，您可以在其中使用用於 Cmdlet 名稱的動詞和名詞來取代 *\<動詞*> 和 *\<名詞 >* 預留位置。 例如， [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet 是由稱為 `GetProcessCommand`的類別所實。

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>如果沒有管線輸入覆寫 BeginProcessing 方法（AC02）

如果您的 Cmdlet 不接受來自管線的輸入，則應該在[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法中執行處理。 使用此方法可讓 Windows PowerShell 維護 Cmdlet 之間的順序。 管線中的第一個 Cmdlet 一律會傳回其物件，然後管線中的其餘 Cmdlet 就有機會開始處理。

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>若要處理停止要求，請覆寫 StopProcessing 方法（AC03）

覆寫[StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing)方法，讓您的 Cmdlet 可以處理停止信號。 某些 Cmdlet 會花很長的時間來完成其作業，並可讓您在呼叫 Windows PowerShell 執行時間之間進行較長的時間傳遞，例如當 Cmdlet 在長時間執行的 RPC 呼叫中封鎖執行緒時。 這包括對[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法進行呼叫的 Cmdlet、 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法，以及其他可能需要很長時間才能完成的意見反應機制，都包含在這種情況下。 在這些情況下，使用者可能需要傳送停止信號給這些 Cmdlet。

### <a name="implement-the-idisposable-interface-ac04"></a>執行 IDisposable 介面（AC04）

如果您的 Cmdlet 具有不會由[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法處置（寫入管線）的物件，您的 Cmdlet 可能需要額外的物件處置。 例如，如果您的 Cmdlet 會在[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法中開啟檔案控制代碼，並讓控制碼保持開啟以供[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法使用，則必須在處理結束時關閉此控制碼（handle）。

Windows PowerShell 執行時間並不一定會呼叫[system.servicemodel 方法。](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 例如，如果 Cmdlet 在其作業中途取消，或在 Cmdlet 的任何部分發生終止錯誤，則可能不會呼叫[system.servicemodel 方法。](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 因此，需要物件清除之 Cmdlet 的 .NET Framework 類別應該會執行完整的[IDisposable](/dotnet/api/System.IDisposable)介面模式，包括完成項，讓 Windows PowerShell 執行時間可以在處理結束時同時呼叫 System.web 和[IDisposable](/dotnet/api/System.IDisposable.Dispose)方法，以進行[管理](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)。

### <a name="use-serialization-friendly-parameter-types-ac05"></a>使用序列化易懂的參數類型（AC05）

若要支援在遠端電腦上執行 Cmdlet，請使用可在用戶端電腦上輕鬆序列化，然後在伺服器電腦上解除凍結的類型。 下列類型可供序列化。

基本類型：

- Byte、SByte、Decimal、Single、Double、Int16、Int32、Int64、Uint16、UInt32 和 UInt64。

- 布林值、Guid、位元組 []、TimeSpan、DateTime、Uri 和版本。

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

- 容器（上述類型的清單和字典）

### <a name="use-securestring-for-sensitive-data-ac06"></a>針對機密資料使用 SecureString （AC06）

處理敏感性資料時，請一律使用[Securestring](/dotnet/api/System.Security.SecureString)資料類型。 這可能包括參數的管線輸入，以及將機密資料傳回至管線。

## <a name="see-also"></a>另請參閱

[必要的開發指導方針](./required-development-guidelines.md)

[強烈建議的開發指導方針](./strongly-encouraged-development-guidelines.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
