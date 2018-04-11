---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 SendMetaConfigurationApply 方法
ms.openlocfilehash: ab82b239ddfdb4075d9440cd66343266b3c08eda
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b994d-103">MSFT_DSCLocalConfigurationManager 類別的 SendMetaConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="b994d-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b994d-104">設定用於控制設定代理程式的本機設定管理員設定。</span><span class="sxs-lookup"><span data-stu-id="b994d-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="b994d-105">語法</span><span class="sxs-lookup"><span data-stu-id="b994d-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="b994d-106">參數</span><span class="sxs-lookup"><span data-stu-id="b994d-106">Parameters</span></span>
----------

<span data-ttu-id="b994d-107">*ConfigurationData* \[in\] 設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="b994d-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="b994d-108">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="b994d-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="b994d-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="b994d-109">Return value</span></span>
------------

<span data-ttu-id="b994d-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="b994d-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b994d-111">備註</span><span class="sxs-lookup"><span data-stu-id="b994d-111">Remarks</span></span>

<span data-ttu-id="b994d-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="b994d-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b994d-113">需求</span><span class="sxs-lookup"><span data-stu-id="b994d-113">Requirements</span></span>
------------
><span data-ttu-id="b994d-114">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b994d-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b994d-115">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b994d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b994d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b994d-116">See also</span></span>


[<span data-ttu-id="b994d-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b994d-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)