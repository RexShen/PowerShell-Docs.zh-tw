---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: StopConfiguration 方法
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953355"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="e9f94-103">StopConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="e9f94-103">StopConfiguration method</span></span>

<span data-ttu-id="e9f94-104">停止進行中的設定變更。</span><span class="sxs-lookup"><span data-stu-id="e9f94-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="e9f94-105">語法</span><span class="sxs-lookup"><span data-stu-id="e9f94-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="e9f94-106">參數</span><span class="sxs-lookup"><span data-stu-id="e9f94-106">Parameters</span></span>

<span data-ttu-id="e9f94-107">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="e9f94-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="e9f94-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e9f94-108">Return value</span></span>

<span data-ttu-id="e9f94-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e9f94-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e9f94-110">備註</span><span class="sxs-lookup"><span data-stu-id="e9f94-110">Remarks</span></span>

<span data-ttu-id="e9f94-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="e9f94-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e9f94-112">需求</span><span class="sxs-lookup"><span data-stu-id="e9f94-112">Requirements</span></span>

<span data-ttu-id="e9f94-113">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e9f94-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e9f94-114">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e9f94-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e9f94-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9f94-115">See also</span></span>

[<span data-ttu-id="e9f94-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e9f94-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
