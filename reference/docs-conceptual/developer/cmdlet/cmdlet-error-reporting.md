---
title: Cmdlet 錯誤報表 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error records [PowerShell], terminating
- non-terminating errors [PowerShell]
- error records [PowerShell]
- terminating errors [PowerShell]
- error records [PowerShell], non-terminating
ms.assetid: 0b014035-52ea-44cb-ab38-bbe463c5465a
caps.latest.revision: 8
ms.openlocfilehash: 5dfec318438ca139518c596011ac5e56445738ea
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365917"
---
# <a name="cmdlet-error-reporting"></a>Cmdlet 錯誤報表

Cmdlet 應該根據錯誤是終止錯誤還是非終止錯誤，以不同的方式報告錯誤。 終止錯誤是導致管線立即終止的錯誤，或在沒有理由繼續處理時所發生的錯誤。 非終止錯誤是報告目前錯誤狀況的錯誤，但 Cmdlet 可以繼續處理輸入物件。 發生非終止錯誤時，使用者通常會收到問題的通知，但此 Cmdlet 會繼續處理下一個輸入物件。

## <a name="terminating-and-nonterminating-errors"></a>終止和非終止錯誤

下列指導方針可用於判斷錯誤狀況是終止錯誤或非終止錯誤。

- 錯誤狀況是否會讓您的 Cmdlet 無法成功處理任何進一步的輸入物件？ 若是如此，這就是終止錯誤。

- 是否有與特定輸入物件或輸入物件子集相關的錯誤狀況？ 若是如此，這就是非終止錯誤。

- Cmdlet 是否接受多個輸入物件，讓處理常式在另一個輸入物件上可能會成功？ 若是如此，這就是非終止錯誤。

- 可以接受多個輸入物件的 Cmdlet 應該決定什麼是終止和非終止錯誤，即使特定情況僅適用于單一輸入物件也是如此。

- Cmdlet 可以在擲回終止例外狀況之前，接收任意數目的輸入物件，並傳送任何數目的成功或錯誤物件。 接收的輸入物件數目與傳送的成功和錯誤物件之間沒有任何關聯性。

- 只能接受0-1 輸入物件和只產生0-1 輸出物件的 Cmdlet 應該將錯誤視為終止錯誤，並產生終止例外狀況。

## <a name="reporting-nonterminating-errors"></a>報告非終止錯誤

非終止錯誤的報告應一律在 Cmdlet 的[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法（ [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法）中執行，或的指令程式（或）的程式中，system.servicemodel[方法....](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 這些類型的錯誤會藉由呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法來回報，然後再將錯誤記錄傳送至錯誤資料流程。

## <a name="reporting-terminating-errors"></a>報告終止錯誤

終止錯誤會藉由擲回例外狀況或藉由呼叫[ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法來回報。 請注意，Cmdlet 也可以攔截並重新擲回例外狀況（例如**OutOfMemory**），不過，它們不需要重新擲回例外狀況，因為 PowerShell 執行時間也會加以攔截。

您也可以針對您的情況特定的問題定義自己的例外狀況，或使用其錯誤記錄將其他資訊新增至現有的例外狀況。

## <a name="error-records"></a>錯誤記錄

PowerShell 描述[ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件的非終止錯誤狀況。 每個物件都會提供錯誤類別目錄資訊、選擇性的目標物件，以及有關錯誤狀況的詳細資料。

### <a name="error-identifiers"></a>錯誤識別碼

錯誤識別碼是一個簡單字串，可識別 Cmdlet 內的錯誤狀況。
PowerShell 會將此識別碼與 Cmdlet 識別碼結合，以建立可在稍後篩選錯誤資料流程或記錄錯誤時、回應特定錯誤時，或其他使用者特定活動時使用的完整錯誤識別碼。

指定錯誤識別碼時，應遵循下列指導方針：

- 將不同、高度特定的錯誤識別碼指派給不同的程式碼路徑。 每個呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或[ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)的程式碼路徑，都應該有自己的錯誤識別碼。（可能為）。

- 對於終止和非終止錯誤而言，錯誤識別碼應該是 Common Language Runtime （CLR）例外狀況類型的唯一。

- 請勿變更 Cmdlet 或 PowerShell 提供者版本之間的錯誤識別碼的語法。 建立錯誤識別碼的語義之後，它應該會在 Cmdlet 的整個生命週期中保持不變。

- 針對終止錯誤，請針對特定 CLR 例外狀況類型使用唯一的錯誤識別碼。 如果例外狀況類型變更，請使用新的錯誤識別碼。

- 針對非終止錯誤，請針對特定的輸入物件使用特定的錯誤識別碼。

- 針對 tersely 對應至所回報錯誤的識別碼，選擇 [文字]。 請勿使用空白字元或標點符號。

- 不要產生無法重現的錯誤識別碼。 例如，請勿產生包含進程識別碼的識別碼。 只有當錯誤識別碼對應至其他遇到相同問題的使用者所看到的識別碼時，才有用。

### <a name="error-categories"></a>錯誤類別

錯誤類別是用來將使用者的錯誤分組。 PowerShell 會定義這些類別和 Cmdlet，而且在產生錯誤記錄時，PowerShell 提供者必須在兩者之間進行選擇。

如需可用錯誤類別的描述，請參閱[ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory)列舉。 一般來說，您應該盡可能避免使用**aad-userreadusingalternativesecurityid-noerror**、 **UndefinedError**和**GenericError** 。

當使用者將 `$ErrorView` 設定為**CategoryView**時，可以根據分類來查看錯誤。

## <a name="see-also"></a>另請參閱

[Cmdlet 總覽](./cmdlet-overview.md)

[Cmdlet 輸出的類型](./types-of-cmdlet-output.md)

[Windows PowerShell 參考](../windows-powershell-reference.md)
