---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: SendMetaConfigurationApply 方法
ms.openlocfilehash: b2e420bafb8ea22aea43800f6e429d3ed785d1e8
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954875"
---
# <a name="sendmetaconfigurationapply-method"></a>SendMetaConfigurationApply 方法

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

**MOF**：DscCore.mof

**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
