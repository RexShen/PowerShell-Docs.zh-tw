---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: c34c581b9af74f3199437b26971b902f6b39620f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202083"
---
# <span data-ttu-id="dcc81-103">New-Service</span><span class="sxs-lookup"><span data-stu-id="dcc81-103">New-Service</span></span>

## <span data-ttu-id="dcc81-104">概要</span><span class="sxs-lookup"><span data-stu-id="dcc81-104">SYNOPSIS</span></span>
<span data-ttu-id="dcc81-105">建立新的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="dcc81-105">Creates a new Windows service.</span></span>

## <span data-ttu-id="dcc81-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dcc81-106">SYNTAX</span></span>

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-SecurityDescriptorSddl <String>] [-StartupType <ServiceStartupType>] [-Credential <PSCredential>]
 [-DependsOn <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="dcc81-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dcc81-107">DESCRIPTION</span></span>

<span data-ttu-id="dcc81-108">此 `New-Service` Cmdlet 會在登錄和服務資料庫中建立 Windows 服務的新專案。</span><span class="sxs-lookup"><span data-stu-id="dcc81-108">The `New-Service` cmdlet creates a new entry for a Windows service in the registry and in the service database.</span></span> <span data-ttu-id="dcc81-109">新的服務需要在服務期間執行的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="dcc81-109">A new service requires an executable file that runs during the service.</span></span>

<span data-ttu-id="dcc81-110">此 Cmdlet 的參數可讓您設定服務的顯示名稱、描述、啟動類型與相依性。</span><span class="sxs-lookup"><span data-stu-id="dcc81-110">The parameters of this cmdlet let you set the display name, description, startup type, and dependencies of the service.</span></span>

## <span data-ttu-id="dcc81-111">範例</span><span class="sxs-lookup"><span data-stu-id="dcc81-111">EXAMPLES</span></span>

### <span data-ttu-id="dcc81-112">範例1：建立服務</span><span class="sxs-lookup"><span data-stu-id="dcc81-112">Example 1: Create a service</span></span>

```powershell
New-Service -Name "TestService" -BinaryPathName "C:\WINDOWS\System32\svchost.exe -k netsvcs"
```

<span data-ttu-id="dcc81-113">此命令會建立名為 TestService 的服務。</span><span class="sxs-lookup"><span data-stu-id="dcc81-113">This command creates a service named TestService.</span></span>

### <span data-ttu-id="dcc81-114">範例2：建立包含描述、啟動類型和顯示名稱的服務</span><span class="sxs-lookup"><span data-stu-id="dcc81-114">Example 2: Create a service that includes description, startup type, and display name</span></span>

```powershell
$params = @{
  Name = "TestService"
  BinaryPathName = "C:\WINDOWS\System32\svchost.exe -k netsvcs"
  DependsOn = "NetLogon"
  DisplayName = "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
}
New-Service @params
```

<span data-ttu-id="dcc81-115">此命令會建立名為 TestService 的服務。</span><span class="sxs-lookup"><span data-stu-id="dcc81-115">This command creates a service named TestService.</span></span> <span data-ttu-id="dcc81-116">它使用的參數 `New-Service` 來指定新服務的描述、啟動類型和顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="dcc81-116">It uses the parameters of `New-Service` to specify a description, startup type, and display name for the new service.</span></span>

### <span data-ttu-id="dcc81-117">範例3：查看新的服務</span><span class="sxs-lookup"><span data-stu-id="dcc81-117">Example 3: View the new service</span></span>

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

<span data-ttu-id="dcc81-118">此命令會使用 `Get-CimInstance` 來取得新服務的 **Win32_Service** 物件。</span><span class="sxs-lookup"><span data-stu-id="dcc81-118">This command uses `Get-CimInstance` to get the **Win32_Service** object for the new service.</span></span> <span data-ttu-id="dcc81-119">此物件包含啟動模式和服務描述。</span><span class="sxs-lookup"><span data-stu-id="dcc81-119">This object includes the start mode and the service description.</span></span>

### <span data-ttu-id="dcc81-120">範例4：在建立時設定服務的 SecurityDescriptor。</span><span class="sxs-lookup"><span data-stu-id="dcc81-120">Example 4: Set the SecurityDescriptor of a service when creating.</span></span>

<span data-ttu-id="dcc81-121">此範例會新增要建立之服務的 **SecurityDescriptor** 。</span><span class="sxs-lookup"><span data-stu-id="dcc81-121">This example adds the **SecurityDescriptor** of the service being created.</span></span>

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
$params = @{
  BinaryPathName = "C:\WINDOWS\System32\svchost.exe -k netsvcs"
  DependsOn = "NetLogon"
  DisplayName "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
  SecurityDescriptorSddl = $SDDL
}
New-Service @params
```

<span data-ttu-id="dcc81-122">**SecurityDescriptor** 會儲存在變數中 `$SDDLToSet` 。</span><span class="sxs-lookup"><span data-stu-id="dcc81-122">The **SecurityDescriptor** is stored in the `$SDDLToSet` variable.</span></span> <span data-ttu-id="dcc81-123">**SecurityDescriptorSddl** 參數會使用 `$SDDL` 來設定新服務的 **SecurityDescriptor** 。</span><span class="sxs-lookup"><span data-stu-id="dcc81-123">The **SecurityDescriptorSddl** parameter uses `$SDDL` to set the **SecurityDescriptor** of the new service.</span></span>

## <span data-ttu-id="dcc81-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dcc81-124">PARAMETERS</span></span>

### <span data-ttu-id="dcc81-125">-BinaryPathName</span><span class="sxs-lookup"><span data-stu-id="dcc81-125">-BinaryPathName</span></span>

<span data-ttu-id="dcc81-126">指定服務的可執行檔路徑。</span><span class="sxs-lookup"><span data-stu-id="dcc81-126">Specifies the path of the executable file for the service.</span></span> <span data-ttu-id="dcc81-127">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="dcc81-127">This parameter is required.</span></span>

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

### <span data-ttu-id="dcc81-128">-Credential</span><span class="sxs-lookup"><span data-stu-id="dcc81-128">-Credential</span></span>

<span data-ttu-id="dcc81-129">將服務所使用的帳戶指定為 [服務登入帳戶](/windows/desktop/ad/about-service-logon-accounts)。</span><span class="sxs-lookup"><span data-stu-id="dcc81-129">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="dcc81-130">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="dcc81-130">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="dcc81-131">如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="dcc81-131">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="dcc81-132">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="dcc81-132">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="dcc81-133">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="dcc81-133">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="dcc81-134">-DependsOn</span><span class="sxs-lookup"><span data-stu-id="dcc81-134">-DependsOn</span></span>

<span data-ttu-id="dcc81-135">指定新服務所依存之其他服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="dcc81-135">Specifies the names of other services upon which the new service depends.</span></span> <span data-ttu-id="dcc81-136">若要輸入多個服務名稱，請使用逗號來分隔名稱。</span><span class="sxs-lookup"><span data-stu-id="dcc81-136">To enter multiple service names, use a comma to separate the names.</span></span>

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

### <span data-ttu-id="dcc81-137">-Description</span><span class="sxs-lookup"><span data-stu-id="dcc81-137">-Description</span></span>

<span data-ttu-id="dcc81-138">指定服務的描述。</span><span class="sxs-lookup"><span data-stu-id="dcc81-138">Specifies a description of the service.</span></span>

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

### <span data-ttu-id="dcc81-139">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="dcc81-139">-DisplayName</span></span>

<span data-ttu-id="dcc81-140">指定服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="dcc81-140">Specifies a display name for the service.</span></span>

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

### <span data-ttu-id="dcc81-141">-Name</span><span class="sxs-lookup"><span data-stu-id="dcc81-141">-Name</span></span>

<span data-ttu-id="dcc81-142">指定服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="dcc81-142">Specifies the name of the service.</span></span>
<span data-ttu-id="dcc81-143">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="dcc81-143">This parameter is required.</span></span>

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

### <span data-ttu-id="dcc81-144">-StartupType</span><span class="sxs-lookup"><span data-stu-id="dcc81-144">-StartupType</span></span>

<span data-ttu-id="dcc81-145">設定服務的啟動類型。</span><span class="sxs-lookup"><span data-stu-id="dcc81-145">Sets the startup type of the service.</span></span> <span data-ttu-id="dcc81-146">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="dcc81-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="dcc81-147">**自動** -服務會在系統啟動時啟動或由作業系統啟動。</span><span class="sxs-lookup"><span data-stu-id="dcc81-147">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="dcc81-148">如果自動啟動的服務依賴手動啟動的服務，以手動方式啟動的服務也會在系統啟動時自動啟動。</span><span class="sxs-lookup"><span data-stu-id="dcc81-148">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="dcc81-149">**AutomaticDelayedStart** -在系統開機之後不久就會開始。</span><span class="sxs-lookup"><span data-stu-id="dcc81-149">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="dcc81-150">**停用** -服務已停用，且無法由使用者或應用程式啟動。</span><span class="sxs-lookup"><span data-stu-id="dcc81-150">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="dcc81-151">**InvalidValue** -不支援此值。</span><span class="sxs-lookup"><span data-stu-id="dcc81-151">**InvalidValue** - This value is not supported.</span></span> <span data-ttu-id="dcc81-152">使用此值會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="dcc81-152">Using this value results in an error.</span></span>
- <span data-ttu-id="dcc81-153">**手動** -此服務只會由使用者以手動方式啟動，使用服務控制管理員或由應用程式啟動。</span><span class="sxs-lookup"><span data-stu-id="dcc81-153">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

 <span data-ttu-id="dcc81-154">預設值為 [ **自動** ]。</span><span class="sxs-lookup"><span data-stu-id="dcc81-154">The default value is **Automatic** .</span></span>

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

### <span data-ttu-id="dcc81-155">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="dcc81-155">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="dcc81-156">以 **Sddl** 格式指定服務的 **SecurityDescriptor** 。</span><span class="sxs-lookup"><span data-stu-id="dcc81-156">Specifies the **SecurityDescriptor** for the service in **Sddl** format.</span></span>

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

### <span data-ttu-id="dcc81-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="dcc81-157">-Confirm</span></span>

<span data-ttu-id="dcc81-158">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="dcc81-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="dcc81-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="dcc81-159">-WhatIf</span></span>

<span data-ttu-id="dcc81-160">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="dcc81-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="dcc81-161">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="dcc81-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="dcc81-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dcc81-162">CommonParameters</span></span>

<span data-ttu-id="dcc81-163">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="dcc81-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dcc81-164">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="dcc81-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dcc81-165">輸入</span><span class="sxs-lookup"><span data-stu-id="dcc81-165">INPUTS</span></span>

### <span data-ttu-id="dcc81-166">無</span><span class="sxs-lookup"><span data-stu-id="dcc81-166">None</span></span>

<span data-ttu-id="dcc81-167">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dcc81-167">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="dcc81-168">輸出</span><span class="sxs-lookup"><span data-stu-id="dcc81-168">OUTPUTS</span></span>

### <span data-ttu-id="dcc81-169">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="dcc81-169">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="dcc81-170">此 Cmdlet 會傳回代表新服務的物件。</span><span class="sxs-lookup"><span data-stu-id="dcc81-170">This cmdlet returns an object that represents the new service.</span></span>

## <span data-ttu-id="dcc81-171">注意</span><span class="sxs-lookup"><span data-stu-id="dcc81-171">NOTES</span></span>

<span data-ttu-id="dcc81-172">若要在 Windows Vista 和更新版本的 Windows 作業系統上執行此 Cmdlet，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="dcc81-172">To run this cmdlet on Windows Vista and later versions of the Windows operating system, start PowerShell by using the Run as administrator option.</span></span>

## <span data-ttu-id="dcc81-173">相關連結</span><span class="sxs-lookup"><span data-stu-id="dcc81-173">RELATED LINKS</span></span>

[<span data-ttu-id="dcc81-174">Get-Service</span><span class="sxs-lookup"><span data-stu-id="dcc81-174">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="dcc81-175">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="dcc81-175">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="dcc81-176">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="dcc81-176">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="dcc81-177">Set-Service</span><span class="sxs-lookup"><span data-stu-id="dcc81-177">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="dcc81-178">Start-Service</span><span class="sxs-lookup"><span data-stu-id="dcc81-178">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="dcc81-179">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="dcc81-179">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="dcc81-180">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="dcc81-180">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="dcc81-181">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="dcc81-181">Remove-Service</span></span>](Remove-Service.md)

