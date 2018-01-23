---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 ApplyConfiguration 方法"
ms.openlocfilehash: 72fbedf30e5058d8003ed620400d6b443d50dff6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bbf42-103">MSFT_DSCLocalConfigurationManager 類別的 ApplyConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="bbf42-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bbf42-104">使用設定代理程式套用擱置中的設定。</span><span class="sxs-lookup"><span data-stu-id="bbf42-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span> 

<span data-ttu-id="bbf42-105">如果沒有任何擱置中的設定，這個方法會重新套用目前的設定。</span><span class="sxs-lookup"><span data-stu-id="bbf42-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="bbf42-106">語法</span><span class="sxs-lookup"><span data-stu-id="bbf42-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="bbf42-107">參數</span><span class="sxs-lookup"><span data-stu-id="bbf42-107">Parameters</span></span>
----------

<span data-ttu-id="bbf42-108">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="bbf42-108">*force* \[in\]</span></span>  
<span data-ttu-id="bbf42-109">如果這是 **true**，就算有擱置中的設定，也會重新套用目前的設定。</span><span class="sxs-lookup"><span data-stu-id="bbf42-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="bbf42-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="bbf42-110">Return value</span></span>
------------

<span data-ttu-id="bbf42-111">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="bbf42-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bbf42-112">備註</span><span class="sxs-lookup"><span data-stu-id="bbf42-112">Remarks</span></span>

<span data-ttu-id="bbf42-113">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="bbf42-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bbf42-114">需求</span><span class="sxs-lookup"><span data-stu-id="bbf42-114">Requirements</span></span>
------------
><span data-ttu-id="bbf42-115">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bbf42-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="bbf42-116">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bbf42-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="bbf42-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbf42-117">See also</span></span>


[<span data-ttu-id="bbf42-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bbf42-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



