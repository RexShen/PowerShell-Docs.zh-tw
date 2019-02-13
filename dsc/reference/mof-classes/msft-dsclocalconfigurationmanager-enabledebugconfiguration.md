---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 EnableDebugConfiguration 方法
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676683"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 類別的 EnableDebugConfiguration 方法

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

**MOF：** DscCore.mof

**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)