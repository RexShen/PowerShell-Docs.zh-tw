---
ms.date: 07/17/2020
ms.topic: reference
title: TestConfiguration 方法
description: TestConfiguration 方法
ms.openlocfilehash: ed26fcad2286ca753fb4b1845b8c6ad0741d491b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648922"
---
# <a name="testconfiguration-method"></a><span data-ttu-id="ffee0-103">TestConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="ffee0-103">TestConfiguration method</span></span>

<span data-ttu-id="ffee0-104">將設定文件傳送到受管理的節點，並對文件驗證目前的設定。</span><span class="sxs-lookup"><span data-stu-id="ffee0-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="ffee0-105">語法</span><span class="sxs-lookup"><span data-stu-id="ffee0-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="ffee0-106">參數</span><span class="sxs-lookup"><span data-stu-id="ffee0-106">Parameters</span></span>

<span data-ttu-id="ffee0-107">**configurationData** \[in\] 組態的環境資料。</span><span class="sxs-lookup"><span data-stu-id="ffee0-107">**configurationData** \[in\] Environment data for the configuration.</span></span>

<span data-ttu-id="ffee0-108">**InDesiredState** \[out\] 傳回時，指定受控節點是否為設定文件所指定的狀態。</span><span class="sxs-lookup"><span data-stu-id="ffee0-108">**InDesiredState** \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="ffee0-109">**ResourcesInDesiredState** \[out\] 傳回時，包含指定資源為所需狀態之 **MSFT_ResourceInDesiredState** 類別的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="ffee0-109">**ResourcesInDesiredState** \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="ffee0-110">**ResourcesNotInDesiredState** \[out\] 傳回時，包含指定資源不為所需狀態之 **MSFT_ResourceNotInDesiredState** 類別的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="ffee0-110">**ResourcesNotInDesiredState** \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="ffee0-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="ffee0-111">Return value</span></span>

<span data-ttu-id="ffee0-112">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="ffee0-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ffee0-113">備註</span><span class="sxs-lookup"><span data-stu-id="ffee0-113">Remarks</span></span>

<span data-ttu-id="ffee0-114">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="ffee0-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ffee0-115">需求</span><span class="sxs-lookup"><span data-stu-id="ffee0-115">Requirements</span></span>

<span data-ttu-id="ffee0-116">**MOF** ：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ffee0-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ffee0-117">**命名空間** ：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ffee0-117">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ffee0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffee0-118">See also</span></span>

[<span data-ttu-id="ffee0-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ffee0-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
