---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '開始一致性檢查。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_performrequiredconfigurationchecks'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 類別的 PerformRequiredConfigurationChecks 方法'
---

# MSFT_DSCLocalConfigurationManager 類別的 PerformRequiredConfigurationChecks 方法

使用工作排程器開始一致性檢查。

語法
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

參數
----------

*Flags* \[in\]  
位元遮罩，指定要執行的一致性檢查類型。 下列值有效，且可以透過位元 **OR** 運算進行結合︰

|值 |描述 |
|:--- |:---|
|**1** | 標準的一致性檢查。 |
|**2** | 重新開機後持續的一致性檢查。 此值不應與其他值結合。 |
|**4** | 應從節點中繼設定中所指定的提取伺服器，提取設定。 此值應一律使用 **5** 的值和 **1** 結合。 |
|**8** | 將狀態傳送到報表伺服器。 |

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


