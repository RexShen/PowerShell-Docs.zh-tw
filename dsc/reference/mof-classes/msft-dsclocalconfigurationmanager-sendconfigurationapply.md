---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApply 方法
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078245"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c5e05-103">MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="c5e05-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c5e05-104">將設定文件傳送到受管理的節點，並使用設定代理程式套用設定。</span><span class="sxs-lookup"><span data-stu-id="c5e05-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="c5e05-105">語法</span><span class="sxs-lookup"><span data-stu-id="c5e05-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="c5e05-106">參數</span><span class="sxs-lookup"><span data-stu-id="c5e05-106">Parameters</span></span>

<span data-ttu-id="c5e05-107">*ConfigurationData* \[in\] 設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="c5e05-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="c5e05-108">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="c5e05-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="c5e05-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="c5e05-109">Return value</span></span>

<span data-ttu-id="c5e05-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="c5e05-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c5e05-111">備註</span><span class="sxs-lookup"><span data-stu-id="c5e05-111">Remarks</span></span>

<span data-ttu-id="c5e05-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="c5e05-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c5e05-113">需求</span><span class="sxs-lookup"><span data-stu-id="c5e05-113">Requirements</span></span>

<span data-ttu-id="c5e05-114">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c5e05-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c5e05-115">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c5e05-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c5e05-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5e05-116">See also</span></span>

[<span data-ttu-id="c5e05-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c5e05-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)