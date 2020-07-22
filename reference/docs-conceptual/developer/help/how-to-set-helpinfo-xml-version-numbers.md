---
title: 如何設定 HelpInfo XML 版本號碼
ms.date: 09/12/2016
ms.openlocfilehash: 42164f98414da0b6f1a0021e9d860c57a63a9eec
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892977"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>如何設定 HelpInfo XML 版本號碼

本主題說明如何在可更新的說明資訊檔案（通常稱為「HelpInfo XML 檔案」）中設定並增加版本號碼。

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>如何設定 HelpInfo XML 版本號碼

HelpInfo XML 檔案中的版本號碼對於「可更新的說明」作業而言是不可或缺的。 只有當遠端 HelpInfo XML 檔案中 UI 文化特性的版本號碼大於本機 HelpInfo XML 中該 UI 文化特性的版本號碼，或沒有本機 HelpInfo XML 檔案時， [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)和[get-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlet 才會下載新的說明檔。

HelpInfo XML 檔案會使用 Microsoft .NET Framework 的**system.object**類別中定義的4部分版本號碼。 格式為 `N1.N2.N3.N4`。 模組作者可以使用**System. version**類別所允許的任何版本編號配置。 「可更新的說明」只需要在該 UI 文化特性的新版 CAB 檔案上傳到 HelpInfo XML 檔案中的**HelpContentURI**元素所指定的位置時，才會增加 ui 文化特性的版本號碼。

下列範例顯示在2.15.0.10 版本時，德文（de） UI 文化特性的 HelpInfo XML 檔案元素。

```xml
<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

UI 文化特性的版本號碼會反映該 UI 文化特性的 CAB 檔案版本。 版本號碼會套用至整個 CAB 檔案。 您無法為 CAB 檔案中的不同檔案設定不同的版本號碼。 每個 UI 文化特性的版本號碼會獨立評估，而且不需要與模組支援之其他 UI 文化特性的版本號碼相關。
