---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: df4fda68508e21700235d2b772c6dd43c8e1fe1e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203495"
---
# <span data-ttu-id="4f5b3-103">Set-Service</span><span class="sxs-lookup"><span data-stu-id="4f5b3-103">Set-Service</span></span>

## <span data-ttu-id="4f5b3-104">概要</span><span class="sxs-lookup"><span data-stu-id="4f5b3-104">SYNOPSIS</span></span>
<span data-ttu-id="4f5b3-105">啟動、停止並擱置服務，然後變更其屬性。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-105">Starts, stops, and suspends a service, and changes its properties.</span></span>

## <span data-ttu-id="4f5b3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4f5b3-106">SYNTAX</span></span>

### <span data-ttu-id="4f5b3-107">Name (預設值)</span><span class="sxs-lookup"><span data-stu-id="4f5b3-107">Name (Default)</span></span>

```
Set-Service [-ComputerName <String[]>] [-Name] <String> [-DisplayName <String>]
 [-Description <String>] [-StartupType <ServiceStartMode>] [-Status <String>] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4f5b3-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="4f5b3-108">InputObject</span></span>

```
Set-Service [-ComputerName <String[]>] [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Status <String>] [-InputObject <ServiceController>] [-PassThru]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4f5b3-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4f5b3-109">DESCRIPTION</span></span>

<span data-ttu-id="4f5b3-110">此 `Set-Service` Cmdlet 會變更服務的屬性，例如 **Status** 、 **Description** 、 **DisplayName** 和 **StartupType** 。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-110">The `Set-Service` cmdlet changes the properties of a service such as the **Status** , **Description** , **DisplayName** , and **StartupType** .</span></span> <span data-ttu-id="4f5b3-111">`Set-Service` 可以啟動、停止、暫停或暫停服務。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-111">`Set-Service` can start, stop, suspend, or pause a service.</span></span> <span data-ttu-id="4f5b3-112">若要識別服務，請輸入其服務名稱或提交服務物件。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-112">To identify a service, enter its service name or submit a service object.</span></span> <span data-ttu-id="4f5b3-113">或者，將服務名稱或服務物件沿著管線向下傳送至 `Set-Service` 。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-113">Or, send a service name or service object down the pipeline to `Set-Service`.</span></span>

## <span data-ttu-id="4f5b3-114">範例</span><span class="sxs-lookup"><span data-stu-id="4f5b3-114">EXAMPLES</span></span>

### <span data-ttu-id="4f5b3-115">範例1：變更顯示名稱</span><span class="sxs-lookup"><span data-stu-id="4f5b3-115">Example 1: Change a display name</span></span>

<span data-ttu-id="4f5b3-116">在此範例中，服務的顯示名稱已變更。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-116">In this example, a service's display name is changed.</span></span> <span data-ttu-id="4f5b3-117">若要查看原始顯示名稱，請使用 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-117">To view the original display name, use `Get-Service`.</span></span>

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

<span data-ttu-id="4f5b3-118">`Set-Service` 使用 **Name** 參數來指定服務的名稱 **LanmanWorkstation** 。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-118">`Set-Service` uses the **Name** parameter to specify the service's name, **LanmanWorkstation** .</span></span> <span data-ttu-id="4f5b3-119">**DisplayName** 參數指定新的顯示名稱 [ **LanMan 工作站** ]。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-119">The **DisplayName** parameter specifies the new display name, **LanMan Workstation** .</span></span>

### <span data-ttu-id="4f5b3-120">範例2：變更服務的啟動類型</span><span class="sxs-lookup"><span data-stu-id="4f5b3-120">Example 2: Change the startup type of services</span></span>

<span data-ttu-id="4f5b3-121">此範例顯示如何變更服務的啟動類型。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-121">This example shows how to change a service's startup type.</span></span>

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

