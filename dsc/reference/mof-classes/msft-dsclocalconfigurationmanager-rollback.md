---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679362"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="40269-103">MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法</span><span class="sxs-lookup"><span data-stu-id="40269-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="40269-104">將設定復原回先前的版本。</span><span class="sxs-lookup"><span data-stu-id="40269-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="40269-105">語法</span><span class="sxs-lookup"><span data-stu-id="40269-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="40269-106">參數</span><span class="sxs-lookup"><span data-stu-id="40269-106">Parameters</span></span>

<span data-ttu-id="40269-107">*configurationNumber* \[in\] 指定要求的設定。</span><span class="sxs-lookup"><span data-stu-id="40269-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="40269-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="40269-108">Return value</span></span>

<span data-ttu-id="40269-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="40269-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="40269-110">備註</span><span class="sxs-lookup"><span data-stu-id="40269-110">Remarks</span></span>

<span data-ttu-id="40269-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="40269-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="40269-112">需求</span><span class="sxs-lookup"><span data-stu-id="40269-112">Requirements</span></span>

<span data-ttu-id="40269-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="40269-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="40269-114">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="40269-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="40269-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40269-115">See also</span></span>

[<span data-ttu-id="40269-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="40269-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)