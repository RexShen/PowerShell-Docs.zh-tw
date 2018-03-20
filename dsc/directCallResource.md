---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "直接呼叫 DSC 資源方法"
ms.openlocfilehash: 68344d1be5c41e5ce4660e0a62019fa0a52c2541
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="9e29f-103">直接呼叫 DSC 資源方法</span><span class="sxs-lookup"><span data-stu-id="9e29f-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="9e29f-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9e29f-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="9e29f-105">您可以使用 [Invoke DscResource](https://technet.microsoft.com/library/mt517869.aspx) Cmdlet，直接呼叫 DSC 資源的函數或方法 (MOF 形式資源的 **Get-TargetResource**、**Set-TargetResource** 以及 **Test-TargetResource** 函數，或是類別形式資源的 **Get**、**Set** 與 **Test** 方法)。</span><span class="sxs-lookup"><span data-stu-id="9e29f-105">You can use the [Invoke-DscResource](https://technet.microsoft.com/library/mt517869.aspx) cmdlet to directly call the functions or methods of a DSC resource (The **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span> <span data-ttu-id="9e29f-106">這類方法適用於協力廠商想要使用 DSC 資源時，或是作為開發資源的有力工具。</span><span class="sxs-lookup"><span data-stu-id="9e29f-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span> 

<span data-ttu-id="9e29f-107">這個 Cmdlet 通常搭配中繼設定屬性 `refreshMode = 'Disabled'` 一起使用，但可用於任何 **refreshMode** 設定。</span><span class="sxs-lookup"><span data-stu-id="9e29f-107">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="9e29f-108">呼叫 **Invoke DscResource** Cmdlet 時，可以使用 **Method** 參數來指定要呼叫的方法或函數。</span><span class="sxs-lookup"><span data-stu-id="9e29f-108">When calling the **Invoke-DscResource** cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="9e29f-109">您指定資源的屬性，方法是將雜湊表作為 **Property** 參數值加以傳遞。</span><span class="sxs-lookup"><span data-stu-id="9e29f-109">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="9e29f-110">直接呼叫資源方法的範例如下︰</span><span class="sxs-lookup"><span data-stu-id="9e29f-110">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="9e29f-111">請確定檔案存在</span><span class="sxs-lookup"><span data-stu-id="9e29f-111">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="9e29f-112">請測試檔案存在</span><span class="sxs-lookup"><span data-stu-id="9e29f-112">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="9e29f-113">請取得檔案的內容</span><span class="sxs-lookup"><span data-stu-id="9e29f-113">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

><span data-ttu-id="9e29f-114">**注意︰** 不支援直接呼叫複合資源方法。</span><span class="sxs-lookup"><span data-stu-id="9e29f-114">**Note:** Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="9e29f-115">請改為呼叫組成複合資源之基礎資源的方法。</span><span class="sxs-lookup"><span data-stu-id="9e29f-115">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e29f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e29f-116">See Also</span></span>
- [<span data-ttu-id="9e29f-117">撰寫自訂的 DSC 資源與 MOF</span><span class="sxs-lookup"><span data-stu-id="9e29f-117">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md) 
- [<span data-ttu-id="9e29f-118">使用 PowerShell 類別撰寫自訂的 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="9e29f-118">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
- [<span data-ttu-id="9e29f-119">對 DSC 資源執行偵錯</span><span class="sxs-lookup"><span data-stu-id="9e29f-119">Debugging DSC resources</span></span>](debugResource.md)

