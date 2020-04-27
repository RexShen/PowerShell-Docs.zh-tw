---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: RollBack 方法
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954935"
---
# <a name="rollback-method"></a><span data-ttu-id="77e47-103">RollBack 方法</span><span class="sxs-lookup"><span data-stu-id="77e47-103">RollBack method</span></span>

<span data-ttu-id="77e47-104">將設定復原回先前的版本。</span><span class="sxs-lookup"><span data-stu-id="77e47-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="77e47-105">語法</span><span class="sxs-lookup"><span data-stu-id="77e47-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="77e47-106">參數</span><span class="sxs-lookup"><span data-stu-id="77e47-106">Parameters</span></span>

<span data-ttu-id="77e47-107">*configurationNumber* \[in\] 指定要求的設定。</span><span class="sxs-lookup"><span data-stu-id="77e47-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="77e47-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="77e47-108">Return value</span></span>

<span data-ttu-id="77e47-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="77e47-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="77e47-110">備註</span><span class="sxs-lookup"><span data-stu-id="77e47-110">Remarks</span></span>

<span data-ttu-id="77e47-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="77e47-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="77e47-112">需求</span><span class="sxs-lookup"><span data-stu-id="77e47-112">Requirements</span></span>

<span data-ttu-id="77e47-113">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="77e47-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="77e47-114">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="77e47-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="77e47-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77e47-115">See also</span></span>

[<span data-ttu-id="77e47-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="77e47-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
