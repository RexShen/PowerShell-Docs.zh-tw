---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: 758b0a8ef9a5f65f0e7cfa7f3633086cf9f0445d
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891763"
---
# <span data-ttu-id="a65b4-103">New-Service</span><span class="sxs-lookup"><span data-stu-id="a65b4-103">New-Service</span></span>

## <span data-ttu-id="a65b4-104">概要</span><span class="sxs-lookup"><span data-stu-id="a65b4-104">SYNOPSIS</span></span>
<span data-ttu-id="a65b4-105">建立新的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="a65b4-105">Creates a new Windows service.</span></span>

## <span data-ttu-id="a65b4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a65b4-106">SYNTAX</span></span>

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Credential <PSCredential>] [-DependsOn <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a65b4-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a65b4-107">DESCRIPTION</span></span>

<span data-ttu-id="a65b4-108">此 `New-Service` Cmdlet 會在登錄和服務資料庫中建立 Windows 服務的新專案。</span><span class="sxs-lookup"><span data-stu-id="a65b4-108">The `New-Service` cmdlet creates a new entry for a Windows service in the registry and in the service database.</span></span> <span data-ttu-id="a65b4-109">新的服務需要在服務期間執行的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="a65b4-109">A new service requires an executable file that runs during the service.</span></span>

<span data-ttu-id="a65b4-110">此 Cmdlet 的參數可讓您設定服務的顯示名稱、描述、啟動類型與相依性。</span><span class="sxs-lookup"><span data-stu-id="a65b4-110">The parameters of this cmdlet let you set the display name, description, startup type, and dependencies of the service.</span></span>

## <span data-ttu-id="a65b4-111">範例</span><span class="sxs-lookup"><span data-stu-id="a65b4-111">EXAMPLES</span></span>

### <span data-ttu-id="a65b4-112">範例1：建立服務</span><span class="sxs-lookup"><span data-stu-id="a65b4-112">Example 1: Create a service</span></span>

```powershell
New-Service -Name "TestService" -BinaryPathName '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
```

<span data-ttu-id="a65b4-113">此命令會建立名為 TestService 的服務。</span><span class="sxs-lookup"><span data-stu-id="a65b4-113">This command creates a service named TestService.</span></span>

### <span data-ttu-id="a65b4-114">範例2：建立包含描述、啟動類型和顯示名稱的服務</span><span class="sxs-lookup"><span data-stu-id="a65b4-114">Example 2: Create a service that includes description, startup type, and display name</span></span>

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

<span data-ttu-id="a65b4-115">此命令會建立名為 TestService 的服務。</span><span class="sxs-lookup"><span data-stu-id="a65b4-115">This command creates a service named TestService.</span></span> <span data-ttu-id="a65b4-116">它使用的參數 `New-Service` 來指定新服務的描述、啟動類型和顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="a65b4-116">It uses the parameters of `New-Service` to specify a description, startup type, and display name for the new service.</span></span>

### <span data-ttu-id="a65b4-117">範例3：查看新的服務</span><span class="sxs-lookup"><span data-stu-id="a65b4-117">Example 3: View the new service</span></span>

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

<span data-ttu-id="a65b4-118">此命令會使用 `Get-CimInstance` 來取得新服務的 **Win32_Service** 物件。</span><span class="sxs-lookup"><span data-stu-id="a65b4-118">This command uses `Get-CimInstance` to get the **Win32_Service** object for the new service.</span></span> <span data-ttu-id="a65b4-119">此物件包含啟動模式和服務描述。</span><span class="sxs-lookup"><span data-stu-id="a65b4-119">This object includes the start mode and the service description.</span></span>

### <span data-ttu-id="a65b4-120">範例4：刪除服務</span><span class="sxs-lookup"><span data-stu-id="a65b4-120">Example 4: Delete a service</span></span>

```powershell
sc.exe delete TestService
# - or -
(Get-CimInstance -Class Win32_Service -Filter "name='TestService'").delete()
```

<span data-ttu-id="a65b4-121">此範例顯示兩種刪除 TestService 服務的方法。</span><span class="sxs-lookup"><span data-stu-id="a65b4-121">This example shows two ways to delete the TestService service.</span></span> <span data-ttu-id="a65b4-122">第一個命令使用的 [刪除] 選項 `Sc.exe` 。</span><span class="sxs-lookup"><span data-stu-id="a65b4-122">The first command uses the delete option of `Sc.exe`.</span></span> <span data-ttu-id="a65b4-123">第二個命令會使用傳回之 **Win32_Service** 物件的 **Delete** 方法 `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="a65b4-123">The second command uses the **Delete** method of the **Win32_Service** objects that `Get-CimInstance` returns.</span></span>

## <span data-ttu-id="a65b4-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a65b4-124">PARAMETERS</span></span>

### <span data-ttu-id="a65b4-125">-BinaryPathName</span><span class="sxs-lookup"><span data-stu-id="a65b4-125">-BinaryPathName</span></span>

<span data-ttu-id="a65b4-126">指定服務的可執行檔路徑。</span><span class="sxs-lookup"><span data-stu-id="a65b4-126">Specifies the path of the executable file for the service.</span></span> <span data-ttu-id="a65b4-127">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="a65b4-127">This parameter is required.</span></span>

<span data-ttu-id="a65b4-128">服務二進位檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="a65b4-128">The fully qualified path to the service binary file.</span></span> <span data-ttu-id="a65b4-129">如果路徑包含空格，則必須以引號括住，才能正確地解讀。</span><span class="sxs-lookup"><span data-stu-id="a65b4-129">If the path contains a space, it must be quoted so that it is correctly interpreted.</span></span> <span data-ttu-id="a65b4-130">例如， `d:\my share\myservice.exe` 應該指定為 `'"d:\my share\myservice.exe"'` 。</span><span class="sxs-lookup"><span data-stu-id="a65b4-130">For example, `d:\my share\myservice.exe` should be specified as `'"d:\my share\myservice.exe"'`.</span></span>

<span data-ttu-id="a65b4-131">路徑也可以包含自動啟動服務的引數。</span><span class="sxs-lookup"><span data-stu-id="a65b4-131">The path can also include arguments for an auto-start service.</span></span> <span data-ttu-id="a65b4-132">例如 `'"d:\myshare\myservice.exe arg1 arg2"'`。</span><span class="sxs-lookup"><span data-stu-id="a65b4-132">For example, `'"d:\myshare\myservice.exe arg1 arg2"'`.</span></span> <span data-ttu-id="a65b4-133">這些引數會傳遞至服務進入點。</span><span class="sxs-lookup"><span data-stu-id="a65b4-133">These arguments are passed to the service entry point.</span></span>

<span data-ttu-id="a65b4-134">如需詳細資訊，請參閱 [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) API 的 **lpBinaryPathName** 參數。</span><span class="sxs-lookup"><span data-stu-id="a65b4-134">For more information, see the **lpBinaryPathName** parameter of [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) API.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a65b4-135">-Credential</span><span class="sxs-lookup"><span data-stu-id="a65b4-135">-Credential</span></span>

<span data-ttu-id="a65b4-136">將服務所使用的帳戶指定為 [服務登入帳戶](/windows/desktop/ad/about-service-logon-accounts)。</span><span class="sxs-lookup"><span data-stu-id="a65b4-136">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="a65b4-137">輸入使用者名稱（例如 **User01** 或 **Domain01\User01**），或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="a65b4-137">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="a65b4-138">如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="a65b4-138">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="a65b4-139">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="a65b4-139">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="a65b4-140">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="a65b4-140">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="a65b4-141">-DependsOn</span><span class="sxs-lookup"><span data-stu-id="a65b4-141">-DependsOn</span></span>

<span data-ttu-id="a65b4-142">指定新服務所依存之其他服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="a65b4-142">Specifies the names of other services upon which the new service depends.</span></span> <span data-ttu-id="a65b4-143">若要輸入多個服務名稱，請使用逗號來分隔名稱。</span><span class="sxs-lookup"><span data-stu-id="a65b4-143">To enter multiple service names, use a comma to separate the names.</span></span>

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

### <span data-ttu-id="a65b4-144">-Description</span><span class="sxs-lookup"><span data-stu-id="a65b4-144">-Description</span></span>

<span data-ttu-id="a65b4-145">指定服務的描述。</span><span class="sxs-lookup"><span data-stu-id="a65b4-145">Specifies a description of the service.</span></span>

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

### <span data-ttu-id="a65b4-146">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="a65b4-146">-DisplayName</span></span>

<span data-ttu-id="a65b4-147">指定服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="a65b4-147">Specifies a display name for the service.</span></span>

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

### <span data-ttu-id="a65b4-148">-Name</span><span class="sxs-lookup"><span data-stu-id="a65b4-148">-Name</span></span>

<span data-ttu-id="a65b4-149">指定服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="a65b4-149">Specifies the name of the service.</span></span> <span data-ttu-id="a65b4-150">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="a65b4-150">This parameter is required.</span></span>

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

### <span data-ttu-id="a65b4-151">-StartupType</span><span class="sxs-lookup"><span data-stu-id="a65b4-151">-StartupType</span></span>

<span data-ttu-id="a65b4-152">設定服務的啟動類型。</span><span class="sxs-lookup"><span data-stu-id="a65b4-152">Sets the startup type of the service.</span></span> <span data-ttu-id="a65b4-153">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="a65b4-153">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a65b4-154">**自動** -服務會在系統啟動時啟動或由作業系統啟動。</span><span class="sxs-lookup"><span data-stu-id="a65b4-154">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="a65b4-155">如果自動啟動的服務依賴手動啟動的服務，以手動方式啟動的服務也會在系統啟動時自動啟動。</span><span class="sxs-lookup"><span data-stu-id="a65b4-155">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="a65b4-156">**停用** -服務已停用，且無法由使用者或應用程式啟動。</span><span class="sxs-lookup"><span data-stu-id="a65b4-156">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="a65b4-157">**手動** -此服務只會由使用者以手動方式啟動，使用服務控制管理員或由應用程式啟動。</span><span class="sxs-lookup"><span data-stu-id="a65b4-157">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>
- <span data-ttu-id="a65b4-158">**開機** -表示該服務是由系統載入器啟動的設備磁碟機。</span><span class="sxs-lookup"><span data-stu-id="a65b4-158">**Boot** - Indicates that the service is a device driver started by the system loader.</span></span> <span data-ttu-id="a65b4-159">這個值僅適用於裝置驅動程式。</span><span class="sxs-lookup"><span data-stu-id="a65b4-159">This value is valid only for device drivers.</span></span>
- <span data-ttu-id="a65b4-160">**系統** -表示服務是由 ' IOInitSystem ( # A1 ' 函式啟動的設備磁碟機。</span><span class="sxs-lookup"><span data-stu-id="a65b4-160">**System** - Indicates that the service is a device driver started by the 'IOInitSystem()' function.</span></span> <span data-ttu-id="a65b4-161">這個值僅適用於裝置驅動程式。</span><span class="sxs-lookup"><span data-stu-id="a65b4-161">This value is valid only for device drivers.</span></span>

 <span data-ttu-id="a65b4-162">預設值為 [ **自動**]。</span><span class="sxs-lookup"><span data-stu-id="a65b4-162">The default value is **Automatic**.</span></span>

```yaml
Type: System.ServiceProcess.ServiceStartMode
Parameter Sets: (All)
Aliases:
Accepted values: Boot, System, Automatic, Manual, Disabled

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a65b4-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a65b4-163">-Confirm</span></span>

<span data-ttu-id="a65b4-164">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="a65b4-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a65b4-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a65b4-165">-WhatIf</span></span>

<span data-ttu-id="a65b4-166">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="a65b4-166">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a65b4-167">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="a65b4-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a65b4-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a65b4-168">CommonParameters</span></span>

<span data-ttu-id="a65b4-169">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a65b4-169">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a65b4-170">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a65b4-170">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a65b4-171">輸入</span><span class="sxs-lookup"><span data-stu-id="a65b4-171">INPUTS</span></span>

### <span data-ttu-id="a65b4-172">無</span><span class="sxs-lookup"><span data-stu-id="a65b4-172">None</span></span>

<span data-ttu-id="a65b4-173">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a65b4-173">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a65b4-174">輸出</span><span class="sxs-lookup"><span data-stu-id="a65b4-174">OUTPUTS</span></span>

### <span data-ttu-id="a65b4-175">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="a65b4-175">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="a65b4-176">此 Cmdlet 會傳回代表新服務的物件。</span><span class="sxs-lookup"><span data-stu-id="a65b4-176">This cmdlet returns an object that represents the new service.</span></span>

## <span data-ttu-id="a65b4-177">注意</span><span class="sxs-lookup"><span data-stu-id="a65b4-177">NOTES</span></span>

<span data-ttu-id="a65b4-178">若要執行此 Cmdlet，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a65b4-178">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

<span data-ttu-id="a65b4-179">若要刪除服務，請使用 Sc.exe，或使用 `Get-CimInstance` Cmdlet 取得代表服務的 **Win32_Service** 物件，然後使用 **delete** 方法來刪除服務。</span><span class="sxs-lookup"><span data-stu-id="a65b4-179">To delete a service, use Sc.exe, or use the `Get-CimInstance` cmdlet to get the **Win32_Service** object that represents the service and then use the **Delete** method to delete the service.</span></span> <span data-ttu-id="a65b4-180">傳回的物件沒有 `Get-Service` delete 方法。</span><span class="sxs-lookup"><span data-stu-id="a65b4-180">The object that `Get-Service` returns does not have a delete method.</span></span>

## <span data-ttu-id="a65b4-181">相關連結</span><span class="sxs-lookup"><span data-stu-id="a65b4-181">RELATED LINKS</span></span>

[<span data-ttu-id="a65b4-182">Get-Service</span><span class="sxs-lookup"><span data-stu-id="a65b4-182">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="a65b4-183">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="a65b4-183">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="a65b4-184">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="a65b4-184">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="a65b4-185">Set-Service</span><span class="sxs-lookup"><span data-stu-id="a65b4-185">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="a65b4-186">Start-Service</span><span class="sxs-lookup"><span data-stu-id="a65b4-186">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="a65b4-187">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="a65b4-187">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="a65b4-188">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="a65b4-188">Suspend-Service</span></span>](Suspend-Service.md)
