---
ms.date: 07/14/2020
keywords: dsc,powershell,設定,安裝
title: DisableDebugConfiguration 方法
ms.openlocfilehash: 52d55ff6b1fd126482bbaa9480efc131ab2f100c
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463749"
---
# <a name="disabledebugconfiguration-method"></a>DisableDebugConfiguration 方法

停用 DSC 資源偵錯。

## <a name="syntax"></a>語法

```mof
uint32 DisableDebugConfiguration();
```

## <a name="parameters"></a>參數

這個方法沒有任何參數。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF：** DscCore.mof

**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
