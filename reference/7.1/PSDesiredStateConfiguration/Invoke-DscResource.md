---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: 8425c3e68573fe214ec5de465c8492e0bf99b309
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2020
ms.locfileid: "93206055"
---
# <span data-ttu-id="56803-103">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="56803-103">Invoke-DscResource</span></span>

## <span data-ttu-id="56803-104">概要</span><span class="sxs-lookup"><span data-stu-id="56803-104">SYNOPSIS</span></span>
<span data-ttu-id="56803-105">執行指定 PowerShell Desired State Configuration (DSC) 資源的方法。</span><span class="sxs-lookup"><span data-stu-id="56803-105">Runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

## <span data-ttu-id="56803-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="56803-106">SYNTAX</span></span>

```
Invoke-DscResource [-Name] <String> [[-ModuleName] <ModuleSpecification>] [-Method] <String>
 [-Property] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="56803-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="56803-107">DESCRIPTION</span></span>

<span data-ttu-id="56803-108">`Invoke-DscResource` Cmdlet 會執行指定之 PowerShell Desired State Configuration (DSC) 資源的方法。</span><span class="sxs-lookup"><span data-stu-id="56803-108">The `Invoke-DscResource` cmdlet runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

<span data-ttu-id="56803-109">此 Cmdlet 會直接叫用 DSC 資源，而不需建立設定文件。</span><span class="sxs-lookup"><span data-stu-id="56803-109">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span> <span data-ttu-id="56803-110">使用此 Cmdlet，設定管理產品可以使用 DSC 資源來管理 windows 或 Linux。</span><span class="sxs-lookup"><span data-stu-id="56803-110">Using this cmdlet, configuration management products can manage windows or Linux by using DSC resources.</span></span> <span data-ttu-id="56803-111">當 DSC 引擎在啟用了偵錯的情況下執行時，此 Cmdlet 也會啟用資源的偵錯。</span><span class="sxs-lookup"><span data-stu-id="56803-111">This cmdlet also enables debugging of resources when the DSC engine is running with debugging enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="56803-112">`Invoke-DscResource` 是 PowerShell 7 中的實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="56803-112">`Invoke-DscResource` is an experimental feature in PowerShell 7.</span></span> <span data-ttu-id="56803-113">若要使用 Cmdlet，您必須使用下列命令來啟用它。</span><span class="sxs-lookup"><span data-stu-id="56803-113">To use the cmdlet, you must enable it using the following command.</span></span>
>
> `Enable-ExperimentalFeature PSDesiredStateConfiguration.InvokeDscResource`

## <span data-ttu-id="56803-114">範例</span><span class="sxs-lookup"><span data-stu-id="56803-114">EXAMPLES</span></span>

### <span data-ttu-id="56803-115">範例1：指定資源的必要屬性來叫用資源的 Set 方法</span><span class="sxs-lookup"><span data-stu-id="56803-115">Example 1: Invoke the Set method of a resource by specifying its mandatory properties</span></span>

<span data-ttu-id="56803-116">這個範例會叫用名為 **WindowsProcess** 之資源的 **Set** 方法，並提供必要的 **Path** 和 **Arguments** 屬性來啟動指定的 Windows 進程。</span><span class="sxs-lookup"><span data-stu-id="56803-116">This example invokes the **Set** method of a resource named **WindowsProcess** and provides the mandatory **Path** and **Arguments** properties to start the specified Windows process.</span></span>

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

### <span data-ttu-id="56803-117">範例2：叫用指定模組之資源的測試方法</span><span class="sxs-lookup"><span data-stu-id="56803-117">Example 2: Invoke the Test method of a resource for a specified module</span></span>

<span data-ttu-id="56803-118">這個範例會叫用名為 **WindowsProcess** 之資源的 **測試** 方法，該資源位於名為 **PSDesiredStateConfiguration** 的模組中。</span><span class="sxs-lookup"><span data-stu-id="56803-118">This example invokes the **Test** method of a resource named **WindowsProcess** , which is in the module named **PSDesiredStateConfiguration** .</span></span>

```powershell
$SplatParam = @{
  Name = 'WindowsProcess'
  ModuleName = 'PSDesiredStateConfiguration'
  Property = @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''}
  Method = Test
}

