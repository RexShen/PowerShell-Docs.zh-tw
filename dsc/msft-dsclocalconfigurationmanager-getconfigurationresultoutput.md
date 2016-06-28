---
title: "MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationResultOutput 方法"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: 8f13964dfbbe1cd827c58232a35d1cbacddeed1b

---

# MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationResultOutput 方法

擷取與特定工作相關聯的設定代理程式輸出。

語法
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

參數
----------

*jobId* \[in\]  
取得輸出資料之工作的識別碼。

*resumeOutputBookmark* \[in\]  
指定輸出應該接續前一個書籤。

*output* \[out\]  
所指定之工作的輸出。

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


