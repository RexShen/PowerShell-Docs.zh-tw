---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: ApplyConfiguration 方法
ms.openlocfilehash: 0425b9a7db37e421830ba37da8f5c0a4877a1b72
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953455"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="8e92f-103">ApplyConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="8e92f-103">ApplyConfiguration method</span></span>

<span data-ttu-id="8e92f-104">使用設定代理程式套用擱置中的設定。</span><span class="sxs-lookup"><span data-stu-id="8e92f-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="8e92f-105">如果沒有任何擱置中的設定，這個方法會重新套用目前的設定。</span><span class="sxs-lookup"><span data-stu-id="8e92f-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="8e92f-106">語法</span><span class="sxs-lookup"><span data-stu-id="8e92f-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="8e92f-107">參數</span><span class="sxs-lookup"><span data-stu-id="8e92f-107">Parameters</span></span>

<span data-ttu-id="8e92f-108">*force* \[in\] 如果這是 **true**，就算有擱置中的設定，也會重新套用目前的設定。</span><span class="sxs-lookup"><span data-stu-id="8e92f-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="8e92f-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="8e92f-109">Return value</span></span>

<span data-ttu-id="8e92f-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8e92f-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8e92f-111">備註</span><span class="sxs-lookup"><span data-stu-id="8e92f-111">Remarks</span></span>

<span data-ttu-id="8e92f-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="8e92f-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8e92f-113">需求</span><span class="sxs-lookup"><span data-stu-id="8e92f-113">Requirements</span></span>

<span data-ttu-id="8e92f-114">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8e92f-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8e92f-115">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8e92f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8e92f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e92f-116">See also</span></span>

[<span data-ttu-id="8e92f-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8e92f-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
