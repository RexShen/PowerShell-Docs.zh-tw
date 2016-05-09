---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '擷取與特定工作相關的設定代理程式輸出。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getconfigurationresultoutput'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationResultOutput 方法'
---

# MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationResultOutput 方法

擷取與特定工作相關聯的設定代理程式輸出。

語法
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

參數
----------

*jobID* \[in\]  
取得輸出資料之工作的識別碼。

*resumeOutputBookmark* \[in\]  
指定輸出應該接續前一個書籤。

*output* \[out\]  
所指定之工作的輸出。

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


