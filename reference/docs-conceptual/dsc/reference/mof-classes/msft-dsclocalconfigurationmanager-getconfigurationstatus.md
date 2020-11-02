---
ms.date: 07/17/2020
ms.topic: reference
title: GetConfigurationStatus 方法
description: GetConfigurationStatus 方法
ms.openlocfilehash: fe25d17069d9011e931ac50fec27cb9ebafba365
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650857"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="cd046-103">GetConfigurationStatus 方法</span><span class="sxs-lookup"><span data-stu-id="cd046-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="cd046-104">取得設定狀態歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="cd046-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd046-105">語法</span><span class="sxs-lookup"><span data-stu-id="cd046-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="cd046-106">參數</span><span class="sxs-lookup"><span data-stu-id="cd046-106">Parameters</span></span>

<span data-ttu-id="cd046-107">**All** \[in\] 若此方法應傳回電腦上所執行所有設定的相關資訊，包括設定應用程式與一致性檢查，即為 **true** 。</span><span class="sxs-lookup"><span data-stu-id="cd046-107">**All** \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="cd046-108">**configurationStatus** \[out\] 在傳回時會包含定義設定的 **MSFT_DSCConfigurationStatus** 類別之內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="cd046-108">**configurationStatus** \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="cd046-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="cd046-109">Return value</span></span>

<span data-ttu-id="cd046-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="cd046-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cd046-111">備註</span><span class="sxs-lookup"><span data-stu-id="cd046-111">Remarks</span></span>

<span data-ttu-id="cd046-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="cd046-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cd046-113">需求</span><span class="sxs-lookup"><span data-stu-id="cd046-113">Requirements</span></span>

<span data-ttu-id="cd046-114">**MOF** ：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cd046-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="cd046-115">**命名空間** ：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cd046-115">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="cd046-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd046-116">See also</span></span>

[<span data-ttu-id="cd046-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cd046-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
