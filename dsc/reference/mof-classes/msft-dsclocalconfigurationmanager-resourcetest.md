---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 ResourceTest 方法
ms.openlocfilehash: e7645b0c6b93b96cb01f72c1c92d468f7642ea13
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078549"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4d3ea-103">MSFT_DSCLocalConfigurationManager 類別的 ResourceTest 方法</span><span class="sxs-lookup"><span data-stu-id="4d3ea-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4d3ea-104">直接呼叫 DSC 資源的 **Test** 方法。</span><span class="sxs-lookup"><span data-stu-id="4d3ea-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="4d3ea-105">語法</span><span class="sxs-lookup"><span data-stu-id="4d3ea-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="4d3ea-106">參數</span><span class="sxs-lookup"><span data-stu-id="4d3ea-106">Parameters</span></span>

<span data-ttu-id="4d3ea-107">*ResourceType* \[in\] 要呼叫的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="4d3ea-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="4d3ea-108">*ModuleName* \[in\] 包含要呼叫之資源的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="4d3ea-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="4d3ea-109">*resourceProperty* \[in\] 在雜湊表中指定資源的屬性名稱與其值，分別作為索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="4d3ea-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="4d3ea-110">使用 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) Cmdlet，探索資源的屬性和其類型。</span><span class="sxs-lookup"><span data-stu-id="4d3ea-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="4d3ea-111">*InDesiredState* \[out\] 傳回時，如果目標節點是想要的狀態，這個屬性會設定為 **true**。</span><span class="sxs-lookup"><span data-stu-id="4d3ea-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="4d3ea-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="4d3ea-112">Return value</span></span>

<span data-ttu-id="4d3ea-113">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="4d3ea-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4d3ea-114">備註</span><span class="sxs-lookup"><span data-stu-id="4d3ea-114">Remarks</span></span>

<span data-ttu-id="4d3ea-115">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="4d3ea-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4d3ea-116">需求</span><span class="sxs-lookup"><span data-stu-id="4d3ea-116">Requirements</span></span>

<span data-ttu-id="4d3ea-117">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4d3ea-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4d3ea-118">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4d3ea-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4d3ea-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d3ea-119">See also</span></span>

[<span data-ttu-id="4d3ea-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4d3ea-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)