---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 ResourceGet 方法
ms.openlocfilehash: 1b74adf2327af2e0f9416f1d00eac4e3b75e9013
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078566"
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8fd90-103">MSFT_DSCLocalConfigurationManager 類別的 ResourceGet 方法</span><span class="sxs-lookup"><span data-stu-id="8fd90-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8fd90-104">直接呼叫 DSC 資源的 **Get** 方法。</span><span class="sxs-lookup"><span data-stu-id="8fd90-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="8fd90-105">語法</span><span class="sxs-lookup"><span data-stu-id="8fd90-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="8fd90-106">參數</span><span class="sxs-lookup"><span data-stu-id="8fd90-106">Parameters</span></span>

<span data-ttu-id="8fd90-107">*ResourceType* \[in\] 要呼叫的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="8fd90-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="8fd90-108">*ModuleName* \[in\] 包含要呼叫之資源的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="8fd90-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="8fd90-109">*resourceProperty* \[in\] 在雜湊表中指定資源的屬性名稱與其值，分別作為索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="8fd90-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="8fd90-110">使用 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) Cmdlet，探索資源的屬性和其類型。</span><span class="sxs-lookup"><span data-stu-id="8fd90-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="8fd90-111">*configurations* \[out\] 傳回時，包含設定的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="8fd90-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="8fd90-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="8fd90-112">Return value</span></span>

<span data-ttu-id="8fd90-113">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8fd90-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8fd90-114">備註</span><span class="sxs-lookup"><span data-stu-id="8fd90-114">Remarks</span></span>

<span data-ttu-id="8fd90-115">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="8fd90-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8fd90-116">需求</span><span class="sxs-lookup"><span data-stu-id="8fd90-116">Requirements</span></span>

<span data-ttu-id="8fd90-117">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8fd90-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8fd90-118">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8fd90-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8fd90-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fd90-119">See also</span></span>

[<span data-ttu-id="8fd90-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8fd90-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)