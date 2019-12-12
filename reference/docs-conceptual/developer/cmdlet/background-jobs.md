---
title: 背景作業 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363557"
---
# <a name="background-jobs"></a>背景作業

Cmdlet 可以在內部或 Windows PowerShell*背景工作*執行其動作。 當 Cmdlet 以背景工作的形式執行時，工作會以非同步方式在自己的執行緒中完成，並與 Cmdlet 所使用的管線執行緒分開。 從使用者的觀點來看，當 Cmdlet 以背景工作的形式執行時，即使工作需要相當長的時間才能完成，命令提示字元還是會立即傳回，而且當作業執行時，使用者可以繼續執行而不中斷。

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>背景工作、子作業和作業存放庫

支援背景工作的 Cmdlet 所傳回的工作物件會定義作業。 （[啟動作業](/powershell/module/Microsoft.PowerShell.Core/Start-Job)Cmdlet 也會傳回工作物件）。作業的名稱、用來指定作業的識別碼、狀態資訊和子工作都會包含在此定義中。 作業不會執行任何工作。 每個背景工作都至少有一個子工作，因為子作業會執行實際的工作。 當您執行 Cmdlet，讓工作以背景工作的形式執行時，此 Cmdlet 必須將作業和子作業新增至通用存放庫，稱為「*作業存放庫*」。

如需如何在命令列處理背景工作的詳細資訊，請參閱下列各項：

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>撰寫以背景工作方式執行的 Cmdlet

若要撰寫可當做背景工作執行的 Cmdlet，您必須完成下列工作：

- 定義 `asJob` 切換參數，讓使用者可以決定是否要以背景工作的方式執行 Cmdlet。

- 建立一個衍生自[system.web](/dotnet/api/System.Management.Automation.Job)類別的物件。 這個物件可以是自訂工作物件或 Windows PowerShell 所提供的工作物件，例如[Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob)物件。

- 在記錄處理方法中，加入 `if` 語句，以偵測是否應該以背景工作的方式執行 Cmdlet。

- 若為自訂工作物件，請執行 job 類別。

- 根據 Cmdlet 是否以背景工作的方式執行，傳回適當的物件。

如需程式碼範例，請參閱[如何支援作業](./how-to-support-jobs.md)。

## <a name="background-job-related-apis"></a>背景作業相關的 Api

Windows PowerShell 會提供下列 Api 來管理背景工作。

[System.web](/dotnet/api/System.Management.Automation.Job)會衍生自訂工作物件。 這是抽象類別。

[Jobrepository](/dotnet/api/System.Management.Automation.JobRepository)會管理並提供目前作用中背景工作的相關資訊。

[Jobstate](/dotnet/api/System.Management.Automation.JobState)會定義背景作業的狀態。 狀態包括 [已啟動]、[執行中] 和 [已停止]。

[Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo)提供背景工作狀態的相關資訊，而且如果上次狀態變更是由錯誤所造成，則作業會進入其目前狀態的原因。

[Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs)提供背景工作變更狀態時所引發事件的引數。

## <a name="windows-powershell-job-cmdlets"></a>Windows PowerShell 作業 Cmdlet

Windows PowerShell 會提供下列 Cmdlet 來管理背景工作。

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
