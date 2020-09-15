---
ms.date: 07/17/2020
keywords: dsc,powershell,設定,安裝
title: RollBack 方法
ms.openlocfilehash: 301b8926d2ebf1ebe524f52a67928d34e26d860e
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464327"
---
# <a name="rollback-method"></a><span data-ttu-id="4b1ea-103">RollBack 方法</span><span class="sxs-lookup"><span data-stu-id="4b1ea-103">RollBack method</span></span>

<span data-ttu-id="4b1ea-104">將設定復原回先前的版本。</span><span class="sxs-lookup"><span data-stu-id="4b1ea-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="4b1ea-105">語法</span><span class="sxs-lookup"><span data-stu-id="4b1ea-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="4b1ea-106">參數</span><span class="sxs-lookup"><span data-stu-id="4b1ea-106">Parameters</span></span>

<span data-ttu-id="4b1ea-107">**configurationNumber** \[in\] 指定要求的設定。</span><span class="sxs-lookup"><span data-stu-id="4b1ea-107">**configurationNumber** \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="4b1ea-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="4b1ea-108">Return value</span></span>

<span data-ttu-id="4b1ea-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="4b1ea-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4b1ea-110">備註</span><span class="sxs-lookup"><span data-stu-id="4b1ea-110">Remarks</span></span>

<span data-ttu-id="4b1ea-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="4b1ea-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4b1ea-112">需求</span><span class="sxs-lookup"><span data-stu-id="4b1ea-112">Requirements</span></span>

<span data-ttu-id="4b1ea-113">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4b1ea-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4b1ea-114">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4b1ea-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4b1ea-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b1ea-115">See also</span></span>

[<span data-ttu-id="4b1ea-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4b1ea-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
