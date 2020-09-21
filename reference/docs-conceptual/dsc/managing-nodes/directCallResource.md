---
ms.date: 08/11/2020
keywords: dsc,powershell,設定,安裝
title: 直接呼叫 DSC 資源方法
ms.openlocfilehash: 029a278c938e414820e172b85fac3cb3ad4b4afa
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2020
ms.locfileid: "88162489"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="25582-103">直接呼叫 DSC 資源方法</span><span class="sxs-lookup"><span data-stu-id="25582-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="25582-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="25582-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="25582-105">您可使用[Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) Cmdlet，直接呼叫 DSC 資源的函式或方法 (MOF 形資源的 `Get-TargetResource`、`Set-TargetResource` 和 `Test-TargetResource` 函式，或類別形資源的 **Get**、**Set** 和 **Test** 方法)。</span><span class="sxs-lookup"><span data-stu-id="25582-105">You can use the [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet to directly call the functions or methods of a DSC resource (The `Get-TargetResource`, `Set-TargetResource`, and `Test-TargetResource` functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span> <span data-ttu-id="25582-106">這類方法適用於協力廠商想要使用 DSC 資源時，或是作為開發資源的有力工具。</span><span class="sxs-lookup"><span data-stu-id="25582-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

> [!NOTE]
> <span data-ttu-id="25582-107">在 PowerShell 7.0 以上的版本中，`Invoke-DscResource` 不再支援叫用 WMI DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="25582-107">In PowerShell 7.0+, `Invoke-DscResource` no longer supports invoking WMI DSC resources.</span></span> <span data-ttu-id="25582-108">這包括 **PSDesiredStateConfiguration** 中的**檔案**和**記錄**資源。</span><span class="sxs-lookup"><span data-stu-id="25582-108">This includes the **File** and **Log** resources in **PSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="25582-109">這個 Cmdlet 通常搭配中繼設定屬性 `refreshMode = 'Disabled'` 一起使用，但可用於任何 **refreshMode** 設定。</span><span class="sxs-lookup"><span data-stu-id="25582-109">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="25582-110">呼叫 `Invoke-DscResource` Cmdlet 時，您可使用 **Method** 參數來指定要呼叫的方法或函式。</span><span class="sxs-lookup"><span data-stu-id="25582-110">When calling the `Invoke-DscResource` cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="25582-111">您指定資源的屬性，方法是將雜湊表作為 **Property** 參數值加以傳遞。</span><span class="sxs-lookup"><span data-stu-id="25582-111">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="25582-112">直接呼叫資源方法的範例如下︰</span><span class="sxs-lookup"><span data-stu-id="25582-112">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="25582-113">請確定檔案存在</span><span class="sxs-lookup"><span data-stu-id="25582-113">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
              DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
              Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="25582-114">請測試檔案存在</span><span class="sxs-lookup"><span data-stu-id="25582-114">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="25582-115">請取得檔案的內容</span><span class="sxs-lookup"><span data-stu-id="25582-115">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

>[!NOTE]
> <span data-ttu-id="25582-116">不支援直接呼叫複合資源方法。</span><span class="sxs-lookup"><span data-stu-id="25582-116">Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="25582-117">請改為呼叫組成複合資源之基礎資源的方法。</span><span class="sxs-lookup"><span data-stu-id="25582-117">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="25582-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25582-118">See Also</span></span>

- [<span data-ttu-id="25582-119">撰寫自訂的 DSC 資源與 MOF</span><span class="sxs-lookup"><span data-stu-id="25582-119">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="25582-120">使用 PowerShell 類別撰寫自訂的 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="25582-120">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
- [<span data-ttu-id="25582-121">對 DSC 資源執行偵錯</span><span class="sxs-lookup"><span data-stu-id="25582-121">Debugging DSC resources</span></span>](../troubleshooting/debugResource.md)
