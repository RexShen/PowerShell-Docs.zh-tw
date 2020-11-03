---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Runspace
ms.openlocfilehash: 12530b9cf30b34598dfc3a049f5553920abecc4f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204608"
---
# <span data-ttu-id="1bd5b-103">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="1bd5b-103">Get-Runspace</span></span>

## <span data-ttu-id="1bd5b-104">概要</span><span class="sxs-lookup"><span data-stu-id="1bd5b-104">SYNOPSIS</span></span>
<span data-ttu-id="1bd5b-105">取得 PowerShell 主機進程內的作用中的空間。</span><span class="sxs-lookup"><span data-stu-id="1bd5b-105">Gets active runspaces within a PowerShell host process.</span></span>

## <span data-ttu-id="1bd5b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1bd5b-106">SYNTAX</span></span>

### <span data-ttu-id="1bd5b-107">NameParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="1bd5b-107">NameParameterSet (Default)</span></span>

```
Get-Runspace [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="1bd5b-108">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="1bd5b-108">IdParameterSet</span></span>

```
Get-Runspace [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="1bd5b-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="1bd5b-109">InstanceIdParameterSet</span></span>

```
Get-Runspace [-InstanceId] <Guid[]> [<CommonParameters>]
```

## <span data-ttu-id="1bd5b-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1bd5b-110">DESCRIPTION</span></span>

<span data-ttu-id="1bd5b-111">`Get-Runspace`Cmdlet 會取得 PowerShell 主機進程中的作用中的工作空間。</span><span class="sxs-lookup"><span data-stu-id="1bd5b-111">The `Get-Runspace` cmdlet gets active runspaces in a PowerShell host process.</span></span>

## <span data-ttu-id="1bd5b-112">範例</span><span class="sxs-lookup"><span data-stu-id="1bd5b-112">EXAMPLES</span></span>

### <span data-ttu-id="1bd5b-113">範例1：取得執行空間</span><span class="sxs-lookup"><span data-stu-id="1bd5b-113">Example 1: Get runspaces</span></span>

```powershell
Get-Runspace
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
  2 Runspace2       localhost       Local         Opened        Available
  3 Runspace3       localhost       Local         Opened        Available
```

### <span data-ttu-id="1bd5b-114">範例2：依識別碼取得運行空間</span><span class="sxs-lookup"><span data-stu-id="1bd5b-114">Example 2: Get runspace by Id</span></span>

```powershell
Get-Runspace -Id 2
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  2 Runspace2       localhost       Local         Opened        Available
```

### <span data-ttu-id="1bd5b-115">範例3：依名稱取得運行空間</span><span class="sxs-lookup"><span data-stu-id="1bd5b-115">Example 3: Get runspace by Name</span></span>

```powershell
Get-Runspace -Name Runspace1
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

### <span data-ttu-id="1bd5b-116">範例4：依 InstanceId 取得運行空間</span><span class="sxs-lookup"><span data-stu-id="1bd5b-116">Example 4: Get runspace by InstanceId</span></span>

<span data-ttu-id="1bd5b-117">在此範例中，我們會使用參數來識別可用的運行時， `Name` 並將傳回物件儲存至變數 `$activeRunspace` 。</span><span class="sxs-lookup"><span data-stu-id="1bd5b-117">In this example, we identify an available runspace using the `Name` parameter and store the return object to the variable `$activeRunspace`.</span></span> <span data-ttu-id="1bd5b-118">這可讓您在後續的執行中使用 **運行** 時的屬性 `Get-Runspace` 。</span><span class="sxs-lookup"><span data-stu-id="1bd5b-118">This allows you to use the properties of the **Runspace** in subsequent runs of `Get-Runspace`.</span></span>

```powershell
$activeRunspace = Get-Runspace -Name Runspace1
Get-Runspace -InstanceId $activeRunspace.InstanceId
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

## <span data-ttu-id="1bd5b-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1bd5b-119">PARAMETERS</span></span>

### <span data-ttu-id="1bd5b-120">-Id</span><span class="sxs-lookup"><span data-stu-id="1bd5b-120">-Id</span></span>

<span data-ttu-id="1bd5b-121">指定運行空間的識別碼</span><span class="sxs-lookup"><span data-stu-id="1bd5b-121">Specifies the Id of a runspace</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1bd5b-122">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="1bd5b-122">-InstanceId</span></span>

<span data-ttu-id="1bd5b-123">指定執行中工作的執行個體識別碼 GUID。</span><span class="sxs-lookup"><span data-stu-id="1bd5b-123">Specifies the instance ID GUID of a running job.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1bd5b-124">-Name</span><span class="sxs-lookup"><span data-stu-id="1bd5b-124">-Name</span></span>

<span data-ttu-id="1bd5b-125">指定運行空間的名稱</span><span class="sxs-lookup"><span data-stu-id="1bd5b-125">Specifies the Name of a runspace</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1bd5b-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1bd5b-126">CommonParameters</span></span>

<span data-ttu-id="1bd5b-127">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="1bd5b-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1bd5b-128">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="1bd5b-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1bd5b-129">輸入</span><span class="sxs-lookup"><span data-stu-id="1bd5b-129">INPUTS</span></span>

## <span data-ttu-id="1bd5b-130">輸出</span><span class="sxs-lookup"><span data-stu-id="1bd5b-130">OUTPUTS</span></span>

### <span data-ttu-id="1bd5b-131">系統管理。運行空間</span><span class="sxs-lookup"><span data-stu-id="1bd5b-131">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="1bd5b-132">您可以使用管線將命令的結果傳送 `Get-Runspace` 至 `Debug-Runspace` 。</span><span class="sxs-lookup"><span data-stu-id="1bd5b-132">You can pipe the results of a `Get-Runspace` command to `Debug-Runspace`.</span></span>

## <span data-ttu-id="1bd5b-133">注意</span><span class="sxs-lookup"><span data-stu-id="1bd5b-133">NOTES</span></span>

## <span data-ttu-id="1bd5b-134">相關連結</span><span class="sxs-lookup"><span data-stu-id="1bd5b-134">RELATED LINKS</span></span>

[<span data-ttu-id="1bd5b-135">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="1bd5b-135">Debug-Runspace</span></span>](Debug-Runspace.md)
