---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: RollBack 方法
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727033"
---
# <a name="rollback-method"></a><span data-ttu-id="169a6-103">RollBack 方法</span><span class="sxs-lookup"><span data-stu-id="169a6-103">RollBack method</span></span>

<span data-ttu-id="169a6-104">將設定復原回先前的版本。</span><span class="sxs-lookup"><span data-stu-id="169a6-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="169a6-105">語法</span><span class="sxs-lookup"><span data-stu-id="169a6-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="169a6-106">參數</span><span class="sxs-lookup"><span data-stu-id="169a6-106">Parameters</span></span>

<span data-ttu-id="169a6-107">*configurationNumber* \[in\] 指定要求的設定。</span><span class="sxs-lookup"><span data-stu-id="169a6-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="169a6-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="169a6-108">Return value</span></span>

<span data-ttu-id="169a6-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="169a6-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="169a6-110">備註</span><span class="sxs-lookup"><span data-stu-id="169a6-110">Remarks</span></span>

<span data-ttu-id="169a6-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="169a6-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="169a6-112">需求</span><span class="sxs-lookup"><span data-stu-id="169a6-112">Requirements</span></span>

<span data-ttu-id="169a6-113">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="169a6-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="169a6-114">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="169a6-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="169a6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="169a6-115">See also</span></span>

[<span data-ttu-id="169a6-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="169a6-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
