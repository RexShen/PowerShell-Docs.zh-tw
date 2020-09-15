---
ms.date: 07/17/2020
keywords: dsc,powershell,設定,安裝
title: GetConfigurationStatus 方法
ms.openlocfilehash: c2c478151428052d656832fb4079f12d666a910d
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464040"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="95d3b-103">GetConfigurationStatus 方法</span><span class="sxs-lookup"><span data-stu-id="95d3b-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="95d3b-104">取得設定狀態歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="95d3b-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="95d3b-105">語法</span><span class="sxs-lookup"><span data-stu-id="95d3b-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="95d3b-106">參數</span><span class="sxs-lookup"><span data-stu-id="95d3b-106">Parameters</span></span>

<span data-ttu-id="95d3b-107">**All** \[in\] 若此方法應傳回電腦上所執行所有設定的相關資訊，包括設定應用程式與一致性檢查，即為 **true**。</span><span class="sxs-lookup"><span data-stu-id="95d3b-107">**All** \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="95d3b-108">**configurationStatus** \[out\] 在傳回時會包含定義設定的 **MSFT_DSCConfigurationStatus** 類別之內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="95d3b-108">**configurationStatus** \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="95d3b-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="95d3b-109">Return value</span></span>

<span data-ttu-id="95d3b-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="95d3b-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="95d3b-111">備註</span><span class="sxs-lookup"><span data-stu-id="95d3b-111">Remarks</span></span>

<span data-ttu-id="95d3b-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="95d3b-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="95d3b-113">需求</span><span class="sxs-lookup"><span data-stu-id="95d3b-113">Requirements</span></span>

<span data-ttu-id="95d3b-114">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="95d3b-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="95d3b-115">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="95d3b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="95d3b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95d3b-116">See also</span></span>

[<span data-ttu-id="95d3b-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="95d3b-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
