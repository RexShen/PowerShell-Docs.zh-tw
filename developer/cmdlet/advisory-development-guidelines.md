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
ms.openlocfilehash: 97a2d3587f8f69edc92150474e94a620ff9a2f71
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854544"
---
# <a name="advisory-development-guidelines"></a>建議性開發指導方針

本章節描述您應該考慮以確保良好的開發和使用者體驗的指導方針。 有時它們可能適用，而有時不可能。

## <a name="design-guidelines"></a>設計指導方針

- [支援的 InputObject 參數 (AD01)](./advisory-development-guidelines.md#AD01)

- [Force 參數 （ad02 移） 的支援](./advisory-development-guidelines.md#AD02)

- [處理透過 Windows PowerShell (AD03) 的認證](./advisory-development-guidelines.md#AD03)

- [支援編碼的參數 (AD04)](./advisory-development-guidelines.md#AD04)

- [測試 Cmdlet 應該會傳回布林值 (AD05)](./advisory-development-guidelines.md#AD05)

## <a name="code-guidelines"></a>程式碼的指導方針

- [請依照下列 Cmdlet 類別命名慣例 (AC01)](./advisory-development-guidelines.md#AC01)

- [如果沒有管線輸入覆寫 BeginProcessing 方法 (AC02)](./advisory-development-guidelines.md#AC02)

- [若要處理停止要求覆寫 StopProcessing 方法 (AC03)](./advisory-development-guidelines.md#AC03)

- [實作 IDisposable 介面 (AC04)](./advisory-development-guidelines.md#AC04)

- [使用序列化參數型別 (AC05)](./advisory-development-guidelines.md#AC05)

- [使用 SecureString，機密資料 (AC06)](./advisory-development-guidelines.md#AC06)

## <a name="design-guidelines"></a>設計指導方針

設計 cmdlet 時，就應該考慮下列指導方針。 當您找到適用於您情況的設計指導方針時，請務必查看類似的指導方針中的程式碼的方針。

### <a name="support-an-inputobject-parameter-ad01"></a>支援的 InputObject 參數 (AD01)

Windows PowerShell 會直接使用 Microsoft.NET Framework 物件，因為.NET Framework 物件通常會提供完全符合類型的使用者需要執行特定作業。 `InputObject` 會接受這類物件做為輸入參數的標準名稱。 比方說，此範例**停止程序**中的 cmdlet [StopProc 教學課程](./stopproc-tutorial.md)定義`InputObject`類型支援從管線輸入處理序的參數。 使用者可以取得一組處理程序物件的、 操作這些選取的確切的物件，若要停止，並再將其傳遞給**停止處理序**直接 cmdlet。

### <a name="support-the-force-parameter-ad02"></a>Force 參數 （ad02 移） 的支援

有時候，指令程式必須保護使用者不會執行要求的作業。 這類指令程式應該支援`Force`參數，以允許使用者覆寫該保護，如果使用者具有權限來執行此作業。

例如， [Remove-item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet 通常也不會移除唯讀檔案。 不過，此 cmdlet 支援`Force`參數讓使用者可以強制移除唯讀檔案。 如果使用者已修改的唯讀屬性，權限，而且使用者會移除檔案，使用`Force`參數可簡化此作業。 不過，如果使用者沒有權限可移除檔案，`Force`參數沒有任何作用。

### <a name="handle-credentials-through-windows-powershell-ad03"></a>處理透過 Windows PowerShell (AD03) 的認證

Cmdlet 應該定義`Credential`參數表示的認證。 這個參數必須是型別[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) ，且必須使用的認證屬性宣告中定義。 這項支援未直接提供完整的認證時，會自動提示使用者的使用者名稱、 密碼，或兩者。 如需有關認證屬性的詳細資訊，請參閱[認證屬性宣告](./credential-attribute-declaration.md)。

### <a name="support-encoding-parameters-ad04"></a>支援編碼的參數 (AD04)

如果您的 cmdlet 會讀取或寫入的文字或二進位格式，例如寫入或讀取的檔案中的檔案系統中，從您的 cmdlet 就必須要有 Encoding 參數，指定文字以二進位格式的編碼方式。

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>測試 Cmdlet 應該會傳回布林值 (AD05)

執行測試，針對其資源的指令程式應該會傳回[System.Boolean](/dotnet/api/System.Boolean)類型至管線，以便它們可以用於條件運算式。

## <a name="code-guidelines"></a>程式碼的指導方針

撰寫 cmdlet 程式碼時，應該考慮下列指導方針。 當您找到適用於您情況的指導方針時，請務必查看類似的指導方針的設計方針。

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>請依照下列 Cmdlet 類別命名慣例 (AC01)

根據下列標準的命名慣例，讓您的 cmdlet 更容易被找到，而幫助使用者了解完全指令程式做什麼。 這種做法是使用 Windows PowerShell，因為 cmdlet 是公用類型的其他開發人員特別重要。

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>定義正確的命名空間中的 Cmdlet

您通常會將附加至.NET Framework 命名空間中定義 cmdlet 類別 」。命令"代表的產品 cmdlet 執行所在之命名空間。 比方說，隨附於 Windows PowerShell 的 cmdlet 定義於`Microsoft.PowerShell.Commands`命名空間。

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>名稱比對 Cmdlet 名稱在 Cmdlet 類別

當您命名實作指令程式的.NET Framework 類別時，將類別命名為"*\<動詞 >**\<名詞 >**\<命令 >*」，您用來取代*\<動詞 >* 並*\<名詞 >* 預留位置取代為用於的 cmdlet 名稱的名詞與動詞命令。 例如， [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)指令程式藉由呼叫類別`GetProcessCommand`。

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>如果沒有管線輸入覆寫 BeginProcessing 方法 (AC02)

如果您的 cmdlet 不接受來自管線的輸入，應該在實作處理[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法。 使用這個方法可讓 Windows PowerShell 來維護 cmdlet 之間的順序。 在管線中的其餘 cmdlet 有機會開始其處理之前，管線中的第一個 cmdlet 一律會傳回其物件。

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>若要處理停止要求覆寫 StopProcessing 方法 (AC03)

覆寫[System.Management.Automation.Cmdlet.Stopprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing)方法，使您的 cmdlet 能夠處理停止訊號。 某些 cmdlet 需要一些時間才能完成其作業，並可讓 Windows PowerShell 執行階段，例如當此 cmdlet 會封鎖長時間執行的 RPC 呼叫的執行緒的呼叫之間傳遞很長的時間。 這包括對進行呼叫的 cmdlet [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法，以[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法，以及其他意見反應可能需要很長的時間才能完成的機制。 在這些情況下可能需要使用者將停止訊號傳送至這些 cmdlet。

### <a name="implement-the-idisposable-interface-ac04"></a>實作 IDisposable 介面 (AC04)

如果您的 cmdlet 未處置的物件 （寫入管線） 所[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法中，您的 cmdlet 可能會需要額外的物件可供使用。 例如，如果您的指令程式會開啟檔案控制代碼，以其[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法，並維持控制代碼開啟以供[System.Management.Automation.Cmdlet.Processrecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，這個控制代碼已關閉結尾的處理。

Windows PowerShell 執行階段不會一律呼叫[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。 例如， [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)如果 cmdlet 可透過其作業中途取消或終止錯誤發生在 cmdlet 的任何部分，可能不會呼叫方法。 因此，需要物件清除指令程式的.NET Framework 類別應實作完整[System.Idisposable](/dotnet/api/System.IDisposable)介面模式，包括完成項，可讓 Windows PowerShell 執行階段呼叫兩者[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)並[System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose)結尾的處理方法。

### <a name="use-serialization-friendly-parameter-types-ac05"></a>使用序列化參數型別 (AC05)

若要支援在遠端電腦上執行您的 cmdlet，使用型別，可以輕鬆地序列化用戶端電腦上，並接著解除凍結伺服器電腦上。 下列型別會序列化。

基本類型：

- 位元組、 SByte、 Decimal、 單一、 Double、 Int16、 Int32、 Int64、 Uint16、 UInt32 和 UInt64。

- 布林值、 Guid、 Byte []、 TimeSpan、 DateTime、 Uri 和版本。

- Char、 String，XmlDocument。

內建的 rehydratable 類型：

- PSPrimitiveDictionary

- SwitchParmeter

- PSListModifier

- PSCredential

- Ip 位址 MailAddress

- CultureInfo

- X509Certificate2, X500DistinguishedName

- DirectorySecurity，FileSecurity，RegistrySecurity

其他類型：

- SecureString

- 容器 （list 和 dictionary 的上述類型）

### <a name="use-securestring-for-sensitive-data-ac06"></a>使用 SecureString，機密資料 (AC06)

永遠處理敏感性資料時使用[System.Security.Securestring](/dotnet/api/System.Security.SecureString)資料型別。 這可能包括參數，以及將機密資料傳回至管線的管線輸入。

## <a name="see-also"></a>另請參閱

[所需的開發指導方針](./required-development-guidelines.md)

[極力建議您的開發指導方針](./strongly-encouraged-development-guidelines.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
