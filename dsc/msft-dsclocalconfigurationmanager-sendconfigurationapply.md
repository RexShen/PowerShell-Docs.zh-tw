---
title: "MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApply 方法"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: 701063dfa37fe4ba8b014cadadd10339b7fd1bf7

---


# MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApply 方法

將設定文件傳送到受管理的節點，並使用設定代理程式套用設定。

語法
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

參數
----------

*ConfigurationData* \[in\]  
設定的環境資料。

*force* \[in\]  
**true** 表示強制停止該設定。

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


