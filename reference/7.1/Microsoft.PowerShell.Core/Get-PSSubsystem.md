---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 10/15/2020
online version: ''
schema: 2.0.0
ms.openlocfilehash: 34998e7c4a6876821df949019970dc1d87297397
ms.sourcegitcommit: c9e56ec489522c706b8d6b8733f3f015d6d7e893
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208551"
---
# <span data-ttu-id="dfc67-101">Get-PSSubsystem</span><span class="sxs-lookup"><span data-stu-id="dfc67-101">Get-PSSubsystem</span></span>

## <span data-ttu-id="dfc67-102">概要</span><span class="sxs-lookup"><span data-stu-id="dfc67-102">SYNOPSIS</span></span>
<span data-ttu-id="dfc67-103">抓取在 PowerShell 中註冊之子系統的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dfc67-103">Retrieves information about the subsystems registered in PowerShell.</span></span>

## <span data-ttu-id="dfc67-104">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dfc67-104">SYNTAX</span></span>

### <span data-ttu-id="dfc67-105">GetAllSet (預設) </span><span class="sxs-lookup"><span data-stu-id="dfc67-105">GetAllSet (Default)</span></span>

```
Get-PSSubsystem [<CommonParameters>]
```

### <span data-ttu-id="dfc67-106">GetByKindSet</span><span class="sxs-lookup"><span data-stu-id="dfc67-106">GetByKindSet</span></span>

```
Get-PSSubsystem -Kind <SubsystemKind> [<CommonParameters>]
```

### <span data-ttu-id="dfc67-107">GetByTypeSet</span><span class="sxs-lookup"><span data-stu-id="dfc67-107">GetByTypeSet</span></span>

```
Get-PSSubsystem -SubsystemType <Type> [<CommonParameters>]
```

## <span data-ttu-id="dfc67-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dfc67-108">DESCRIPTION</span></span>

<span data-ttu-id="dfc67-109">抓取在 PowerShell 中註冊之子系統的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dfc67-109">Retrieves information about the subsystems registered in PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="dfc67-110">這是實驗性的功能。</span><span class="sxs-lookup"><span data-stu-id="dfc67-110">This is an experimental feature.</span></span> <span data-ttu-id="dfc67-111">只有啟用此功能時，才可使用此 Cmdlet `PSSubsystemPluginModel` 。</span><span class="sxs-lookup"><span data-stu-id="dfc67-111">This cmdlet is only available when the `PSSubsystemPluginModel` feature is enabled.</span></span> <span data-ttu-id="dfc67-112">如需詳細資訊，請參閱 [使用實驗性功能](/powershell/scripting/learn/experimental-features)。</span><span class="sxs-lookup"><span data-stu-id="dfc67-112">For more information, see [Using Experimental Features](/powershell/scripting/learn/experimental-features).</span></span>

<span data-ttu-id="dfc67-113">並讓您將 `System.Management.Automation.dll` 的元件區分為本身組件中的個別子系統。</span><span class="sxs-lookup"><span data-stu-id="dfc67-113">The feature makes it possible to separate components of `System.Management.Automation.dll` into individual subsystems that reside in their own assembly.</span></span> <span data-ttu-id="dfc67-114">這種區隔可減少核心 PowerShell 引擎的磁碟使用量，並讓這些元件成為選用功能，只需安裝最低版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="dfc67-114">This separation reduces the disk footprint of the core PowerShell engine and allows these components to become optional features for a minimal PowerShell installation.</span></span>

<span data-ttu-id="dfc67-115">目前僅支援 **CommandPredictor** 子系統。</span><span class="sxs-lookup"><span data-stu-id="dfc67-115">Currently, only the **CommandPredictor** subsystem is supported.</span></span> <span data-ttu-id="dfc67-116">這個子系統可搭配使用 PSReadLine 模組，以提供自訂預測外掛程式。</span><span class="sxs-lookup"><span data-stu-id="dfc67-116">This subsystem is used along with the PSReadLine module to provide custom prediction plugins.</span></span> <span data-ttu-id="dfc67-117">未來，您可以將 **Job** 、 **CommandCompleter** 、 **Remoting** 和其他元件區分為 `System.Management.Automation.dll` 以外的子系統組件。</span><span class="sxs-lookup"><span data-stu-id="dfc67-117">In future, **Job** , **CommandCompleter** , **Remoting** and other components could be separated into subsystem assemblies outside of `System.Management.Automation.dll`.</span></span>

