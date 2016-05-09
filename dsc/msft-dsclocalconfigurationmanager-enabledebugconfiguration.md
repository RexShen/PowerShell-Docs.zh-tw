---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '啟用偵錯 DSC 設定。'
MS-HAID: 'cimwin32a.msft\_dsclocalconfigurationmanager\_enabledebugconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 類別的 EnableDebugConfiguration 方法'
---

# MSFT_DSCLocalConfigurationManager 類別的 EnableDebugConfiguration 方法

啟用 DSC 資源偵錯。

語法
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

參數
----------

*BreakAll* \[in\]  
在資源指令碼的每一行中設定中斷點。

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


