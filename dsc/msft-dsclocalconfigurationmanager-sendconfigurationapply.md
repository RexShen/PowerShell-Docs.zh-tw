---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '將設定文件傳送到受管理的節點，並使用設定代理程式套用設定。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_sendconfigurationapply'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApply 方法'
---

# MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApply 方法

將設定文件傳送到受管理的節點，並使用設定代理程式套用設定。

語法
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

參數
----------

*ConfigurationData* \[in\]  
設定的環境資料。

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


