---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 SendConfiguration 方法
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676559"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ae147-103">MSFT_DSCLocalConfigurationManager 類別的 SendConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="ae147-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ae147-104">將設定文件傳送到受管理的節點，並將其儲存為擱置變更。</span><span class="sxs-lookup"><span data-stu-id="ae147-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae147-105">語法</span><span class="sxs-lookup"><span data-stu-id="ae147-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="ae147-106">參數</span><span class="sxs-lookup"><span data-stu-id="ae147-106">Parameters</span></span>

<span data-ttu-id="ae147-107">*ConfigurationData* \[in\] 設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="ae147-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="ae147-108">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="ae147-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="ae147-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="ae147-109">Return value</span></span>

<span data-ttu-id="ae147-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="ae147-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ae147-111">備註</span><span class="sxs-lookup"><span data-stu-id="ae147-111">Remarks</span></span>

<span data-ttu-id="ae147-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="ae147-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ae147-113">需求</span><span class="sxs-lookup"><span data-stu-id="ae147-113">Requirements</span></span>

<span data-ttu-id="ae147-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ae147-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ae147-115">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ae147-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ae147-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae147-116">See also</span></span>

[<span data-ttu-id="ae147-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ae147-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)