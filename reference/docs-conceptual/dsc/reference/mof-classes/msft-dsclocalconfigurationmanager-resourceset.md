---
ms.date: 07/17/2020
keywords: dsc,powershell,設定,安裝
title: ResourceSet 方法
ms.openlocfilehash: c015960b2a5ffca0d28b714d571aa616400555bd
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464041"
---
# <a name="resourceset-method"></a>ResourceSet 方法

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

**ResourceType** \[in\] 要呼叫的資源名稱。

**ModuleName** \[in\] 包含要呼叫之資源的模組名稱。

**resourceProperty** \[in\] 在雜湊表中指定資源的屬性名稱與其值，分別作為機碼與值。 使用 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) Cmdlet，探索資源的屬性和其類型。

**RebootRequired** \[out\] 傳回時，如果需要將目標節點重新開機，這個屬性會設定為 **true**。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF**：DscCore.mof

**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
