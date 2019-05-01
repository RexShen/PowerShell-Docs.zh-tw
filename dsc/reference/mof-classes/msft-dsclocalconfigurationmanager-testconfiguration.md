---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 TestConfiguration 方法
ms.openlocfilehash: d746832b01310f43a7aae33dd0fa70c0928bb3e0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078073"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fe00e-103">MSFT_DSCLocalConfigurationManager 類別的 TestConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="fe00e-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fe00e-104">將設定文件傳送到受管理的節點，並對文件驗證目前的設定。</span><span class="sxs-lookup"><span data-stu-id="fe00e-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="fe00e-105">語法</span><span class="sxs-lookup"><span data-stu-id="fe00e-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="fe00e-106">參數</span><span class="sxs-lookup"><span data-stu-id="fe00e-106">Parameters</span></span>

<span data-ttu-id="fe00e-107">*configurationData* \[in\] 設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="fe00e-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="fe00e-108">*InDesiredState* \[out\] 傳回時，指定受控節點是否為設定文件所指定的狀態。</span><span class="sxs-lookup"><span data-stu-id="fe00e-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="fe00e-109">*ResourcesInDesiredState* \[out\] 傳回時，包含指定資源為所需狀態之 **MSFT_ResourceInDesiredState** 類別的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="fe00e-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="fe00e-110">*ResourcesNotInDesiredState* \[out\] 傳回時，包含指定資源不為所需狀態之 **MSFT_ResourceNotInDesiredState** 類別的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="fe00e-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="fe00e-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="fe00e-111">Return value</span></span>

<span data-ttu-id="fe00e-112">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="fe00e-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fe00e-113">備註</span><span class="sxs-lookup"><span data-stu-id="fe00e-113">Remarks</span></span>

<span data-ttu-id="fe00e-114">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="fe00e-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fe00e-115">需求</span><span class="sxs-lookup"><span data-stu-id="fe00e-115">Requirements</span></span>

<span data-ttu-id="fe00e-116">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fe00e-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="fe00e-117">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fe00e-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="fe00e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe00e-118">See also</span></span>

[<span data-ttu-id="fe00e-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fe00e-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)