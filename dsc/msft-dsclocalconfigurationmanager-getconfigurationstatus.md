---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '取得設定狀態歷程記錄。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getconfigurationstatus'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationStatus 方法'
---

# MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationStatus 方法

取得設定狀態歷程記錄。

語法
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

參數
----------

*All* \[in\]  
為 **true** (如果這個方法應會傳回執行在機器上所有設定的相關資訊，包括
設定應用程式與一致性檢查)。

*configurationStatus* \[out\]  
在傳回時會包含定義設定的 **MSFT_DSCConfigurationStatus** 類別之內嵌執行個體。

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


