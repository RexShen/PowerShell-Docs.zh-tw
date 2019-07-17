---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: ApplyConfiguration 方法
ms.openlocfilehash: 0425b9a7db37e421830ba37da8f5c0a4877a1b72
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727172"
---
# <a name="applyconfiguration-method"></a>ApplyConfiguration 方法

使用設定代理程式套用擱置中的設定。

如果沒有任何擱置中的設定，這個方法會重新套用目前的設定。

## <a name="syntax"></a>語法

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>參數

*force* \[in\] 如果這是 **true**，就算有擱置中的設定，也會重新套用目前的設定。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF**：DscCore.mof

**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
