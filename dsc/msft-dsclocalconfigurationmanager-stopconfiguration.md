---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 StopConfiguration 方法"
ms.openlocfilehash: 66d00cb40750e91e4b369a2e8cebb449697406d9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e5526-103">MSFT_DSCLocalConfigurationManager 類別的 StopConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="e5526-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e5526-104">停止進行中的設定變更。</span><span class="sxs-lookup"><span data-stu-id="e5526-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="e5526-105">語法</span><span class="sxs-lookup"><span data-stu-id="e5526-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="e5526-106">參數</span><span class="sxs-lookup"><span data-stu-id="e5526-106">Parameters</span></span>
----------

<span data-ttu-id="e5526-107">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="e5526-107">*force* \[in\]</span></span>  
<span data-ttu-id="e5526-108">**true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="e5526-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="e5526-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="e5526-109">Return value</span></span>
------------

<span data-ttu-id="e5526-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e5526-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5526-111">備註</span><span class="sxs-lookup"><span data-stu-id="e5526-111">Remarks</span></span>

<span data-ttu-id="e5526-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="e5526-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5526-113">需求</span><span class="sxs-lookup"><span data-stu-id="e5526-113">Requirements</span></span>
------------
><span data-ttu-id="e5526-114">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e5526-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e5526-115">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e5526-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e5526-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5526-116">See also</span></span>


[<span data-ttu-id="e5526-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e5526-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



