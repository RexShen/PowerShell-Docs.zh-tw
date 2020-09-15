---
ms.date: 07/17/2020
keywords: dsc,powershell,設定,安裝
title: GetMetaConfiguration 方法
ms.openlocfilehash: 5111cb3b15e0fba0bf71b412580efdd3cd95b2dc
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463970"
---
# <a name="getmetaconfiguration-method"></a>GetMetaConfiguration 方法

取得用於控制設定代理程式的本機設定管理員設定。

## <a name="syntax"></a>語法

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a>參數

**MetaConfiguration** \[out\] 傳回時，包含定義設定之 **MSFT_DSCMetaConfiguration** 類別的內嵌執行個體。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF**：DscCore.mof

**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
