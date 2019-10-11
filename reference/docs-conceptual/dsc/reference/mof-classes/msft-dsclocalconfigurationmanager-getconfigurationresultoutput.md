---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: GetConfigurationResultOutput 方法
ms.openlocfilehash: 480e710ce1a208253f0e664474c3e9bab296066a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953415"
---
# <a name="getconfigurationresultoutput-method"></a>GetConfigurationResultOutput 方法

擷取與特定工作相關聯的設定代理程式輸出。

## <a name="syntax"></a>語法

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a>參數

*jobId* \[in\] 取得輸出資料之工作的識別碼。

*resumeOutputBookmark* \[in\] 指定輸出應該接續前一個書籤。

*output* \[out\] 指定之工作的輸出。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF**：DscCore.mof

**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
