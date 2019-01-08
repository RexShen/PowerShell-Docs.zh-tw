---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047378"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9cade-103">MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法</span><span class="sxs-lookup"><span data-stu-id="9cade-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9cade-104">將設定復原回先前的版本。</span><span class="sxs-lookup"><span data-stu-id="9cade-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="9cade-105">語法</span><span class="sxs-lookup"><span data-stu-id="9cade-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="9cade-106">參數</span><span class="sxs-lookup"><span data-stu-id="9cade-106">Parameters</span></span>

<span data-ttu-id="9cade-107">*configurationNumber* \[in\] 指定要求的設定。</span><span class="sxs-lookup"><span data-stu-id="9cade-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="9cade-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="9cade-108">Return value</span></span>

<span data-ttu-id="9cade-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="9cade-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9cade-110">備註</span><span class="sxs-lookup"><span data-stu-id="9cade-110">Remarks</span></span>

<span data-ttu-id="9cade-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="9cade-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9cade-112">需求</span><span class="sxs-lookup"><span data-stu-id="9cade-112">Requirements</span></span>

<span data-ttu-id="9cade-113">MOF\*\*DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9cade-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9cade-114">-NamespaceRoot\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9cade-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9cade-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cade-115">See also</span></span>

[<span data-ttu-id="9cade-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9cade-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)