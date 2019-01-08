---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 ResourceSet 方法
ms.openlocfilehash: 2712b7ff0a19e643c1f343d436c084f8970c9dd4
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047327"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a1698-103">MSFT_DSCLocalConfigurationManager 類別的 ResourceSet 方法</span><span class="sxs-lookup"><span data-stu-id="a1698-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a1698-104">直接呼叫 DSC 資源的 **Set** 方法。</span><span class="sxs-lookup"><span data-stu-id="a1698-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="a1698-105">語法</span><span class="sxs-lookup"><span data-stu-id="a1698-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="a1698-106">參數</span><span class="sxs-lookup"><span data-stu-id="a1698-106">Parameters</span></span>

<span data-ttu-id="a1698-107">*ResourceType* \[in\] 要呼叫的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="a1698-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="a1698-108">*ModuleName* \[in\] 包含要呼叫之資源的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="a1698-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="a1698-109">*resourceProperty* \[in\] 在雜湊表中指定資源的屬性名稱與其值，分別作為索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="a1698-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="a1698-110">使用 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) Cmdlet，探索資源的屬性和其類型。</span><span class="sxs-lookup"><span data-stu-id="a1698-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="a1698-111">*RebootRequired* \[out\] 傳回時，如果需要重新啟動目標節點，這個屬性會設定為 **true**。</span><span class="sxs-lookup"><span data-stu-id="a1698-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="a1698-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="a1698-112">Return value</span></span>

<span data-ttu-id="a1698-113">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="a1698-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a1698-114">備註</span><span class="sxs-lookup"><span data-stu-id="a1698-114">Remarks</span></span>

<span data-ttu-id="a1698-115">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="a1698-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a1698-116">需求</span><span class="sxs-lookup"><span data-stu-id="a1698-116">Requirements</span></span>

<span data-ttu-id="a1698-117">MOF\*\*DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a1698-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a1698-118">-NamespaceRoot\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a1698-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a1698-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1698-119">See also</span></span>

[<span data-ttu-id="a1698-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a1698-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)