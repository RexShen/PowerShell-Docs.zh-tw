

# MSFT_DSCLocalConfigurationManager 類別

本機設定管理員 (LCM) 可控制設定檔的狀態，並會使用設定代理程式套用設定。

下列語法已經過受管理物件格式 (MOF) 程式碼簡化，並包含所有已繼承的屬性。

## 語法
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## 成員
-------

**MSFT_DSCLocalConfigurationManager** 類別有以下成員：

-   [方法][]

### 方法

**MSFT_DSCLocalConfigurationManager** 類別有這些方法。

|方法 |描述 |
|:--- |:---|
| [ApplyConfiguration](msft-dsclocalconfigurationmanager-applyconfiguration.md)| 使用設定代理程式套用擱置中的設定。| 
| [DisableDebugConfiguration](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| 停用 DSC 資源偵錯。| 
| [EnableDebugConfiguration](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| 啟用 DSC 資源偵錯。| 
| [GetConfiguration](msft-dsclocalconfigurationmanager-getconfiguration.md)| 將設定文件傳送到受管理的節點，並使用設定代理程式的 **Get** 方法來套用設定。| 
| [GetConfigurationResultOutput](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| 取得與特定工作相關的設定代理程式輸出。| 
| [GetConfigurationStatus](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| 取得設定狀態歷程記錄。| 
| [GetMetaConfiguration](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| 取得用於控制設定代理程式的 LCM 設定。| 
| [PerformRequiredConfigurationChecks](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| 開始一致性檢查。| 
| [RemoveConfiguration](msft-dsclocalconfigurationmanager-removeconfiguration.md)| 移除設定檔。| 
| [ResourceGet](msft-dsclocalconfigurationmanager-resourceget.md)| 直接呼叫 DSC 資源的 **Get** 方法。| 
| [ResourceSet](msft-dsclocalconfigurationmanager-resourceset.md)| 直接呼叫 DSC 資源的 **Set** 方法。| 
| [ResourceTest](msft-dsclocalconfigurationmanager-resourcetest.md)| 直接呼叫 DSC 資源的 **Test** 方法。| 
| [復原](msft-dsclocalconfigurationmanager-rollback.md)| 復原回先前的設定。| 
| [SendConfiguration](msft-dsclocalconfigurationmanager-sendconfiguration.md)| 將設定文件傳送到受管理的節點，並將其儲存為擱置中。將設定文件傳送到受管理的節點，並將其儲存為擱置變更。| 
| [SendConfigurationApply](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| 將設定文件傳送到受管理的節點，並使用設定代理程式套用設定。| 
| [SendConfigurationApplyAsync](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| 將設定文件傳送到受管理的節點，並開始使用設定代理程式套用設定。 使用 GetConfigurationResultOutput 來擷取結果輸出。| 
| [SendMetaConfigurationApply](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| 設定用於控制設定代理程式的 LCM 設定。| 
| [StopConfiguration](msft-dsclocalconfigurationmanager-stopconfiguration.md)| 停止進行中的設定。| 
| [TestConfiguration](msft-dsclocalconfigurationmanager-testconfiguration.md)| 將設定文件傳送到受管理的節點，並對文件驗證目前的設定。| 



 

## 需求
------------
>**MOF：**DscCore.mof

>**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration



 

 





<!--HONumber=Apr16_HO2-->