<span data-ttu-id="4f5b3-122">`Set-Service` 使用 **Name** 參數來指定服務的名稱（ **BITS** ）。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-122">`Set-Service` uses the **Name** parameter to specify the service's name, **BITS** .</span></span> <span data-ttu-id="4f5b3-123">**StartupType** 參數會將服務設定為 **自動** 。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-123">The **StartupType** parameter sets the service to **Automatic** .</span></span>

<span data-ttu-id="4f5b3-124">`Get-Service` 使用 **Name** 參數來指定 **BITS** 服務，並將物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-124">`Get-Service` uses the **Name** parameter to specify the **BITS** service and sends the object down the pipeline.</span></span> <span data-ttu-id="4f5b3-125">`Select-Object` 使用 **Property** 參數來顯示 **BITS** 服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-125">`Select-Object` uses the **Property** parameter to display the **BITS** service's status.</span></span>

### <span data-ttu-id="4f5b3-126">範例3：變更服務的描述</span><span class="sxs-lookup"><span data-stu-id="4f5b3-126">Example 3: Change the description of a service</span></span>

<span data-ttu-id="4f5b3-127">此範例會變更 BITS 服務的描述，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-127">This example changes the BITS service's description and displays the result.</span></span>

<span data-ttu-id="4f5b3-128">`Get-CimInstance`使用 Cmdlet 的原因是它會傳回包含服務 **描述** 的 **Win32_Service** 物件。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-128">The `Get-CimInstance` cmdlet is used because it returns a **Win32_Service** object that includes the service's **Description** .</span></span>

```powershell
Get-CimInstance Win32_Service -Filter 'Name = "BITS"'  | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth. If the service is
              disabled, then any applications that depend on BITS, such as Windows Update or MSN
              Explorer, will be unable to automatically download programs and other information.
```

```powershell
Set-Service -Name BITS -Description "Transfers files in the background using idle network bandwidth."
Get-CimInstance Win32_Service -Filter 'Name = "BITS"' | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth.
```

<span data-ttu-id="4f5b3-129">`Get-CimInstance` 將物件向下傳送至管線， `Format-List` 並顯示服務的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-129">`Get-CimInstance` sends the object down the pipeline to `Format-List` and displays the service's name and description.</span></span> <span data-ttu-id="4f5b3-130">為了進行比較，此命令會在更新描述之前和之後執行。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-130">For comparison purposes, the command is run before and after the description is updated.</span></span>

<span data-ttu-id="4f5b3-131">`Set-Service` 使用 **Name** 參數來指定 **BITS** 服務。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-131">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="4f5b3-132">**Description** 參數會指定服務描述的更新文字。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-132">The **Description** parameter specifies the updated text for the services' description.</span></span>

### <span data-ttu-id="4f5b3-133">範例4：啟動服務</span><span class="sxs-lookup"><span data-stu-id="4f5b3-133">Example 4: Start a service</span></span>

<span data-ttu-id="4f5b3-134">在此範例中，會啟動服務。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-134">In this example, a service is started.</span></span>

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

<span data-ttu-id="4f5b3-135">`Set-Service` 使用 **Name** 參數來指定服務 **WinRM** 。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-135">`Set-Service` uses the **Name** parameter to specify the service, **WinRM** .</span></span> <span data-ttu-id="4f5b3-136">**Status** 參數會使用執行的 **值來** 啟動服務。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-136">The **Status** parameter uses the value **Running** to start the service.</span></span> <span data-ttu-id="4f5b3-137">**PassThru** 參數會輸出顯示結果的 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-137">The **PassThru** parameter outputs a **ServiceController** object that displays the results.</span></span>

### <span data-ttu-id="4f5b3-138">範例5：暫止服務</span><span class="sxs-lookup"><span data-stu-id="4f5b3-138">Example 5: Suspend a service</span></span>

<span data-ttu-id="4f5b3-139">此範例會使用管線來暫停至服務。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-139">This example uses the pipeline to pause to service.</span></span>

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

