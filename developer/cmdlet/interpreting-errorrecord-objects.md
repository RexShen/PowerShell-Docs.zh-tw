---
title: 解譯 ErrorRecord 物件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: 32ebf2531237bfd1042310ccc4155193a58401fd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058771"
---
# <a name="interpreting-errorrecord-objects"></a>解譯 ErrorRecord 物件

在大部分情況下， [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件都代表所用的命令或指令碼產生非終止錯誤。 終止錯誤也可以指定的其他資訊中透過 ErrorRecord [System.Management.Automation.Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord)介面。

如果您想要撰寫的指令碼或主應用程式能夠處理特定的錯誤，您必須解譯命令或指令碼執行期間所發生的錯誤處理常式[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件來判定是否它表示您想要處理的錯誤類別。

當 cmdlet 發生終止或非終止錯誤，它應該建立描述錯誤狀況的錯誤記錄。 主應用程式必須調查這些錯誤記錄，並執行任何動作將會減少錯誤。 主應用程式也必須調查錯誤記錄的非終止錯誤，無法處理記錄，但能夠繼續，以及它必須調查錯誤造成管線，以停止的終止錯誤的記錄。

> [!NOTE]
> 終止錯誤，此 cmdlet 會呼叫[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法。 對於非終止錯誤，此 cmdlet 會呼叫[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法。

## <a name="error-record-design"></a>錯誤記錄設計

錯誤記錄被設計來提供額外的錯誤資訊，同時確保每個錯誤記錄中結合的資訊唯一不提供例外狀況。 這個唯一性可讓主應用程式，讓它可以識別錯誤狀況，並必須採取動作的主機，請檢查錯誤記錄的不同部分。

## <a name="interpreting-error-records"></a>解譯錯誤記錄

您可以檢閱錯誤記錄以識別錯誤的幾個部分。 這些組件包括下列各項：

- 錯誤類別目錄

- 錯誤例外狀況

- 完整的錯誤識別項 (FQID)

- 其他資訊

### <a name="the-error-category"></a>錯誤類別目錄

Error 記錄的錯誤類別是其中一個所提供的預先定義常數[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)列舉型別。 這項資訊是透過[System.Management.Automation.ErrorRecord.CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo)屬性[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件。

CloseError、 OpenError、 InvalidType、 ReadError 和 WriteError 類別目錄，以及其他錯誤類別目錄，可以指定此 cmdlet。 主應用程式可以使用的錯誤類別，來擷取錯誤群組。

### <a name="the-exception"></a>例外狀況

包含錯誤記錄中的例外狀況由指令程式提供，並可以透過存取[System.Management.Automation.ErrorRecord.Exception*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception)屬性[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件。

主機應用程式可以使用`is`關鍵字來辨識例外狀況是特定類別或衍生的類別。 最好是到分支上的例外狀況類型，如下列範例所示。

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

如此一來，您攔截衍生的類別。 不過，有問題如果還原序列化例外狀況。

### <a name="the-fqid"></a>FQID

FQID 是可用來識別錯誤的最特定資訊。 它是包含的 cmdlet 定義識別項、 在 cmdlet 類別中，並回報錯誤的來源名稱的字串。 一般情況下，錯誤記錄相當於在 Windows 事件記錄檔的事件記錄。 FQID 相當於下列的元組，用來識別該事件記錄的類別: (*記錄檔名稱*，*來源*，*事件識別碼*)。

FQID 被設計來進行檢查以單一字串。 不過，情況下存在所在的錯誤識別碼是主應用程式來剖析。 下列範例是語式正確的完整限定的錯誤識別碼。

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

在上述範例中，第一個語彙基元會是錯誤識別碼，接著會在 cmdlet 類別的名稱。 錯誤識別碼可以是單一語彙基元，或允許分支上的識別項的檢查點分隔的識別碼。 請勿使用空格或標點符號錯誤識別項中。 請務必特別是使用逗號;Windows PowerShell 使用逗號來分隔識別碼和 cmdlet 類別名稱。

### <a name="other-information"></a>其他資訊

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件可能也會提供描述發生錯誤的環境的資訊。 這項資訊包括錯誤詳細資料，引動過程的詳細資訊，並發生錯誤時正在處理的目標物件等項目。 雖然這項資訊可能很有用，主應用程式，它是不通常用來識別錯誤。 這項資訊是可透過下列屬性：

[System.Management.Automation.ErrorRecord.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System.Management.Automation.ErrorRecord.InvocationInfo](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System.Management.Automation.ErrorRecord.TargetObject](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>另請參閱

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[新增非終止錯誤報告到您的 Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell 的錯誤報告](./error-reporting-concepts.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
