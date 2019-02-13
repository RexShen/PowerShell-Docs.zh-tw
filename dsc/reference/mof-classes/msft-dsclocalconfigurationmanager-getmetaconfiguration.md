---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 GetMetaConfiguration 方法
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676921"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 類別的 GetMetaConfiguration 方法

取得用於控制設定代理程式的本機設定管理員設定。

## <a name="syntax"></a>語法

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a>參數

*MetaConfiguration* \[out\] 傳回時，包含定義設定之 **MSFT_DSCMetaConfiguration** 類別的內嵌執行個體。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF：** DscCore.mof

**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)