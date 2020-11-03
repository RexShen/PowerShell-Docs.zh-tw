---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: d73d8d6a30e6b7c08b5a0b7988ea2327be34002a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203943"
---
# <span data-ttu-id="f2eb8-103">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="f2eb8-103">Invoke-DscResource</span></span>

## <span data-ttu-id="f2eb8-104">概要</span><span class="sxs-lookup"><span data-stu-id="f2eb8-104">SYNOPSIS</span></span>
<span data-ttu-id="f2eb8-105">執行指定 DSC 資源的方法。</span><span class="sxs-lookup"><span data-stu-id="f2eb8-105">Runs a method of a specified DSC resource.</span></span>

## <span data-ttu-id="f2eb8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f2eb8-106">SYNTAX</span></span>

```
Invoke-DscResource [-Name] <String> [-Method] <String> -ModuleName <ModuleSpecification> -Property <Hashtable>
 [<CommonParameters>]
```

## <span data-ttu-id="f2eb8-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f2eb8-107">DESCRIPTION</span></span>
<span data-ttu-id="f2eb8-108">**DscResource 指令程式** 會執行指定 Windows PowerShell DESIRED STATE CONFIGURATION (DSC) 資源的方法。</span><span class="sxs-lookup"><span data-stu-id="f2eb8-108">The **Invoke-DscResource** cmdlet runs a method of a specified Windows PowerShell Desired State Configuration (DSC) resource.</span></span>
<span data-ttu-id="f2eb8-109">執行此 Cmdlet 之前，請將本機 Configuration Manager (LCM) 的重新整理模式設定為停用。</span><span class="sxs-lookup"><span data-stu-id="f2eb8-109">Before you run this cmdlet, set the refresh mode of the Local Configuration Manager (LCM) to Disabled.</span></span>

<span data-ttu-id="f2eb8-110">此 Cmdlet 會直接叫用 DSC 資源，而不需建立設定文件。</span><span class="sxs-lookup"><span data-stu-id="f2eb8-110">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span>
<span data-ttu-id="f2eb8-111">使用此 Cmdlet，設定管理產品可以使用 DSC 資源來管理 windows。</span><span class="sxs-lookup"><span data-stu-id="f2eb8-111">Using this cmdlet, configuration management products can manage windows by using DSC resources.</span></span>
<span data-ttu-id="f2eb8-112">當 DSC 引擎或 LCM 在啟用偵錯工具的情況下執行時，此 Cmdlet 也會啟用資源的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="f2eb8-112">This cmdlet also enables debugging of resources when the DSC engine or LCM is running with debugging enabled.</span></span>

## <span data-ttu-id="f2eb8-113">範例</span><span class="sxs-lookup"><span data-stu-id="f2eb8-113">EXAMPLES</span></span>

### <span data-ttu-id="f2eb8-114">範例1：指定資源的必要屬性來叫用資源的 Set 方法</span><span class="sxs-lookup"><span data-stu-id="f2eb8-114">Example 1: Invoke the Set method of a resource by specifying its mandatory properties</span></span>

```
PS C:\> Invoke-DscResource -Name Log -Method Set -Property @{Message = 'Hello World'} -ModuleName PSDesiredStateConfiguration
```

<span data-ttu-id="f2eb8-115">此命令會叫用名為 Log 的資源的 **Set** 方法，並為其指定 **訊息** 屬性。</span><span class="sxs-lookup"><span data-stu-id="f2eb8-115">This command invokes the **Set** method of a resource named Log and specifies a **Message** property for it.</span></span>

### <span data-ttu-id="f2eb8-116">範例2：叫用指定模組之資源的測試方法</span><span class="sxs-lookup"><span data-stu-id="f2eb8-116">Example 2: Invoke the Test method of a resource for a specified module</span></span>

```
PS C:\> Invoke-DscResource -Name WindowsProcess -Method Test -Property @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''} -ModuleName PSDesiredStateConfiguration
```

