---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 ApplyConfiguration 方法"
ms.openlocfilehash: febaf972a2a452eb9aaf3ec7fbc5e41f3f463a58
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# MSFT_DSCLocalConfigurationManager 類別的 ApplyConfiguration 方法

使用設定代理程式套用擱置中的設定。 

如果沒有任何擱置中的設定，這個方法會重新套用目前的設定。


<a id="syntax" class="xliff"></a>
## 語法
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

<a id="parameters" class="xliff"></a>
## 參數
----------

*force* \[in\]  
如果這是 **true**，就算有擱置中的設定，也會重新套用目前的設定。

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

 

 



