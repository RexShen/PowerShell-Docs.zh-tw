---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: 0c007f1becd7364806cfd47e18cf05995b81e0f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203988"
---
# <span data-ttu-id="478a3-103">Get-Service</span><span class="sxs-lookup"><span data-stu-id="478a3-103">Get-Service</span></span>

## <span data-ttu-id="478a3-104">概要</span><span class="sxs-lookup"><span data-stu-id="478a3-104">SYNOPSIS</span></span>
<span data-ttu-id="478a3-105">取得本機電腦或遠端電腦上的服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-105">Gets the services on a local or remote computer.</span></span>

## <span data-ttu-id="478a3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="478a3-106">SYNTAX</span></span>

### <span data-ttu-id="478a3-107">Default (預設值)</span><span class="sxs-lookup"><span data-stu-id="478a3-107">Default (Default)</span></span>

```
Get-Service [[-Name] <String[]>] [-ComputerName <String[]>] [-DependentServices] [-RequiredServices]
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="478a3-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="478a3-108">DisplayName</span></span>

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] -DisplayName <String[]>
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="478a3-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="478a3-109">InputObject</span></span>

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## <span data-ttu-id="478a3-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="478a3-110">DESCRIPTION</span></span>

<span data-ttu-id="478a3-111">**Get-help** Cmdlet 會取得代表本機電腦或遠端電腦上之服務的物件，包括執行中和已停止的服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-111">The **Get-Service** cmdlet gets objects that represent the services on a local computer or on a remote computer, including running and stopped services.</span></span>

<span data-ttu-id="478a3-112">您可以藉由指定服務的服務名稱或顯示名稱，或使用管線將服務物件傳送至此 Cmdlet，來指示此 Cmdlet 只取得特定的服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-112">You can direct this cmdlet to get only particular services by specifying the service name or the display name of the services, or you can pipe service objects to this cmdlet.</span></span>

## <span data-ttu-id="478a3-113">範例</span><span class="sxs-lookup"><span data-stu-id="478a3-113">EXAMPLES</span></span>

### <span data-ttu-id="478a3-114">範例1：取得電腦上的所有服務</span><span class="sxs-lookup"><span data-stu-id="478a3-114">Example 1: Get all services on the computer</span></span>

```powershell
Get-Service
```

<span data-ttu-id="478a3-115">此命令會取得電腦上的所有服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-115">This command gets all of the services on the computer.</span></span>
<span data-ttu-id="478a3-116">它的行為就像您輸入 `Get-Service *` 的一樣。</span><span class="sxs-lookup"><span data-stu-id="478a3-116">It behaves as though you typed `Get-Service *`.</span></span>
<span data-ttu-id="478a3-117">預設顯示會展示狀態、服務名稱及每個服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="478a3-117">The default display shows the status, service name, and display name of each service.</span></span>

### <span data-ttu-id="478a3-118">範例2：取得以搜尋字串開頭的服務</span><span class="sxs-lookup"><span data-stu-id="478a3-118">Example 2: Get services that begin with a search string</span></span>

```powershell
Get-Service "wmi*"
```

<span data-ttu-id="478a3-119">此命令會取得服務名稱開頭為 WMI 的服務， (Windows Management Instrumentation) 的縮寫。</span><span class="sxs-lookup"><span data-stu-id="478a3-119">This command retrieves services with service names that begin with WMI (the acronym for Windows Management Instrumentation).</span></span>

### <span data-ttu-id="478a3-120">範例3：顯示包含搜尋字串的服務</span><span class="sxs-lookup"><span data-stu-id="478a3-120">Example 3: Display services that include a search string</span></span>

```powershell
Get-Service -Displayname "*network*"
```

<span data-ttu-id="478a3-121">此命令會顯示顯示名稱包含「網路」文字的服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-121">This command displays services with a display name that includes the word network.</span></span>
<span data-ttu-id="478a3-122">搜尋顯示名稱會尋找網路相關的服務，即使服務名稱並不包含 "Net"，例如 xmlprov (網路佈建服務)。</span><span class="sxs-lookup"><span data-stu-id="478a3-122">Searching the display name finds network-related services even when the service name does not include "Net", such as xmlprov, the Network Provisioning Service.</span></span>

### <span data-ttu-id="478a3-123">範例4：取得以搜尋字串和排除開頭的服務</span><span class="sxs-lookup"><span data-stu-id="478a3-123">Example 4: Get services that begin with a search string and an exclusion</span></span>

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

<span data-ttu-id="478a3-124">這些命令只會取得服務名稱開頭為 win 的服務，但 WinRM 服務除外。</span><span class="sxs-lookup"><span data-stu-id="478a3-124">These commands get only the services with service names that begin with win, except for the WinRM service.</span></span>

### <span data-ttu-id="478a3-125">範例5：顯示目前作用中的服務</span><span class="sxs-lookup"><span data-stu-id="478a3-125">Example 5: Display services that are currently active</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

<span data-ttu-id="478a3-126">此命令只會顯示目前使用中的服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-126">This command displays only the services that are currently active.</span></span>
<span data-ttu-id="478a3-127">它會使用 **get-help** Cmdlet 取得電腦上的所有服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-127">It uses the **Get-Service** cmdlet to get all of the services on the computer.</span></span>
<span data-ttu-id="478a3-128">管線運算子 (|) 將結果傳遞給 Where-Object Cmdlet，此 Cmdlet 只會選取 Status 屬性等於「正在執行」的服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-128">The pipeline operator (|) passes the results to the Where-Object cmdlet, which selects only the services with a Status property that equals Running.</span></span>

<span data-ttu-id="478a3-129">Status 只是服務物件的一個屬性。</span><span class="sxs-lookup"><span data-stu-id="478a3-129">Status is only one property of service objects.</span></span>
<span data-ttu-id="478a3-130">若要查看所有屬性，請輸入 `Get-Service | Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="478a3-130">To see all of the properties, type `Get-Service | Get-Member`.</span></span>

