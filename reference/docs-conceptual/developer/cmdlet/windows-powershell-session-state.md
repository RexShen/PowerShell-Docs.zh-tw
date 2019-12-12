---
title: Windows PowerShell 會話狀態 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369097"
---
# <a name="windows-powershell-session-state"></a>Windows PowerShell 工作階段狀態

會話狀態指的是 Windows PowerShell 會話或模組的目前設定。 Windows PowerShell 會話是一種操作環境，由命令列使用者以互動方式使用，或由主應用程式以程式設計方式使用。 會話的會話狀態稱為「全域會話」狀態。

從開發人員的觀點來看，Windows PowerShell 會話是指主應用程式開啟 Windows PowerShell 執行時間和關閉執行時間時之間的時間。 另一種方式是，會話是在執行時間存在時叫用的 Windows PowerShell 引擎實例的存留期。

## <a name="module-session-state"></a>模組會話狀態

每當模組或其中一個嵌套模組匯入會話時，就會建立模組會話狀態。 當模組匯出元素（例如 Cmdlet、函式或腳本）時，該專案的參考會加入至會話的全域會話狀態。 不過，當元素執行時，它會在模組的會話狀態中執行。

## <a name="session-state-data"></a>會話狀態資料

會話狀態資料可以是公用或私用。 公用資料可供從會話狀態外部呼叫，而私用資料僅供從會話狀態內呼叫。 例如，模組可以具有只能由模組呼叫的私用函式，或只能由已匯出的公用元素在內部進行呼叫的函式。 這類似于 .NET Framework 類型的私用和公用成員。

目前 Windows PowerShell 會話的內容中，目前的執行引擎實例會儲存會話狀態資料。 會話狀態資料是由下列專案所組成：

- 路徑資訊

- 磁片磁碟機資訊

- Windows PowerShell 提供者資訊

- 模組所匯出模組專案（例如 Cmdlet、函式和腳本）的已匯入模組和參考的相關資訊。 這項資訊和這些參考僅適用于全域會話狀態。

- 會話狀態變數資訊

## <a name="accessing-session-state-data-within-cmdlets"></a>存取 Cmdlet 內的會話狀態資料

Cmdlet 可以透過 Cmdlet 類別的[PSCmdlet. Sessionstate *](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)屬性，或直接透過[Sessionstate](/dotnet/api/System.Management.Automation.SessionState)類別，來存取會話狀態資料（可能為間接）。 [Sessionstate](/dotnet/api/System.Management.Automation.SessionState)類別所提供的屬性可用來調查不同類型的會話狀態資料。

## <a name="see-also"></a>另請參閱

[System.web. PSCmdlet. Sessionstate](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[Sessionstate 嗎？Displayproperty = Fullname](/dotnet/api/System.Management.Automation.SessionState)

[Windows PowerShell Cmdlet](./cmdlet-overview.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
