---
ms.date: 07/14/2020
ms.topic: reference
title: ApplyConfiguration 方法
description: ApplyConfiguration 方法
ms.openlocfilehash: aa99221b33d39c3ecc70156a11eaee10b540e2dc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664280"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="86752-103">ApplyConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="86752-103">ApplyConfiguration method</span></span>

<span data-ttu-id="86752-104">使用設定代理程式套用擱置中的設定。</span><span class="sxs-lookup"><span data-stu-id="86752-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="86752-105">如果沒有任何擱置中的設定，這個方法會重新套用目前的設定。</span><span class="sxs-lookup"><span data-stu-id="86752-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="86752-106">語法</span><span class="sxs-lookup"><span data-stu-id="86752-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="86752-107">參數</span><span class="sxs-lookup"><span data-stu-id="86752-107">Parameters</span></span>

### <a name="force"></a><span data-ttu-id="86752-108">force</span><span class="sxs-lookup"><span data-stu-id="86752-108">force</span></span>

<span data-ttu-id="86752-109">如果這是 **true** ，就算有擱置中的設定，也會重新套用目前的設定。</span><span class="sxs-lookup"><span data-stu-id="86752-109">If this is **true** , the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="86752-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="86752-110">Return value</span></span>

<span data-ttu-id="86752-111">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="86752-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="86752-112">備註</span><span class="sxs-lookup"><span data-stu-id="86752-112">Remarks</span></span>

<span data-ttu-id="86752-113">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="86752-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="86752-114">需求</span><span class="sxs-lookup"><span data-stu-id="86752-114">Requirements</span></span>

<span data-ttu-id="86752-115">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="86752-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="86752-116">**Namespace** ：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="86752-116">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="86752-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86752-117">See also</span></span>

[<span data-ttu-id="86752-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="86752-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
