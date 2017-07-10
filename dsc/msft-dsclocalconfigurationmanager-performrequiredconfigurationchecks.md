---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 PerformRequiredConfigurationChecks 方法"
ms.openlocfilehash: 26110b3920104da7343b8d55cf63440c12accbbc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# MSFT_DSCLocalConfigurationManager 類別的 PerformRequiredConfigurationChecks 方法

使用工作排程器開始一致性檢查。

<a id="syntax" class="xliff"></a>
語法
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a id="parameters" class="xliff"></a>
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


 

 



