---
title: Windows PowerShell 錯誤記錄 |Microsoft Docs
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
ms.openlocfilehash: 5412d88b690a1f5f1ef387416e3bf9da3a32c95d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369107"
---
# <a name="windows-powershell-error-records"></a>Windows PowerShell 錯誤記錄

Cmdlet 必須傳遞[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件，以識別終止和非終止錯誤的錯誤狀況。

[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件會包含下列資訊：

- 描述錯誤的例外狀況。 通常，這是 Cmdlet 攔截並轉換成錯誤記錄的例外狀況。 每個錯誤記錄都必須包含例外狀況。

如果 Cmdlet 未攔截到例外狀況，則必須建立新的例外狀況，並選擇最能描述錯誤情況的例外狀況類別。 不過，您不需要擲回例外狀況，因為它可以透過[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件的[ErrorRecord. exception](/dotnet/api/System.Management.Automation.ErrorRecord.Exception)屬性來加以存取的。

- 提供目標指示項的錯誤識別碼，可用於診斷目的和 Windows PowerShell 腳本，以處理特定錯誤處理常式的特定錯誤狀況。 每個錯誤記錄都必須包含錯誤識別碼（請參閱錯誤識別碼）。

- 提供一般指示項的錯誤分類，可用於診斷目的。 每個錯誤記錄都必須指定錯誤類別（請參閱錯誤類別）。

- 選擇性的取代錯誤訊息和建議的動作（請參閱取代錯誤訊息）。

- 擲回錯誤之 Cmdlet 的選擇性調用資訊。 這項資訊是由 Windows PowerShell 所指定（請參閱調用訊息）。

- 發生錯誤時正在處理的目標物件。 這可能是輸入物件，也可能是您的 Cmdlet 正在處理的另一個物件。 例如，針對命令 `remove-item -recurse c:\somedirectory`，此錯誤可能是 "c:\somedirectory\lockedfile" 的 FileInfo 物件實例。 目標物件資訊是選擇性的。

## <a name="error-identifier"></a>錯誤識別碼

當您建立錯誤記錄時，請指定識別碼，以在您的 Cmdlet 中指定錯誤狀況。 Windows PowerShell 會將目標識別碼與您的 Cmdlet 名稱結合，以建立完整的錯誤識別碼。 您可以透過[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件的[ErrorRecord. FullyQualifiedErrorId](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId)屬性來存取完整的錯誤識別碼（error identifier）。 錯誤識別碼本身無法使用。 它僅適用于完整錯誤識別碼的一部分。

當您建立錯誤記錄時，請使用下列指導方針來產生錯誤識別碼：

- 將錯誤識別碼特定于錯誤狀況。 針對診斷用途，以及處理具有特定錯誤處理常式之特定錯誤狀況的腳本，鎖定錯誤識別碼。 使用者應該能夠使用錯誤識別碼來識別錯誤及其來源。 錯誤識別碼也會從現有的例外狀況中針對特定的錯誤情況啟用報告，因此不需要新的例外子類別。

- 一般來說，請將不同的錯誤識別碼指派給不同的程式碼路徑。 使用者會受益于特定識別碼。 通常，每個呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或[Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)的程式碼路徑都有它自己的識別碼（identifier）。 作為規則，當您為錯誤訊息定義新的範本字串時，請定義新的識別碼，反之亦然。 請勿使用錯誤訊息做為識別碼。

- 當您使用特定的錯誤識別碼發行程式碼時，您可以使用該識別碼來建立錯誤的語義，以提供完整的產品支援週期。 請勿在語義上與原始內容不同的內容中重複使用它。 如果此錯誤的語義變更，請建立，然後使用新的識別碼。

- 一般來說，您應該只針對特定 CLR 類型的例外狀況使用特定的錯誤識別碼。 如果例外狀況的類型或目標物件的類型變更，請建立，然後使用新的識別碼。

- 選擇您的錯誤識別碼文字，以簡明地對應至您所報告的錯誤。 使用標準 .NET Framework 命名和大小寫慣例。 請勿使用空白字元或標點符號。 請勿將錯誤識別碼當地語系化。

- 請勿以不可重現的方式動態產生錯誤識別碼。 例如，請勿併入錯誤資訊，例如處理序識別碼。 只有當錯誤識別碼對應至其他遇到相同錯誤狀況的使用者所看到的錯誤識別碼時，才有用。

## <a name="error-category"></a>錯誤類別

當您建立錯誤記錄時，請使用[ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0)列舉所定義的其中一個常數來指定錯誤的類別。 當使用者將 `$ErrorView` 變數設定為 `"CategoryView"`時，Windows PowerShell 會使用錯誤類別來顯示錯誤資訊。

避免使用[ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) **NotSpecified**常數。 如果您有任何有關錯誤或造成錯誤之作業的資訊，請選擇最能描述錯誤或作業的類別，即使類別不是完全相符。

Windows PowerShell 所顯示的資訊稱為類別目錄檢視字串，並是從[Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)類別的屬性所建立。 （這個類別是透過[ErrorRecord. CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo)屬性來存取）。

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

下列清單說明顯示的資訊：

- Category： Windows PowerShell 定義的[ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0)常數。

- TargetName：根據預設，當發生錯誤時，Cmdlet 正在處理的物件名稱。 或者，另一個 Cmdlet 定義的字串。

- TargetType：根據預設，目標物件的類型。 或者，另一個 Cmdlet 定義的字串。

- 活動：根據預設，建立錯誤記錄的 Cmdlet 名稱。 或者，其他 Cmdlet 定義的字串。

- 原因：根據預設，例外狀況類型。 或者，另一個 Cmdlet 定義的字串。

## <a name="replacement-error-message"></a>取代錯誤訊息

當您開發 Cmdlet 的錯誤記錄時，錯誤的預設錯誤訊息是來自[system.object](/dotnet/api/System.Exception.Message)屬性中的預設郵件內文。 這是唯讀屬性，其郵件內文僅供偵錯工具之用（根據 .NET Framework 方針）。 我們建議您建立一個錯誤訊息，以取代或擴大預設郵件內文。 讓訊息更方便使用者易懂，並更明確地提供給 Cmdlet。

取代訊息是由[ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)物件所提供。 請使用此物件的下列其中一個函式，因為它們會提供可供 Windows PowerShell 使用的其他當地語系化資訊。

- [ErrorDetails （Cmdlet，string，string，Object []）](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Management_Automation_Cmdlet_System_String_System_String_System_Object___)：如果您的範本字串是在執行 Cmdlet 的相同元件中的資源字串，或您想要透過[GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString)方法的覆寫載入範本字串，請使用這個函式。

- [ErrorDetails （Assembly，string，string，Object []）](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Reflection_Assembly_System_String_System_String_System_Object___)：如果範本字串位於另一個元件中，而您未透過[GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString)的覆寫載入它，請使用這個函式。

取代訊息應符合 .NET Framework 的設計指導方針，可讓您以較小的差異來撰寫例外狀況訊息。 指導方針說明應該為開發人員撰寫例外狀況訊息。 應該為 Cmdlet 使用者撰寫這些取代訊息。

您必須在呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或[Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法之前，先新增取代錯誤訊息，然後再加以加入。 若要新增取代訊息，請設定錯誤記錄的[ErrorRecord. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)屬性。 設定此屬性時，Windows PowerShell 會顯示[ErrorDetails *](/dotnet/api/System.Management.Automation.ErrorDetails.Message)屬性，而不是預設郵件內文。

## <a name="recommended-action-information"></a>建議的動作資訊

[ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)物件也可以提供錯誤發生時建議哪些動作的相關資訊。

## <a name="invocation-information"></a>調用資訊

當 Cmdlet 使用[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或[Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)來報告錯誤記錄時，Windows PowerShell 會自動新增資訊，以描述發生錯誤時所叫用的命令，而不會有問題。 這項資訊是由[Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)物件所提供，其中包含命令所叫用的 Cmdlet 名稱、命令本身，以及管線或腳本的相關資訊。 這個屬性是唯讀的。

## <a name="see-also"></a>另請參閱

[WriteError 的管理元件](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Throwterminatingerror * 的 *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[ErrorCategory。](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0)

[Errorcategoryinfo。](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[ErrorRecord。](/dotnet/api/System.Management.Automation.ErrorRecord)

[ErrorDetails。](/dotnet/api/System.Management.Automation.ErrorDetails)

[Invocationinfo。](/dotnet/api/System.Management.Automation.InvocationInfo)

[Windows PowerShell 錯誤報表](./error-reporting-concepts.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
