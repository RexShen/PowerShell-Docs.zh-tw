---
description: 說明進階排程工作主題，包括構成排程工作基礎的檔案結構。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_advanced?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Advanced
ms.openlocfilehash: 7b09a72e8ad7e68641c73d2f7e59065dbf8f889b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207255"
---
# <a name="about-scheduled-jobs-advanced"></a>關於排程工作 Advanced

## <a name="short-description"></a>簡短描述

說明進階排程工作主題，包括構成排程工作基礎的檔案結構。

## <a name="long-description"></a>完整描述

如需 **PSScheduledJob** 模組中所含 Cmdlet 的詳細資訊，請參閱 [PSScheduledJob](xref:PSScheduledJob)。

## <a name="scheduled-job-directories-and-files"></a>排程的工作目錄和檔案

PowerShell 排程工作是 PowerShell 作業和工作排程器工作。
每個排程工作都是在工作排程器中註冊，並以 Microsoft .NET Framework 序列化 XML 格式儲存在磁片上。

當您建立排程工作時，PowerShell 會在本機電腦的目錄中建立排程工作的目錄 `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` 。 目錄名稱與作業名稱相同。

以下是範例 **ScheduledJobs** 目錄。

```powershell
Get-ChildItem $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs
```

```Output
Directory: C:\Users\User01\AppData\Local
               \Microsoft\Windows\PowerShell\ScheduledJobs

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         9/29/2011  10:03 AM            ArchiveProjects
d----         9/30/2011   1:18 PM            Inventory
d----        10/20/2011   9:15 AM            Backup-Scripts
d----         11/7/2011  10:40 AM            ProcessJob
d----         11/2/2011  10:25 AM            SecureJob
d----         9/27/2011   1:29 PM            Test-HelpFiles
d----         9/26/2011   4:22 PM            DeployPackage
```

每個排程工作都有自己的目錄。 目錄包含已排程的工作 XML 檔案和 **輸出** 子目錄。

```powershell
$Path = "$home\AppData\Local\Microsoft\Windows\PowerShell"
$Path += "\ScheduledJobs\ProcessJob"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/1/2011   3:00 PM            Output
-a---         11/1/2011   3:43 PM       7281 ScheduledJobDefinition.xml
```

排程工作的 **輸出** 目錄包含其執行歷程記錄。
每次工作觸發程式啟動排程工作時，PowerShell 會在輸出目錄中建立時間戳記命名的目錄。 時間戳記目錄包含 **Results.xml** 檔案中的作業結果，以及 **Status.xml** 檔案中的作業狀態。

下列命令會顯示 **ProcessJob** 排程工作的執行歷程記錄目錄。

```powershell
$Path = "$home\AppData\Local\Microsoft"
$Path += "\Windows\PowerShell\ScheduledJobs\ProcessJob\Output"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft
               \Windows\PowerShell\ScheduledJobs\ProcessJob\Output

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/2/2011   3:00 AM            20111102-030002-260
d----         11/3/2011   3:00 AM            20111103-030002-277
d----         11/4/2011   3:00 AM            20111104-030002-209
d----         11/5/2011   3:00 AM            20111105-030002-251
d----         11/6/2011   3:00 AM            20111106-030002-174
d----         11/7/2011  12:00 AM            20111107-000001-914
d----         11/7/2011   3:00 AM            20111107-030002-376
```

```powershell
$Path = "$home\AppData\Local\Microsoft\Windows\PowerShell\"
$Path += "ScheduledJobs\ProcessJob\Output\20111102-030002-260"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output\20111102-030002-260

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         11/2/2011   3:00 AM     581106 Results.xml
-a---         11/2/2011   3:00 AM       9451 Status.xml
```

您可以開啟和檢查 **ScheduledJobDefinition.xml** 、 **Results.xml** 和 **Status.xml** 檔案，或使用 `Select-XML` Cmdlet 來剖析檔案。

> [!WARNING]
> 請勿編輯 XML 檔案。 如果任何 XML 檔案包含不正確 XML，PowerShell 就會刪除排程工作和其執行歷程記錄，包括工作結果。

## <a name="start-a-scheduled-job-immediately"></a>立即啟動排程工作

您可以使用下列兩種方式之一來立即啟動排程工作：

- 執行 `Start-Job` Cmdlet 以啟動任何排程工作。
- 將 **RunNow** 參數新增至 `Register-ScheduledJob` 命令，以在命令執行時立即啟動工作。

使用 Cmdlet 啟動的作業 `Start-Job` 是標準的 PowerShell 背景工作，而不是排程工作的實例。 就像所有背景工作一樣，這些工作會立即開始，而不會受限於工作選項或由工作觸發程式所影響。 作業輸出不會儲存在排程工作目錄的 **輸出** 目錄中。

下列命令會使用 Cmdlet 的 **DefinitionName** 參數 `Start-Job` 來啟動 ProcessJob 排程工作。

```powershell
Start-Job -DefinitionName ProcessJob
```

若要管理作業並取得工作結果，請使用 job Cmdlet。 如需工作 Cmdlet 的詳細資訊，請參閱 [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md)。

