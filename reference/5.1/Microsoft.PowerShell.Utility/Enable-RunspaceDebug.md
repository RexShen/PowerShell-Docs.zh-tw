---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-runspacedebug?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-RunspaceDebug
ms.openlocfilehash: 54fb9500a924d2e5de98489fa4fb391accb23d0c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203323"
---
# <span data-ttu-id="000d0-103">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="000d0-103">Enable-RunspaceDebug</span></span>

## <span data-ttu-id="000d0-104">概要</span><span class="sxs-lookup"><span data-stu-id="000d0-104">SYNOPSIS</span></span>
<span data-ttu-id="000d0-105">在附加偵錯工具之前保留任何中斷點的空間上啟用偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="000d0-105">Enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="000d0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="000d0-106">SYNTAX</span></span>

### <span data-ttu-id="000d0-107">RunspaceNameParameterSet (預設) </span><span class="sxs-lookup"><span data-stu-id="000d0-107">RunspaceNameParameterSet (Default)</span></span>

```
Enable-RunspaceDebug [-BreakAll] [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="000d0-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="000d0-108">RunspaceParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="000d0-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="000d0-109">RunspaceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="000d0-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="000d0-110">RunspaceInstanceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="000d0-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="000d0-111">ProcessNameParameterSet</span></span>

```
Enable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="000d0-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="000d0-112">DESCRIPTION</span></span>

<span data-ttu-id="000d0-113">此 `Enable-RunspaceDebug` Cmdlet 會在保留任何中斷點的空間上啟用偵錯工具，直到附加偵錯工具為止。</span><span class="sxs-lookup"><span data-stu-id="000d0-113">The `Enable-RunspaceDebug` cmdlet enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="000d0-114">範例</span><span class="sxs-lookup"><span data-stu-id="000d0-114">EXAMPLES</span></span>

### <span data-ttu-id="000d0-115">1：啟用預設運行時偵錯工具</span><span class="sxs-lookup"><span data-stu-id="000d0-115">1: Enable the default runspace debugger</span></span>

```powershell
Enable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            True       False
```

## <span data-ttu-id="000d0-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="000d0-116">PARAMETERS</span></span>

### <span data-ttu-id="000d0-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="000d0-117">-AppDomainName</span></span>

<span data-ttu-id="000d0-118">裝載 PowerShell 運行空間的應用程式域的名稱。</span><span class="sxs-lookup"><span data-stu-id="000d0-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="000d0-119">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="000d0-119">-BreakAll</span></span>

<span data-ttu-id="000d0-120">使運行時中的任何執行中命令或腳本停止進入步驟模式，不論偵錯工具目前是否已連接。</span><span class="sxs-lookup"><span data-stu-id="000d0-120">Causes any running command or script in the Runspace to stop in step mode, regardless of whether a debugger is currently attached.</span></span> <span data-ttu-id="000d0-121">腳本或命令將保持停止，直到附加偵錯工具來偵測目前的停止點為止。</span><span class="sxs-lookup"><span data-stu-id="000d0-121">The script or command will remain stopped until a debugger is attached to debug the current stop point.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: RunspaceNameParameterSet, RunspaceParameterSet, RunspaceIdParameterSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="000d0-122">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="000d0-122">-ProcessName</span></span>

<span data-ttu-id="000d0-123">裝載 PowerShell 運行空間之進程的名稱。</span><span class="sxs-lookup"><span data-stu-id="000d0-123">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="000d0-124">-運行時</span><span class="sxs-lookup"><span data-stu-id="000d0-124">-Runspace</span></span>

<span data-ttu-id="000d0-125">要停用的一或多個 **運行** 時物件。</span><span class="sxs-lookup"><span data-stu-id="000d0-125">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="000d0-126">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="000d0-126">-RunspaceId</span></span>

<span data-ttu-id="000d0-127">要停用的一或多個 **運行** 時識別碼號碼。</span><span class="sxs-lookup"><span data-stu-id="000d0-127">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="000d0-128">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="000d0-128">-RunspaceInstanceId</span></span>

<span data-ttu-id="000d0-129">要停用的一或多個 **運行空間** guid。</span><span class="sxs-lookup"><span data-stu-id="000d0-129">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="000d0-130">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="000d0-130">-RunspaceName</span></span>

<span data-ttu-id="000d0-131">要停用的一或多個 **運行空間** 名稱。</span><span class="sxs-lookup"><span data-stu-id="000d0-131">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="000d0-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="000d0-132">CommonParameters</span></span>

<span data-ttu-id="000d0-133">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="000d0-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="000d0-134">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="000d0-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="000d0-135">輸入</span><span class="sxs-lookup"><span data-stu-id="000d0-135">INPUTS</span></span>

## <span data-ttu-id="000d0-136">輸出</span><span class="sxs-lookup"><span data-stu-id="000d0-136">OUTPUTS</span></span>

## <span data-ttu-id="000d0-137">注意</span><span class="sxs-lookup"><span data-stu-id="000d0-137">NOTES</span></span>

## <span data-ttu-id="000d0-138">相關連結</span><span class="sxs-lookup"><span data-stu-id="000d0-138">RELATED LINKS</span></span>

[<span data-ttu-id="000d0-139">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="000d0-139">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="000d0-140">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="000d0-140">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)
