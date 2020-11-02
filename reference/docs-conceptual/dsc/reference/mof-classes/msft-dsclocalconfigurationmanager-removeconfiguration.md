---
ms.date: 07/17/2020
ms.topic: reference
title: RemoveConfiguration 方法
description: RemoveConfiguration 方法
ms.openlocfilehash: d5988ac014c457407c56a097c9a376427376eb3f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650725"
---
# <a name="removeconfiguration-method"></a>RemoveConfiguration 方法

移除設定檔。

## <a name="syntax"></a>語法

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a>參數

**Stage** \[in\] 指定要移除的設定文件。 下列是有效值：

|值 |描述 |
|:--- |:---|
|**1** | **目前的** 設定文件 (current.mof)。 |
|**2** | **擱置中的** 設定文件 (pending.mof)。  |
|**4** | **之前的** 設定文件 (previous.mof)。 |

*Force* \[in\] **true** 表示強制移除設定。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF** ：DscCore.mof

**命名空間** ：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
