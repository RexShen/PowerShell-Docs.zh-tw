---
ms.date: 07/17/2020
ms.topic: reference
title: ResourceGet 方法
description: ResourceGet 方法
ms.openlocfilehash: bff737f04e02740fa09fd82d7b27c75b11303dad
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650757"
---
# <a name="resourceget-method"></a>ResourceGet 方法

直接呼叫 DSC 資源的 **Get** 方法。

## <a name="syntax"></a>語法

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a>參數

**ResourceType** \[in\] 要呼叫的資源名稱。

**ModuleName** \[in\] 包含要呼叫之資源的模組名稱。

**resourceProperty** \[in\] 在雜湊表中指定資源的屬性名稱與其值，分別作為機碼與值。 使用 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) Cmdlet，探索資源的屬性和其類型。

**configurations** \[out\] 傳回時，包含設定的內嵌執行個體。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF** ：DscCore.mof

**命名空間** ：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
