---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 SendMetaConfigurationApply 方法
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047435"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7b7cf-103">MSFT_DSCLocalConfigurationManager 類別的 SendMetaConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="7b7cf-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7b7cf-104">設定用於控制設定代理程式的本機設定管理員設定。</span><span class="sxs-lookup"><span data-stu-id="7b7cf-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="7b7cf-105">語法</span><span class="sxs-lookup"><span data-stu-id="7b7cf-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="7b7cf-106">參數</span><span class="sxs-lookup"><span data-stu-id="7b7cf-106">Parameters</span></span>

<span data-ttu-id="7b7cf-107">*ConfigurationData* \[in\] 設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="7b7cf-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="7b7cf-108">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="7b7cf-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="7b7cf-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="7b7cf-109">Return value</span></span>

<span data-ttu-id="7b7cf-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="7b7cf-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7b7cf-111">備註</span><span class="sxs-lookup"><span data-stu-id="7b7cf-111">Remarks</span></span>

<span data-ttu-id="7b7cf-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="7b7cf-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7b7cf-113">需求</span><span class="sxs-lookup"><span data-stu-id="7b7cf-113">Requirements</span></span>

<span data-ttu-id="7b7cf-114">MOF\*\*DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7b7cf-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7b7cf-115">-NamespaceRoot\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7b7cf-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7b7cf-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b7cf-116">See also</span></span>

[<span data-ttu-id="7b7cf-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7b7cf-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)