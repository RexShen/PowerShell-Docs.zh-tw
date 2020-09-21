---
ms.date: 07/17/2020
keywords: dsc,powershell,設定,安裝
title: ResourceTest 方法
ms.openlocfilehash: 7ef65227342091cb2a5063aaf95a2780d217f85a
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463800"
---
# <a name="resourcetest-method"></a><span data-ttu-id="2ed82-103">ResourceTest 方法</span><span class="sxs-lookup"><span data-stu-id="2ed82-103">ResourceTest method</span></span>

<span data-ttu-id="2ed82-104">直接呼叫 DSC 資源的 **Test** 方法。</span><span class="sxs-lookup"><span data-stu-id="2ed82-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="2ed82-105">語法</span><span class="sxs-lookup"><span data-stu-id="2ed82-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="2ed82-106">參數</span><span class="sxs-lookup"><span data-stu-id="2ed82-106">Parameters</span></span>

<span data-ttu-id="2ed82-107">**ResourceType** \[in\] 要呼叫的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="2ed82-107">**ResourceType** \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="2ed82-108">**ModuleName** \[in\] 包含要呼叫之資源的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="2ed82-108">**ModuleName** \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="2ed82-109">\***resourceProperty** \[in\] 會在雜湊表中將資源的屬性名稱與其值分別指定為機碼與值。</span><span class="sxs-lookup"><span data-stu-id="2ed82-109">\***resourceProperty** \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="2ed82-110">使用 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) Cmdlet，探索資源的屬性和其類型。</span><span class="sxs-lookup"><span data-stu-id="2ed82-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="2ed82-111">*InDesiredState*\* \[out\] 傳回時，如果目標節點是想要的狀態，則這個屬性會設定為 **true**。</span><span class="sxs-lookup"><span data-stu-id="2ed82-111">*InDesiredState*\* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="2ed82-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="2ed82-112">Return value</span></span>

<span data-ttu-id="2ed82-113">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="2ed82-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ed82-114">備註</span><span class="sxs-lookup"><span data-stu-id="2ed82-114">Remarks</span></span>

<span data-ttu-id="2ed82-115">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="2ed82-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ed82-116">需求</span><span class="sxs-lookup"><span data-stu-id="2ed82-116">Requirements</span></span>

<span data-ttu-id="2ed82-117">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2ed82-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="2ed82-118">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2ed82-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="2ed82-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ed82-119">See also</span></span>

[<span data-ttu-id="2ed82-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2ed82-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
