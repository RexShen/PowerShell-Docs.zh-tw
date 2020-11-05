---
ms.date: 08/11/2020
keywords: dsc,powershell,設定,安裝
title: 直接呼叫 DSC 資源方法
description: Invoke-DscResource Cmdlet 可以用來呼叫 DSC 資源的函式或方法。 其可由想要使用 DSC 資源的協力廠商使用，或是作為開發資源時的有用工具。
ms.openlocfilehash: 5ccf0f589b60cef4ec197d1e0a583af9ed60d5e7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650999"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="d8c95-105">直接呼叫 DSC 資源方法</span><span class="sxs-lookup"><span data-stu-id="d8c95-105">Calling DSC resource methods directly</span></span>

> <span data-ttu-id="d8c95-106">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d8c95-106">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d8c95-107">您可使用 [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) Cmdlet，直接呼叫 DSC 資源的函式或方法 (MOF 形資源的 `Get-TargetResource`、`Set-TargetResource` 和 `Test-TargetResource` 函式，或類別形資源的 **Get** 、 **Set** 和 **Test** 方法)。</span><span class="sxs-lookup"><span data-stu-id="d8c95-107">You can use the [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet to directly call the functions or methods of a DSC resource (The `Get-TargetResource`, `Set-TargetResource`, and `Test-TargetResource` functions of a MOF-based resource, or the **Get** , **Set** , and **Test** methods of a class-based resource).</span></span> <span data-ttu-id="d8c95-108">這類方法適用於協力廠商想要使用 DSC 資源時，或是作為開發資源的有力工具。</span><span class="sxs-lookup"><span data-stu-id="d8c95-108">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

> [!NOTE]
> <span data-ttu-id="d8c95-109">在 PowerShell 7.0 以上的版本中，`Invoke-DscResource` 不再支援叫用 WMI DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="d8c95-109">In PowerShell 7.0+, `Invoke-DscResource` no longer supports invoking WMI DSC resources.</span></span> <span data-ttu-id="d8c95-110">這包括 **PSDesiredStateConfiguration** 中的 **檔案** 和 **記錄** 資源。</span><span class="sxs-lookup"><span data-stu-id="d8c95-110">This includes the **File** and **Log** resources in **PSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="d8c95-111">這個 Cmdlet 通常搭配中繼設定屬性 `refreshMode = 'Disabled'` 一起使用，但可用於任何 **refreshMode** 設定。</span><span class="sxs-lookup"><span data-stu-id="d8c95-111">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="d8c95-112">呼叫 `Invoke-DscResource` Cmdlet 時，您可使用 **Method** 參數來指定要呼叫的方法或函式。</span><span class="sxs-lookup"><span data-stu-id="d8c95-112">When calling the `Invoke-DscResource` cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="d8c95-113">您指定資源的屬性，方法是將雜湊表作為 **Property** 參數值加以傳遞。</span><span class="sxs-lookup"><span data-stu-id="d8c95-113">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="d8c95-114">直接呼叫資源方法的範例如下︰</span><span class="sxs-lookup"><span data-stu-id="d8c95-114">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="d8c95-115">請確定檔案存在</span><span class="sxs-lookup"><span data-stu-id="d8c95-115">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
              DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
              Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="d8c95-116">請測試檔案存在</span><span class="sxs-lookup"><span data-stu-id="d8c95-116">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="d8c95-117">請取得檔案的內容</span><span class="sxs-lookup"><span data-stu-id="d8c95-117">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

> [!NOTE]
> <span data-ttu-id="d8c95-118">不支援直接呼叫複合資源方法。</span><span class="sxs-lookup"><span data-stu-id="d8c95-118">Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="d8c95-119">請改為呼叫組成複合資源之基礎資源的方法。</span><span class="sxs-lookup"><span data-stu-id="d8c95-119">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8c95-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8c95-120">See Also</span></span>

- [<span data-ttu-id="d8c95-121">撰寫自訂的 DSC 資源與 MOF</span><span class="sxs-lookup"><span data-stu-id="d8c95-121">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="d8c95-122">使用 PowerShell 類別撰寫自訂的 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="d8c95-122">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
- [<span data-ttu-id="d8c95-123">對 DSC 資源執行偵錯</span><span class="sxs-lookup"><span data-stu-id="d8c95-123">Debugging DSC resources</span></span>](../troubleshooting/debugResource.md)
