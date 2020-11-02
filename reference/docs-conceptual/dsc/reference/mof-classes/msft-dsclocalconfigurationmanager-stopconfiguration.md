---
ms.date: 07/17/2020
ms.topic: reference
title: StopConfiguration 方法
description: StopConfiguration 方法
ms.openlocfilehash: 854c0dbe8554c08413735a5a7bc872776e0b0a6c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644630"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="c3324-103">StopConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="c3324-103">StopConfiguration method</span></span>

<span data-ttu-id="c3324-104">停止進行中的設定變更。</span><span class="sxs-lookup"><span data-stu-id="c3324-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="c3324-105">語法</span><span class="sxs-lookup"><span data-stu-id="c3324-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="c3324-106">參數</span><span class="sxs-lookup"><span data-stu-id="c3324-106">Parameters</span></span>

<span data-ttu-id="c3324-107">**force** \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="c3324-107">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="c3324-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="c3324-108">Return value</span></span>

<span data-ttu-id="c3324-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="c3324-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3324-110">備註</span><span class="sxs-lookup"><span data-stu-id="c3324-110">Remarks</span></span>

<span data-ttu-id="c3324-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="c3324-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c3324-112">需求</span><span class="sxs-lookup"><span data-stu-id="c3324-112">Requirements</span></span>

<span data-ttu-id="c3324-113">**MOF** ：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c3324-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c3324-114">**命名空間** ：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c3324-114">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c3324-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3324-115">See also</span></span>

[<span data-ttu-id="c3324-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c3324-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
