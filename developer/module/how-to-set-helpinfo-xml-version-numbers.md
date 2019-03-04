---
title: 如何設定 HelpInfo XML 版本號碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: 4929a5b1c9f73bb12b6df975e03fc529db3565ef
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863314"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>如何設定 HelpInfo XML 版本號碼

本主題說明如何設定及增加版本號碼，在可更新的說明資訊檔案中，通常稱為 「 HelpInfo XML 檔案 」。

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>如何設定 HelpInfo XML 版本號碼

HelpInfo XML 檔案中的版本號碼操作是很重要的可更新的說明。 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)並[Save-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 在遠端 HelpInfo XML 檔案中的 UI 文化特性的版本號碼大於該 UI 文化特性的版本號碼時，才下載新的說明檔本機 HelpInfo XML，或沒有本機 HelpInfo XML 檔案。
HelpInfo XML 檔案中的版本號碼操作是很重要的可更新的說明。 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)並[Save-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 在遠端 HelpInfo XML 檔案中的 UI 文化特性的版本號碼大於該 UI 文化特性的版本號碼時，才下載新的說明檔本機 HelpInfo XML，或沒有本機 HelpInfo XML 檔案。

HelpInfo XML 檔案會使用定義於 4 部分版本號碼**System.Version**的 Microsoft.NET Framework 類別。 格式是`N1.N2.N3.N4`。 模組作者可以使用編號配置所允許的任何版本**System.Version**類別。 可更新的說明，只有版本號碼 UI 文化特性增加時需要新版的 UI 文化特性的 CAB 檔案上傳至所指定的位置**HelpContentURI** HelpInfo XML 檔案中的項目。

下列範例顯示德文 (DE-DE) UI 文化特性的版本時 2.15.0.10 HelpInfo XML 檔案的項目。

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

UI 文化特性的版本號碼會反映該 UI 文化特性的 CAB 檔案的版本。 版本號碼套用到整個封包檔。 您無法在封包檔中設定不同的版本號碼不同的檔案。 版本號碼，每個 UI 文化特性獨立進行評估，並不需要與相關的其他模組支援的 UI 文化特性的版本號碼。