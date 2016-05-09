---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '復原回先前的設定。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_rollback'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法'
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


 

 





<!--HONumber=Apr16_HO2-->


