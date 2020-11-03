---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessioncapability?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionCapability
ms.openlocfilehash: c5e3cb677a736595d1acd98c6f4be4d43b2151ba
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204520"
---
# <span data-ttu-id="3ec8e-103">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="3ec8e-103">Get-PSSessionCapability</span></span>

## <span data-ttu-id="3ec8e-104">概要</span><span class="sxs-lookup"><span data-stu-id="3ec8e-104">SYNOPSIS</span></span>
<span data-ttu-id="3ec8e-105">取得特定使用者對於限制工作階段設定的能力。</span><span class="sxs-lookup"><span data-stu-id="3ec8e-105">Gets the capabilities of a specific user on a constrained session configuration.</span></span>

## <span data-ttu-id="3ec8e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3ec8e-106">SYNTAX</span></span>

```
Get-PSSessionCapability [-ConfigurationName] <String> [-Username] <String> [-Full] [<CommonParameters>]
```

## <span data-ttu-id="3ec8e-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3ec8e-107">DESCRIPTION</span></span>

<span data-ttu-id="3ec8e-108">**Get-PSSessionCapability** Cmdlet 會取得特定使用者對於限制工作階段設定的能力。</span><span class="sxs-lookup"><span data-stu-id="3ec8e-108">The **Get-PSSessionCapability** cmdlet gets the capabilities of a specific user on a constrained session configuration.</span></span>
<span data-ttu-id="3ec8e-109">若要稽核使用者的自訂工作階段設定，請使用此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3ec8e-109">Use this cmdlet to audit customized session configurations for users.</span></span>

<span data-ttu-id="3ec8e-110">從 Windows PowerShell 5.0 開始，您可以在工作階段設定 (.pssc) 檔案中使用 **RoleDefinitions** 屬性。</span><span class="sxs-lookup"><span data-stu-id="3ec8e-110">Starting in Windows PowerShell 5.0, you can use the **RoleDefinitions** property in a session configuration (.pssc) file.</span></span>
<span data-ttu-id="3ec8e-111">使用這個屬性可讓您根據群組成員資格，授與使用者對於單一限制端點不同的能力。</span><span class="sxs-lookup"><span data-stu-id="3ec8e-111">Using this property lets you grant users different capabilities on a single constrained endpoint based on group membership.</span></span>
<span data-ttu-id="3ec8e-112">**Get-PSSessionCapability** Cmdlet 在稽核這些端點時可讓您決定授與使用者的實際能力，降低複雜性。</span><span class="sxs-lookup"><span data-stu-id="3ec8e-112">The **Get-PSSessionCapability** cmdlet reduces complexity when auditing these endpoints by letting you determine the exact capabilities granted to a user.</span></span>

<span data-ttu-id="3ec8e-113">根據預設， **Get-PSSessionCapability** Cmdlet 會傳回一份指定使用者可在指定端點中執行的命令清單。</span><span class="sxs-lookup"><span data-stu-id="3ec8e-113">By default, the **Get-PSSessionCapability** cmdlet returns a list of commands the specified user can run in the specified endpoint.</span></span>
<span data-ttu-id="3ec8e-114">這相當於使用者在指定的端點中執行 **Get-Command** 。</span><span class="sxs-lookup"><span data-stu-id="3ec8e-114">This is equivalent to the user running **Get-Command** in the specified endpoint.</span></span>
<span data-ttu-id="3ec8e-115">搭配 *Full* 參數執行時，此 Cmdlet 會傳回 **InitialSessionState** 物件。</span><span class="sxs-lookup"><span data-stu-id="3ec8e-115">When run with the *Full* parameter, this cmdlet returns an **InitialSessionState** object.</span></span>
<span data-ttu-id="3ec8e-116">此物件包含有關指定的使用者會與指定的端點互動之 PowerShell 運行時的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3ec8e-116">This object contains details about the PowerShell runspace the specified user would interact with for the specified endpoint.</span></span>
<span data-ttu-id="3ec8e-117">它包含語言模式、執行原則和環境變數等資訊。</span><span class="sxs-lookup"><span data-stu-id="3ec8e-117">It includes information such as Language Mode, Execution Policy, and Environmental Variables.</span></span>

