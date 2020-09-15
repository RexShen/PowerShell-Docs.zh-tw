---
ms.date: 07/17/2020
keywords: dsc,powershell,設定,安裝
title: StopConfiguration 方法
ms.openlocfilehash: 76e50c98b09dca86983320918c6899082580672a
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463698"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="ee8c6-103">StopConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="ee8c6-103">StopConfiguration method</span></span>

<span data-ttu-id="ee8c6-104">停止進行中的設定變更。</span><span class="sxs-lookup"><span data-stu-id="ee8c6-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="ee8c6-105">語法</span><span class="sxs-lookup"><span data-stu-id="ee8c6-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="ee8c6-106">參數</span><span class="sxs-lookup"><span data-stu-id="ee8c6-106">Parameters</span></span>

<span data-ttu-id="ee8c6-107">**force** \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="ee8c6-107">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="ee8c6-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="ee8c6-108">Return value</span></span>

<span data-ttu-id="ee8c6-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="ee8c6-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ee8c6-110">備註</span><span class="sxs-lookup"><span data-stu-id="ee8c6-110">Remarks</span></span>

<span data-ttu-id="ee8c6-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="ee8c6-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee8c6-112">需求</span><span class="sxs-lookup"><span data-stu-id="ee8c6-112">Requirements</span></span>

<span data-ttu-id="ee8c6-113">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ee8c6-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ee8c6-114">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ee8c6-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ee8c6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee8c6-115">See also</span></span>

[<span data-ttu-id="ee8c6-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ee8c6-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
