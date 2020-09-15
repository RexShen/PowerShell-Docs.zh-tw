---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
title: 資訊串流
ms.openlocfilehash: 1a8df66f7489910b964ec398e90b76e9f30cd2e2
ms.sourcegitcommit: 87b9b989f261b52969e99159e99ee28ad8d8839a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86567836"
---
# <a name="information-stream"></a><span data-ttu-id="a4a6b-103">資訊串流</span><span class="sxs-lookup"><span data-stu-id="a4a6b-103">Information Stream</span></span>

<span data-ttu-id="a4a6b-104">PowerShell 5.0 新增了新的結構化**資訊**串流，可在指令碼與其主機之間傳送結構化資料。</span><span class="sxs-lookup"><span data-stu-id="a4a6b-104">PowerShell 5.0 adds a new structured **Information** stream to transmit structured data between a script and its host.</span></span> <span data-ttu-id="a4a6b-105">`Write-Host` 也已更新，可將其輸出發出到**資訊**串流，您現在可在其中擷取輸出或將其轉為無回應。</span><span class="sxs-lookup"><span data-stu-id="a4a6b-105">`Write-Host` has also been updated to emit its output to the **Information** stream where you can now capture or silence it.</span></span> <span data-ttu-id="a4a6b-106">搭配 `Write-Information`InformationVariable**和**InformationAction**一般參數使用的新** Cmdlet 能夠提供更多彈性和功能。</span><span class="sxs-lookup"><span data-stu-id="a4a6b-106">The new `Write-Information` cmdlet used with **InformationVariable** and **InformationAction** common parameters enables more flexibility and capability.</span></span>

<span data-ttu-id="a4a6b-107">下列函式會使用利用新**資訊**串流的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a4a6b-107">The following function uses cmdlets that take advantage of the new **Information** stream.</span></span>

```powershell
function OutputGusher {
  [CmdletBinding()]
  param()
  Write-Host -ForegroundColor Green 'Preparing to give you output!'
  Write-Host '============================='
  Write-Host 'I ' -ForegroundColor White -NoNewline
  Write-Host '<3 ' -ForegroundColor Red -NoNewline
  Write-Host 'Output' -ForegroundColor White
  Write-Host '============================='

  $p = Get-Process -id $pid
  $p

  Write-Information $p -Tag Process
  Write-Information 'Some spammy logging information' -Tag LogLow
  Write-Information 'Some important logging information' -Tag LogHigh

  Write-Host
  Write-Host -ForegroundColor Green 'SCRIPT COMPLETE!!'
}
```

<span data-ttu-id="a4a6b-108">下列範例顯示執行此函式的結果。</span><span class="sxs-lookup"><span data-stu-id="a4a6b-108">The following examples show the results of running this function.</span></span>

```powershell
$r = OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

<span data-ttu-id="a4a6b-109">`$r` 變數已擷取指令碼變數 `$p` 中的程序資訊。</span><span class="sxs-lookup"><span data-stu-id="a4a6b-109">The `$r` variable has captured the process information in the script variable `$p`.</span></span>

```powershell
$r.Id
4008
```

<span data-ttu-id="a4a6b-110">不同於 `Write-Host` Cmdlet，使用 **的**InformationVariable`Write-Information` 參數可讓您擷取變數中的輸出。</span><span class="sxs-lookup"><span data-stu-id="a4a6b-110">Unlike the `Write-Host` cmdlet, using the **InformationVariable** parameter of `Write-Information` allows you to capture the output in a variable.</span></span> <span data-ttu-id="a4a6b-111">使用**標記**，您可以針對要傳送到**資訊**串流的訊息建立不同通道。</span><span class="sxs-lookup"><span data-stu-id="a4a6b-111">Using the **Tag**, you can create separate channels for message sent to the **Information** stream.</span></span>

```powershell
$r = OutputGusher -InformationVariable iv
$ivOutput = $iv | Group-Object -AsHash { $_.Tags[0] } -AsString
$ivOutput
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================
SCRIPT COMPLETE!!

Name                 Value
----                 -----
LogLow               {Some spammy logging information}
LogHigh              {Some important logging information}
Process              {System.Diagnostics.Process (powershell)}
PSHOST               {Preparing to give you output!, =============================, I , <3 ...}
```

<span data-ttu-id="a4a6b-112">當您使用標記來將訊息傳送到**資訊**串流時，該訊息不會顯示於主應用程式中，但可使用標記名稱來擷取。</span><span class="sxs-lookup"><span data-stu-id="a4a6b-112">When you send a message to the **Information** stream with a tag, that message is not displayed in the host application but can be retrieved using the tag name.</span></span> <span data-ttu-id="a4a6b-113">例如：</span><span class="sxs-lookup"><span data-stu-id="a4a6b-113">For example:</span></span>

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```
