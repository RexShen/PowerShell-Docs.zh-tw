---
title: 錯誤報告概念 |Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068176"
---
# <a name="error-reporting-concepts"></a>錯誤報告概念

Windows PowerShell 提供兩種機制來報告錯誤： 機制之一*終止錯誤*和另一個機制來*非終止錯誤*。 務必針對您的 cmdlet，來報告錯誤正確，讓主應用程式執行您的 cmdlet 可因應以適當方式。

您的指令程式應該呼叫[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法發生錯誤時則否，或不應該允許 cmdlet 以繼續處理其輸入的物件。 您的指令程式應該呼叫[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)指令程式可以繼續處理輸入的物件時，報告非終止錯誤的方法。 這兩種方法提供主應用程式可用來調查的錯誤原因的錯誤記錄。

您可以使用下列指導方針來判斷錯誤是否為終止或非終止錯誤。

- 錯誤會終止錯誤，如果它會防止您的 cmdlet，從繼續處理目前的物件或已成功處理任何進一步的輸入的物件，不論其內容。

- 如果不想您的 cmdlet 以繼續處理目前的物件或任何進一步的輸入的物件，不論其內容，錯誤會終止錯誤。

- 錯誤發生的 cmdlet 中，不會接受或傳回物件，或是接受或傳回只有一個物件的 cmdlet 中發生，是終止錯誤。

- 如果您想要繼續處理目前的物件和任何進一步的輸入物件的 cmdlet，錯誤會是一個非終止錯誤。

- 如果它與相關的特定輸入的物件或輸入物件的子集，錯誤會是一個非終止錯誤。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
