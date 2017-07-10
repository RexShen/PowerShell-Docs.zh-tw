---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 GetMetaConfiguration 方法"
ms.openlocfilehash: 4f209014e9fde5841a9bce743f5364e6677d1e41
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# MSFT_DSCLocalConfigurationManager 類別的 GetMetaConfiguration 方法

取得用於控制設定代理程式的本機設定管理員設定。

<a id="syntax" class="xliff"></a>
語法
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a id="parameters" class="xliff"></a>
參數
----------

*MetaConfiguration* \[out\]  
傳回時，包含定義設定之 **MSFT_DSCMetaConfiguration** 類別的內嵌執行個體。

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


 

 



