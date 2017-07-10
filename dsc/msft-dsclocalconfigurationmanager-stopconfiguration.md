---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 StopConfiguration 方法"
ms.openlocfilehash: f0b550615b20f07f99c8ed7009805c45794bfe22
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# MSFT_DSCLocalConfigurationManager 類別的 StopConfiguration 方法

停止進行中的設定變更。

<a id="syntax" class="xliff"></a>
語法
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a id="parameters" class="xliff"></a>
參數
----------

*force* \[in\]  
**true** 表示強制停止該設定。

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


 

 



