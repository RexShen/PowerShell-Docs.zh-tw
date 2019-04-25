---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: a1e90a0b96f74decb55343292b97befaf1a85f8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058109"
---
# <a name="class-based-dsc-resources"></a>以類別為基礎的 DSC 資源

## <a name="defining-dsc-resources-with-classes"></a>以類別定義 DSC 資源

根據意見反應，我們讓撰寫以類別為基礎的 DSC 資源更簡單且更容易了解。
以類別為基礎的 DSC 資源和 Cmdlet DSC 資源提供者之間的主要差異如下︰

* 不需要結構描述的 MOF 檔案。
* 不需要模組資料夾中的 **DSCResource** 子資料夾。
* PowerShell 模組檔案可以包含多個 DSC 資源類別。

如需詳細資訊，請參閱[使用 PowerShell 類別撰寫自訂 DSC 資源](https://msdn.microsoft.com/powershell/dsc/authoringresource)。
