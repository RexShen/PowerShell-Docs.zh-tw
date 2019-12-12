---
title: 解讀 ErrorRecord 物件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: 32ebf2531237bfd1042310ccc4155193a58401fd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365417"
---
# <a name="interpreting-errorrecord-objects"></a>解譯 ErrorRecord 物件

在大多數情況下， [ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件代表命令或腳本所產生的非終止錯誤。 終止錯誤也可以透過[Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord)介面，在 ErrorRecord 中指定其他資訊。

如果您想要在腳本或主控制項中寫入錯誤處理常式，以處理命令或腳本執行期間所發生的特定錯誤，您必須解讀[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件，以判斷它是否代表您要處理之錯誤的類別。

當 Cmdlet 遇到終止或非終止錯誤時，應該會建立描述錯誤狀況的錯誤記錄。 主應用程式必須調查這些錯誤記錄，並執行任何動作來減輕錯誤。 主應用程式也必須調查錯誤記錄，找出無法處理記錄但可以繼續的非終止錯誤，而且必須調查錯誤記錄，以找出導致管線停止的終止錯誤。

> [!NOTE]
> 針對終止錯誤，此 Cmdlet 會呼叫[Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法。 若為非終止錯誤，此 Cmdlet 會呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法。

## <a name="error-record-design"></a>錯誤記錄設計

錯誤記錄的設計目的是要提供例外狀況中未提供的其他錯誤資訊，同時確保每個錯誤記錄中的合併資訊都是唯一的。 這項唯一性可讓主應用程式檢查錯誤記錄的不同部分，讓它能夠識別錯誤狀況，以及主機必須採取的動作。

## <a name="interpreting-error-records"></a>解讀錯誤記錄

您可以檢查錯誤記錄的幾個部分，以找出錯誤。 這些元件包括下列各項：

- 錯誤分類

- 錯誤例外狀況

- 完整的錯誤識別碼（FQID）

- 其他資訊

### <a name="the-error-category"></a>錯誤分類

錯誤記錄的錯誤類別是[Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)列舉所提供的其中一個預先定義常數。 這項資訊可透過[ErrorRecord.](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) [ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件的 CategoryInfo 屬性來取得，而提供。

此 Cmdlet 可以指定 CloseError、OpenError、InvalidType、ReadError 和 WriteError 類別目錄，以及其他錯誤分類。 主應用程式可以使用錯誤類別來捕捉錯誤群組。

### <a name="the-exception"></a>例外狀況

錯誤記錄中包含的例外狀況是由指令程式所提供，而且可以透過[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件的[ErrorRecord. exception *](/dotnet/api/System.Management.Automation.ErrorRecord.Exception)屬性來存取。

主應用程式可以使用 `is` 關鍵字來識別例外狀況屬於特定類別或衍生類別。 較好的方式是在例外狀況類型上分支，如下列範例所示。

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

如此一來，您就可以攔截衍生的類別。 不過，如果已還原序列化例外狀況，就會發生問題。

### <a name="the-fqid"></a>FQID

FQID 是您可以用來識別錯誤的最特定資訊。 它是一個字串，其中包含 Cmdlet 定義的識別碼、Cmdlet 類別的名稱，以及報告錯誤的來源。 一般來說，錯誤記錄類似于 Windows 事件記錄檔的事件記錄。 FQID 類似于下列元組，可識別事件記錄的類別：（*記錄名稱*、*來源*、*事件識別碼*）。

FQID 的設計是要檢查成單一字串。 不過，有一些案例是由主應用程式剖析的錯誤識別碼所設計。 下列範例是格式正確的完整錯誤識別碼。

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

在上述範例中，第一個權杖是錯誤識別碼，後面接著 Cmdlet 類別的名稱。 錯誤識別碼可以是單一權杖，也可以是以點分隔的識別碼，以允許在檢查識別碼時進行分支。 請勿在錯誤識別碼中使用空白字元或標點符號。 特別重要的是不要使用逗號;Windows PowerShell 會使用逗號來分隔識別碼和 Cmdlet 類別名稱。

### <a name="other-information"></a>其他資訊

[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件也可能會提供描述發生錯誤之環境的資訊。 這項資訊包含錯誤詳細資料、調用資訊，以及發生錯誤時正在處理的目標物件等專案。 雖然這種資訊對主應用程式可能很有用，但通常不會用來識別錯誤。 這項資訊可透過下列屬性取得：

[System.web. ErrorRecord. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System.web. ErrorRecord. InvocationInfo](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System.web. ErrorRecord. TargetObject](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>另請參閱

[ErrorRecord。](/dotnet/api/System.Management.Automation.ErrorRecord)

[Errorcategory。](/dotnet/api/System.Management.Automation.ErrorCategory)

[Errorcategoryinfo。](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[WriteError 的管理元件](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Throwterminatingerror * 的 *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[將非終止的錯誤報表新增至您的 Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell 錯誤報表](./error-reporting-concepts.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