### <span data-ttu-id="478a3-131">範例6：取得遠端電腦上的服務</span><span class="sxs-lookup"><span data-stu-id="478a3-131">Example 6: Get the services on a remote computer</span></span>

```powershell
Get-Service -ComputerName "Server02"
```

<span data-ttu-id="478a3-132">此命令會取得 Server02 遠端電腦上的服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-132">This command gets the services on the Server02 remote computer.</span></span>

<span data-ttu-id="478a3-133">因為「 **取得服務** 」的 *ComputerName* 參數不會使用 Windows PowerShell 遠端處理，所以即使電腦未設定 Windows PowerShell 的遠端功能，您還是可以使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="478a3-133">Because the *ComputerName* parameter of **Get-Service** does not use Windows PowerShell remoting, you can use this parameter even if the computer is not configured for remoting in Windows PowerShell.</span></span>

### <span data-ttu-id="478a3-134">範例7：列出本機電腦上具有相依服務的服務</span><span class="sxs-lookup"><span data-stu-id="478a3-134">Example 7: List the services on the local computer that have dependent services</span></span>

```powershell
Get-Service |
  Where-Object {$_.DependentServices} |
    Format-List -Property Name, DependentServices, @{
      Label="NoOfDependentServices"; Expression={$_.dependentservices.count}
    }
```

```Output
Name                  : AudioEndpointBuilder
DependentServices     : {AudioSrv}
NoOfDependentServices : 1

Name                  : Dhcp
DependentServices     : {WinHttpAutoProxySvc}
NoOfDependentServices : 1
...
```

<span data-ttu-id="478a3-135">第一個命令使用 **get-help** Cmdlet 取得電腦上的服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-135">The first command uses the **Get-Service** cmdlet to get the services on the computer.</span></span>
<span data-ttu-id="478a3-136">管線運算子 (|) 會將服務傳送至 **Where 物件** Cmdlet，此 Cmdlet 會選取 **DependentServices** 屬性不是 null 的服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-136">A pipeline operator (|) sends the services to the **Where-Object** cmdlet, which selects the services whose **DependentServices** property is not null.</span></span>

