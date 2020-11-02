---
ms.date: 07/14/2020
ms.topic: reference
title: ApplyConfiguration 方法
description: ApplyConfiguration 方法
ms.openlocfilehash: aa99221b33d39c3ecc70156a11eaee10b540e2dc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664280"
---
# <a name="applyconfiguration-method"></a>ApplyConfiguration 方法

使用設定代理程式套用擱置中的設定。

如果沒有任何擱置中的設定，這個方法會重新套用目前的設定。

## <a name="syntax"></a>語法

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>參數

### <a name="force"></a>force

如果這是 **true** ，就算有擱置中的設定，也會重新套用目前的設定。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF：** DscCore.mof

**Namespace** ：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
