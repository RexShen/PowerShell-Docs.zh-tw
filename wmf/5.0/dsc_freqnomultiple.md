---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: e1faf71436c8ba0ae02a166ce06d03de9f66f094
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="eeb50-102">RefreshMode 和 ConfigurationMode 的頻率不需要是彼此的倍數</span><span class="sxs-lookup"><span data-stu-id="eeb50-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="eeb50-103">在 DSC 先前的版本中，LCM 會將 `RefreshFrequencyMins` 和 `ConfigurationModeFrequencyMins` 視為彼此的倍數。</span><span class="sxs-lookup"><span data-stu-id="eeb50-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="eeb50-104">WMF 5.0 RTM 中這些屬性會彼此獨立的進行處理。</span><span class="sxs-lookup"><span data-stu-id="eeb50-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="eeb50-105">如需詳細資訊，請參閱[設定本機設定管理員](https://msdn.microsoft.com/powershell/dsc/metaconfig)。</span><span class="sxs-lookup"><span data-stu-id="eeb50-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>