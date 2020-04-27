---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: ResourceTest 方法
ms.openlocfilehash: ff06fd645a94055e79aa0f8d20f2f06e16483720
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954945"
---
# <a name="resourcetest-method"></a>ResourceTest 方法

直接呼叫 DSC 資源的 **Test** 方法。

## <a name="syntax"></a>語法

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a>參數

*ResourceType* \[in\] 要呼叫的資源名稱。

*ModuleName* \[in\] 包含要呼叫之資源的模組名稱。

*resourceProperty* \[in\] 在雜湊表中指定資源的屬性名稱與其值，分別作為機碼與值。 使用 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) Cmdlet，探索資源的屬性和其類型。

*InDesiredState* \[out\] 傳回時，如果目標節點是所需狀態，這個屬性會設定為 **true**。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF**：DscCore.mof

**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
