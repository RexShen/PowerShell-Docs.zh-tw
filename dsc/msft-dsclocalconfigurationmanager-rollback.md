---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法
ms.openlocfilehash: c0a801c4037921e700e447d1434e246df0a63a4f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d7b56-103">MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法</span><span class="sxs-lookup"><span data-stu-id="d7b56-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d7b56-104">將設定復原回先前的版本。</span><span class="sxs-lookup"><span data-stu-id="d7b56-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="d7b56-105">語法</span><span class="sxs-lookup"><span data-stu-id="d7b56-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="d7b56-106">參數</span><span class="sxs-lookup"><span data-stu-id="d7b56-106">Parameters</span></span>
----------

<span data-ttu-id="d7b56-107">*configurationNumber* \[in\] 指定要求的設定。</span><span class="sxs-lookup"><span data-stu-id="d7b56-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="d7b56-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="d7b56-108">Return value</span></span>
------------

<span data-ttu-id="d7b56-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d7b56-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7b56-110">備註</span><span class="sxs-lookup"><span data-stu-id="d7b56-110">Remarks</span></span>

<span data-ttu-id="d7b56-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="d7b56-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d7b56-112">需求</span><span class="sxs-lookup"><span data-stu-id="d7b56-112">Requirements</span></span>
------------
><span data-ttu-id="d7b56-113">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d7b56-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d7b56-114">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d7b56-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d7b56-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7b56-115">See also</span></span>


[<span data-ttu-id="d7b56-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d7b56-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)