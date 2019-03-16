---
title: 指令程式錯誤報告 |Microsoft Docs
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
ms.openlocfilehash: 45f5934314a2871ceb921c7a66b9dfb658d0bd99
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057938"
---
# <a name="cmdlet-error-reporting"></a>Cmdlet 錯誤報告

以不同的方式取決於是否錯誤會終止錯誤的錯誤或非終止錯誤，就應該報告 Cmdlet。 終止的錯誤是錯誤造成管線，以立即終止或沒有理由繼續處理時，發生的錯誤。 非終止錯誤會報告目前的錯誤狀況，這些錯誤，但此指令程式可以繼續處理輸入的物件。 非終止錯誤，問題，通常會通知使用者，但此 cmdlet 會繼續處理下一個輸入的物件。

## <a name="terminating-and-nonterminating-errors"></a>終止和非終止錯誤

下列指導方針可用來判斷錯誤狀況是終止的錯誤或非終止錯誤。

- 沒有錯誤狀況防止 cmdlet 成功處理任何進一步的輸入物件嗎？ 如果是的話，這會是終止錯誤。

- 與特定的輸入的物件或輸入的物件子集相關的錯誤狀況？ 如果是的話，這是一個非終止錯誤。

- 此 cmdlet 是否接受多個輸入的物件，例如處理可能在另一個輸入物件上成功？ 如果是的話，這是一個非終止錯誤。

- Cmdlet 可接受多個輸入的物件應該決定什麼終止和非終止錯誤，即使是在特定情況下套用至只有單一的輸入物件。

- 指令程式可以接收任何數目的輸入物件，並擲回終止的例外狀況之前傳送任何數目的成功或錯誤的物件。 沒有任何收到的輸入物件的數目和傳送的成功和錯誤物件數目之間的關聯性。

- 可以接受輸入物件只有 0-1，並產生只 0-1 的 Cmdlet 會輸出物件應該視為的終止錯誤的錯誤，並會產生終止的例外狀況。

## <a name="reporting-nonterminating-errors"></a>報告非終止錯誤

報告非終止錯誤應該永遠是 cmdlet 的實作內[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法， [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，或有[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。 藉由呼叫報告這些錯誤類型[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)再傳送至錯誤資料流的錯誤記錄的方法。

## <a name="reporting-terminating-errors"></a>報告的終止錯誤

終止錯誤會報告所擲回例外狀況，或藉由呼叫[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法。 請注意 cmdlet 也可以攔截並重新擲回例外狀況，例如 OutOfMemory，不過，它們不需要重新擲回例外狀況，因為 Windows PowerShell 執行階段會同時攔截。

您也可以定義自己的例外狀況的特定問題，您的情況，或將其他資訊新增至現有的例外狀況，使用其錯誤記錄。

## <a name="error-records"></a>錯誤記錄

Windows PowerShell 說明使用非終止錯誤條件[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件。 每個[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件會提供錯誤類別目錄資訊、 選擇性目標物件和錯誤狀況的相關詳細資料。

### <a name="error-identifiers"></a>錯誤識別碼

錯誤識別碼是簡單的字串，識別在 cmdlet 中的錯誤狀況。 Windows PowerShell 會結合以建立完整的錯誤識別碼時篩選回應特定的錯誤時的錯誤資料流或記錄錯誤，可以稍後使用 cmdlet 識別項，或與其他使用者特定活動，這個識別項。

指定錯誤的識別碼時，應該遵循下列指導方針。

- 不同、 非常特定，錯誤識別碼指派給不同的程式碼路徑。 每個呼叫的程式碼路徑[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或是[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)應該有自己的錯誤識別碼。

- 錯誤識別碼應該是唯一的終止和非終止錯誤的 CLR 例外狀況類型。

- 不會變更錯誤識別項 cmdlet 的 Windows PowerShell 提供者的版本之間的語意。 建立語意錯誤識別項之後，它應該保持不變的整個生命週期的 cmdlet。

- 終止錯誤，請針對特定的 CLR 例外狀況類型中使用唯一的錯誤識別碼。 如果例外狀況類型變更，請使用新的錯誤識別碼。

- 對於非終止錯誤，請針對特定的輸入物件中使用特定的錯誤識別碼。

- 選擇識別碼 tersely 對應到所回報的錯誤文字。 請勿使用空格或標點符號。

- 不會產生不是可重現的錯誤識別碼。 比方說，不會產生包含處理序識別項的識別項。 錯誤識別碼在它們發生相同問題的其他使用者所見的識別項對應時，才很有用。

### <a name="error-categories"></a>錯誤類別目錄

錯誤類別目錄用來群組使用者的錯誤。 這些類別會定義 Windows PowerShell 和 cmdlet 與 Windows PowerShell 提供者必須產生的錯誤記錄時之間做出選擇。

如需錯誤類別目錄所提供的說明，請參閱 < [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)列舉型別。 一般情況下，您應該避免使用 NoError、 UndefinedError 和 GenericError 盡可能。

使用者可以檢視這些設定時，根據分類的錯誤 」`$ErrorView`"到"CategoryView 」。

## <a name="see-also"></a>另請參閱

[Windows PowerShell Cmdlets](./cmdlet-overview.md)

[Cmdlet Output](./types-of-cmdlet-output.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
