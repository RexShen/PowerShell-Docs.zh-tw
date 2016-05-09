---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '取得用於控制設定代理程式的本機設定管理員設定。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getmetaconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 類別的 GetMetaConfiguration 方法'
---

# MSFT_DSCLocalConfigurationManager 類別的 GetMetaConfiguration 方法

取得用於控制設定代理程式的本機設定管理員設定。

語法
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

參數
----------

*MetaConfiguration* \[out\]  
傳回時，包含定義設定之 **MSFT_DSCMetaConfiguration** 類別的內嵌執行個體。

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


