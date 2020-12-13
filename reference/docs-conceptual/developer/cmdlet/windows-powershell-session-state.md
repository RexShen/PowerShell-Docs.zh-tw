---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 工作階段狀態
description: Windows PowerShell 工作階段狀態
ms.openlocfilehash: 51de92f1f392f708cf49c7ccb4a6808fd628076c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668128"
---
# <a name="windows-powershell-session-state"></a>Windows PowerShell 工作階段狀態

會話狀態是指 Windows PowerShell 會話或模組的目前設定。 Windows PowerShell 會話是由命令列使用者以互動方式或由主應用程式以程式設計方式使用的操作環境。 會話的會話狀態稱為全域會話狀態。

從開發人員的觀點來看，Windows PowerShell 會話是指主應用程式開啟 Windows PowerShell 的執行時間與關閉該執行時間之間的時間。 另一種方式是，會話是在執行時間存在時所叫用的 Windows PowerShell 引擎實例的存留期。

## <a name="module-session-state"></a>模組會話狀態

每當模組或其中一個的嵌套模組匯入會話時，就會建立模組會話狀態。 當模組匯出元素（例如 Cmdlet、函式或腳本）時，會將該元素的參考加入會話的全域會話狀態。 不過，當元素執行時，它會在模組的會話狀態中執行。

## <a name="session-state-data"></a>Session-State 資料

會話狀態資料可以是公用或私用。 公用資料可供來自會話狀態之外的呼叫，而私用資料僅供來自會話狀態內的呼叫使用。 例如，模組可以有私用函式只能由模組呼叫，或只能由已匯出的公用元素在內部呼叫。 這類似于 .NET Framework 類型的私用和公共成員。

會話狀態資料會由目前的執行引擎實例儲存在目前 Windows PowerShell 會話的內容中。 會話狀態資料包含下列專案：

- 路徑資訊

- 磁片磁碟機資訊

- Windows PowerShell 提供者資訊

- 匯入模組的相關資訊，以及模組元素的參考 (例如模組所匯出的 Cmdlet、函式和腳本) 。 此資訊和這些參考僅適用于全域會話狀態。

- 會話狀態變數資訊

## <a name="accessing-session-state-data-within-cmdlets"></a>存取 Cmdlet 內的 Session-State 資料

Cmdlet 可以透過 Cmdlet 類別的 [PSCmdlet. Sessionstate *](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) 屬性間接存取會話狀態資料，或直接透過 [Sessionstate](/dotnet/api/System.Management.Automation.SessionState) 類別來存取會話狀態資料。 [Sessionstate](/dotnet/api/System.Management.Automation.SessionState)類別所提供的屬性可用來調查不同類型的會話狀態資料。

## <a name="see-also"></a>另請參閱

[PSCmdlet. Sessionstate。](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[Sessionstate 嗎？Displayproperty = Fullname](/dotnet/api/System.Management.Automation.SessionState)

[Windows PowerShell Cmdlet](./cmdlet-overview.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell 殼層 SDK](../windows-powershell-reference.md)