<span data-ttu-id="478a3-137">另一個管線運算子會將結果傳送給 Format-List Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="478a3-137">Another pipeline operator sends the results to the Format-List cmdlet.</span></span>
<span data-ttu-id="478a3-138">此命令會使用其 *Property* 參數來顯示服務的名稱、相依服務的名稱，以及顯示每個服務所擁有之相依服務數目的計算屬性。</span><span class="sxs-lookup"><span data-stu-id="478a3-138">The command uses its *Property* parameter to display the name of the service, the name of the dependent services, and a calculated property that displays the number of dependent services that each service has.</span></span>

### <span data-ttu-id="478a3-139">範例8：依屬性值排序服務</span><span class="sxs-lookup"><span data-stu-id="478a3-139">Example 8: Sort services by property value</span></span>

```powershell
Get-Service "s*" | Sort-Object status
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  stisvc             Windows Image Acquisition (WIA)
Stopped  SwPrv              MS Software Shadow Copy Provider
Stopped  SysmonLog          Performance Logs and Alerts
Running  Spooler            Print Spooler
Running  srservice          System Restore Service
Running  SSDPSRV            SSDP Discovery Service
Running  ShellHWDetection   Shell Hardware Detection
Running  Schedule           Task Scheduler
Running  SCardSvr           Smart Card
Running  SamSs              Security Accounts Manager
Running  SharedAccess       Windows Firewall/Internet Connectio...
Running  SENS               System Event Notification
Running  seclogon           Secondary Logon
```

<span data-ttu-id="478a3-140">此命令顯示當您依 [ **狀態** ] 屬性的值以遞增順序排序服務時，已停止的服務會在執行服務之前出現。</span><span class="sxs-lookup"><span data-stu-id="478a3-140">This command shows that when you sort services in ascending order by the value of their **Status** property, stopped services appear before running services.</span></span>
<span data-ttu-id="478a3-141">發生這種情況是因為 Status 的值是列舉，其中已停止的值為1，而且執行的值為4。</span><span class="sxs-lookup"><span data-stu-id="478a3-141">This happens because the value of Status is an enumeration, in which Stopped has a value of 1, and Running has a value of 4.</span></span>

<span data-ttu-id="478a3-142">若要先列出執行中的服務，請使用 Sort-Object Cmdlet 的 *遞減* 參數。</span><span class="sxs-lookup"><span data-stu-id="478a3-142">To list running services first, use the *Descending* parameter of the Sort-Object cmdlet.</span></span>

### <span data-ttu-id="478a3-143">範例9：取得多部電腦上的服務</span><span class="sxs-lookup"><span data-stu-id="478a3-143">Example 9: Get services on multiple computers</span></span>

```powershell
Get-Service -Name "WinRM" -ComputerName "localhost", "Server01", "Server02" |
 Format-Table -Property MachineName, Status, Name, DisplayName -auto
```

```Output
MachineName    Status  Name  DisplayName
------------   ------  ----  -----------
localhost      Running WinRM Windows Remote Management (WS-Management)
Server01       Running WinRM Windows Remote Management (WS-Management)
Server02       Running WinRM Windows Remote Management (WS-Management)
```

<span data-ttu-id="478a3-144">此命令會使用 **get-help** Cmdlet 在兩部遠端電腦上執行 Get-Service Winrm 命令，並在本機電腦上執行 ( "localhost" ) 。</span><span class="sxs-lookup"><span data-stu-id="478a3-144">This command uses the **Get-Service** cmdlet to run a Get-Service Winrm command on two remote computers and the local computer ("localhost").</span></span>

