---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 StopConfiguration 方法
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047118"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5a7d8-103">MSFT_DSCLocalConfigurationManager 類別的 StopConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="5a7d8-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5a7d8-104">停止進行中的設定變更。</span><span class="sxs-lookup"><span data-stu-id="5a7d8-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="5a7d8-105">語法</span><span class="sxs-lookup"><span data-stu-id="5a7d8-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="5a7d8-106">參數</span><span class="sxs-lookup"><span data-stu-id="5a7d8-106">Parameters</span></span>

<span data-ttu-id="5a7d8-107">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="5a7d8-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="5a7d8-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="5a7d8-108">Return value</span></span>

<span data-ttu-id="5a7d8-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="5a7d8-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5a7d8-110">備註</span><span class="sxs-lookup"><span data-stu-id="5a7d8-110">Remarks</span></span>

<span data-ttu-id="5a7d8-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="5a7d8-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5a7d8-112">需求</span><span class="sxs-lookup"><span data-stu-id="5a7d8-112">Requirements</span></span>

<span data-ttu-id="5a7d8-113">MOF\*\*DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5a7d8-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5a7d8-114">-NamespaceRoot\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5a7d8-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5a7d8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a7d8-115">See also</span></span>

[<span data-ttu-id="5a7d8-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5a7d8-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)