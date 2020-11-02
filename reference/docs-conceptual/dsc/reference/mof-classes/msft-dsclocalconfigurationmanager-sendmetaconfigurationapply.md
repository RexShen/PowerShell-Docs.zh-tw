---
ms.date: 07/17/2020
ms.topic: reference
title: SendMetaConfigurationApply 方法
description: SendMetaConfigurationApply 方法
ms.openlocfilehash: 27c58819c0249ace011c475e500e565e5daed9bb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648956"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="d1b1f-103">SendMetaConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="d1b1f-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="d1b1f-104">設定用於控制設定代理程式的本機設定管理員設定。</span><span class="sxs-lookup"><span data-stu-id="d1b1f-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="d1b1f-105">語法</span><span class="sxs-lookup"><span data-stu-id="d1b1f-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="d1b1f-106">參數</span><span class="sxs-lookup"><span data-stu-id="d1b1f-106">Parameters</span></span>

<span data-ttu-id="d1b1f-107">**ConfigurationData** \[in\] 設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="d1b1f-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="d1b1f-108">**force** \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="d1b1f-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="d1b1f-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="d1b1f-109">Return value</span></span>

<span data-ttu-id="d1b1f-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d1b1f-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d1b1f-111">備註</span><span class="sxs-lookup"><span data-stu-id="d1b1f-111">Remarks</span></span>

<span data-ttu-id="d1b1f-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="d1b1f-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d1b1f-113">需求</span><span class="sxs-lookup"><span data-stu-id="d1b1f-113">Requirements</span></span>

<span data-ttu-id="d1b1f-114">**MOF** ：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d1b1f-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d1b1f-115">**命名空間** ：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d1b1f-115">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d1b1f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1b1f-116">See also</span></span>

[<span data-ttu-id="d1b1f-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d1b1f-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
