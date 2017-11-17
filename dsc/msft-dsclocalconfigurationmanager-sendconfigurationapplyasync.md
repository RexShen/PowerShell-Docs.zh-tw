---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApplyAsync 方法"
ms.openlocfilehash: e680bfd1c5b39d364c90cf5ef6b43d0a568af23a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f02f4-103">MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApplyAsync 方法</span><span class="sxs-lookup"><span data-stu-id="f02f4-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f02f4-104">將設定文件非同步地傳送到受管理的節點，並使用設定代理程式套用設定。</span><span class="sxs-lookup"><span data-stu-id="f02f4-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="f02f4-105">語法</span><span class="sxs-lookup"><span data-stu-id="f02f4-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="f02f4-106">參數</span><span class="sxs-lookup"><span data-stu-id="f02f4-106">Parameters</span></span>
----------

<span data-ttu-id="f02f4-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f02f4-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="f02f4-108">設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="f02f4-108">The environment data for the configuration.</span></span>

<span data-ttu-id="f02f4-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f02f4-109">*force* \[in\]</span></span>  
<span data-ttu-id="f02f4-110">**true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="f02f4-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="f02f4-111">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f02f4-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="f02f4-112">傳送設定之工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f02f4-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="f02f4-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="f02f4-113">Return value</span></span>
------------

<span data-ttu-id="f02f4-114">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="f02f4-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f02f4-115">備註</span><span class="sxs-lookup"><span data-stu-id="f02f4-115">Remarks</span></span>

<span data-ttu-id="f02f4-116">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="f02f4-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f02f4-117">需求</span><span class="sxs-lookup"><span data-stu-id="f02f4-117">Requirements</span></span>
------------
><span data-ttu-id="f02f4-118">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f02f4-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="f02f4-119">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f02f4-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="f02f4-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f02f4-120">See also</span></span>


[<span data-ttu-id="f02f4-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f02f4-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



