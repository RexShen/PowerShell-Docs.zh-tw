---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: SendConfigurationApplyAsync 方法
ms.openlocfilehash: c0e6dc9418757ee719e848fa8e7006dd73d91ad8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953375"
---
# <a name="sendconfigurationapplyasync-method"></a><span data-ttu-id="41e4e-103">SendConfigurationApplyAsync 方法</span><span class="sxs-lookup"><span data-stu-id="41e4e-103">SendConfigurationApplyAsync method</span></span>

<span data-ttu-id="41e4e-104">將設定文件非同步地傳送到受管理的節點，並使用設定代理程式套用設定。</span><span class="sxs-lookup"><span data-stu-id="41e4e-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="41e4e-105">語法</span><span class="sxs-lookup"><span data-stu-id="41e4e-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="41e4e-106">參數</span><span class="sxs-lookup"><span data-stu-id="41e4e-106">Parameters</span></span>

<span data-ttu-id="41e4e-107">*ConfigurationData* \[in\] 設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="41e4e-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="41e4e-108">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="41e4e-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="41e4e-109">*jobId* \[in\] 傳送設定之工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="41e4e-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="41e4e-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="41e4e-110">Return value</span></span>

<span data-ttu-id="41e4e-111">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="41e4e-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="41e4e-112">備註</span><span class="sxs-lookup"><span data-stu-id="41e4e-112">Remarks</span></span>

<span data-ttu-id="41e4e-113">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="41e4e-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="41e4e-114">需求</span><span class="sxs-lookup"><span data-stu-id="41e4e-114">Requirements</span></span>

<span data-ttu-id="41e4e-115">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="41e4e-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="41e4e-116">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="41e4e-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="41e4e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41e4e-117">See also</span></span>

[<span data-ttu-id="41e4e-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="41e4e-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
