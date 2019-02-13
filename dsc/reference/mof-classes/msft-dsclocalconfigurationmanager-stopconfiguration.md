---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 StopConfiguration 方法
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679008"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e186d-103">MSFT_DSCLocalConfigurationManager 類別的 StopConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="e186d-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e186d-104">停止進行中的設定變更。</span><span class="sxs-lookup"><span data-stu-id="e186d-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="e186d-105">語法</span><span class="sxs-lookup"><span data-stu-id="e186d-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="e186d-106">參數</span><span class="sxs-lookup"><span data-stu-id="e186d-106">Parameters</span></span>

<span data-ttu-id="e186d-107">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="e186d-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="e186d-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e186d-108">Return value</span></span>

<span data-ttu-id="e186d-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e186d-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e186d-110">備註</span><span class="sxs-lookup"><span data-stu-id="e186d-110">Remarks</span></span>

<span data-ttu-id="e186d-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="e186d-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e186d-112">需求</span><span class="sxs-lookup"><span data-stu-id="e186d-112">Requirements</span></span>

<span data-ttu-id="e186d-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e186d-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e186d-114">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e186d-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e186d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e186d-115">See also</span></span>

[<span data-ttu-id="e186d-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e186d-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)