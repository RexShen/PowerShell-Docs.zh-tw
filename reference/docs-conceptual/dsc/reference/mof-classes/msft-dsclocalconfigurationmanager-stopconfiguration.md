---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: StopConfiguration 方法
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953355"
---
# <a name="stopconfiguration-method"></a>StopConfiguration 方法

停止進行中的設定變更。

## <a name="syntax"></a>語法

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>參數

*force* \[in\] **true** 表示強制停止該設定。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF**：DscCore.mof

**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
