---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: 587f3f592f4aab53c95bbc6d37ea37d7f2364aec
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="updates-to-fileinfo-object"></a><span data-ttu-id="e8397-102">FileInfo 物件的更新</span><span class="sxs-lookup"><span data-stu-id="e8397-102">Updates to FileInfo object</span></span>
<span data-ttu-id="e8397-103">檔案版本資訊可能會產生誤導，尤其是在已修補檔案的情況下。</span><span class="sxs-lookup"><span data-stu-id="e8397-103">File version information can be misleading, particularly in cases where the file was patched.</span></span> <span data-ttu-id="e8397-104">這一版的 WMF 5.0 將新的 **FileVersionRaw** 和 **ProductVersionRaw** 指令碼屬性加入 FileInfo 物件中。</span><span class="sxs-lookup"><span data-stu-id="e8397-104">This release of WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to FileInfo objects.</span></span> <span data-ttu-id="e8397-105">此處是為 powershell.exe 顯示的屬性 (假設 $pid 是 PowerShell 處理程序的識別碼) ︰</span><span class="sxs-lookup"><span data-stu-id="e8397-105">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117

