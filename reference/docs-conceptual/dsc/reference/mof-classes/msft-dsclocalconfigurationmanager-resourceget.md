---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: ResourceGet 方法
ms.openlocfilehash: dbe610dfcef5ef6c79783801ecb6fdb7408bdfa5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954995"
---
# <a name="resourceget-method"></a><span data-ttu-id="fee01-103">ResourceGet 方法</span><span class="sxs-lookup"><span data-stu-id="fee01-103">ResourceGet method</span></span>

<span data-ttu-id="fee01-104">直接呼叫 DSC 資源的 **Get** 方法。</span><span class="sxs-lookup"><span data-stu-id="fee01-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="fee01-105">語法</span><span class="sxs-lookup"><span data-stu-id="fee01-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="fee01-106">參數</span><span class="sxs-lookup"><span data-stu-id="fee01-106">Parameters</span></span>

<span data-ttu-id="fee01-107">*ResourceType* \[in\] 要呼叫的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="fee01-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="fee01-108">*ModuleName* \[in\] 包含要呼叫之資源的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="fee01-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="fee01-109">*resourceProperty* \[in\] 在雜湊表中指定資源的屬性名稱與其值，分別作為索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="fee01-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="fee01-110">使用 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) Cmdlet，探索資源的屬性和其類型。</span><span class="sxs-lookup"><span data-stu-id="fee01-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="fee01-111">*configurations* \[out\] 傳回時，包含設定的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="fee01-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="fee01-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="fee01-112">Return value</span></span>

<span data-ttu-id="fee01-113">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="fee01-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fee01-114">備註</span><span class="sxs-lookup"><span data-stu-id="fee01-114">Remarks</span></span>

<span data-ttu-id="fee01-115">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="fee01-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fee01-116">需求</span><span class="sxs-lookup"><span data-stu-id="fee01-116">Requirements</span></span>

<span data-ttu-id="fee01-117">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fee01-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="fee01-118">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fee01-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="fee01-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fee01-119">See also</span></span>

[<span data-ttu-id="fee01-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fee01-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
