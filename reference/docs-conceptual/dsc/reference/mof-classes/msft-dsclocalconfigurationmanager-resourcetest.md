---
ms.date: 07/17/2020
ms.topic: reference
title: ResourceTest 方法
description: ResourceTest 方法
ms.openlocfilehash: cbac53ea96a59ec92fa840f75cd264a3125b965a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650668"
---
# <a name="resourcetest-method"></a>ResourceTest 方法

直接呼叫 DSC 資源的 **Test** 方法。

## <a name="syntax"></a>語法

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a>參數

**ResourceType** \[in\] 要呼叫的資源名稱。

**ModuleName** \[in\] 包含要呼叫之資源的模組名稱。

**_resourceProperty_* \[in\] 在雜湊表中將資源的屬性名稱與其值分別指定為機碼與值。 使用 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) Cmdlet，探索資源的屬性和其類型。

*InDesiredState** \[out\] 傳回時，如果目標節點是想要的狀態，則這個屬性會設定為 **true** 。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF** ：DscCore.mof

**命名空間** ：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
