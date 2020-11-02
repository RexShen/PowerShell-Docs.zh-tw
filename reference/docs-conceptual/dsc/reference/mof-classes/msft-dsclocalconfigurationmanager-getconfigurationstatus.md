---
ms.date: 07/17/2020
ms.topic: reference
title: GetConfigurationStatus 方法
description: GetConfigurationStatus 方法
ms.openlocfilehash: fe25d17069d9011e931ac50fec27cb9ebafba365
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650857"
---
# <a name="getconfigurationstatus-method"></a>GetConfigurationStatus 方法

取得設定狀態歷程記錄。

## <a name="syntax"></a>語法

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a>參數

**All** \[in\] 若此方法應傳回電腦上所執行所有設定的相關資訊，包括設定應用程式與一致性檢查，即為 **true** 。

**configurationStatus** \[out\] 在傳回時會包含定義設定的 **MSFT_DSCConfigurationStatus** 類別之內嵌執行個體。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF** ：DscCore.mof

**命名空間** ：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
