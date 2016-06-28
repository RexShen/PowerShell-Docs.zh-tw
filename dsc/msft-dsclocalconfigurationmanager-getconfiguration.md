---
title: "MSFT_DSCLocalConfigurationManager 類別的 GetConfiguration 方法"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 919438862ca9786447b690d2db10e905da0a7c42
ms.openlocfilehash: 19d4790f22491e0bb11de1e315d1ee3b07929d55

---

# MSFT_DSCLocalConfigurationManager 類別的 GetConfiguration 方法

將設定文件傳送到受管理的節點，並使用設定代理程式的 **Get** 方法來套用設定。

語法
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

參數
----------

*configurationData* \[in\]  
指定要傳送的設定資料。

*configurations* \[out\]  
傳回時，包含設定的內嵌執行個體。

## 傳回值
------------

若成功即傳回零；否則傳回錯誤碼。

## 備註

此為靜態方法。

## 需求
------------
>**MOF：**DscCore.mof

>**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration


## 另請參閱


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
 

 






<!--HONumber=Jun16_HO4-->


