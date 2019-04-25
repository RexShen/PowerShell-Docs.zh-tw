---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: e01f6ceea361f5a9b3de645346d0652986b6267d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057225"
---
# <a name="nonewline-parameter"></a><span data-ttu-id="95c92-102">NoNewLine 參數</span><span class="sxs-lookup"><span data-stu-id="95c92-102">NoNewLine parameter</span></span>
<span data-ttu-id="95c92-103">**Out-File\*\*\*\*Add-Content** 和 **Set-Content** 現在有新的 **–NoNewline** 參數，只會省略輸出之後的新行。</span><span class="sxs-lookup"><span data-stu-id="95c92-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="95c92-104">如未指定 **–NoNewline**，每個片段都會放在不同的行︰</span><span class="sxs-lookup"><span data-stu-id="95c92-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```
