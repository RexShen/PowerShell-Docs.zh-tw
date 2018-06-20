---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApply 方法
ms.openlocfilehash: c578f4f52d3ea70e7bcf683ac204d6e484d4630d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222151"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c6b0f-103">MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="c6b0f-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c6b0f-104">將設定文件傳送到受管理的節點，並使用設定代理程式套用設定。</span><span class="sxs-lookup"><span data-stu-id="c6b0f-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="c6b0f-105">語法</span><span class="sxs-lookup"><span data-stu-id="c6b0f-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="c6b0f-106">參數</span><span class="sxs-lookup"><span data-stu-id="c6b0f-106">Parameters</span></span>
----------

<span data-ttu-id="c6b0f-107">*ConfigurationData* \[in\] 設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="c6b0f-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="c6b0f-108">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="c6b0f-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="c6b0f-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="c6b0f-109">Return value</span></span>
------------

<span data-ttu-id="c6b0f-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="c6b0f-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c6b0f-111">備註</span><span class="sxs-lookup"><span data-stu-id="c6b0f-111">Remarks</span></span>

<span data-ttu-id="c6b0f-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="c6b0f-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c6b0f-113">需求</span><span class="sxs-lookup"><span data-stu-id="c6b0f-113">Requirements</span></span>
------------
><span data-ttu-id="c6b0f-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c6b0f-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="c6b0f-115">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c6b0f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="c6b0f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6b0f-116">See also</span></span>


[<span data-ttu-id="c6b0f-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c6b0f-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)