<span data-ttu-id="4f5b3-140">`Get-Service` 使用 **Name** 參數來指定 **排程** 服務，然後將物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-140">`Get-Service` uses the **Name** parameter to specify the **Schedule** service, and sends the object down the pipeline.</span></span> <span data-ttu-id="4f5b3-141">`Set-Service` 使用 **Status** 參數將服務設定為 **暫停** 。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-141">`Set-Service` uses the **Status** parameter to set the service to **Paused** .</span></span>

### <span data-ttu-id="4f5b3-142">範例6：停止服務</span><span class="sxs-lookup"><span data-stu-id="4f5b3-142">Example 6: Stop a service</span></span>

<span data-ttu-id="4f5b3-143">此範例會使用變數來停止服務。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-143">This example uses a variable to stop a service.</span></span>

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

<span data-ttu-id="4f5b3-144">`Get-Service` 使用 **Name** 參數來指定服務（ **Schedule** ）。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-144">`Get-Service` uses the **Name** parameter to specify the service, **Schedule** .</span></span> <span data-ttu-id="4f5b3-145">物件會儲存在變數中 `$S` 。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-145">The object is stored in the variable, `$S`.</span></span> <span data-ttu-id="4f5b3-146">`Set-Service` 使用 **InputObject** 參數並指定儲存的物件 `$S` 。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-146">`Set-Service` uses the **InputObject** parameter and specifies the object stored `$S`.</span></span> <span data-ttu-id="4f5b3-147">**Status** 參數會將服務設定為「 **已停止** 」。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-147">The **Status** parameter sets the service to **Stopped** .</span></span>

## <span data-ttu-id="4f5b3-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4f5b3-148">PARAMETERS</span></span>

### <span data-ttu-id="4f5b3-149">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="4f5b3-149">-ComputerName</span></span>

<span data-ttu-id="4f5b3-150">指定一或多部電腦。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-150">Specifies one or more computers.</span></span> <span data-ttu-id="4f5b3-151">針對 [遠端電腦]，輸入 NetBIOS 名稱、IP 位址或完整功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-151">For remote computers, type the NetBIOS name, an IP address, or a fully qualified domain name.</span></span> <span data-ttu-id="4f5b3-152">如果未指定 **ComputerName** 參數，則命令會在本機電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-152">If the **ComputerName** parameter isn't specified, the command runs on the local computer.</span></span>

<span data-ttu-id="4f5b3-153">此參數不依賴 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-153">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="4f5b3-154">即使您的電腦未設定為執行遠端命令，您也可以使用 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-154">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f5b3-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4f5b3-155">-Confirm</span></span>

<span data-ttu-id="4f5b3-156">在執行之前提示您確認 `Set-Service` 。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-156">Prompts you for confirmation before running `Set-Service`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f5b3-157">-Description</span><span class="sxs-lookup"><span data-stu-id="4f5b3-157">-Description</span></span>

<span data-ttu-id="4f5b3-158">指定服務的新描述。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-158">Specifies a new description for the service.</span></span>

<span data-ttu-id="4f5b3-159">服務描述會顯示在 [ **電腦管理]、[服務** ] 中。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-159">The service description appears in **Computer Management, Services** .</span></span> <span data-ttu-id="4f5b3-160">**描述** 不是 `Get-Service` **ServiceController** 物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-160">The **Description** isn't a property of the `Get-Service` **ServiceController** object.</span></span> <span data-ttu-id="4f5b3-161">若要查看服務描述，請使用傳回 `Get-CimInstance` 代表服務的 **Win32_Service** 物件。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-161">To see the service description, use `Get-CimInstance` that returns a **Win32_Service** object that represents the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f5b3-162">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="4f5b3-162">-DisplayName</span></span>

<span data-ttu-id="4f5b3-163">指定服務的新顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-163">Specifies a new display name for the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: DN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f5b3-164">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4f5b3-164">-InputObject</span></span>

