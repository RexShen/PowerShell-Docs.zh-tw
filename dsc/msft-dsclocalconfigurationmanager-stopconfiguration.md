---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 StopConfiguration 方法
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893870"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e5ad3-103">MSFT_DSCLocalConfigurationManager 類別的 StopConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="e5ad3-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e5ad3-104">停止進行中的設定變更。</span><span class="sxs-lookup"><span data-stu-id="e5ad3-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="e5ad3-105">語法</span><span class="sxs-lookup"><span data-stu-id="e5ad3-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="e5ad3-106">參數</span><span class="sxs-lookup"><span data-stu-id="e5ad3-106">Parameters</span></span>

<span data-ttu-id="e5ad3-107">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="e5ad3-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="e5ad3-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e5ad3-108">Return value</span></span>

<span data-ttu-id="e5ad3-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e5ad3-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5ad3-110">備註</span><span class="sxs-lookup"><span data-stu-id="e5ad3-110">Remarks</span></span>

<span data-ttu-id="e5ad3-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="e5ad3-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5ad3-112">需求</span><span class="sxs-lookup"><span data-stu-id="e5ad3-112">Requirements</span></span>

<span data-ttu-id="e5ad3-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e5ad3-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e5ad3-114">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e5ad3-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e5ad3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5ad3-115">See also</span></span>

[<span data-ttu-id="e5ad3-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e5ad3-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)