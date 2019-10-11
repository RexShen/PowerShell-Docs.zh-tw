---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: TestConfiguration 方法
ms.openlocfilehash: 384134212e3b29b63dc045aee4b708c87c970302
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954865"
---
# <a name="testconfiguration-method"></a>TestConfiguration 方法

將設定文件傳送到受管理的節點，並對文件驗證目前的設定。

## <a name="syntax"></a>語法

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a>參數

*configurationData* \[in\] 設定的環境資料。

*InDesiredState* \[out\] 傳回時，指定受控節點是否為設定文件所指定的狀態。

*ResourcesInDesiredState* \[out\] 傳回時，包含指定資源為所需狀態之 **MSFT_ResourceInDesiredState** 類別的內嵌執行個體。

*ResourcesNotInDesiredState* \[out\] 傳回時，包含指定資源不為所需狀態之 **MSFT_ResourceNotInDesiredState** 類別的內嵌執行個體。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF**：DscCore.mof

**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
