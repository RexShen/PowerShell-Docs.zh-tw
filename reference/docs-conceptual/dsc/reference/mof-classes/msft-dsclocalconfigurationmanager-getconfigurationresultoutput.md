---
ms.date: 07/17/2020
ms.topic: reference
title: GetConfigurationResultOutput 方法
description: GetConfigurationResultOutput 方法
ms.openlocfilehash: 7c885109b3078189b7ac653733a5fb24db66312e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644716"
---
# <a name="getconfigurationresultoutput-method"></a>GetConfigurationResultOutput 方法

擷取與特定工作相關聯的設定代理程式輸出。

## <a name="syntax"></a>語法

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a>參數

**jobId** \[in\] 要取得輸出資料之作業的識別碼。

**resumeOutputBookmark** \[in\] 指定輸出應該接續前一個書籤。

**output** \[out\] 指定之工作的輸出。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF** ：DscCore.mof

**命名空間** ：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
