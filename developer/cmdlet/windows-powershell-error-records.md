---
title: Windows PowerShell 錯誤會記錄 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error category [PowerShell SDK]
- error identifier [PowerShell SDK]
- error records [PowerShell SDK]
- error category string [PowerShell SDK]
ms.assetid: bdd66fea-eb63-4bb6-9cbe-9a799e5e0db5
caps.latest.revision: 9
ms.openlocfilehash: f6f5e50c55b477cbbeeaaf4f3ea665d5dc07758c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067037"
---
# <a name="windows-powershell-error-records"></a>Windows PowerShell 錯誤記錄

指令程式必須通過[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)可識別終止和非終止錯誤的錯誤條件物件。

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件包含下列資訊：

- 描述錯誤的例外狀況。 通常，這是此 cmdlet 會攔截到並轉換成錯誤記錄的例外狀況。 每個錯誤記錄必須包含例外狀況。

如果此 cmdlet 未攔截例外狀況，它必須建立新的例外狀況，並選擇最符合錯誤狀況的例外狀況類別。 不過，您不需要擲回例外狀況，因為它可以透過存取[System.Management.Automation.ErrorRecord.Exception](/dotnet/api/System.Management.Automation.ErrorRecord.Exception)屬性[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件。

- 提供可用來進行診斷及 Windows PowerShell 指令碼以處理特定錯誤條件，以特定的錯誤處理常式的目標指示項的錯誤識別碼。 每個錯誤記錄必須包含錯誤識別項 （請參閱錯誤識別項）。

- 提供可用於診斷用途的一般指示項的錯誤分類。 每個錯誤記錄必須指定的錯誤分類 （請參閱錯誤類別目錄）。

- 選擇性取代錯誤訊息和建議的動作 （請參閱補充錯誤訊息）。

- 選擇性的引動過程會擲回錯誤 cmdlet 資訊。 這項資訊由 Windows PowerShell （請參閱叫用訊息）。

- 發生錯誤時正在處理的目標物件。 這可能是輸入的物件，或可能是您的 cmdlet 所處理的另一個物件。 例如，對於命令`remove-item -recurse c:\somedirectory`，錯誤可能是"c:\somedirectory\lockedfile 」 的 FileInfo 物件的執行個體。 目標物件的資訊是選擇性的。

## <a name="error-identifier"></a>錯誤識別碼

當您建立錯誤記錄時，指定識別項，指定您 cmdlet 中的錯誤狀況。 Windows PowerShell 會將目標的識別碼結合您 cmdlet 來建立完整的錯誤識別項的名稱。 您可以透過完整的錯誤識別碼[System.Management.Automation.ErrorRecord.FullyQualifiedErrorId](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId)屬性[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件。 錯誤識別碼不是使用本身中。 它位於只為一部分的完整格式的錯誤識別碼。

使用下列指導方針，當您建立錯誤記錄時產生錯誤識別碼：

- 對錯誤狀況特定錯誤的識別碼。 進行診斷，並處理以特定的錯誤處理常式的特定錯誤狀況的指令碼為目標的錯誤識別碼。 使用者應該能夠使用錯誤識別碼，以找出錯誤和其來源。 錯誤識別碼也會啟用，因此不需要新的例外狀況子類別，從現有的例外狀況的特定錯誤狀況的報告。

- 一般情況下，將不同的錯誤識別碼指派給不同的程式碼路徑中。 而使用者也會從特定的識別項。 通常，每個呼叫的程式碼路徑[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或是[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)有它自己的識別碼。 因此，請定義新的識別碼，當您定義新的範本字串，如錯誤訊息，反之亦然。 請勿使用做為識別項的錯誤訊息。

- 當您發行程式碼使用特定的錯誤識別碼時，您建立的語意錯誤與該識別項，為您完成的產品支援生命週期。 不重複使用它在語意不同於原始內容的內容中。 如果此錯誤的語意變更，請建立，然後使用 新的識別碼。

- 您通常應該使用特定的錯誤識別碼，只針對特定的 CLR 類型的例外狀況。 如果例外狀況類型或目標物件的類型變更時，建立，然後使用 新的識別碼。

- 選擇您的錯誤識別碼精確對應至您所回報的錯誤文字。 使用標準的.NET Framework 名稱和大小寫慣例。 請勿使用空格或標點符號。 未當地語系化識別碼時發生錯誤。

- 不要以動態方式產生錯誤識別碼無法重現的方式。 比方說，不會包含錯誤的資訊，例如處理序識別碼。 錯誤識別碼是由遇到相同的錯誤狀況的其他使用者看到的錯誤識別碼與對應時，才適用。

## <a name="error-category"></a>錯誤類別目錄

當您建立錯誤記錄時，指定使用其中一個常數所定義的錯誤類別目錄[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)列舉型別。 Windows PowerShell 使用的錯誤類別來顯示資訊時發生錯誤，當使用者設定`$ErrorView`變數設為`"CategoryView"`。

請避免使用[System.Management.Automation.Errorcategory.Notspecified](/dotnet/api/System.Management.Automation.ErrorCategory.NotSpecified)常數。 如果您有任何資訊或造成錯誤的作業相關的錯誤，選擇最能描述錯誤或作業類別目錄，即使此分類不是個完美組合。

Windows PowerShell 所顯示的資訊稱為 「 類別目錄檢視的字串，並建置屬性的[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)類別。 (這個類別經由錯誤[System.Management.Automation.ErrorRecord.CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo)屬性。)

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

下列清單描述所顯示的資訊：

- 類別：Windows PowerShell 定義[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)常數。

- TargetName:依預設，物件的名稱 cmdlet 已處理時，發生錯誤。 或者，另一個 cmdlet 定義的字串。

- TargetType:根據預設，目標物件的型別。 或者，另一個 cmdlet 定義的字串。

- 活動：根據預設，建立錯誤記錄 cmdlet 的名稱。 或某些其他 cmdlet 定義的字串。

- 原因：根據預設，例外狀況類型。 或者，另一個 cmdlet 定義的字串。

## <a name="replacement-error-message"></a>取代錯誤訊息

當您開發 cmdlet 的錯誤記錄時，預設的錯誤訊息的錯誤是來自中的預設訊息文字[System.Exception.Message](/dotnet/api/System.Exception.Message)屬性。 這是唯讀屬性，其訊息文字僅供偵錯之用 （根據.NET Framework 的指導方針）。 我們建議您建立錯誤訊息來取代或增強了預設訊息文字。 讓使用者更容易使用且更特定訊息給 cmdlet。

取代訊息由提供[System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)物件。 因為它們提供可供 Windows PowerShell 的其他當地語系化資訊，請使用此物件的下列建構函式的其中一個選項。

- [ErrorDetails.ErrorDetails (Cmdlet、 字串、 字串、 物件\[System.Management.Automation.ErrorDetails.%23Ctor%28System.Management.Automation.Cmdlet%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29 嗎？Displayproperty = Fullname>](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Management.Automation.Cmdlet%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29):使用這個建構函式，如果您範本字串的 cmdlet 採用相同的組件中的資源字串，或如果您想要載入的覆寫透過範本字串[System.Management.Automation.Cmdlet.GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString)方法。

- [ErrorDetails.ErrorDetails (組件、 字串、 字串、 物件\[System.Management.Automation.ErrorDetails.%23Ctor%28System.Reflection.Assembly%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29 嗎？Displayproperty = Fullname>](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Reflection.Assembly%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29):如果範本字串在另一個組件中，且您不會載入它的覆寫透過使用這個建構函式[System.Management.Automation.Cmdlet.GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString)。

取代訊息應該符合.NET Framework 設計方針，以寫入有些許不同的例外狀況訊息。 應該將例外狀況訊息寫入為開發人員指導方針狀態。 這些取代應該將訊息寫入指令程式使用者。

必須新增取代錯誤訊息，才能[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或是[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法受到呼叫。 若要新增的取代訊息，請設定[System.Management.Automation.ErrorRecord.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)錯誤記錄的屬性。 當設定這個屬性時，Windows PowerShell 會顯示[System.Management.Automation.ErrorDetails.Message*](/dotnet/api/System.Management.Automation.ErrorDetails.Message)屬性而不是預設訊息文字。

## <a name="recommended-action-information"></a>建議的動作資訊

[System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)物件也可以提供資訊就會發生錯誤時，建議的動作。

## <a name="invocation-information"></a>引動過程的資訊

當 cmdlet 時，使用[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或是[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)回報的錯誤記錄，Windows PowerShell會自動加入描述發生錯誤時叫用命令的資訊。 這項資訊由[System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)物件，其中包含已叫用命令，命令本身，此 cmdlet 的名稱以及管線或指令碼的相關資訊。 這個屬性是唯讀的。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Windows PowerShell 的錯誤報告](./error-reporting-concepts.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
