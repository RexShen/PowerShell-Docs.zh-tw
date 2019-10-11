---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: StopConfiguration 方法
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953355"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="f19d0-103">StopConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="f19d0-103">StopConfiguration method</span></span>

<span data-ttu-id="f19d0-104">停止進行中的設定變更。</span><span class="sxs-lookup"><span data-stu-id="f19d0-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="f19d0-105">語法</span><span class="sxs-lookup"><span data-stu-id="f19d0-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="f19d0-106">參數</span><span class="sxs-lookup"><span data-stu-id="f19d0-106">Parameters</span></span>

<span data-ttu-id="f19d0-107">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="f19d0-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="f19d0-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="f19d0-108">Return value</span></span>

<span data-ttu-id="f19d0-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="f19d0-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f19d0-110">備註</span><span class="sxs-lookup"><span data-stu-id="f19d0-110">Remarks</span></span>

<span data-ttu-id="f19d0-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="f19d0-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f19d0-112">需求</span><span class="sxs-lookup"><span data-stu-id="f19d0-112">Requirements</span></span>

<span data-ttu-id="f19d0-113">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f19d0-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f19d0-114">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f19d0-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f19d0-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f19d0-115">See also</span></span>

[<span data-ttu-id="f19d0-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f19d0-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
