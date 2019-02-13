---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 RemoveConfiguration 方法
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676554"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 類別的 RemoveConfiguration 方法

移除設定檔。

## <a name="syntax"></a>語法

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a>參數

*Stage* \[in\] 指定要移除的設定文件。 下列是有效值：

|值 |描述 |
|:--- |:---|
|**1** | **目前的**設定文件 (current.mof)。 |
|**2** | **擱置中的**設定文件 (pending.mof)。  |
|**4** | **之前的**設定文件 (previous.mof)。 |

*Force* \[in\] **true** 表示強制移除設定。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF：** DscCore.mof

**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)