<span data-ttu-id="478a3-145">此命令會在遠端電腦上執行，並將結果傳回本機電腦。</span><span class="sxs-lookup"><span data-stu-id="478a3-145">The command runs on the remote computers, and the results are returned to the local computer.</span></span>
<span data-ttu-id="478a3-146">管線運算子 (|) 將結果傳送至 **格式資料表** Cmdlet，此 Cmdlet 會將服務格式化為資料表。</span><span class="sxs-lookup"><span data-stu-id="478a3-146">A pipeline operator (|) sends the results to the **Format-Table** cmdlet, which formats the services as a table.</span></span>
<span data-ttu-id="478a3-147">**Format 資料表** 命令使用 *Property* 參數來指定顯示在資料表中的屬性，包括 **MachineName** 屬性。</span><span class="sxs-lookup"><span data-stu-id="478a3-147">The **Format-Table** command uses the *Property* parameter to specify the properties displayed in the table, including the **MachineName** property.</span></span>

### <span data-ttu-id="478a3-148">範例10：取得服務的相依服務</span><span class="sxs-lookup"><span data-stu-id="478a3-148">Example 10: Get the dependent services of a service</span></span>

```powershell
Get-Service "WinRM" -RequiredServices
```

<span data-ttu-id="478a3-149">此命令會取得 WinRM 服務所需的服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-149">This command gets the services that the WinRM service requires.</span></span>

<span data-ttu-id="478a3-150">此命令會傳回服務之 **ServicesDependedOn** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="478a3-150">The command returns the value of the **ServicesDependedOn** property of the service.</span></span>

### <span data-ttu-id="478a3-151">範例11：透過管線運算子取得服務</span><span class="sxs-lookup"><span data-stu-id="478a3-151">Example 11: Get a service through the pipeline operator</span></span>

```powershell
"WinRM" | Get-Service
```

<span data-ttu-id="478a3-152">此命令會取得本機電腦上的 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-152">This command gets the WinRM service on the local computer.</span></span>
<span data-ttu-id="478a3-153">此範例示範您可以使用管線將服務名稱字串 (以引號括住) 至 **取得服務** 。</span><span class="sxs-lookup"><span data-stu-id="478a3-153">This example shows that you can pipe a service name string (enclosed in quotation marks) to **Get-Service** .</span></span>

## <span data-ttu-id="478a3-154">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="478a3-154">PARAMETERS</span></span>

### <span data-ttu-id="478a3-155">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="478a3-155">-ComputerName</span></span>

<span data-ttu-id="478a3-156">取得在指定電腦上執行的服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-156">Gets the services running on the specified computers.</span></span>
<span data-ttu-id="478a3-157">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="478a3-157">The default is the local computer.</span></span>

<span data-ttu-id="478a3-158">輸入遠端電腦 (FQDN) 的 NetBIOS 名稱、IP 位址或完整功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="478a3-158">Type the NetBIOS name, an IP address, or a fully qualified domain name (FQDN) of a remote computer.</span></span>
<span data-ttu-id="478a3-159">若要指定本機電腦，請輸入電腦名稱、句點 (.)，或者 localhost。</span><span class="sxs-lookup"><span data-stu-id="478a3-159">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="478a3-160">此參數不必依賴 Windows PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="478a3-160">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="478a3-161">即使您的電腦未設定為執行遠端命令，您也可以使用 **Get-Service** 的 *ComputerName* 參數。</span><span class="sxs-lookup"><span data-stu-id="478a3-161">You can use the *ComputerName* parameter of **Get-Service** even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="478a3-162">-DependentServices</span><span class="sxs-lookup"><span data-stu-id="478a3-162">-DependentServices</span></span>

<span data-ttu-id="478a3-163">指出此 Cmdlet 只會取得相依于指定服務的服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-163">Indicates that this cmdlet gets only the services that depend upon the specified service.</span></span>

<span data-ttu-id="478a3-164">根據預設，此 Cmdlet 會取得所有服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-164">By default, this cmdlet gets all services.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="478a3-165">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="478a3-165">-DisplayName</span></span>

