---
ms.date: 07/17/2020
ms.topic: reference
title: ResourceGet 方法
description: ResourceGet 方法
ms.openlocfilehash: bff737f04e02740fa09fd82d7b27c75b11303dad
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650757"
---
# <a name="resourceget-method"></a><span data-ttu-id="500d0-103">ResourceGet 方法</span><span class="sxs-lookup"><span data-stu-id="500d0-103">ResourceGet method</span></span>

<span data-ttu-id="500d0-104">直接呼叫 DSC 資源的 **Get** 方法。</span><span class="sxs-lookup"><span data-stu-id="500d0-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="500d0-105">語法</span><span class="sxs-lookup"><span data-stu-id="500d0-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="500d0-106">參數</span><span class="sxs-lookup"><span data-stu-id="500d0-106">Parameters</span></span>

<span data-ttu-id="500d0-107">**ResourceType** \[in\] 要呼叫的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="500d0-107">**ResourceType** \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="500d0-108">**ModuleName** \[in\] 包含要呼叫之資源的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="500d0-108">**ModuleName** \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="500d0-109">**resourceProperty** \[in\] 在雜湊表中指定資源的屬性名稱與其值，分別作為機碼與值。</span><span class="sxs-lookup"><span data-stu-id="500d0-109">**resourceProperty** \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="500d0-110">使用 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) Cmdlet，探索資源的屬性和其類型。</span><span class="sxs-lookup"><span data-stu-id="500d0-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="500d0-111">**configurations** \[out\] 傳回時，包含設定的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="500d0-111">**configurations** \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="500d0-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="500d0-112">Return value</span></span>

<span data-ttu-id="500d0-113">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="500d0-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="500d0-114">備註</span><span class="sxs-lookup"><span data-stu-id="500d0-114">Remarks</span></span>

<span data-ttu-id="500d0-115">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="500d0-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="500d0-116">需求</span><span class="sxs-lookup"><span data-stu-id="500d0-116">Requirements</span></span>

<span data-ttu-id="500d0-117">**MOF** ：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="500d0-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="500d0-118">**命名空間** ：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="500d0-118">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="500d0-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="500d0-119">See also</span></span>

[<span data-ttu-id="500d0-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="500d0-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
