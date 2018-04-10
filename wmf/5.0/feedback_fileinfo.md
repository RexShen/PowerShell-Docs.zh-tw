---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: 6356902193fc6ec651b2f7e53f8885cb59f17542
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="updates-to-fileinfo-object"></a><span data-ttu-id="e41a4-102">FileInfo 物件的更新</span><span class="sxs-lookup"><span data-stu-id="e41a4-102">Updates to FileInfo object</span></span>
<span data-ttu-id="e41a4-103">檔案版本資訊可能會產生誤導，尤其是在已修補檔案的情況下。</span><span class="sxs-lookup"><span data-stu-id="e41a4-103">File version information can be misleading, particularly in cases where the file was patched.</span></span> <span data-ttu-id="e41a4-104">這一版的 WMF 5.0 將新的 **FileVersionRaw** 和 **ProductVersionRaw** 指令碼屬性加入 FileInfo 物件中。</span><span class="sxs-lookup"><span data-stu-id="e41a4-104">This release of WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to FileInfo objects.</span></span> <span data-ttu-id="e41a4-105">此處是為 powershell.exe 顯示的屬性 (假設 $pid 是 PowerShell 處理程序的識別碼) ︰</span><span class="sxs-lookup"><span data-stu-id="e41a4-105">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117