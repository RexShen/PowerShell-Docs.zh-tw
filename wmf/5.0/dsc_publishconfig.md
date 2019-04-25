---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: db4543b788ad0a5c7aa32706246446533b901d09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085808"
---
# <a name="deliver-a-configuration-document-without-applying"></a>傳遞設定文件，但不套用它

[Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) Cmdlet 將設定 MOF 檔案複製到目標節點，但不會套用此設定。
直到下個一致性階段，或當您執行 [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) Cmdlet 時才會套用此設定。
