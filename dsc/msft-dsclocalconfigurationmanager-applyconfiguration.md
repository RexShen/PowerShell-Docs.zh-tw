---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 ApplyConfiguration 方法
ms.openlocfilehash: ef8488246b2c8614452d32009e45535f0ff2e184
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a9ef3-103">MSFT_DSCLocalConfigurationManager 類別的 ApplyConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="a9ef3-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a9ef3-104">使用設定代理程式套用擱置中的設定。</span><span class="sxs-lookup"><span data-stu-id="a9ef3-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="a9ef3-105">如果沒有任何擱置中的設定，這個方法會重新套用目前的設定。</span><span class="sxs-lookup"><span data-stu-id="a9ef3-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="a9ef3-106">語法</span><span class="sxs-lookup"><span data-stu-id="a9ef3-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="a9ef3-107">參數</span><span class="sxs-lookup"><span data-stu-id="a9ef3-107">Parameters</span></span>
----------

<span data-ttu-id="a9ef3-108">*force* \[in\] 如果這是 **true**，就算有擱置中的設定，也會重新套用目前的設定。</span><span class="sxs-lookup"><span data-stu-id="a9ef3-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="a9ef3-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="a9ef3-109">Return value</span></span>
------------

<span data-ttu-id="a9ef3-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="a9ef3-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a9ef3-111">備註</span><span class="sxs-lookup"><span data-stu-id="a9ef3-111">Remarks</span></span>

<span data-ttu-id="a9ef3-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="a9ef3-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a9ef3-113">需求</span><span class="sxs-lookup"><span data-stu-id="a9ef3-113">Requirements</span></span>
------------
><span data-ttu-id="a9ef3-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a9ef3-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a9ef3-115">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a9ef3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a9ef3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9ef3-116">See also</span></span>


[<span data-ttu-id="a9ef3-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a9ef3-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)