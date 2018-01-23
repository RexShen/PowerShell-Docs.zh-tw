---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 TestConfiguration 方法"
ms.openlocfilehash: 04f0f3146473dc71f492086449d9dce5467c55db
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0a7fe-103">MSFT_DSCLocalConfigurationManager 類別的 TestConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="0a7fe-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0a7fe-104">將設定文件傳送到受管理的節點，並對文件驗證目前的設定。</span><span class="sxs-lookup"><span data-stu-id="0a7fe-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="0a7fe-105">語法</span><span class="sxs-lookup"><span data-stu-id="0a7fe-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="0a7fe-106">參數</span><span class="sxs-lookup"><span data-stu-id="0a7fe-106">Parameters</span></span>
----------

<span data-ttu-id="0a7fe-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="0a7fe-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="0a7fe-108">設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="0a7fe-108">Environment data for the confuguration.</span></span>

<span data-ttu-id="0a7fe-109">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="0a7fe-109">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="0a7fe-110">傳回時，指定受管理的節點是否為設定文件所指定的狀態。</span><span class="sxs-lookup"><span data-stu-id="0a7fe-110">On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="0a7fe-111">*ResourcesInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="0a7fe-111">*ResourcesInDesiredState* \[out\]</span></span>  
<span data-ttu-id="0a7fe-112">傳回時，包含指定資源為所需狀態之 **MSFT_ResourceInDesiredState** 類別的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a7fe-112">On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="0a7fe-113">*ResourcesNotInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="0a7fe-113">*ResourcesNotInDesiredState* \[out\]</span></span>  
<span data-ttu-id="0a7fe-114">傳回時，包含指定資源不為所需狀態之 **MSFT_ResourceNotInDesiredState** 類別的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a7fe-114">On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="0a7fe-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="0a7fe-115">Return value</span></span>
------------

<span data-ttu-id="0a7fe-116">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="0a7fe-116">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a7fe-117">備註</span><span class="sxs-lookup"><span data-stu-id="0a7fe-117">Remarks</span></span>

<span data-ttu-id="0a7fe-118">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="0a7fe-118">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0a7fe-119">需求</span><span class="sxs-lookup"><span data-stu-id="0a7fe-119">Requirements</span></span>
------------
><span data-ttu-id="0a7fe-120">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0a7fe-120">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="0a7fe-121">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0a7fe-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="0a7fe-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a7fe-122">See also</span></span>


[<span data-ttu-id="0a7fe-123">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0a7fe-123">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



