---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 SendMetaConfigurationApply 方法
ms.openlocfilehash: 46acd86ac52b7b6b39f06fc65af2498b4f5348ed
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218836"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5eee7-103">MSFT_DSCLocalConfigurationManager 類別的 SendMetaConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="5eee7-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5eee7-104">設定用於控制設定代理程式的本機設定管理員設定。</span><span class="sxs-lookup"><span data-stu-id="5eee7-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="5eee7-105">語法</span><span class="sxs-lookup"><span data-stu-id="5eee7-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="5eee7-106">參數</span><span class="sxs-lookup"><span data-stu-id="5eee7-106">Parameters</span></span>
----------

<span data-ttu-id="5eee7-107">*ConfigurationData* \[in\] 設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="5eee7-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="5eee7-108">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="5eee7-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="5eee7-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="5eee7-109">Return value</span></span>
------------

<span data-ttu-id="5eee7-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="5eee7-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5eee7-111">備註</span><span class="sxs-lookup"><span data-stu-id="5eee7-111">Remarks</span></span>

<span data-ttu-id="5eee7-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="5eee7-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5eee7-113">需求</span><span class="sxs-lookup"><span data-stu-id="5eee7-113">Requirements</span></span>
------------
><span data-ttu-id="5eee7-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5eee7-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5eee7-115">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5eee7-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5eee7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5eee7-116">See also</span></span>


[<span data-ttu-id="5eee7-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5eee7-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)