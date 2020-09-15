---
ms.date: 07/17/2020
keywords: dsc,powershell,設定,安裝
title: SendConfigurationApplyAsync 方法
ms.openlocfilehash: 4cfac5edb5fed94ee69deb98d7aa6be56b51c5b3
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463732"
---
# <a name="sendconfigurationapplyasync-method"></a>SendConfigurationApplyAsync 方法

將設定文件非同步地傳送到受管理的節點，並使用設定代理程式套用設定。

## <a name="syntax"></a>語法

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a>參數

**ConfigurationData** \[in\] 設定的環境資料。

**force** \[in\] **true** 表示強制停止該設定。

**jobId** \[in\] 傳送設定之工作的識別碼。

## <a name="return-value"></a>傳回值

若成功即傳回零；否則傳回錯誤碼。

## <a name="remarks"></a>備註

此為靜態方法。

## <a name="requirements"></a>需求

**MOF**：DscCore.mof

**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另請參閱

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
