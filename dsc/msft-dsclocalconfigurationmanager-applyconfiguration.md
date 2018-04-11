---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 ApplyConfiguration 方法
ms.openlocfilehash: 2844e354e0d054b13b92267ce314536d88a1c33e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="48c95-103">MSFT_DSCLocalConfigurationManager 類別的 ApplyConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="48c95-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="48c95-104">使用設定代理程式套用擱置中的設定。</span><span class="sxs-lookup"><span data-stu-id="48c95-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="48c95-105">如果沒有任何擱置中的設定，這個方法會重新套用目前的設定。</span><span class="sxs-lookup"><span data-stu-id="48c95-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="48c95-106">語法</span><span class="sxs-lookup"><span data-stu-id="48c95-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="48c95-107">參數</span><span class="sxs-lookup"><span data-stu-id="48c95-107">Parameters</span></span>
----------

<span data-ttu-id="48c95-108">*force* \[in\] 如果這是 **true**，就算有擱置中的設定，也會重新套用目前的設定。</span><span class="sxs-lookup"><span data-stu-id="48c95-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="48c95-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="48c95-109">Return value</span></span>
------------

<span data-ttu-id="48c95-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="48c95-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="48c95-111">備註</span><span class="sxs-lookup"><span data-stu-id="48c95-111">Remarks</span></span>

<span data-ttu-id="48c95-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="48c95-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="48c95-113">需求</span><span class="sxs-lookup"><span data-stu-id="48c95-113">Requirements</span></span>
------------
><span data-ttu-id="48c95-114">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="48c95-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="48c95-115">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="48c95-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="48c95-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48c95-116">See also</span></span>


[<span data-ttu-id="48c95-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="48c95-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)