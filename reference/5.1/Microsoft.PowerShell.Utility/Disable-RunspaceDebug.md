---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-runspacedebug?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-RunspaceDebug
ms.openlocfilehash: 79fe5c58f26f9146adfca18827f65cff53bde23f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203324"
---
# <span data-ttu-id="2b0d2-103">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="2b0d2-103">Disable-RunspaceDebug</span></span>

## <span data-ttu-id="2b0d2-104">概要</span><span class="sxs-lookup"><span data-stu-id="2b0d2-104">SYNOPSIS</span></span>
<span data-ttu-id="2b0d2-105">停用一或多個執行程式的偵錯工具，並釋放任何暫止的偵錯工具停止。</span><span class="sxs-lookup"><span data-stu-id="2b0d2-105">Disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="2b0d2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2b0d2-106">SYNTAX</span></span>

### <span data-ttu-id="2b0d2-107">RunspaceNameParameterSet (預設) </span><span class="sxs-lookup"><span data-stu-id="2b0d2-107">RunspaceNameParameterSet (Default)</span></span>

```
Disable-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="2b0d2-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="2b0d2-108">RunspaceParameterSet</span></span>

```
Disable-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="2b0d2-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="2b0d2-109">RunspaceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="2b0d2-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="2b0d2-110">RunspaceInstanceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="2b0d2-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="2b0d2-111">ProcessNameParameterSet</span></span>

```
Disable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="2b0d2-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2b0d2-112">DESCRIPTION</span></span>

<span data-ttu-id="2b0d2-113">此 `Disable-RunspaceDebug` Cmdlet 會停用一或多個執行程式的偵錯工具，並釋放任何擱置中的偵錯工具停止。</span><span class="sxs-lookup"><span data-stu-id="2b0d2-113">The `Disable-RunspaceDebug` cmdlet disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="2b0d2-114">範例</span><span class="sxs-lookup"><span data-stu-id="2b0d2-114">EXAMPLES</span></span>

### <span data-ttu-id="2b0d2-115">1：停用預設運行時偵錯工具</span><span class="sxs-lookup"><span data-stu-id="2b0d2-115">1: Disable the default runspace debugger</span></span>

```powershell
Disable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="2b0d2-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2b0d2-116">PARAMETERS</span></span>

### <span data-ttu-id="2b0d2-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="2b0d2-117">-AppDomainName</span></span>

<span data-ttu-id="2b0d2-118">裝載 PowerShell 運行空間的應用程式域的名稱。</span><span class="sxs-lookup"><span data-stu-id="2b0d2-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b0d2-119">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="2b0d2-119">-ProcessName</span></span>

<span data-ttu-id="2b0d2-120">裝載 PowerShell 運行空間之進程的名稱。</span><span class="sxs-lookup"><span data-stu-id="2b0d2-120">The name of the process that hosts the PowerShell runspace.</span></span>

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b0d2-121">-運行時</span><span class="sxs-lookup"><span data-stu-id="2b0d2-121">-Runspace</span></span>

<span data-ttu-id="2b0d2-122">要停用的一或多個 **運行** 時物件。</span><span class="sxs-lookup"><span data-stu-id="2b0d2-122">One or more **Runspace** objects to be disabled.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.Runspace[]
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2b0d2-123">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="2b0d2-123">-RunspaceId</span></span>

<span data-ttu-id="2b0d2-124">要停用的一或多個 **運行** 時識別碼號碼。</span><span class="sxs-lookup"><span data-stu-id="2b0d2-124">One or more **Runspace** Id numbers to be disabled.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: RunspaceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b0d2-125">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="2b0d2-125">-RunspaceInstanceId</span></span>

<span data-ttu-id="2b0d2-126">要停用的一或多個 **運行空間** guid。</span><span class="sxs-lookup"><span data-stu-id="2b0d2-126">One or more **Runspace** GUIDs to be disabled.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: RunspaceInstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b0d2-127">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="2b0d2-127">-RunspaceName</span></span>

<span data-ttu-id="2b0d2-128">要停用的一或多個 **運行空間** 名稱。</span><span class="sxs-lookup"><span data-stu-id="2b0d2-128">One or more **Runspace** names to be disabled.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RunspaceNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b0d2-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2b0d2-129">CommonParameters</span></span>

<span data-ttu-id="2b0d2-130">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2b0d2-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2b0d2-131">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2b0d2-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2b0d2-132">輸入</span><span class="sxs-lookup"><span data-stu-id="2b0d2-132">INPUTS</span></span>

## <span data-ttu-id="2b0d2-133">輸出</span><span class="sxs-lookup"><span data-stu-id="2b0d2-133">OUTPUTS</span></span>

## <span data-ttu-id="2b0d2-134">注意</span><span class="sxs-lookup"><span data-stu-id="2b0d2-134">NOTES</span></span>

## <span data-ttu-id="2b0d2-135">相關連結</span><span class="sxs-lookup"><span data-stu-id="2b0d2-135">RELATED LINKS</span></span>

[<span data-ttu-id="2b0d2-136">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="2b0d2-136">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

[<span data-ttu-id="2b0d2-137">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="2b0d2-137">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)
