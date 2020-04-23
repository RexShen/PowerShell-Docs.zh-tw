---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
title: 資訊串流
ms.openlocfilehash: c54603cf0dd4f0b69f8147620130f9f29bc3e5ec
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "71147608"
---
# <a name="information-stream"></a>資訊串流

PowerShell 5.0 新增了新的結構化**資訊**串流，可在指令碼與其主機之間傳送結構化資料。 `Write-Host` 也已更新，可將其輸出發出到**資訊**串流，您現在可在其中擷取輸出或將其轉為無回應。 搭配 `Write-Information`InformationVariable**和**InformationAction**一般參數使用的新** Cmdlet 能夠提供更多彈性和功能。

下列函式會使用利用新**資訊**串流的 Cmdlet。

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

下列範例顯示執行此函式的結果。

```powershell
$r = c:\temp\OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

`$r` 變數已擷取指令碼變數 `$p` 中的程序資訊。

```powershell
$r.Id
4008
```

不同於 `Write-Host` Cmdlet，使用 **的**InformationVariable`Write-Information` 參數可讓您擷取變數中的輸出。 使用**標記**，您可以針對要傳送到**資訊**串流的訊息建立不同通道。

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

當您使用標記來將訊息傳送到**資訊**串流時，該訊息不會顯示於主應用程式中，但可使用標記名稱來擷取。 例如：

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```