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
ms.openlocfilehash: 864372bfb0f43922f6066ff3db19956a7942db49
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811357"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>如何設定 HelpInfo XML 版本號碼

本主題說明如何在可更新的說明資訊檔案（通常稱為「HelpInfo XML 檔案」）中設定並增加版本號碼。

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>如何設定 HelpInfo XML 版本號碼

HelpInfo XML 檔案中的版本號碼對於「可更新的說明」作業而言是不可或缺的。
只有當遠端 HelpInfo XML 檔案中 UI 文化特性的版本號碼大於本機 HelpInfo XML 中該 UI 文化特性的版本號碼，或沒有本機 HelpInfo XML 檔案時， [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)和[get-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlet 才會下載新的說明檔。

HelpInfo XML 檔案會使用 Microsoft .NET Framework 的**system.object**類別中定義的4部分版本號碼。 格式為 `N1.N2.N3.N4`。 模組作者可以使用**System. version**類別所允許的任何版本編號配置。 「可更新的說明」只需要在該 UI 文化特性的新版 CAB 檔案上傳到 HelpInfo XML 檔案中的**HelpContentURI**元素所指定的位置時，才會增加 ui 文化特性的版本號碼。

下列範例顯示在2.15.0.10 版本時，德文（de） UI 文化特性的 HelpInfo XML 檔案元素。

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

UI 文化特性的版本號碼會反映該 UI 文化特性的 CAB 檔案版本。 版本號碼會套用至整個 CAB 檔案。 您無法為 CAB 檔案中的不同檔案設定不同的版本號碼。 每個 UI 文化特性的版本號碼會獨立評估，而且不需要與模組支援之其他 UI 文化特性的版本號碼相關。
