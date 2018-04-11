---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 StopConfiguration 方法
ms.openlocfilehash: dadb6912af2e4450381958ed465799056da49946
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="00119-103">MSFT_DSCLocalConfigurationManager 類別的 StopConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="00119-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="00119-104">停止進行中的設定變更。</span><span class="sxs-lookup"><span data-stu-id="00119-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="00119-105">語法</span><span class="sxs-lookup"><span data-stu-id="00119-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="00119-106">參數</span><span class="sxs-lookup"><span data-stu-id="00119-106">Parameters</span></span>
----------

<span data-ttu-id="00119-107">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="00119-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="00119-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="00119-108">Return value</span></span>
------------

<span data-ttu-id="00119-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="00119-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="00119-110">備註</span><span class="sxs-lookup"><span data-stu-id="00119-110">Remarks</span></span>

<span data-ttu-id="00119-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="00119-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="00119-112">需求</span><span class="sxs-lookup"><span data-stu-id="00119-112">Requirements</span></span>
------------
><span data-ttu-id="00119-113">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="00119-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="00119-114">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="00119-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="00119-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00119-115">See also</span></span>


[<span data-ttu-id="00119-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="00119-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)