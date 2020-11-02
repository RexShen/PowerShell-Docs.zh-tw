---
ms.date: 07/17/2020
ms.topic: reference
title: StopConfiguration 方法
description: StopConfiguration 方法
ms.openlocfilehash: 854c0dbe8554c08413735a5a7bc872776e0b0a6c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644630"
---
# <a name="stopconfiguration-method"></a>StopConfiguration 方法

停止進行中的設定變更。

## <a name="syntax"></a>語法

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>參數

**force** \[in\] **true** 表示強制停止該設定。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF** ：DscCore.mof

**命名空間** ：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
