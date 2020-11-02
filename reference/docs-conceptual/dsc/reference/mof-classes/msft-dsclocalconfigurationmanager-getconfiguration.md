---
ms.date: 07/17/2020
ms.topic: reference
title: GetConfiguration 方法
description: GetConfiguration 方法
ms.openlocfilehash: a49f810bd227142c8c3ae4de45f69450400e4e8c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650887"
---
# <a name="getconfiguration-method"></a><span data-ttu-id="41702-103">GetConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="41702-103">GetConfiguration method</span></span>

<span data-ttu-id="41702-104">將設定文件傳送到受管理的節點，並使用設定代理程式的 **Get** 方法來套用設定。</span><span class="sxs-lookup"><span data-stu-id="41702-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="41702-105">語法</span><span class="sxs-lookup"><span data-stu-id="41702-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="41702-106">參數</span><span class="sxs-lookup"><span data-stu-id="41702-106">Parameters</span></span>

<span data-ttu-id="41702-107">**configurationData** \[in\] 指定要傳送的設定資料。</span><span class="sxs-lookup"><span data-stu-id="41702-107">**configurationData** \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="41702-108">**configurations** \[out\] 傳回時，包含設定的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="41702-108">**configurations** \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="41702-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="41702-109">Return value</span></span>

<span data-ttu-id="41702-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="41702-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="41702-111">備註</span><span class="sxs-lookup"><span data-stu-id="41702-111">Remarks</span></span>

<span data-ttu-id="41702-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="41702-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="41702-113">需求</span><span class="sxs-lookup"><span data-stu-id="41702-113">Requirements</span></span>

<span data-ttu-id="41702-114">**MOF** ：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="41702-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="41702-115">**命名空間** ：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="41702-115">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="41702-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41702-116">See also</span></span>

[<span data-ttu-id="41702-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="41702-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
