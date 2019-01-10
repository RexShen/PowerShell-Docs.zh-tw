---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 ResourceSet 方法
ms.openlocfilehash: 2712b7ff0a19e643c1f343d436c084f8970c9dd4
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047327"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 類別的 ResourceSet 方法

直接呼叫 DSC 資源的 **Set** 方法。

## <a name="syntax"></a>語法

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a>參數

*ResourceType* \[in\] 要呼叫的資源名稱。

*ModuleName* \[in\] 包含要呼叫之資源的模組名稱。

*resourceProperty* \[in\] 在雜湊表中指定資源的屬性名稱與其值，分別作為索引鍵和值。 使用 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) Cmdlet，探索資源的屬性和其類型。

*RebootRequired* \[out\] 傳回時，如果需要重新啟動目標節點，這個屬性會設定為 **true**。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

MOF**DscCore.mof

-NamespaceRoot\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)