<span data-ttu-id="4f5b3-165">指定代表要變更之服務的 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-165">Specifies a **ServiceController** object that represents the service to change.</span></span> <span data-ttu-id="4f5b3-166">輸入包含物件的變數，或輸入可取得物件的命令或運算式，例如 `Get-Service` 命令。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-166">Enter a variable that contains the object, or type a command or expression that gets the object, such as a `Get-Service` command.</span></span> <span data-ttu-id="4f5b3-167">您可以使用管線將服務物件傳送至 `Set-Service` 。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-167">You can use the pipeline to send a service object to `Set-Service`.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4f5b3-168">-Name</span><span class="sxs-lookup"><span data-stu-id="4f5b3-168">-Name</span></span>

<span data-ttu-id="4f5b3-169">指定要變更之服務的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-169">Specifies the service name of the service to be changed.</span></span> <span data-ttu-id="4f5b3-170">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-170">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="4f5b3-171">您可以使用管線將服務名稱傳送至 `Set-Service` 。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-171">You can use the pipeline to send a service name to `Set-Service`.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4f5b3-172">-PassThru</span><span class="sxs-lookup"><span data-stu-id="4f5b3-172">-PassThru</span></span>

<span data-ttu-id="4f5b3-173">傳回代表已變更之服務的 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-173">Returns a **ServiceController** object that represents the services that were changed.</span></span> <span data-ttu-id="4f5b3-174">依預設， `Set-Service` 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-174">By default, `Set-Service` doesn't generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f5b3-175">-StartupType</span><span class="sxs-lookup"><span data-stu-id="4f5b3-175">-StartupType</span></span>

<span data-ttu-id="4f5b3-176">設定服務的啟動類型。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-176">Sets the startup type of the service.</span></span> <span data-ttu-id="4f5b3-177">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="4f5b3-177">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4f5b3-178">**自動** -服務會在系統啟動時啟動或由作業系統啟動。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-178">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="4f5b3-179">如果自動啟動的服務依賴手動啟動的服務，以手動方式啟動的服務也會在系統啟動時自動啟動。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-179">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="4f5b3-180">**停用** -服務已停用，且無法由使用者或應用程式啟動。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-180">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="4f5b3-181">**手動** -此服務只會由使用者以手動方式啟動，使用服務控制管理員或由應用程式啟動。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-181">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>
- <span data-ttu-id="4f5b3-182">**開機** -表示該服務是由系統載入器啟動的設備磁碟機。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-182">**Boot** - Indicates that the service is a device driver started by the system loader.</span></span> <span data-ttu-id="4f5b3-183">這個值僅適用於裝置驅動程式。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-183">This value is valid only for device drivers.</span></span>
- <span data-ttu-id="4f5b3-184">**系統** -表示服務是由 ' IOInitSystem ( # A1 ' 函式啟動的設備磁碟機。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-184">**System** - Indicates that the service is a device driver started by the 'IOInitSystem()' function.</span></span> <span data-ttu-id="4f5b3-185">這個值僅適用於裝置驅動程式。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-185">This value is valid only for device drivers.</span></span>

 <span data-ttu-id="4f5b3-186">預設值為 [ **自動** ]。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-186">The default value is **Automatic** .</span></span>

