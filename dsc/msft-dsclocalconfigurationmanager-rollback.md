---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893013"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="28397-103">MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法</span><span class="sxs-lookup"><span data-stu-id="28397-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="28397-104">將設定復原回先前的版本。</span><span class="sxs-lookup"><span data-stu-id="28397-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="28397-105">語法</span><span class="sxs-lookup"><span data-stu-id="28397-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="28397-106">參數</span><span class="sxs-lookup"><span data-stu-id="28397-106">Parameters</span></span>

<span data-ttu-id="28397-107">*configurationNumber* \[in\] 指定要求的設定。</span><span class="sxs-lookup"><span data-stu-id="28397-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="28397-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="28397-108">Return value</span></span>

<span data-ttu-id="28397-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="28397-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="28397-110">備註</span><span class="sxs-lookup"><span data-stu-id="28397-110">Remarks</span></span>

<span data-ttu-id="28397-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="28397-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="28397-112">需求</span><span class="sxs-lookup"><span data-stu-id="28397-112">Requirements</span></span>

<span data-ttu-id="28397-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="28397-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="28397-114">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="28397-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="28397-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28397-115">See also</span></span>

[<span data-ttu-id="28397-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="28397-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)