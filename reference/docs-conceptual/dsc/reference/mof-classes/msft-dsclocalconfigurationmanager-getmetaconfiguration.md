---
ms.date: 07/17/2020
ms.topic: reference
title: GetMetaConfiguration 方法
description: GetMetaConfiguration 方法
ms.openlocfilehash: deca6b8ec342a34543bbe0e1fabbc2a740a88feb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644733"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="49356-103">GetMetaConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="49356-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="49356-104">取得用於控制設定代理程式的本機設定管理員設定。</span><span class="sxs-lookup"><span data-stu-id="49356-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="49356-105">語法</span><span class="sxs-lookup"><span data-stu-id="49356-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="49356-106">參數</span><span class="sxs-lookup"><span data-stu-id="49356-106">Parameters</span></span>

<span data-ttu-id="49356-107">**MetaConfiguration** \[out\] 傳回時，包含定義設定之 **MSFT_DSCMetaConfiguration** 類別的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="49356-107">**MetaConfiguration** \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="49356-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="49356-108">Return value</span></span>

<span data-ttu-id="49356-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="49356-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="49356-110">備註</span><span class="sxs-lookup"><span data-stu-id="49356-110">Remarks</span></span>

<span data-ttu-id="49356-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="49356-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="49356-112">需求</span><span class="sxs-lookup"><span data-stu-id="49356-112">Requirements</span></span>

<span data-ttu-id="49356-113">**MOF** ：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="49356-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="49356-114">**命名空間** ：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="49356-114">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="49356-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49356-115">See also</span></span>

[<span data-ttu-id="49356-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="49356-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
