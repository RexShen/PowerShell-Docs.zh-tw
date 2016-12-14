---
title: "MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationStatus 方法"
ms.date: 2016-05-16
keywords: "PowerShell，DSC"
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: b430e98c7ec287c0efcf2c2e2736253797242904
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationStatus 方法

取得設定狀態歷程記錄。

<a name="syntax"></a>語法
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a>參數
----------

*All* \[in\]  
若此方法應傳回機器上所執行所有設定的相關資訊，包括設定應用程式與一致性檢查，即為 **true**。

*configurationStatus* \[out\]  
在傳回時會包含定義設定的 **MSFT_DSCConfigurationStatus** 類別之內嵌執行個體。

## <a name="return-value"></a>傳回值
------------

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求
------------
>**MOF：**DscCore.mof

>**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>另請參閱


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 



