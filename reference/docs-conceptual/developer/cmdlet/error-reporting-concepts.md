---
title: 錯誤報表概念 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: 2f185e415e3effc2cf09a282ca1167e3bcfb7d6a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364617"
---
# <a name="error-reporting-concepts"></a>錯誤報告概念

Windows PowerShell 提供兩種報告錯誤的機制：一個用於*終止錯誤*的機制，以及另一個*非終止錯誤*的機制。 您的 Cmdlet 必須正確地報告錯誤，讓執行 Cmdlet 的主應用程式能夠以適當的方式回應。

當不是或不應允許 Cmdlet 繼續處理其輸入物件的錯誤發生時，您的 Cmdlet 應該會呼叫[Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法。 當 Cmdlet 可以繼續處理輸入物件時，您的 Cmdlet 應該會呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法來報告非終止的錯誤。 這兩種方法都會提供錯誤記錄，讓主應用程式用來調查錯誤的原因。

使用下列指導方針，判斷錯誤是否為終止或非終止錯誤。

- 錯誤是終止錯誤，如果它會防止您的 Cmdlet 繼續處理目前的物件，或不能成功處理任何進一步的輸入物件（不論其內容為何）。

- 如果您不想讓 Cmdlet 繼續處理目前的物件或任何進一步的輸入物件（不論其內容為何），錯誤就是終止錯誤。

- 如果錯誤發生在不接受或傳回物件的 Cmdlet 中，或如果它發生在接受或只傳回一個物件的 Cmdlet 中，就會有一個終止錯誤。

- 如果您想要讓 Cmdlet 繼續處理目前的物件和任何進一步的輸入物件，則會發生非終止錯誤。

- 如果錯誤與特定的輸入物件或輸入物件的子集相關，則會發生非終止錯誤。

## <a name="see-also"></a>另請參閱

[Throwterminatingerror * 的 *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[WriteError 的管理元件](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