```yaml
Type: System.ServiceProcess.ServiceStartMode
Parameter Sets: (All)
Aliases: StartMode, SM, ST
Accepted values: Boot, System, Automatic, Manual, Disabled

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f5b3-187">-Status</span><span class="sxs-lookup"><span data-stu-id="4f5b3-187">-Status</span></span>

<span data-ttu-id="4f5b3-188">指定服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-188">Specifies the status for the service.</span></span>

<span data-ttu-id="4f5b3-189">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="4f5b3-189">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="4f5b3-190">已 **暫停** 。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-190">**Paused** .</span></span> <span data-ttu-id="4f5b3-191">暫停服務。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-191">Suspends the service.</span></span>
- <span data-ttu-id="4f5b3-192">**正在** 執行。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-192">**Running** .</span></span> <span data-ttu-id="4f5b3-193">啟動服務。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-193">Starts the service.</span></span>
- <span data-ttu-id="4f5b3-194">**已停止** 。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-194">**Stopped** .</span></span> <span data-ttu-id="4f5b3-195">停止服務。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-195">Stops the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Paused, Running, Stopped

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f5b3-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4f5b3-196">-WhatIf</span></span>

<span data-ttu-id="4f5b3-197">顯示執行時所發生 `Set-Service` 的情況。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-197">Shows what would happen if `Set-Service` runs.</span></span> <span data-ttu-id="4f5b3-198">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-198">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f5b3-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4f5b3-199">CommonParameters</span></span>

<span data-ttu-id="4f5b3-200">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4f5b3-201">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4f5b3-202">輸入</span><span class="sxs-lookup"><span data-stu-id="4f5b3-202">INPUTS</span></span>

### <span data-ttu-id="4f5b3-203">System.ServiceProcess.ServiceController、System.String</span><span class="sxs-lookup"><span data-stu-id="4f5b3-203">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="4f5b3-204">您可以使用管線將服務物件或包含服務名稱的字串傳送至 `Set-Service` 。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-204">You can use the pipeline to send a service object or a string that contains a service name to `Set-Service`.</span></span>

## <span data-ttu-id="4f5b3-205">輸出</span><span class="sxs-lookup"><span data-stu-id="4f5b3-205">OUTPUTS</span></span>

### <span data-ttu-id="4f5b3-206">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="4f5b3-206">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="4f5b3-207">依預設， `Set-Service` 不會傳回任何物件。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-207">By default, `Set-Service` doesn't return any objects.</span></span> <span data-ttu-id="4f5b3-208">使用 **PassThru** 參數輸出 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-208">Use the **PassThru** parameter to output a **ServiceController** object.</span></span>

## <span data-ttu-id="4f5b3-209">注意</span><span class="sxs-lookup"><span data-stu-id="4f5b3-209">NOTES</span></span>

<span data-ttu-id="4f5b3-210">`Set-Service` 需要較高的許可權。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-210">`Set-Service` requires elevated permissions.</span></span> <span data-ttu-id="4f5b3-211">使用 [ **以系統管理員身分執行** ] 選項。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-211">Use the **Run as administrator** option.</span></span>

<span data-ttu-id="4f5b3-212">`Set-Service` 只有在目前的使用者有權管理服務時，才能控制服務。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-212">`Set-Service` can only control services when the current user has permissions to manage services.</span></span> <span data-ttu-id="4f5b3-213">如果命令無法正確運作，您可能沒有必要的許可權。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-213">If a command doesn't work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="4f5b3-214">若要尋找服務的服務名稱或顯示名稱，請使用 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-214">To find a service's service name or display name, use `Get-Service`.</span></span> <span data-ttu-id="4f5b3-215">服務名稱是在 [ **名稱** ] 資料行中，而顯示名稱則是在 [ **DisplayName** ] 欄位中。</span><span class="sxs-lookup"><span data-stu-id="4f5b3-215">The service names are in the **Name** column and the display names are in the **DisplayName** column.</span></span>

## <span data-ttu-id="4f5b3-216">相關連結</span><span class="sxs-lookup"><span data-stu-id="4f5b3-216">RELATED LINKS</span></span>

[<span data-ttu-id="4f5b3-217">Get-Service</span><span class="sxs-lookup"><span data-stu-id="4f5b3-217">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="4f5b3-218">New-Service</span><span class="sxs-lookup"><span data-stu-id="4f5b3-218">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="4f5b3-219">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="4f5b3-219">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="4f5b3-220">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="4f5b3-220">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="4f5b3-221">Start-Service</span><span class="sxs-lookup"><span data-stu-id="4f5b3-221">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="4f5b3-222">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="4f5b3-222">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="4f5b3-223">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="4f5b3-223">Suspend-Service</span></span>](Suspend-Service.md)
