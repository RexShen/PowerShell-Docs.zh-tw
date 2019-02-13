---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApplyAsync 方法
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679470"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5d61f-103">MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApplyAsync 方法</span><span class="sxs-lookup"><span data-stu-id="5d61f-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5d61f-104">將設定文件非同步地傳送到受管理的節點，並使用設定代理程式套用設定。</span><span class="sxs-lookup"><span data-stu-id="5d61f-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="5d61f-105">語法</span><span class="sxs-lookup"><span data-stu-id="5d61f-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="5d61f-106">參數</span><span class="sxs-lookup"><span data-stu-id="5d61f-106">Parameters</span></span>

<span data-ttu-id="5d61f-107">*ConfigurationData* \[in\] 設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="5d61f-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="5d61f-108">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="5d61f-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="5d61f-109">*jobId* \[in\] 傳送設定之工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5d61f-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="5d61f-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="5d61f-110">Return value</span></span>

<span data-ttu-id="5d61f-111">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="5d61f-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5d61f-112">備註</span><span class="sxs-lookup"><span data-stu-id="5d61f-112">Remarks</span></span>

<span data-ttu-id="5d61f-113">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="5d61f-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5d61f-114">需求</span><span class="sxs-lookup"><span data-stu-id="5d61f-114">Requirements</span></span>

<span data-ttu-id="5d61f-115">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5d61f-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5d61f-116">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5d61f-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5d61f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d61f-117">See also</span></span>

[<span data-ttu-id="5d61f-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5d61f-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)