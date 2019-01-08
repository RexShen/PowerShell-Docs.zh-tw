---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApplyAsync 方法
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047333"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fd8a1-103">MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApplyAsync 方法</span><span class="sxs-lookup"><span data-stu-id="fd8a1-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fd8a1-104">將設定文件非同步地傳送到受管理的節點，並使用設定代理程式套用設定。</span><span class="sxs-lookup"><span data-stu-id="fd8a1-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="fd8a1-105">語法</span><span class="sxs-lookup"><span data-stu-id="fd8a1-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="fd8a1-106">參數</span><span class="sxs-lookup"><span data-stu-id="fd8a1-106">Parameters</span></span>

<span data-ttu-id="fd8a1-107">*ConfigurationData* \[in\] 設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="fd8a1-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="fd8a1-108">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="fd8a1-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="fd8a1-109">*jobId* \[in\] 傳送設定之工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="fd8a1-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="fd8a1-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="fd8a1-110">Return value</span></span>

<span data-ttu-id="fd8a1-111">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="fd8a1-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fd8a1-112">備註</span><span class="sxs-lookup"><span data-stu-id="fd8a1-112">Remarks</span></span>

<span data-ttu-id="fd8a1-113">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="fd8a1-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fd8a1-114">需求</span><span class="sxs-lookup"><span data-stu-id="fd8a1-114">Requirements</span></span>

<span data-ttu-id="fd8a1-115">MOF\*\*DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fd8a1-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="fd8a1-116">-NamespaceRoot\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fd8a1-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="fd8a1-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd8a1-117">See also</span></span>

[<span data-ttu-id="fd8a1-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fd8a1-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)