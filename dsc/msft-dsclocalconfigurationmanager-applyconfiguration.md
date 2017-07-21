---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 ApplyConfiguration 方法"
ms.openlocfilehash: febaf972a2a452eb9aaf3ec7fbc5e41f3f463a58
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7022e-103">MSFT_DSCLocalConfigurationManager 類別的 ApplyConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="7022e-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7022e-104">使用設定代理程式套用擱置中的設定。</span><span class="sxs-lookup"><span data-stu-id="7022e-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span> 

<span data-ttu-id="7022e-105">如果沒有任何擱置中的設定，這個方法會重新套用目前的設定。</span><span class="sxs-lookup"><span data-stu-id="7022e-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="7022e-106">語法</span><span class="sxs-lookup"><span data-stu-id="7022e-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="7022e-107">參數</span><span class="sxs-lookup"><span data-stu-id="7022e-107">Parameters</span></span>
----------

<span data-ttu-id="7022e-108">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="7022e-108">*force* \[in\]</span></span>  
<span data-ttu-id="7022e-109">如果這是 **true**，就算有擱置中的設定，也會重新套用目前的設定。</span><span class="sxs-lookup"><span data-stu-id="7022e-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="7022e-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="7022e-110">Return value</span></span>
------------

<span data-ttu-id="7022e-111">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="7022e-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7022e-112">備註</span><span class="sxs-lookup"><span data-stu-id="7022e-112">Remarks</span></span>

<span data-ttu-id="7022e-113">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="7022e-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7022e-114">需求</span><span class="sxs-lookup"><span data-stu-id="7022e-114">Requirements</span></span>
------------
><span data-ttu-id="7022e-115">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7022e-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7022e-116">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7022e-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7022e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7022e-117">See also</span></span>


[<span data-ttu-id="7022e-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7022e-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



