---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: e921a5ead21f52b7e0d9efd9335c44b99d7d6802
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="deliver-a-configuration-document-without-applying" class="xliff"></a>
# 傳遞設定文件，但不套用它

[Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) Cmdlet 將設定 MOF 檔案複製到目標節點，但不會套用此設定。 直到下個一致性階段，或當您執行 [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) Cmdlet 時才會套用此設定。

