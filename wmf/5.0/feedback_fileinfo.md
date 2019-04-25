---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 5280ef5ff95679dc8721be8f5f81031a4ffe796f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085232"
---
# <a name="updates-to-fileinfo-object"></a>FileInfo 物件的更新
檔案版本資訊可能會產生誤導，尤其是在已修補檔案的情況下。 這一版的 WMF 5.0 將新的 **FileVersionRaw** 和 **ProductVersionRaw** 指令碼屬性加入 FileInfo 物件中。 此處是為 powershell.exe 顯示的屬性 (假設 $pid 是 PowerShell 處理程序的識別碼) ︰

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
