
# MSFT_DSCLocalConfigurationManager 類別的 ApplyConfiguration 方法

使用設定代理程式套用擱置中的設定。 

如果沒有任何擱置中的設定，這個方法會重新套用目前的設定。


## 語法
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## 參數
----------

*force* \[in\]  
如果這是 **true**，就算有擱置中的設定，也會重新套用目前的設定。

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


