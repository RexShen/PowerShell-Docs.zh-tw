---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法"
ms.openlocfilehash: b8597e3eb7872d9894863fb02d927c9f475da44c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="rollback-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法

將設定復原回先前的版本。

<a id="syntax" class="xliff"></a>
語法
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a id="parameters" class="xliff"></a>
參數
----------

*configurationNumber* \[in\]  
指定要求的設定。 

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


 

 