## <span data-ttu-id="dfc67-118">範例</span><span class="sxs-lookup"><span data-stu-id="dfc67-118">EXAMPLES</span></span>

### <span data-ttu-id="dfc67-119">範例 1-顯示所有可用的子系統</span><span class="sxs-lookup"><span data-stu-id="dfc67-119">Example 1 - Display all available subsystems</span></span>

```powershell
Get-PSSubsystem
```

```Output
Kind              SubsystemType     IsRegistered Implementations
----              -------------     ------------ ---------------
CommandPredictor  ICommandPredictor        False {}
```

### <span data-ttu-id="dfc67-120">範例 2-顯示特定種類的所有可用子系統</span><span class="sxs-lookup"><span data-stu-id="dfc67-120">Example 2 - Display all available subsystems of a specific kind</span></span>

```powershell
PS> Get-PSSubsystem -Kind CommandPredictor | Format-List
```

```Output
Kind                      : CommandPredictor
SubsystemType             : System.Management.Automation.Subsystem.ICommandPredictor
AllowUnregistration       : True
AllowMultipleRegistration : True
RequiredCmdlets           : {}
RequiredFunctions         : {}
IsRegistered              : False
Implementations           : {}
```

## <span data-ttu-id="dfc67-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dfc67-121">PARAMETERS</span></span>

### <span data-ttu-id="dfc67-122">-種類</span><span class="sxs-lookup"><span data-stu-id="dfc67-122">-Kind</span></span>


<span data-ttu-id="dfc67-123">指定要傳回的子系統種類。</span><span class="sxs-lookup"><span data-stu-id="dfc67-123">Specifies the kind of subsystem to be returned.</span></span> <span data-ttu-id="dfc67-124">有效的值為： `CommandPredictor` 。</span><span class="sxs-lookup"><span data-stu-id="dfc67-124">Valid values are: `CommandPredictor`.</span></span>

```yaml
Type: System.Management.Automation.Subsystem.SubsystemKind
Parameter Sets: GetByKindSet
Aliases:
Accepted values: CommandPredictor

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="dfc67-125">-SubsystemType</span><span class="sxs-lookup"><span data-stu-id="dfc67-125">-SubsystemType</span></span>

<span data-ttu-id="dfc67-126">指定要傳回之子系統的型別。</span><span class="sxs-lookup"><span data-stu-id="dfc67-126">Specifies the type of subsystem to be returned.</span></span>

```yaml
Type: System.Type
Parameter Sets: GetByTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="dfc67-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dfc67-127">CommonParameters</span></span>

<span data-ttu-id="dfc67-128">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="dfc67-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dfc67-129">如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="dfc67-129">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dfc67-130">輸入</span><span class="sxs-lookup"><span data-stu-id="dfc67-130">INPUTS</span></span>

### <span data-ttu-id="dfc67-131">SubsystemKind （系統管理）</span><span class="sxs-lookup"><span data-stu-id="dfc67-131">System.Management.Automation.Subsystem.SubsystemKind</span></span>

### <span data-ttu-id="dfc67-132">System.Type</span><span class="sxs-lookup"><span data-stu-id="dfc67-132">System.Type</span></span>

## <span data-ttu-id="dfc67-133">輸出</span><span class="sxs-lookup"><span data-stu-id="dfc67-133">OUTPUTS</span></span>

### <span data-ttu-id="dfc67-134">SubsystemInfo （系統管理）</span><span class="sxs-lookup"><span data-stu-id="dfc67-134">System.Management.Automation.Subsystem.SubsystemInfo</span></span>

## <span data-ttu-id="dfc67-135">注意</span><span class="sxs-lookup"><span data-stu-id="dfc67-135">NOTES</span></span>

## <span data-ttu-id="dfc67-136">相關連結</span><span class="sxs-lookup"><span data-stu-id="dfc67-136">RELATED LINKS</span></span>

[<span data-ttu-id="dfc67-137">about_experimental_features</span><span class="sxs-lookup"><span data-stu-id="dfc67-137">about_experimental_features</span></span>](about/about_experimental_features.md)

[<span data-ttu-id="dfc67-138">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="dfc67-138">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="dfc67-139">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="dfc67-139">Enable-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="dfc67-140">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="dfc67-140">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="dfc67-141">使用實驗性功能</span><span class="sxs-lookup"><span data-stu-id="dfc67-141">Using Experimental Features</span></span>](/powershell/scripting/learn/experimental-features)
