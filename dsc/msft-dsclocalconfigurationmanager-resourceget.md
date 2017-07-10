---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 ResourceGet 方法"
ms.openlocfilehash: 7d8b185c49778253dcb4e983ad948775c4cb0842
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="resourceget-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# MSFT_DSCLocalConfigurationManager 類別的 ResourceGet 方法

直接呼叫 DSC 資源的 **Get** 方法。

<a id="syntax" class="xliff"></a>
語法
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a id="parameters" class="xliff"></a>
參數
----------

*ResourceType* \[in\]  
要呼叫的資源名稱。

*ModuleName* \[in\]  
包含要呼叫之資源的模組名稱。

*resourceProperty* \[in\]  
在雜湊表中指定資源的屬性名稱與其值，分別作為索引鍵和值。 使用 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) Cmdlet，探索資源的屬性和其類型。

*configurations* \[out\]  
傳回時，包含設定的內嵌執行個體。

<a id="return-value" class="xliff"></a>
## 傳回值
------------

若成功即傳回零；否則傳回錯誤碼。

<a id="remarks" class="xliff"></a>
## 備註

此為靜態方法。

<a id="requirements" class="xliff"></a>
## 需求
------------
>**MOF：**DscCore.mof

>**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration


<a id="see-also" class="xliff"></a>
## 另請參閱


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 



