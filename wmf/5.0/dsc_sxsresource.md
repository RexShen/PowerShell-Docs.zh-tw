---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 0543afbc72148b1ba713e59655126c069b16ef33
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218428"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>DSC 資源的並行模組版本管理支援

包含 DSC 資源的模組可以並行安裝，且 DSC 設定可以使用安裝於系統上的特定資源版本。

如需詳細資訊，請參閱[使用多個版本的資源](https://msdn.microsoft.com/powershell/dsc/sxsresource)。

## <a name="known-issues"></a>已知問題

下列為此版本中已知的並行安裝問題︰

-   不支援在相同設定中使用兩個不同的 DSC 資源版本。
