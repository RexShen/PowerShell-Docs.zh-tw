---
title: "MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法"
ms.date: 2016-05-16
keywords: "PowerShell，DSC"
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 771a9c7b50aba26f89dbf6b24eb3df67bafeac0a
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法

將設定復原回先前的版本。

<a name="syntax"></a>語法
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a>參數
----------

*configurationNumber* \[in\]  
指定要求的設定。 

## <a name="return-value"></a>傳回值
------------

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求
------------
>**MOF：**DscCore.mof

>**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>另請參閱


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 



