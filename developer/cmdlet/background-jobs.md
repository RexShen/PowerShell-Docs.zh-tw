---
title: 背景工作 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794700"
---
# <a name="background-jobs"></a>背景作業

在內部或 Windows powershell Cmdlet 可以執行其動作*背景工作*。 當 cmdlet 執行背景工作時，工作會在其自己的執行緒不同於 cmdlet 正在使用的管線執行緒以非同步方式完成。 從使用者觀點來看，當指令程式會執行為背景工作，命令提示字元會立即傳回即使工作需要長時間才能完成，且使用者可以繼續使用不中斷工作執行時。

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>背景工作、 子工作與工作存放庫

支援背景工作的 cmdlet 所傳回工作物件會定義工作。 ( [Start-job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet 也會傳回工作物件。)在此定義包含作業，用來指定工作、 狀態資訊和子工作的識別項的名稱。 作業不會執行任何工作。 每個背景工作有至少一個子工作，因為子工作會執行實際工作。 指令程式時，讓背景工作執行的工作，您可以執行 cmdlet，必須將工作與子工作，加入通用儲存機制，稱為*工作存放庫*。

如需有關如何在命令列處理背景工作的詳細資訊，請參閱下列各項：

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>撰寫以背景工作執行的 Cmdlet

若要撰寫的 cmdlet，可以執行為背景工作，您必須完成下列工作：

- 定義`asJob`切換參數，以便使用者可以決定是否要以背景工作方式執行 cmdlet。

- 建立物件衍生自[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job)類別。 這個物件可以是自訂的工作物件或工作物件，提供 Windows powershell，例如[System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob)物件。

- 在記錄處理方法中，新增`if`會偵測是否應該以背景工作執行 cmdlet 的陳述式。

- 自訂的工作物件，實作作業的類別。

- 傳回適當的物件，取決於是否執行背景工作的 cmdlet。

如需程式碼範例，請參閱 <<c0> [ 如何支援工作](./how-to-support-jobs.md)。

## <a name="background-job-related-apis"></a>背景工作相關的 Api

下列 Api 會提供 Windows PowerShell 來管理背景工作。

[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job)衍生自訂的工作物件。 這是抽象類別。

[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository)管理，並提供目前的作用中的背景工作的相關資訊。

[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState)定義背景作業的狀態。 狀態包括啟動、 執行，且已停止。

[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo)提供背景工作的狀態相關資訊，以及如果上次狀態變更，因發生錯誤時，工作進入其目前狀態的原因。

[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs)提供背景工作變更狀態時引發事件的引數。

## <a name="windows-powershell-job-cmdlets"></a>Windows PowerShell 工作 Cmdlet

下列指令程式會提供 Windows PowerShell 來管理背景工作。

[Get-Job](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

取得正在目前工作階段中執行的 Windows PowerShell 背景工作。

[Receive-Job](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

取得目前工作階段中 Windows PowerShell 背景工作的結果。

[Remove-Job](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

刪除 Windows PowerShell 背景工作。

[Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

啟動 Windows PowerShell 背景工作。

[Stop-Job](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

停止 Windows PowerShell 背景工作。

[Wait-Job](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

抑制命令提示字元，直到工作階段中正在執行的其中一個或所有 Windows PowerShell 背景工作完成為止。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
