---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 SendConfiguration 方法
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047124"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0bd54-103">MSFT_DSCLocalConfigurationManager 類別的 SendConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="0bd54-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0bd54-104">將設定文件傳送到受管理的節點，並將其儲存為擱置變更。</span><span class="sxs-lookup"><span data-stu-id="0bd54-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="0bd54-105">語法</span><span class="sxs-lookup"><span data-stu-id="0bd54-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="0bd54-106">參數</span><span class="sxs-lookup"><span data-stu-id="0bd54-106">Parameters</span></span>

<span data-ttu-id="0bd54-107">*ConfigurationData* \[in\] 設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="0bd54-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="0bd54-108">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="0bd54-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="0bd54-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="0bd54-109">Return value</span></span>

<span data-ttu-id="0bd54-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="0bd54-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0bd54-111">備註</span><span class="sxs-lookup"><span data-stu-id="0bd54-111">Remarks</span></span>

<span data-ttu-id="0bd54-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="0bd54-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0bd54-113">需求</span><span class="sxs-lookup"><span data-stu-id="0bd54-113">Requirements</span></span>

<span data-ttu-id="0bd54-114">MOF\*\*DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0bd54-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0bd54-115">-NamespaceRoot\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0bd54-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0bd54-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bd54-116">See also</span></span>

[<span data-ttu-id="0bd54-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0bd54-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)