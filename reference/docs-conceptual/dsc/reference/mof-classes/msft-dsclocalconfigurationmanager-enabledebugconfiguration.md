---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: EnableDebugConfiguration 方法
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953435"
---
# <a name="enabledebugconfiguration-method"></a>EnableDebugConfiguration 方法

啟用 DSC 資源偵錯。

## <a name="syntax"></a>語法

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a>參數

*BreakAll* \[in\] 在資源指令碼的每一行中設定中斷點。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF**：DscCore.mof

**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