Invoke-DscResource @SplatParam
```

## <span data-ttu-id="56803-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="56803-119">PARAMETERS</span></span>

### <span data-ttu-id="56803-120">-Method</span><span class="sxs-lookup"><span data-stu-id="56803-120">-Method</span></span>

<span data-ttu-id="56803-121">指定此 Cmdlet 叫用之資源的方法。</span><span class="sxs-lookup"><span data-stu-id="56803-121">Specifies the method of the resource that this cmdlet invokes.</span></span> <span data-ttu-id="56803-122">此參數可接受的值為： **Get** 、 **Set** 和 **Test** 。</span><span class="sxs-lookup"><span data-stu-id="56803-122">The acceptable values for this parameter are: **Get** , **Set** , and **Test** .</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56803-123">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="56803-123">-ModuleName</span></span>

<span data-ttu-id="56803-124">指定此 Cmdlet 用來叫用指定之資源的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="56803-124">Specifies the name of the module from which this cmdlet invokes the specified resource.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="56803-125">-Name</span><span class="sxs-lookup"><span data-stu-id="56803-125">-Name</span></span>

<span data-ttu-id="56803-126">指定要啟動之 DSC 資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="56803-126">Specifies the name of the DSC resource to start.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="56803-127">-Property</span><span class="sxs-lookup"><span data-stu-id="56803-127">-Property</span></span>

<span data-ttu-id="56803-128">在雜湊表中指定資源的屬性名稱與其值，分別作為索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="56803-128">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56803-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="56803-129">CommonParameters</span></span>

<span data-ttu-id="56803-130">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="56803-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="56803-131">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="56803-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="56803-132">輸入</span><span class="sxs-lookup"><span data-stu-id="56803-132">INPUTS</span></span>

### <span data-ttu-id="56803-133">System.String</span><span class="sxs-lookup"><span data-stu-id="56803-133">System.String</span></span>

### <span data-ttu-id="56803-134">ModuleSpecification。</span><span class="sxs-lookup"><span data-stu-id="56803-134">Microsoft.PowerShell.Commands.ModuleSpecification</span></span>

## <span data-ttu-id="56803-135">輸出</span><span class="sxs-lookup"><span data-stu-id="56803-135">OUTPUTS</span></span>

### <span data-ttu-id="56803-136">System.Object</span><span class="sxs-lookup"><span data-stu-id="56803-136">System.Object</span></span>

## <span data-ttu-id="56803-137">注意</span><span class="sxs-lookup"><span data-stu-id="56803-137">NOTES</span></span>

- <span data-ttu-id="56803-138">先前，除非使用金鑰 **PsDscRunAsCredential** 以使用者內容指定，否則 Windows PowerShell 5.1 資源會在系統內容下執行。</span><span class="sxs-lookup"><span data-stu-id="56803-138">Previously, Windows PowerShell 5.1 resources ran under System context unless specified with user context using the key **PsDscRunAsCredential** .</span></span> <span data-ttu-id="56803-139">在 PowerShell 7.0 中，資源會在使用者的內容中執行，且不再支援 **PsDscRunAsCredential** 。</span><span class="sxs-lookup"><span data-stu-id="56803-139">In PowerShell 7.0, Resources run in the user's context, and **PsDscRunAsCredential** is no longer supported.</span></span> <span data-ttu-id="56803-140">先前使用此金鑰的設定將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="56803-140">Previous configurations using this key will throw an exception.</span></span>

- <span data-ttu-id="56803-141">從 PowerShell 7， `Invoke-DscResource` 不再支援叫用 WMI DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="56803-141">As of PowerShell 7, `Invoke-DscResource` no longer supports invoking WMI DSC resources.</span></span> <span data-ttu-id="56803-142">這包括 **PSDesiredStateConfiguration** 中的 **檔案** 和 **記錄** 資源。</span><span class="sxs-lookup"><span data-stu-id="56803-142">This includes the **File** and **Log** resources in **PSDesiredStateConfiguration** .</span></span>

## <span data-ttu-id="56803-143">相關連結</span><span class="sxs-lookup"><span data-stu-id="56803-143">RELATED LINKS</span></span>

[<span data-ttu-id="56803-144">Windows PowerShell Desired State Configuration 概觀</span><span class="sxs-lookup"><span data-stu-id="56803-144">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="56803-145">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="56803-145">Get-DscResource</span></span>](Get-DscResource.md)
