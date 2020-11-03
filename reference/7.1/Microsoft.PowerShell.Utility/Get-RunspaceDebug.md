---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspacedebug?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-RunspaceDebug
ms.openlocfilehash: 821b532dc44702af4243bf36ca7f5d4089a057d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202800"
---
# <span data-ttu-id="555cd-103">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="555cd-103">Get-RunspaceDebug</span></span>

## <span data-ttu-id="555cd-104">概要</span><span class="sxs-lookup"><span data-stu-id="555cd-104">SYNOPSIS</span></span>
<span data-ttu-id="555cd-105">顯示運行時調試選項。</span><span class="sxs-lookup"><span data-stu-id="555cd-105">Shows runspace debugging options.</span></span>

## <span data-ttu-id="555cd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="555cd-106">SYNTAX</span></span>

### <span data-ttu-id="555cd-107">RunspaceNameParameterSet (預設) </span><span class="sxs-lookup"><span data-stu-id="555cd-107">RunspaceNameParameterSet (Default)</span></span>

```
Get-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="555cd-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="555cd-108">RunspaceParameterSet</span></span>

```
Get-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="555cd-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="555cd-109">RunspaceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="555cd-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="555cd-110">RunspaceInstanceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="555cd-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="555cd-111">ProcessNameParameterSet</span></span>

```
Get-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="555cd-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="555cd-112">DESCRIPTION</span></span>

<span data-ttu-id="555cd-113">此 `Get-RunspaceDebug` Cmdlet 會顯示運行時調試選項。</span><span class="sxs-lookup"><span data-stu-id="555cd-113">The `Get-RunspaceDebug` cmdlet shows runspace debugging options.</span></span>

## <span data-ttu-id="555cd-114">範例</span><span class="sxs-lookup"><span data-stu-id="555cd-114">EXAMPLES</span></span>

### <span data-ttu-id="555cd-115">1：顯示預設運行時偵錯工具的狀態</span><span class="sxs-lookup"><span data-stu-id="555cd-115">1: Show the state of the default runspace debugger</span></span>

```powershell
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="555cd-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="555cd-116">PARAMETERS</span></span>

### <span data-ttu-id="555cd-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="555cd-117">-AppDomainName</span></span>

<span data-ttu-id="555cd-118">裝載 PowerShell 運行空間的應用程式域的名稱。</span><span class="sxs-lookup"><span data-stu-id="555cd-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="555cd-119">-ProcessName</span><span class="sxs-lookup"><span data-stu-id="555cd-119">-ProcessName</span></span>

<span data-ttu-id="555cd-120">裝載 PowerShell 運行空間之進程的名稱。</span><span class="sxs-lookup"><span data-stu-id="555cd-120">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="555cd-121">-運行時</span><span class="sxs-lookup"><span data-stu-id="555cd-121">-Runspace</span></span>

<span data-ttu-id="555cd-122">要停用的一或多個 **運行** 時物件。</span><span class="sxs-lookup"><span data-stu-id="555cd-122">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="555cd-123">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="555cd-123">-RunspaceId</span></span>

<span data-ttu-id="555cd-124">要停用的一或多個 **運行** 時識別碼號碼。</span><span class="sxs-lookup"><span data-stu-id="555cd-124">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="555cd-125">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="555cd-125">-RunspaceInstanceId</span></span>

<span data-ttu-id="555cd-126">要停用的一或多個 **運行空間** guid。</span><span class="sxs-lookup"><span data-stu-id="555cd-126">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="555cd-127">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="555cd-127">-RunspaceName</span></span>

<span data-ttu-id="555cd-128">要停用的一或多個 **運行空間** 名稱。</span><span class="sxs-lookup"><span data-stu-id="555cd-128">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="555cd-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="555cd-129">CommonParameters</span></span>

<span data-ttu-id="555cd-130">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="555cd-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="555cd-131">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="555cd-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="555cd-132">輸入</span><span class="sxs-lookup"><span data-stu-id="555cd-132">INPUTS</span></span>

## <span data-ttu-id="555cd-133">輸出</span><span class="sxs-lookup"><span data-stu-id="555cd-133">OUTPUTS</span></span>

## <span data-ttu-id="555cd-134">注意</span><span class="sxs-lookup"><span data-stu-id="555cd-134">NOTES</span></span>

## <span data-ttu-id="555cd-135">相關連結</span><span class="sxs-lookup"><span data-stu-id="555cd-135">RELATED LINKS</span></span>

[<span data-ttu-id="555cd-136">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="555cd-136">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="555cd-137">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="555cd-137">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

