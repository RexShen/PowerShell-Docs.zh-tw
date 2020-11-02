---
ms.date: 07/17/2020
ms.topic: reference
title: TestConfiguration 方法
description: TestConfiguration 方法
ms.openlocfilehash: ed26fcad2286ca753fb4b1845b8c6ad0741d491b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648922"
---
# <a name="testconfiguration-method"></a>TestConfiguration 方法

將設定文件傳送到受管理的節點，並對文件驗證目前的設定。

## <a name="syntax"></a>語法

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a>參數

**configurationData** \[in\] 組態的環境資料。

**InDesiredState** \[out\] 傳回時，指定受控節點是否為設定文件所指定的狀態。

**ResourcesInDesiredState** \[out\] 傳回時，包含指定資源為所需狀態之 **MSFT_ResourceInDesiredState** 類別的內嵌執行個體。

**ResourcesNotInDesiredState** \[out\] 傳回時，包含指定資源不為所需狀態之 **MSFT_ResourceNotInDesiredState** 類別的內嵌執行個體。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF** ：DscCore.mof

**命名空間** ：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
