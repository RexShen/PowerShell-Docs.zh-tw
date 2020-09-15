---
ms.date: 07/17/2020
keywords: dsc,powershell,設定,安裝
title: SendMetaConfigurationApply 方法
ms.openlocfilehash: 896afe2f3370e108b48583aafb33ee7b0eb1301b
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463715"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="c08b4-103">SendMetaConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="c08b4-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="c08b4-104">設定用於控制設定代理程式的本機設定管理員設定。</span><span class="sxs-lookup"><span data-stu-id="c08b4-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="c08b4-105">語法</span><span class="sxs-lookup"><span data-stu-id="c08b4-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="c08b4-106">參數</span><span class="sxs-lookup"><span data-stu-id="c08b4-106">Parameters</span></span>

<span data-ttu-id="c08b4-107">**ConfigurationData** \[in\] 設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="c08b4-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="c08b4-108">**force** \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="c08b4-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="c08b4-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="c08b4-109">Return value</span></span>

<span data-ttu-id="c08b4-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="c08b4-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c08b4-111">備註</span><span class="sxs-lookup"><span data-stu-id="c08b4-111">Remarks</span></span>

<span data-ttu-id="c08b4-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="c08b4-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c08b4-113">需求</span><span class="sxs-lookup"><span data-stu-id="c08b4-113">Requirements</span></span>

<span data-ttu-id="c08b4-114">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c08b4-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c08b4-115">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c08b4-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c08b4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c08b4-116">See also</span></span>

[<span data-ttu-id="c08b4-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c08b4-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
