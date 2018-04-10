---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: a565f2befddc32f5088fa3e158f58d2dd78d41b4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>DSC 資源的並行模組版本管理支援

包含 DSC 資源的模組可以並行安裝，且 DSC 設定可以使用安裝於系統上的特定資源版本。

如需詳細資訊，請參閱[使用多個版本的資源](https://msdn.microsoft.com/powershell/dsc/sxsresource)。

## <a name="known-issues"></a>已知問題

下列為此版本中已知的並行安裝問題︰

-   不支援在相同設定中使用兩個不同的 DSC 資源版本。