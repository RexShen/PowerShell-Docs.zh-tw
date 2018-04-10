---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: 2af56be1915c148809f52cd9040c45da160ae0a2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="reporting-on-jea"></a><span data-ttu-id="bc91c-102">JEA 上的報告</span><span class="sxs-lookup"><span data-stu-id="bc91c-102">Reporting on JEA</span></span>
<span data-ttu-id="bc91c-103">若要報告 JEA 組態的狀態，您可以使用︰</span><span class="sxs-lookup"><span data-stu-id="bc91c-103">In order to report on the state of your JEA configuration, you can use:</span></span>
1.  <span data-ttu-id="bc91c-104">**Get-PSSessionConfiguration** 以傳回指定電腦上所有註冊端點的清單。</span><span class="sxs-lookup"><span data-stu-id="bc91c-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2.  <span data-ttu-id="bc91c-105">**Get-PSSessionCapability** 以報告任何指定使用者在特定端點上具備的功能。</span><span class="sxs-lookup"><span data-stu-id="bc91c-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="bc91c-106">以下是 **Get PSSessionCapability** 的範例：</span><span class="sxs-lookup"><span data-stu-id="bc91c-106">Here’s an example of **Get-PSSessionCapability**:</span></span>
```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           clear -> Clear-Host
Alias           cls -> Clear-Host
Alias           exsn -> Exit-PSSession
Alias           gcm -> Get-Command
Alias           measure -> Measure-Object
Alias           select -> Select-Object
Function        Clear-Host
Function        Exit-PSSession
Function        Get-Command
Function        Get-FormatData
Function        Get-Help
Function        Get-UserInfo
Function        Measure-Object
Function        Out-Default
Function        Select-Object
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...


```

<span data-ttu-id="bc91c-107">若要報告使用者在 JEA 工作階段期間進行的_動作_，您可以︰</span><span class="sxs-lookup"><span data-stu-id="bc91c-107">To report on the _actions_ users took during a JEA session, you can:</span></span>
1. <span data-ttu-id="bc91c-108">啟用該 JEA 端點的「即時權限提升」("over-the-shoulder") 記錄，並查閱記錄目錄中每個使用者動作的完整記錄</span><span class="sxs-lookup"><span data-stu-id="bc91c-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="bc91c-109">開啟 PowerShell 模組的記錄，並檢查 PowerShell 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="bc91c-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>