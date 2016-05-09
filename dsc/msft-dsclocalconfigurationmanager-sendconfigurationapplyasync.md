---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '將設定文件傳送到受管理的節點，並開始使用設定代理程式套用設定。 使用 GetConfigurationResultOutput 來擷取結果輸出。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_sendconfigurationapplyasync'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApplyAsync 方法'
---

# MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApplyAsync 方法

將設定文件非同步地傳送到受管理的節點，並使用設定代理程式套用設定。

語法
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

參數
----------

*ConfigurationData* \[in\]  
設定的環境資料。

*force* \[in\]  
**true** 表示強制停止該設定。

*jobID* \[in\]  
傳送設定之工作的識別碼。

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


