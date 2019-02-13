---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 SendMetaConfigurationApply 方法
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679145"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 類別的 SendMetaConfigurationApply 方法

設定用於控制設定代理程式的本機設定管理員設定。

## <a name="syntax"></a>語法

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a>參數

*ConfigurationData* \[in\] 設定的環境資料。

*force* \[in\] **true** 表示強制停止該設定。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF：** DscCore.mof

**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)