---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pshostprocessinfo?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSHostProcessInfo
ms.openlocfilehash: 5f3579e002030715d7e5926de5f6209cd61b0367
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202299"
---
# <span data-ttu-id="45e4b-103">Get-PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="45e4b-103">Get-PSHostProcessInfo</span></span>

## <span data-ttu-id="45e4b-104">概要</span><span class="sxs-lookup"><span data-stu-id="45e4b-104">SYNOPSIS</span></span>
<span data-ttu-id="45e4b-105">取得 PowerShell 主機的相關處理資訊。</span><span class="sxs-lookup"><span data-stu-id="45e4b-105">Gets process information about the PowerShell host.</span></span>

## <span data-ttu-id="45e4b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="45e4b-106">SYNTAX</span></span>

### <span data-ttu-id="45e4b-107">ProcessNameParameterSet (預設) </span><span class="sxs-lookup"><span data-stu-id="45e4b-107">ProcessNameParameterSet (Default)</span></span>

```
Get-PSHostProcessInfo [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="45e4b-108">ProcessParameterSet</span><span class="sxs-lookup"><span data-stu-id="45e4b-108">ProcessParameterSet</span></span>

```
Get-PSHostProcessInfo [-Process] <Process[]> [<CommonParameters>]
```

### <span data-ttu-id="45e4b-109">ProcessIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="45e4b-109">ProcessIdParameterSet</span></span>

```
Get-PSHostProcessInfo [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="45e4b-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="45e4b-110">DESCRIPTION</span></span>

<span data-ttu-id="45e4b-111">此 `Get-PSHostProcessInfo` Cmdlet 會取得在本機電腦上執行之 PowerShell 主機進程的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="45e4b-111">The `Get-PSHostProcessInfo` cmdlet gets information about PowerShell host processes running on the local computer.</span></span>

<span data-ttu-id="45e4b-112">從 PowerShell 6.2 開始，非 Windows 平臺支援此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45e4b-112">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

## <span data-ttu-id="45e4b-113">範例</span><span class="sxs-lookup"><span data-stu-id="45e4b-113">EXAMPLES</span></span>

### <span data-ttu-id="45e4b-114">1：取得正在系統上執行的 PowerShell 主機清單</span><span class="sxs-lookup"><span data-stu-id="45e4b-114">1: Get a list of PowerShell hosts running on the system</span></span>

```powershell
Get-PSHostProcessInfo
```

```Output
ProcessName ProcessId AppDomainName    MainWindowTitle
----------- --------- -------------    ---------------
powershell      14676 DefaultAppDomain Windows PowerShell
powershell       5184 DefaultAppDomain Windows PowerShell
```

### <span data-ttu-id="45e4b-115">2：取得特定進程的 PowerShell 主機資訊</span><span class="sxs-lookup"><span data-stu-id="45e4b-115">2: Get PowerShell host information for a specific process</span></span>

```powershell
Get-PSHostProcessInfo -Id 14676
```

```Output
ProcessName ProcessId AppDomainName    MainWindowTitle
----------- --------- -------------    ---------------
powershell      14676 DefaultAppDomain Windows PowerShell
```

## <span data-ttu-id="45e4b-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="45e4b-116">PARAMETERS</span></span>

### <span data-ttu-id="45e4b-117">-Id</span><span class="sxs-lookup"><span data-stu-id="45e4b-117">-Id</span></span>

<span data-ttu-id="45e4b-118">依處理序識別碼指定處理程序。</span><span class="sxs-lookup"><span data-stu-id="45e4b-118">Specifies a process by the process ID.</span></span> <span data-ttu-id="45e4b-119">若要取得處理序識別碼，請執行 `Get-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45e4b-119">To get a process ID, run the `Get-Process` cmdlet.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45e4b-120">-Name</span><span class="sxs-lookup"><span data-stu-id="45e4b-120">-Name</span></span>

<span data-ttu-id="45e4b-121">依處理程序名稱指定處理程序。</span><span class="sxs-lookup"><span data-stu-id="45e4b-121">Specifies a process by the process name.</span></span> <span data-ttu-id="45e4b-122">若要取得處理常式名稱，請執行 `Get-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45e4b-122">To get a process name, run the `Get-Process` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45e4b-123">-Process</span><span class="sxs-lookup"><span data-stu-id="45e4b-123">-Process</span></span>

<span data-ttu-id="45e4b-124">依處理程序物件指定處理程序。</span><span class="sxs-lookup"><span data-stu-id="45e4b-124">Specifies a process by the process object.</span></span> <span data-ttu-id="45e4b-125">使用此參數最簡單的方式是儲存命令的結果，此 `Get-Process` 命令會傳回您要在變數中輸入的進程，然後將變數指定為此參數的值。</span><span class="sxs-lookup"><span data-stu-id="45e4b-125">The simplest way to use this parameter is to save the results of a `Get-Process` command that returns process that you want to enter in a variable, and then specify the variable as the value of this parameter.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="45e4b-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="45e4b-126">CommonParameters</span></span>

<span data-ttu-id="45e4b-127">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="45e4b-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="45e4b-128">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="45e4b-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="45e4b-129">輸入</span><span class="sxs-lookup"><span data-stu-id="45e4b-129">INPUTS</span></span>

### <span data-ttu-id="45e4b-130">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="45e4b-130">System.Diagnostics.Process</span></span>

<span data-ttu-id="45e4b-131">您可以使用管線將 **處理** 程式物件傳送 `Get-Process` 至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45e4b-131">You can pipe a **Process** object from `Get-Process` to this cmdlet.</span></span>

## <span data-ttu-id="45e4b-132">輸出</span><span class="sxs-lookup"><span data-stu-id="45e4b-132">OUTPUTS</span></span>

### <span data-ttu-id="45e4b-133">Exit-pshostprocessinfo。</span><span class="sxs-lookup"><span data-stu-id="45e4b-133">Microsoft.PowerShell.Commands.PSHostProcessInfo</span></span>

## <span data-ttu-id="45e4b-134">注意</span><span class="sxs-lookup"><span data-stu-id="45e4b-134">NOTES</span></span>

## <span data-ttu-id="45e4b-135">相關連結</span><span class="sxs-lookup"><span data-stu-id="45e4b-135">RELATED LINKS</span></span>

[<span data-ttu-id="45e4b-136">Get-Process</span><span class="sxs-lookup"><span data-stu-id="45e4b-136">Get-Process</span></span>](../Microsoft.PowerShell.Management/get-process.md)