<span data-ttu-id="f2eb8-117">此命令會叫用名為 WindowsProcess 之資源的 **測試** 方法，該資源位於名為 PSDesiredStateConfiguration 的模組中。</span><span class="sxs-lookup"><span data-stu-id="f2eb8-117">This command invokes the **Test** method of a resource named WindowsProcess, which is in the module named PSDesiredStateConfiguration.</span></span>

## <span data-ttu-id="f2eb8-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f2eb8-118">PARAMETERS</span></span>

### <span data-ttu-id="f2eb8-119">-Method</span><span class="sxs-lookup"><span data-stu-id="f2eb8-119">-Method</span></span>
<span data-ttu-id="f2eb8-120">指定此 Cmdlet 叫用之資源的方法。</span><span class="sxs-lookup"><span data-stu-id="f2eb8-120">Specifies the method of the resource that this cmdlet invokes.</span></span> <span data-ttu-id="f2eb8-121">此參數可接受的值為： Get、Set 和 Test。</span><span class="sxs-lookup"><span data-stu-id="f2eb8-121">The acceptable values for this parameter are: Get, Set, and Test.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f2eb8-122">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="f2eb8-122">-ModuleName</span></span>
<span data-ttu-id="f2eb8-123">指定此 Cmdlet 用來叫用指定之資源的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="f2eb8-123">Specifies the name of the module from which this cmdlet invokes the specified resource.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f2eb8-124">-Name</span><span class="sxs-lookup"><span data-stu-id="f2eb8-124">-Name</span></span>
<span data-ttu-id="f2eb8-125">指定要啟動之 DSC 資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="f2eb8-125">Specifies the name of the DSC resource to start.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f2eb8-126">-Property</span><span class="sxs-lookup"><span data-stu-id="f2eb8-126">-Property</span></span>
<span data-ttu-id="f2eb8-127">在雜湊表中指定資源的屬性名稱與其值，分別作為索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="f2eb8-127">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="f2eb8-128">使用 **Get-DscResource** Cmdlet，探索資源的屬性和其類型。</span><span class="sxs-lookup"><span data-stu-id="f2eb8-128">Use the **Get-DscResource** cmdlet to discover resource properties and their types.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f2eb8-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f2eb8-129">CommonParameters</span></span>
<span data-ttu-id="f2eb8-130">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f2eb8-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f2eb8-131">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f2eb8-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f2eb8-132">輸入</span><span class="sxs-lookup"><span data-stu-id="f2eb8-132">INPUTS</span></span>

## <span data-ttu-id="f2eb8-133">輸出</span><span class="sxs-lookup"><span data-stu-id="f2eb8-133">OUTPUTS</span></span>

### <span data-ttu-id="f2eb8-134">CimInstance，system.string. 布林值</span><span class="sxs-lookup"><span data-stu-id="f2eb8-134">Microsoft.Management.Infrastructure.CimInstance, System.Boolean</span></span>

## <span data-ttu-id="f2eb8-135">注意</span><span class="sxs-lookup"><span data-stu-id="f2eb8-135">NOTES</span></span>

## <span data-ttu-id="f2eb8-136">相關連結</span><span class="sxs-lookup"><span data-stu-id="f2eb8-136">RELATED LINKS</span></span>

[<span data-ttu-id="f2eb8-137">Windows PowerShell Desired State Configuration 概觀</span><span class="sxs-lookup"><span data-stu-id="f2eb8-137">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="f2eb8-138">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="f2eb8-138">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="f2eb8-139">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="f2eb8-139">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="f2eb8-140">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="f2eb8-140">Get-DscResource</span></span>](Get-DscResource.md)

[<span data-ttu-id="f2eb8-141">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="f2eb8-141">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="f2eb8-142">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="f2eb8-142">Set-DscLocalConfigurationManager</span></span>](Set-DscLocalConfigurationManager.md)

[<span data-ttu-id="f2eb8-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="f2eb8-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="f2eb8-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="f2eb8-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