<span data-ttu-id="478a3-166">以字串陣列指定要抓取之服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="478a3-166">Specifies, as a string array, the display names of services to be retrieved.</span></span>
<span data-ttu-id="478a3-167">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="478a3-167">Wildcards are permitted.</span></span>
<span data-ttu-id="478a3-168">根據預設，此 Cmdlet 會取得電腦上的所有服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-168">By default, this cmdlet gets all services on the computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="478a3-169">-Exclude</span><span class="sxs-lookup"><span data-stu-id="478a3-169">-Exclude</span></span>

<span data-ttu-id="478a3-170">以字串陣列指定此 Cmdlet 從作業中排除的服務或服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-170">Specifies, as a string array, a service or services that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="478a3-171">此參數的值會限定 *Name* 參數。</span><span class="sxs-lookup"><span data-stu-id="478a3-171">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="478a3-172">輸入名稱元素或模式，例如 "s\*"。</span><span class="sxs-lookup"><span data-stu-id="478a3-172">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="478a3-173">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="478a3-173">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="478a3-174">-Include</span><span class="sxs-lookup"><span data-stu-id="478a3-174">-Include</span></span>

<span data-ttu-id="478a3-175">以字串陣列指定此 Cmdlet 在作業中包含的服務或服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-175">Specifies, as a string array, a service or services that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="478a3-176">此參數的值會限定 *Name* 參數。</span><span class="sxs-lookup"><span data-stu-id="478a3-176">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="478a3-177">輸入名稱元素或模式，例如 "s\*"。</span><span class="sxs-lookup"><span data-stu-id="478a3-177">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="478a3-178">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="478a3-178">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="478a3-179">-InputObject</span><span class="sxs-lookup"><span data-stu-id="478a3-179">-InputObject</span></span>

<span data-ttu-id="478a3-180">指定代表要抓取之服務的 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="478a3-180">Specifies **ServiceController** objects representing the services to be retrieved.</span></span>
<span data-ttu-id="478a3-181">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="478a3-181">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>
<span data-ttu-id="478a3-182">您也可以使用管線將服務物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="478a3-182">You can also pipe a service object to this cmdlet.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="478a3-183">-Name</span><span class="sxs-lookup"><span data-stu-id="478a3-183">-Name</span></span>

<span data-ttu-id="478a3-184">指定要抓取之服務的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="478a3-184">Specifies the service names of services to be retrieved.</span></span>
<span data-ttu-id="478a3-185">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="478a3-185">Wildcards are permitted.</span></span>
<span data-ttu-id="478a3-186">根據預設，此 Cmdlet 會取得電腦上的所有服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-186">By default, this cmdlet gets all of the services on the computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="478a3-187">-RequiredServices</span><span class="sxs-lookup"><span data-stu-id="478a3-187">-RequiredServices</span></span>

<span data-ttu-id="478a3-188">指出此 Cmdlet 只會取得此服務所需的服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-188">Indicates that this cmdlet gets only the services that this service requires.</span></span>

<span data-ttu-id="478a3-189">此參數會取得服務之 **ServicesDependedOn** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="478a3-189">This parameter gets the value of the **ServicesDependedOn** property of the service.</span></span>
<span data-ttu-id="478a3-190">根據預設，此 Cmdlet 會取得所有服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-190">By default, this cmdlet gets all services.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="478a3-191">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="478a3-191">CommonParameters</span></span>

<span data-ttu-id="478a3-192">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="478a3-192">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="478a3-193">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="478a3-193">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="478a3-194">輸入</span><span class="sxs-lookup"><span data-stu-id="478a3-194">INPUTS</span></span>

### <span data-ttu-id="478a3-195">System.ServiceProcess.ServiceController、System.String</span><span class="sxs-lookup"><span data-stu-id="478a3-195">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="478a3-196">您可以使用管線將服務物件或服務名稱傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="478a3-196">You can pipe a service object or a service name to this cmdlet.</span></span>

