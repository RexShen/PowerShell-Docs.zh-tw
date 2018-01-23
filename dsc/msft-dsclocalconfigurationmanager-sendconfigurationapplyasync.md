---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApplyAsync 方法"
ms.openlocfilehash: e680d510aaac097f4f0de80660274230e028ed45
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1b43b-103">MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApplyAsync 方法</span><span class="sxs-lookup"><span data-stu-id="1b43b-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1b43b-104">將設定文件非同步地傳送到受管理的節點，並使用設定代理程式套用設定。</span><span class="sxs-lookup"><span data-stu-id="1b43b-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="1b43b-105">語法</span><span class="sxs-lookup"><span data-stu-id="1b43b-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="1b43b-106">參數</span><span class="sxs-lookup"><span data-stu-id="1b43b-106">Parameters</span></span>
----------

<span data-ttu-id="1b43b-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="1b43b-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="1b43b-108">設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="1b43b-108">The environment data for the configuration.</span></span>

<span data-ttu-id="1b43b-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="1b43b-109">*force* \[in\]</span></span>  
<span data-ttu-id="1b43b-110">**true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="1b43b-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="1b43b-111">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="1b43b-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="1b43b-112">傳送設定之工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b43b-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="1b43b-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="1b43b-113">Return value</span></span>
------------

<span data-ttu-id="1b43b-114">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="1b43b-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b43b-115">備註</span><span class="sxs-lookup"><span data-stu-id="1b43b-115">Remarks</span></span>

<span data-ttu-id="1b43b-116">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="1b43b-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1b43b-117">需求</span><span class="sxs-lookup"><span data-stu-id="1b43b-117">Requirements</span></span>
------------
><span data-ttu-id="1b43b-118">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1b43b-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="1b43b-119">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1b43b-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="1b43b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b43b-120">See also</span></span>


[<span data-ttu-id="1b43b-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1b43b-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



