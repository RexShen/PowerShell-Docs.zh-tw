---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DisableDebugConfiguration 方法
ms.openlocfilehash: e3eab98c734b3fd1593ceb2b5d4b40fa69a3bf97
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71955055"
---
# <a name="disabledebugconfiguration-method"></a>DisableDebugConfiguration 方法

停用 DSC 資源偵錯。

## <a name="syntax"></a>語法

```mof
uint32 DisableDebugConfiguration();
```

## <a name="parameters"></a>參數

這個方法沒有任何參數。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF**：DscCore.mof

**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
