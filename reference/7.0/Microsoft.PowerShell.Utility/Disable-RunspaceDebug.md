---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-runspacedebug?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-RunspaceDebug
ms.openlocfilehash: 58665cd06e39784721be9a538b70dd8b7c2a1c14
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201559"
---
# <span data-ttu-id="7ab46-103">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="7ab46-103">Disable-RunspaceDebug</span></span>

## <span data-ttu-id="7ab46-104">概要</span><span class="sxs-lookup"><span data-stu-id="7ab46-104">SYNOPSIS</span></span>
<span data-ttu-id="7ab46-105">停用一或多個執行程式的偵錯工具，並釋放任何暫止的偵錯工具停止。</span><span class="sxs-lookup"><span data-stu-id="7ab46-105">Disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="7ab46-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7ab46-106">SYNTAX</span></span>

### <span data-ttu-id="7ab46-107">RunspaceNameParameterSet (預設) </span><span class="sxs-lookup"><span data-stu-id="7ab46-107">RunspaceNameParameterSet (Default)</span></span>

```
Disable-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="7ab46-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="7ab46-108">RunspaceParameterSet</span></span>

```
Disable-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="7ab46-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="7ab46-109">RunspaceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="7ab46-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="7ab46-110">RunspaceInstanceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="7ab46-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="7ab46-111">ProcessNameParameterSet</span></span>

```
Disable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="7ab46-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7ab46-112">DESCRIPTION</span></span>

<span data-ttu-id="7ab46-113">此 `Disable-RunspaceDebug` Cmdlet 會停用一或多個執行程式的偵錯工具，並釋放任何擱置中的偵錯工具停止。</span><span class="sxs-lookup"><span data-stu-id="7ab46-113">The `Disable-RunspaceDebug` cmdlet disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="7ab46-114">範例</span><span class="sxs-lookup"><span data-stu-id="7ab46-114">EXAMPLES</span></span>

### <span data-ttu-id="7ab46-115">1：停用預設運行時偵錯工具</span><span class="sxs-lookup"><span data-stu-id="7ab46-115">1: Disable the default runspace debugger</span></span>

```powershell
Disable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="7ab46-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7ab46-116">PARAMETERS</span></span>

### <span data-ttu-id="7ab46-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="7ab46-117">-AppDomainName</span></span>

<span data-ttu-id="7ab46-118">裝載 PowerShell 運行空間的應用程式域的名稱。</span><span class="sxs-lookup"><span data-stu-id="7ab46-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="7ab46-119">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="7ab46-119">-ProcessName</span></span>

<span data-ttu-id="7ab46-120">裝載 PowerShell 運行空間之進程的名稱。</span><span class="sxs-lookup"><span data-stu-id="7ab46-120">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="7ab46-121">-運行時</span><span class="sxs-lookup"><span data-stu-id="7ab46-121">-Runspace</span></span>

<span data-ttu-id="7ab46-122">要停用的一或多個 **運行** 時物件。</span><span class="sxs-lookup"><span data-stu-id="7ab46-122">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="7ab46-123">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="7ab46-123">-RunspaceId</span></span>

<span data-ttu-id="7ab46-124">要停用的一或多個 **運行** 時識別碼號碼。</span><span class="sxs-lookup"><span data-stu-id="7ab46-124">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="7ab46-125">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="7ab46-125">-RunspaceInstanceId</span></span>

<span data-ttu-id="7ab46-126">要停用的一或多個 **運行空間** guid。</span><span class="sxs-lookup"><span data-stu-id="7ab46-126">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="7ab46-127">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="7ab46-127">-RunspaceName</span></span>

<span data-ttu-id="7ab46-128">要停用的一或多個 **運行空間** 名稱。</span><span class="sxs-lookup"><span data-stu-id="7ab46-128">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="7ab46-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7ab46-129">CommonParameters</span></span>

<span data-ttu-id="7ab46-130">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="7ab46-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7ab46-131">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="7ab46-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7ab46-132">輸入</span><span class="sxs-lookup"><span data-stu-id="7ab46-132">INPUTS</span></span>

## <span data-ttu-id="7ab46-133">輸出</span><span class="sxs-lookup"><span data-stu-id="7ab46-133">OUTPUTS</span></span>

## <span data-ttu-id="7ab46-134">注意</span><span class="sxs-lookup"><span data-stu-id="7ab46-134">NOTES</span></span>

## <span data-ttu-id="7ab46-135">相關連結</span><span class="sxs-lookup"><span data-stu-id="7ab46-135">RELATED LINKS</span></span>

[<span data-ttu-id="7ab46-136">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="7ab46-136">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

[<span data-ttu-id="7ab46-137">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="7ab46-137">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)
