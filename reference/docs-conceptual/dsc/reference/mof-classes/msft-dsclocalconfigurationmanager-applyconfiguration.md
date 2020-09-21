---
ms.date: 07/14/2020
keywords: dsc,powershell,設定,安裝
title: ApplyConfiguration 方法
ms.openlocfilehash: bec74ccd6f75448484adfd26bf8a4af4e224eb3f
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463834"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="12f48-103">ApplyConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="12f48-103">ApplyConfiguration method</span></span>

<span data-ttu-id="12f48-104">使用設定代理程式套用擱置中的設定。</span><span class="sxs-lookup"><span data-stu-id="12f48-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="12f48-105">如果沒有任何擱置中的設定，這個方法會重新套用目前的設定。</span><span class="sxs-lookup"><span data-stu-id="12f48-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="12f48-106">語法</span><span class="sxs-lookup"><span data-stu-id="12f48-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="12f48-107">參數</span><span class="sxs-lookup"><span data-stu-id="12f48-107">Parameters</span></span>

### <a name="force"></a><span data-ttu-id="12f48-108">force</span><span class="sxs-lookup"><span data-stu-id="12f48-108">force</span></span>

<span data-ttu-id="12f48-109">如果這是 **true**，就算有擱置中的設定，也會重新套用目前的設定。</span><span class="sxs-lookup"><span data-stu-id="12f48-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="12f48-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="12f48-110">Return value</span></span>

<span data-ttu-id="12f48-111">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="12f48-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="12f48-112">備註</span><span class="sxs-lookup"><span data-stu-id="12f48-112">Remarks</span></span>

<span data-ttu-id="12f48-113">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="12f48-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="12f48-114">需求</span><span class="sxs-lookup"><span data-stu-id="12f48-114">Requirements</span></span>

<span data-ttu-id="12f48-115">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="12f48-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="12f48-116">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="12f48-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="12f48-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12f48-117">See also</span></span>

[<span data-ttu-id="12f48-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="12f48-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
