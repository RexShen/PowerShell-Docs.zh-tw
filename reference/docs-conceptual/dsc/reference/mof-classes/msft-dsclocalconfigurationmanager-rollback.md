---
ms.date: 07/17/2020
ms.topic: reference
title: RollBack 方法
description: RollBack 方法
ms.openlocfilehash: 82ca54ed23a3a892b785f603be3b423def5ee636
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650631"
---
# <a name="rollback-method"></a><span data-ttu-id="a9aa4-103">RollBack 方法</span><span class="sxs-lookup"><span data-stu-id="a9aa4-103">RollBack method</span></span>

<span data-ttu-id="a9aa4-104">將設定復原回先前的版本。</span><span class="sxs-lookup"><span data-stu-id="a9aa4-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="a9aa4-105">語法</span><span class="sxs-lookup"><span data-stu-id="a9aa4-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="a9aa4-106">參數</span><span class="sxs-lookup"><span data-stu-id="a9aa4-106">Parameters</span></span>

<span data-ttu-id="a9aa4-107">**configurationNumber** \[in\] 指定要求的設定。</span><span class="sxs-lookup"><span data-stu-id="a9aa4-107">**configurationNumber** \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="a9aa4-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a9aa4-108">Return value</span></span>

<span data-ttu-id="a9aa4-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="a9aa4-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a9aa4-110">備註</span><span class="sxs-lookup"><span data-stu-id="a9aa4-110">Remarks</span></span>

<span data-ttu-id="a9aa4-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="a9aa4-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a9aa4-112">需求</span><span class="sxs-lookup"><span data-stu-id="a9aa4-112">Requirements</span></span>

<span data-ttu-id="a9aa4-113">**MOF** ：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a9aa4-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a9aa4-114">**命名空間** ：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a9aa4-114">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a9aa4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9aa4-115">See also</span></span>

[<span data-ttu-id="a9aa4-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a9aa4-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