## <span data-ttu-id="3ec8e-118">範例</span><span class="sxs-lookup"><span data-stu-id="3ec8e-118">EXAMPLES</span></span>

### <span data-ttu-id="3ec8e-119">範例 1︰取得使用者可用的命令</span><span class="sxs-lookup"><span data-stu-id="3ec8e-119">Example 1: Get commands available for a user</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User'
```

<span data-ttu-id="3ec8e-120">這個範例會在連接到本機電腦上的端點1限制端點時，傳回使用者 CONTOSO\User 可用的命令。</span><span class="sxs-lookup"><span data-stu-id="3ec8e-120">This example returns the commands available to the user CONTOSO\User when connecting to the Endpoint1 constrained endpoint on the local computer.</span></span>

### <span data-ttu-id="3ec8e-121">範例 2︰取得使用者的 Runspace 相關詳細資料</span><span class="sxs-lookup"><span data-stu-id="3ec8e-121">Example 2: Get details about a runspace for a user</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User' -Full
```

<span data-ttu-id="3ec8e-122">此範例會傳回使用者 CONTOSO\User 在連接至端點1限制端點時，會互動的運行時的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3ec8e-122">This example returns details about the runspace the user CONTOSO\User would interact with when connecting to the Endpoint1 constrained endpoint.</span></span>

## <span data-ttu-id="3ec8e-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3ec8e-123">PARAMETERS</span></span>

### <span data-ttu-id="3ec8e-124">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="3ec8e-124">-ConfigurationName</span></span>

<span data-ttu-id="3ec8e-125">指定您要檢查的限制工作階段設定 (端點)。</span><span class="sxs-lookup"><span data-stu-id="3ec8e-125">Specifies the constrained session configuration (endpoint) that you are inspecting.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ec8e-126">-Full</span><span class="sxs-lookup"><span data-stu-id="3ec8e-126">-Full</span></span>

<span data-ttu-id="3ec8e-127">指出此 Cmdlet 會傳回指定使用者在指定限制端點的整個初始工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="3ec8e-127">Indicates that this cmdlet returns the entire initial session state for the specified user at the specified constrained endpoint.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ec8e-128">-Username</span><span class="sxs-lookup"><span data-stu-id="3ec8e-128">-Username</span></span>

<span data-ttu-id="3ec8e-129">指定您要檢查其能力的使用者。</span><span class="sxs-lookup"><span data-stu-id="3ec8e-129">Specifies the user whose capabilities you are inspecting.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ec8e-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3ec8e-130">CommonParameters</span></span>

<span data-ttu-id="3ec8e-131">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3ec8e-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3ec8e-132">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3ec8e-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3ec8e-133">輸入</span><span class="sxs-lookup"><span data-stu-id="3ec8e-133">INPUTS</span></span>

## <span data-ttu-id="3ec8e-134">輸出</span><span class="sxs-lookup"><span data-stu-id="3ec8e-134">OUTPUTS</span></span>

### <span data-ttu-id="3ec8e-135">System.Management.Automation.AliasInfo</span><span class="sxs-lookup"><span data-stu-id="3ec8e-135">System.Management.Automation.AliasInfo</span></span>

### <span data-ttu-id="3ec8e-136">System.Management.Automation.FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="3ec8e-136">System.Management.Automation.FunctionInfo</span></span>

### <span data-ttu-id="3ec8e-137">System.Management.Automation.Runspaces.InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="3ec8e-137">System.Management.Automation.Runspaces.InitialSessionState</span></span>

## <span data-ttu-id="3ec8e-138">注意</span><span class="sxs-lookup"><span data-stu-id="3ec8e-138">NOTES</span></span>

## <span data-ttu-id="3ec8e-139">相關連結</span><span class="sxs-lookup"><span data-stu-id="3ec8e-139">RELATED LINKS</span></span>

[<span data-ttu-id="3ec8e-140">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="3ec8e-140">New-PSRoleCapabilityFile</span></span>](New-PSRoleCapabilityFile.md)
