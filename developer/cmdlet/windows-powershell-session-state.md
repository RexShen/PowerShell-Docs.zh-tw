---
title: Windows PowerShell 工作階段狀態 |Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066969"
---
# <a name="windows-powershell-session-state"></a>Windows PowerShell 工作階段狀態

工作階段狀態指的是 Windows PowerShell 工作階段或模組的目前組態。 Windows PowerShell 工作階段是以互動方式或使用的命令列的使用者以程式設計方式的主應用程式的操作環境。 工作階段的工作階段狀態被指全域工作階段狀態。

開發人員的觀點而言，Windows PowerShell 工作階段是指當主應用程式會開啟 Windows PowerShell runspace 與它在關閉 runspace 時之間的時間。 工作階段探討另一種方式，是在 runspace 存在時，會叫用的 Windows PowerShell 引擎的執行個體的存留期。

## <a name="module-session-state"></a>模組工作階段狀態

每當模組或其中一個其巢狀模組匯入工作階段，會建立模組工作階段狀態。 當模組匯出的項目，例如 cmdlet、 函數或指令碼時，該元素的參考會加入工作階段的全域工作階段狀態。 不過，當執行項目時，它就是模組的工作階段狀態內執行。

## <a name="session-state-data"></a>工作階段狀態資料

工作階段狀態資料可以是公用或私用。 私用資料可供使用才能內的工作階段狀態的呼叫時，就可從外部工作階段狀態的呼叫公用的資料。 例如，模組可以有可以只由模組或只在內部呼叫的私用函式的已匯出的公用項目。 這是類似於.NET Framework 型別的 private 和 public 成員。

工作階段狀態資料會儲存目前的 Windows PowerShell 工作階段的內容中執行引擎的目前執行個體。 工作階段狀態資料是由下列項目所組成：

- 路徑資訊

- 磁碟機資訊

- Windows PowerShell 提供者資訊

- 匯入的模組和模組所匯出的模組項目 （例如 cmdlet、 函數和指令碼） 的參考資訊。 這項資訊，這些參考會只有全域工作階段狀態。

- 工作階段狀態變數的資訊

## <a name="accessing-session-state-data-within-cmdlets"></a>工作階段狀態中存取資料的 Cmdlet

指令程式可以存取工作階段狀態資料，可能是間接透過[System.Management.Automation.PSCmdlet.Sessionstate*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)屬性，在 cmdlet 類別或直接透過[System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState)類別。 [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState)類別提供可用來調查工作階段狀態資料的不同類型的屬性。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.PSCmdlet.Sessionstate](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System.Management.Automation.Sessionstate?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.SessionState)

[Windows PowerShell Cmdlets](./cmdlet-overview.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
