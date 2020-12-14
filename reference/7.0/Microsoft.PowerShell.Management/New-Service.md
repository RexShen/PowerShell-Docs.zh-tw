---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: 7ba9bf66295bcbc2d8f7b7f94007b3fb673882fb
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890969"
---
# <span data-ttu-id="078ba-102">New-Service</span><span class="sxs-lookup"><span data-stu-id="078ba-102">New-Service</span></span>

## <span data-ttu-id="078ba-103">概要</span><span class="sxs-lookup"><span data-stu-id="078ba-103">SYNOPSIS</span></span>
<span data-ttu-id="078ba-104">建立新的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="078ba-104">Creates a new Windows service.</span></span>

## <span data-ttu-id="078ba-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="078ba-105">SYNTAX</span></span>

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-SecurityDescriptorSddl <String>] [-StartupType <ServiceStartupType>] [-Credential <PSCredential>]
 [-DependsOn <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="078ba-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="078ba-106">DESCRIPTION</span></span>

<span data-ttu-id="078ba-107">此 `New-Service` Cmdlet 會在登錄和服務資料庫中建立 Windows 服務的新專案。</span><span class="sxs-lookup"><span data-stu-id="078ba-107">The `New-Service` cmdlet creates a new entry for a Windows service in the registry and in the service database.</span></span> <span data-ttu-id="078ba-108">新的服務需要在服務期間執行的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="078ba-108">A new service requires an executable file that runs during the service.</span></span>

<span data-ttu-id="078ba-109">此 Cmdlet 的參數可讓您設定服務的顯示名稱、描述、啟動類型與相依性。</span><span class="sxs-lookup"><span data-stu-id="078ba-109">The parameters of this cmdlet let you set the display name, description, startup type, and dependencies of the service.</span></span>

## <span data-ttu-id="078ba-110">範例</span><span class="sxs-lookup"><span data-stu-id="078ba-110">EXAMPLES</span></span>

### <span data-ttu-id="078ba-111">範例1：建立服務</span><span class="sxs-lookup"><span data-stu-id="078ba-111">Example 1: Create a service</span></span>

```powershell
New-Service -Name "TestService" -BinaryPathName '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
```

<span data-ttu-id="078ba-112">此命令會建立名為 TestService 的服務。</span><span class="sxs-lookup"><span data-stu-id="078ba-112">This command creates a service named TestService.</span></span>

### <span data-ttu-id="078ba-113">範例2：建立包含描述、啟動類型和顯示名稱的服務</span><span class="sxs-lookup"><span data-stu-id="078ba-113">Example 2: Create a service that includes description, startup type, and display name</span></span>

```powershell
$params = @{
  Name = "TestService"
  BinaryPathName = '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
  DependsOn = "NetLogon"
  DisplayName = "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
}
New-Service @params
```

<span data-ttu-id="078ba-114">此命令會建立名為 TestService 的服務。</span><span class="sxs-lookup"><span data-stu-id="078ba-114">This command creates a service named TestService.</span></span> <span data-ttu-id="078ba-115">它使用的參數 `New-Service` 來指定新服務的描述、啟動類型和顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="078ba-115">It uses the parameters of `New-Service` to specify a description, startup type, and display name for the new service.</span></span>

### <span data-ttu-id="078ba-116">範例3：查看新的服務</span><span class="sxs-lookup"><span data-stu-id="078ba-116">Example 3: View the new service</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -Filter "Name='testservice'"
```

```Output
ExitCode  : 0
Name      : testservice
ProcessId : 0
StartMode : Auto
State     : Stopped
Status    : OK
```

<span data-ttu-id="078ba-117">此命令會使用 `Get-CimInstance` 來取得新服務的 **Win32_Service** 物件。</span><span class="sxs-lookup"><span data-stu-id="078ba-117">This command uses `Get-CimInstance` to get the **Win32_Service** object for the new service.</span></span> <span data-ttu-id="078ba-118">此物件包含啟動模式和服務描述。</span><span class="sxs-lookup"><span data-stu-id="078ba-118">This object includes the start mode and the service description.</span></span>

### <span data-ttu-id="078ba-119">範例4：在建立時設定服務的 SecurityDescriptor。</span><span class="sxs-lookup"><span data-stu-id="078ba-119">Example 4: Set the SecurityDescriptor of a service when creating.</span></span>

<span data-ttu-id="078ba-120">此範例會新增要建立之服務的 **SecurityDescriptor** 。</span><span class="sxs-lookup"><span data-stu-id="078ba-120">This example adds the **SecurityDescriptor** of the service being created.</span></span>

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
$params = @{
  BinaryPathName = '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
  DependsOn = "NetLogon"
  DisplayName "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
  SecurityDescriptorSddl = $SDDL
}
New-Service @params
```

<span data-ttu-id="078ba-121">**SecurityDescriptor** 會儲存在變數中 `$SDDLToSet` 。</span><span class="sxs-lookup"><span data-stu-id="078ba-121">The **SecurityDescriptor** is stored in the `$SDDLToSet` variable.</span></span> <span data-ttu-id="078ba-122">**SecurityDescriptorSddl** 參數會使用 `$SDDL` 來設定新服務的 **SecurityDescriptor** 。</span><span class="sxs-lookup"><span data-stu-id="078ba-122">The **SecurityDescriptorSddl** parameter uses `$SDDL` to set the **SecurityDescriptor** of the new service.</span></span>

## <span data-ttu-id="078ba-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="078ba-123">PARAMETERS</span></span>

### <span data-ttu-id="078ba-124">-BinaryPathName</span><span class="sxs-lookup"><span data-stu-id="078ba-124">-BinaryPathName</span></span>

<span data-ttu-id="078ba-125">指定服務的可執行檔路徑。</span><span class="sxs-lookup"><span data-stu-id="078ba-125">Specifies the path of the executable file for the service.</span></span> <span data-ttu-id="078ba-126">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="078ba-126">This parameter is required.</span></span>

<span data-ttu-id="078ba-127">服務二進位檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="078ba-127">The fully qualified path to the service binary file.</span></span> <span data-ttu-id="078ba-128">如果路徑包含空格，則必須以引號括住，才能正確地解讀。</span><span class="sxs-lookup"><span data-stu-id="078ba-128">If the path contains a space, it must be quoted so that it is correctly interpreted.</span></span> <span data-ttu-id="078ba-129">例如， `d:\my share\myservice.exe` 應該指定為 `'"d:\my share\myservice.exe"'` 。</span><span class="sxs-lookup"><span data-stu-id="078ba-129">For example, `d:\my share\myservice.exe` should be specified as `'"d:\my share\myservice.exe"'`.</span></span>

<span data-ttu-id="078ba-130">路徑也可以包含自動啟動服務的引數。</span><span class="sxs-lookup"><span data-stu-id="078ba-130">The path can also include arguments for an auto-start service.</span></span> <span data-ttu-id="078ba-131">例如 `'"d:\myshare\myservice.exe arg1 arg2"'`。</span><span class="sxs-lookup"><span data-stu-id="078ba-131">For example, `'"d:\myshare\myservice.exe arg1 arg2"'`.</span></span> <span data-ttu-id="078ba-132">這些引數會傳遞至服務進入點。</span><span class="sxs-lookup"><span data-stu-id="078ba-132">These arguments are passed to the service entry point.</span></span>

<span data-ttu-id="078ba-133">如需詳細資訊，請參閱 [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) API 的 **lpBinaryPathName** 參數。</span><span class="sxs-lookup"><span data-stu-id="078ba-133">For more information, see the **lpBinaryPathName** parameter of [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) API.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="078ba-134">-Credential</span><span class="sxs-lookup"><span data-stu-id="078ba-134">-Credential</span></span>

<span data-ttu-id="078ba-135">將服務所使用的帳戶指定為 [服務登入帳戶](/windows/desktop/ad/about-service-logon-accounts)。</span><span class="sxs-lookup"><span data-stu-id="078ba-135">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="078ba-136">輸入使用者名稱（例如 **User01** 或 **Domain01\User01**），或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="078ba-136">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="078ba-137">如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="078ba-137">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="078ba-138">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="078ba-138">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="078ba-139">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="078ba-139">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="078ba-140">-DependsOn</span><span class="sxs-lookup"><span data-stu-id="078ba-140">-DependsOn</span></span>

<span data-ttu-id="078ba-141">指定新服務所依存之其他服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="078ba-141">Specifies the names of other services upon which the new service depends.</span></span> <span data-ttu-id="078ba-142">若要輸入多個服務名稱，請使用逗號來分隔名稱。</span><span class="sxs-lookup"><span data-stu-id="078ba-142">To enter multiple service names, use a comma to separate the names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="078ba-143">-Description</span><span class="sxs-lookup"><span data-stu-id="078ba-143">-Description</span></span>

<span data-ttu-id="078ba-144">指定服務的描述。</span><span class="sxs-lookup"><span data-stu-id="078ba-144">Specifies a description of the service.</span></span>

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

### <span data-ttu-id="078ba-145">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="078ba-145">-DisplayName</span></span>

<span data-ttu-id="078ba-146">指定服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="078ba-146">Specifies a display name for the service.</span></span>

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

### <span data-ttu-id="078ba-147">-Name</span><span class="sxs-lookup"><span data-stu-id="078ba-147">-Name</span></span>

<span data-ttu-id="078ba-148">指定服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="078ba-148">Specifies the name of the service.</span></span> <span data-ttu-id="078ba-149">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="078ba-149">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="078ba-150">-StartupType</span><span class="sxs-lookup"><span data-stu-id="078ba-150">-StartupType</span></span>

<span data-ttu-id="078ba-151">設定服務的啟動類型。</span><span class="sxs-lookup"><span data-stu-id="078ba-151">Sets the startup type of the service.</span></span> <span data-ttu-id="078ba-152">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="078ba-152">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="078ba-153">**自動** -服務會在系統啟動時啟動或由作業系統啟動。</span><span class="sxs-lookup"><span data-stu-id="078ba-153">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="078ba-154">如果自動啟動的服務依賴手動啟動的服務，以手動方式啟動的服務也會在系統啟動時自動啟動。</span><span class="sxs-lookup"><span data-stu-id="078ba-154">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="078ba-155">**AutomaticDelayedStart** -在系統開機之後不久就會開始。</span><span class="sxs-lookup"><span data-stu-id="078ba-155">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="078ba-156">**停用** -服務已停用，且無法由使用者或應用程式啟動。</span><span class="sxs-lookup"><span data-stu-id="078ba-156">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="078ba-157">**InvalidValue** -不支援此值。</span><span class="sxs-lookup"><span data-stu-id="078ba-157">**InvalidValue** - This value is not supported.</span></span> <span data-ttu-id="078ba-158">使用此值會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="078ba-158">Using this value results in an error.</span></span>
- <span data-ttu-id="078ba-159">**手動** -此服務只會由使用者以手動方式啟動，使用服務控制管理員或由應用程式啟動。</span><span class="sxs-lookup"><span data-stu-id="078ba-159">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

 <span data-ttu-id="078ba-160">預設值為 [ **自動**]。</span><span class="sxs-lookup"><span data-stu-id="078ba-160">The default value is **Automatic**.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ServiceStartupType
Parameter Sets: (All)
Aliases:
Accepted values: Automatic, Manual, Disabled, AutomaticDelayedStart, InvalidValue

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="078ba-161">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="078ba-161">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="078ba-162">以 **Sddl** 格式指定服務的 **SecurityDescriptor** 。</span><span class="sxs-lookup"><span data-stu-id="078ba-162">Specifies the **SecurityDescriptor** for the service in **Sddl** format.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sd

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="078ba-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="078ba-163">-Confirm</span></span>

<span data-ttu-id="078ba-164">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="078ba-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="078ba-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="078ba-165">-WhatIf</span></span>

<span data-ttu-id="078ba-166">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="078ba-166">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="078ba-167">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="078ba-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="078ba-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="078ba-168">CommonParameters</span></span>

<span data-ttu-id="078ba-169">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="078ba-169">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="078ba-170">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="078ba-170">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="078ba-171">輸入</span><span class="sxs-lookup"><span data-stu-id="078ba-171">INPUTS</span></span>

### <span data-ttu-id="078ba-172">無</span><span class="sxs-lookup"><span data-stu-id="078ba-172">None</span></span>

<span data-ttu-id="078ba-173">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="078ba-173">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="078ba-174">輸出</span><span class="sxs-lookup"><span data-stu-id="078ba-174">OUTPUTS</span></span>

### <span data-ttu-id="078ba-175">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="078ba-175">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="078ba-176">此 Cmdlet 會傳回代表新服務的物件。</span><span class="sxs-lookup"><span data-stu-id="078ba-176">This cmdlet returns an object that represents the new service.</span></span>

## <span data-ttu-id="078ba-177">注意</span><span class="sxs-lookup"><span data-stu-id="078ba-177">NOTES</span></span>

<span data-ttu-id="078ba-178">此 Cmdlet 僅適用于 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="078ba-178">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="078ba-179">若要執行此 Cmdlet，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="078ba-179">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="078ba-180">相關連結</span><span class="sxs-lookup"><span data-stu-id="078ba-180">RELATED LINKS</span></span>

[<span data-ttu-id="078ba-181">Get-Service</span><span class="sxs-lookup"><span data-stu-id="078ba-181">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="078ba-182">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="078ba-182">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="078ba-183">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="078ba-183">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="078ba-184">Set-Service</span><span class="sxs-lookup"><span data-stu-id="078ba-184">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="078ba-185">Start-Service</span><span class="sxs-lookup"><span data-stu-id="078ba-185">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="078ba-186">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="078ba-186">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="078ba-187">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="078ba-187">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="078ba-188">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="078ba-188">Remove-Service</span></span>](Remove-Service.md)