## <span data-ttu-id="478a3-197">輸出</span><span class="sxs-lookup"><span data-stu-id="478a3-197">OUTPUTS</span></span>

### <span data-ttu-id="478a3-198">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="478a3-198">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="478a3-199">此 Cmdlet 會傳回代表電腦上服務的物件。</span><span class="sxs-lookup"><span data-stu-id="478a3-199">This cmdlet returns objects that represent the services on the computer.</span></span>

## <span data-ttu-id="478a3-200">注意</span><span class="sxs-lookup"><span data-stu-id="478a3-200">NOTES</span></span>

<span data-ttu-id="478a3-201">您也可以使用內建的別名 "gsv" 來參考 **Get Service** 。</span><span class="sxs-lookup"><span data-stu-id="478a3-201">You can also refer to **Get-Service** by its built-in alias, "gsv".</span></span> <span data-ttu-id="478a3-202">如需詳細資訊，請參閱 about_Aliases。</span><span class="sxs-lookup"><span data-stu-id="478a3-202">For more information, see about_Aliases.</span></span>

<span data-ttu-id="478a3-203">只有當目前的使用者具有查看服務的許可權時，此 Cmdlet 才會顯示服務。</span><span class="sxs-lookup"><span data-stu-id="478a3-203">This cmdlet can display services only when the current user has permission to see them.</span></span>
<span data-ttu-id="478a3-204">如果此 Cmdlet 未顯示服務，您可能沒有查看服務的許可權。</span><span class="sxs-lookup"><span data-stu-id="478a3-204">If this cmdlet does not display services, you might not have permission to see them.</span></span>

<span data-ttu-id="478a3-205">若要尋找您系統上每個服務的服務名稱和顯示名稱，請輸入 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="478a3-205">To find the service name and display name of each service on your system, type `Get-Service`.</span></span>
<span data-ttu-id="478a3-206">服務名稱會出現在 Name 欄位中，而顯示名稱會出現在 DisplayName 欄位中。</span><span class="sxs-lookup"><span data-stu-id="478a3-206">The service names appear in the Name column, and the display names appear in the DisplayName column.</span></span>

<span data-ttu-id="478a3-207">當您依狀態值以遞增順序進行排序時，"Stopped" 服務會顯示在 "Running" 服務之前。</span><span class="sxs-lookup"><span data-stu-id="478a3-207">When you sort in ascending order by status value, "Stopped" services appear before "Running" services.</span></span>
<span data-ttu-id="478a3-208">服務的 Status 屬性是一個列舉值，其中狀態的名稱會呈現為整數值。</span><span class="sxs-lookup"><span data-stu-id="478a3-208">The Status property of a service is an enumerated value in which the names of the statuses represent integer values.</span></span>
<span data-ttu-id="478a3-209">排序是根據整數值，而不是根據名稱。</span><span class="sxs-lookup"><span data-stu-id="478a3-209">The sort is based on the integer value, not the name.</span></span>
<span data-ttu-id="478a3-210">"Running" 會出現在 "Stopped" 之前，因為 "Stopped" 的值為 "1"，而 "Running" 的值為 "4"。</span><span class="sxs-lookup"><span data-stu-id="478a3-210">"Running" appears before "Stopped" because "Stopped" has a value of "1", and "Running" has a value of "4".</span></span>

## <span data-ttu-id="478a3-211">相關連結</span><span class="sxs-lookup"><span data-stu-id="478a3-211">RELATED LINKS</span></span>

[<span data-ttu-id="478a3-212">New-Service</span><span class="sxs-lookup"><span data-stu-id="478a3-212">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="478a3-213">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="478a3-213">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="478a3-214">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="478a3-214">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="478a3-215">Set-Service</span><span class="sxs-lookup"><span data-stu-id="478a3-215">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="478a3-216">Start-Service</span><span class="sxs-lookup"><span data-stu-id="478a3-216">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="478a3-217">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="478a3-217">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="478a3-218">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="478a3-218">Suspend-Service</span></span>](Suspend-Service.md)
