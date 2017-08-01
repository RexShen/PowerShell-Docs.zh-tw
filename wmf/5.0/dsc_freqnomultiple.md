---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: 30055cff87159df98029e25409782e0fe2f0bae4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>RefreshMode 和 ConfigurationMode 的頻率不需要是彼此的倍數

在 DSC 先前的版本中，LCM 會將 `RefreshFrequencyMins` 和 `ConfigurationModeFrequencyMins` 視為彼此的倍數。 WMF 5.0 RTM 中這些屬性會彼此獨立的進行處理。 

如需詳細資訊，請參閱[設定本機設定管理員](https://msdn.microsoft.com/powershell/dsc/metaconfig)。

