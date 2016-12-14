---
title: "MSFT_DSCLocalConfigurationManager 類別的 GetConfiguration 方法"
ms.date: 2016-05-16
keywords: "PowerShell，DSC"
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 19d4790f22491e0bb11de1e315d1ee3b07929d55
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 類別的 GetConfiguration 方法

將設定文件傳送到受管理的節點，並使用設定代理程式的 **Get** 方法來套用設定。

<a name="syntax"></a>語法
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a>參數
----------

*ConfigurationData* \[in\]  
指定要傳送的設定資料。

*configurations* \[out\]  
傳回時，包含設定的內嵌執行個體。

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
 

 



