---
title: "MSFT_DSCLocalConfigurationManager 類別的 StopConfiguration 方法"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: 9721486cca6f94d6b156c6ee1992eced6652c123

---

# MSFT_DSCLocalConfigurationManager 類別的 StopConfiguration 方法

停止進行中的設定變更。

語法
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

參數
----------

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


