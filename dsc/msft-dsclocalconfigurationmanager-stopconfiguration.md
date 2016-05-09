---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '停止進行中的設定。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_stopconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 類別的 StopConfiguration 方法'
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


 

 





<!--HONumber=Apr16_HO2-->


