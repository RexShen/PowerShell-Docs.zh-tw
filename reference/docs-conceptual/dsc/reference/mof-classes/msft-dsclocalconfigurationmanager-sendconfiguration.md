---
ms.date: 07/17/2020
ms.topic: reference
title: SendConfiguration 方法
description: SendConfiguration 方法
ms.openlocfilehash: 3939a76ab6672b49559847b0ef1408f1c7be6d0c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650552"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="10b90-103">SendConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="10b90-103">SendConfiguration method</span></span>

<span data-ttu-id="10b90-104">將設定文件傳送到受管理的節點，並將其儲存為擱置變更。</span><span class="sxs-lookup"><span data-stu-id="10b90-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="10b90-105">語法</span><span class="sxs-lookup"><span data-stu-id="10b90-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="10b90-106">參數</span><span class="sxs-lookup"><span data-stu-id="10b90-106">Parameters</span></span>

<span data-ttu-id="10b90-107">**ConfigurationData** \[in\] 設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="10b90-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="10b90-108">**force** \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="10b90-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="10b90-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="10b90-109">Return value</span></span>

<span data-ttu-id="10b90-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="10b90-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="10b90-111">備註</span><span class="sxs-lookup"><span data-stu-id="10b90-111">Remarks</span></span>

<span data-ttu-id="10b90-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="10b90-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="10b90-113">需求</span><span class="sxs-lookup"><span data-stu-id="10b90-113">Requirements</span></span>

<span data-ttu-id="10b90-114">**MOF** ：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="10b90-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="10b90-115">**命名空間** ：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="10b90-115">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="10b90-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10b90-116">See also</span></span>

[<span data-ttu-id="10b90-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="10b90-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
