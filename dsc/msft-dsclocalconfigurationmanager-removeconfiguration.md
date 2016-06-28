---
title: "MSFT_DSCLocalConfigurationManager 類別的 RemoveConfiguration 方法"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: 4f3d74949d98e3ab3f5136303e229c23ed903c5d

---

# MSFT_DSCLocalConfigurationManager 類別的 RemoveConfiguration 方法

移除設定檔。

語法
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

參數
----------

*Stage* \[in\]  
指定要移除的設定文件。 下列是有效值：

|值 |描述 |
|:--- |:---|
|**1** | **目前的**設定文件 (current.mof)。 |
|**2** | **擱置中的**設定文件 (pending.mof)。  |
|**4** | **之前的**設定文件 (previous.mof)。 |

*Force* \[in\]  
**true** 表示強制移除設定。

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


