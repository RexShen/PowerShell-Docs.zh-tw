---
title:  MSFT_DSCLocalConfigurationManager 類別的 ResourceTest 方法
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---


# MSFT_DSCLocalConfigurationManager 類別的 ResourceTest 方法

直接呼叫 DSC 資源的 **Test** 方法。

語法
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

參數
----------

*ResourceType* \[in\]  
要呼叫的資源名稱。

*ModuleName* \[in\]  
包含要呼叫之資源的模組名稱。

*resourceProperty* \[in\]  
在雜湊表中指定資源的屬性名稱與其值，分別作為索引鍵和值。 使用 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) Cmdlet，探索資源的屬性和其類型。

*InDesiredState* \[out\]  
傳回時，如果目標節點是想要的狀態，這個屬性會設定為 **true**。

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


 

 





<!--HONumber=May16_HO3-->


