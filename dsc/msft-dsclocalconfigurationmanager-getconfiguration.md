---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '將設定文件傳送到受管理的節點，並透過 Get 方法使用設定代理程式套用設定。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 類別的 GetConfiguration 方法'
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
 

 





<!--HONumber=Apr16_HO2-->