> [!NOTE]
> 若要在排程工作的實例上使用 Job Cmdlet，必須將 **PSScheduledJob** 模組匯入到會話中。 若要匯入 **PSScheduledJob** 模組，請輸入 `Import-Module PSScheduledJob` 或使用任何排程工作 Cmdlet，例如 `Get-ScheduledJob` 。

## <a name="rename-a-scheduled-job"></a>重新命名排程工作

若要重新命名排程工作，請使用 Cmdlet 的 Name 參數 `Set-ScheduledJob` 。 當您重新命名排程工作時，PowerShell 會變更排程工作的名稱和排程的工作目錄。 但是，它不會變更已執行之排程工作的實例名稱。

## <a name="get-start-and-end-times"></a>取得開始和結束時間

若要取得工作實例開始和結束的日期和時間，請使用針對排程工作所傳回之 Register-scheduledjob 物件的 **PSBeginTime** 和 **PSEndTime** 屬性 `Get-Job` 。

下列範例會使用 Cmdlet 的 **Property** 參數 `Format-Table` ，在資料表中顯示每個工作實例的 **PSBeginTime** 和 **PSEndTime** 屬性。 名為 **Label** 的計算屬性會顯示每個工作實例的經過時間。

```powershell
Get-job -Name UpdateHelpJob | 
  Format-Table -Property ID, PSBeginTime, PSEndTime,
@{Label="Elapsed Time";Expression={$.PsEndTime - $.PSBeginTime}}
```

```Output
Id   PSBeginTime             PSEndTime                Elapsed Time
--   -----------             ---------                ------------
 2   11/3/2011 3:00:01 AM    11/3/2011 3:00:39 AM     00:00:38.0053854
 3   11/4/2011 3:00:02 AM    11/4/2011 3:01:01 AM     00:00:59.1188475
 4   11/5/2011 3:00:02 AM    11/5/2011 3:00:50 AM     00:00:48.3692034
 5   11/6/2011 3:00:01 AM    11/6/2011 3:00:54 AM     00:00:52.8013036
 6   11/7/2011 3:00:01 AM    11/7/2011 3:00:38 AM     00:00:37.1930350
 7   11/8/2011 3:00:01 AM    11/8/2011 3:00:57 AM     00:00:56.2570556
 8   11/9/2011 3:00:03 AM    11/9/2011 3:00:55 AM     00:00:51.8142222
 9   11/10/2011 3:00:02 AM   11/10/2011 3:00:42 AM    00:00:40.7195954
```

## <a name="manage-execution-history"></a>管理執行歷程記錄

您可以決定為每個排程工作儲存的工作實例結果數目，並刪除執行歷程記錄和任何排程工作的已儲存工作結果。

排程工作的 **ExecutionHistoryLength** 屬性會決定為排程工作儲存的工作實例結果數目。 當儲存的結果數目超過 **ExecutionHistoryLength** 屬性的值時，PowerShell 會刪除最舊實例的結果，以騰出空間給最新實例的結果。

根據預設，PowerShell 會儲存每個排程工作的執行歷程記錄和32實例的結果。 若要變更該值，請使用 **MaxResultCount** 或 Cmdlet 的 MaxResultCount `Register-ScheduledJob` 參數 `Set-ScheduledJob` 。

若要刪除排程工作的執行歷程記錄和所有結果，請使用 Cmdlet 的 **ClearExecutionHistory** 參數 `Set-ScheduledJob` 。 刪除此執行歷程記錄並不會防止 PowerShell 儲存排程工作新實例的結果。

下列範例會使用展開來建立將 `$JobParms` 參數值傳遞給 Cmdlet 的參數值 `Register-ScheduledJob` 。 如需詳細資訊，請參閱 [about_Splatting md](../../Microsoft.PowerShell.Core/About/about_Splatting.md)。
`Register-ScheduledJob`用 `@JobParms` 來建立排程工作。 此命令會使用值為12的 **MaxResultCount** 參數，只儲存排程工作的12個最新工作實例結果。

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  MaxResultCount = "12"
}

Register-ScheduledJob @JobParms
```

下列命令會使用 Cmdlet 的 **MaxResultCount** 參數， `Set-ScheduledJob` 將儲存的實例結果數目增加至
15.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 15
```

下列命令會刪除 **ProcessJob** 排程工作的執行歷程記錄和目前儲存的結果。

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

下列命令會取得電腦上所有排程工作的 name 和 **ExecutionHistoryLength** 屬性值，並將它們顯示在資料表中。

```powershell
Get-ScheduledJob | 
  Format-Table -Property Name, ExecutionHistoryLength -AutoSize
```

## <a name="see-also"></a>另請參閱

[about_Scheduled_Jobs_Basics](about_Scheduled_Jobs_Basics.md)

[about_Scheduled_Jobs_Troubleshooting](about_Scheduled_Jobs_Troubleshooting.md)

[about_Scheduled_Jobs](about_Scheduled_Jobs.md)

[about_Splatting md](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

[PSScheduledJob](xref:PSScheduledJob) 模組 Cmdlet

[工作排程器](/windows/desktop/TaskSchd/task-scheduler-reference)
