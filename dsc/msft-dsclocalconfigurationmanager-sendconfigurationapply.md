---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApply 方法"
ms.openlocfilehash: 20f732d35860cccde4e507dc6916e27d0cf8c5f6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="dc7da-103">MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="dc7da-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="dc7da-104">將設定文件傳送到受管理的節點，並使用設定代理程式套用設定。</span><span class="sxs-lookup"><span data-stu-id="dc7da-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="dc7da-105">語法</span><span class="sxs-lookup"><span data-stu-id="dc7da-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="dc7da-106">參數</span><span class="sxs-lookup"><span data-stu-id="dc7da-106">Parameters</span></span>
----------

<span data-ttu-id="dc7da-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="dc7da-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="dc7da-108">設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="dc7da-108">The environment data for the configuration.</span></span>

<span data-ttu-id="dc7da-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="dc7da-109">*force* \[in\]</span></span>  
<span data-ttu-id="dc7da-110">**true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="dc7da-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="dc7da-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="dc7da-111">Return value</span></span>
------------

<span data-ttu-id="dc7da-112">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="dc7da-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="dc7da-113">備註</span><span class="sxs-lookup"><span data-stu-id="dc7da-113">Remarks</span></span>

<span data-ttu-id="dc7da-114">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="dc7da-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="dc7da-115">需求</span><span class="sxs-lookup"><span data-stu-id="dc7da-115">Requirements</span></span>
------------
><span data-ttu-id="dc7da-116">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="dc7da-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="dc7da-117">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="dc7da-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="dc7da-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc7da-118">See also</span></span>


[<span data-ttu-id="dc7da-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="dc7da-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



