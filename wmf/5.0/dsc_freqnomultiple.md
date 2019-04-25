---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 23a5c8832f7c2888880a1ee846d75feaa95ebe47
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058398"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="164ef-102">RefreshMode 和 ConfigurationMode 的頻率不需要是彼此的倍數</span><span class="sxs-lookup"><span data-stu-id="164ef-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="164ef-103">在 DSC 先前的版本中，LCM 會將 `RefreshFrequencyMins` 和 `ConfigurationModeFrequencyMins` 視為彼此的倍數。</span><span class="sxs-lookup"><span data-stu-id="164ef-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="164ef-104">WMF 5.0 RTM 中這些屬性會彼此獨立的進行處理。</span><span class="sxs-lookup"><span data-stu-id="164ef-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="164ef-105">如需詳細資訊，請參閱[設定本機設定管理員](https://msdn.microsoft.com/powershell/dsc/metaconfig)。</span><span class="sxs-lookup"><span data-stu-id="164ef-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
