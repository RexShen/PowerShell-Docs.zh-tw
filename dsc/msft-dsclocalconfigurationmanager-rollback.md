---
title: "MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: 771a9c7b50aba26f89dbf6b24eb3df67bafeac0a

---


# MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法

將設定復原回先前的版本。

語法
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

參數
----------

*configurationNumber* \[in\]  
指定要求的設定。 

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


