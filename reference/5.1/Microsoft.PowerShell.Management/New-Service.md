---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: 3249ce91a63417f2790997d37e2420c6fcb374d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203588"
---
# <span data-ttu-id="203f8-103">New-Service</span><span class="sxs-lookup"><span data-stu-id="203f8-103">New-Service</span></span>

## <span data-ttu-id="203f8-104">概要</span><span class="sxs-lookup"><span data-stu-id="203f8-104">SYNOPSIS</span></span>
<span data-ttu-id="203f8-105">建立新的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="203f8-105">Creates a new Windows service.</span></span>

## <span data-ttu-id="203f8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="203f8-106">SYNTAX</span></span>

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Credential <PSCredential>] [-DependsOn <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="203f8-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="203f8-107">DESCRIPTION</span></span>

<span data-ttu-id="203f8-108">此 `New-Service` Cmdlet 會在登錄和服務資料庫中建立 Windows 服務的新專案。</span><span class="sxs-lookup"><span data-stu-id="203f8-108">The `New-Service` cmdlet creates a new entry for a Windows service in the registry and in the service database.</span></span> <span data-ttu-id="203f8-109">新的服務需要在服務期間執行的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="203f8-109">A new service requires an executable file that runs during the service.</span></span>

<span data-ttu-id="203f8-110">此 Cmdlet 的參數可讓您設定服務的顯示名稱、描述、啟動類型與相依性。</span><span class="sxs-lookup"><span data-stu-id="203f8-110">The parameters of this cmdlet let you set the display name, description, startup type, and dependencies of the service.</span></span>

## <span data-ttu-id="203f8-111">範例</span><span class="sxs-lookup"><span data-stu-id="203f8-111">EXAMPLES</span></span>

### <span data-ttu-id="203f8-112">範例1：建立服務</span><span class="sxs-lookup"><span data-stu-id="203f8-112">Example 1: Create a service</span></span>

```powershell
New-Service -Name "TestService" -BinaryPathName "C:\WINDOWS\System32\svchost.exe -k netsvcs"
```

<span data-ttu-id="203f8-113">此命令會建立名為 TestService 的服務。</span><span class="sxs-lookup"><span data-stu-id="203f8-113">This command creates a service named TestService.</span></span>

### <span data-ttu-id="203f8-114">範例2：建立包含描述、啟動類型和顯示名稱的服務</span><span class="sxs-lookup"><span data-stu-id="203f8-114">Example 2: Create a service that includes description, startup type, and display name</span></span>

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

<span data-ttu-id="203f8-115">此命令會建立名為 TestService 的服務。</span><span class="sxs-lookup"><span data-stu-id="203f8-115">This command creates a service named TestService.</span></span> <span data-ttu-id="203f8-116">它使用的參數 `New-Service` 來指定新服務的描述、啟動類型和顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="203f8-116">It uses the parameters of `New-Service` to specify a description, startup type, and display name for the new service.</span></span>

### <span data-ttu-id="203f8-117">範例3：查看新的服務</span><span class="sxs-lookup"><span data-stu-id="203f8-117">Example 3: View the new service</span></span>

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

<span data-ttu-id="203f8-118">此命令會使用 `Get-CimInstance` 來取得新服務的 **Win32_Service** 物件。</span><span class="sxs-lookup"><span data-stu-id="203f8-118">This command uses `Get-CimInstance` to get the **Win32_Service** object for the new service.</span></span> <span data-ttu-id="203f8-119">此物件包含啟動模式和服務描述。</span><span class="sxs-lookup"><span data-stu-id="203f8-119">This object includes the start mode and the service description.</span></span>

### <span data-ttu-id="203f8-120">範例4：刪除服務</span><span class="sxs-lookup"><span data-stu-id="203f8-120">Example 4: Delete a service</span></span>

```powershell
sc.exe delete TestService
# - or -
(Get-CimInstance -Class Win32_Service -Filter "name='TestService'").delete()
```

<span data-ttu-id="203f8-121">此範例顯示兩種刪除 TestService 服務的方法。</span><span class="sxs-lookup"><span data-stu-id="203f8-121">This example shows two ways to delete the TestService service.</span></span> <span data-ttu-id="203f8-122">第一個命令使用的 [刪除] 選項 `Sc.exe` 。</span><span class="sxs-lookup"><span data-stu-id="203f8-122">The first command uses the delete option of `Sc.exe`.</span></span> <span data-ttu-id="203f8-123">第二個命令會使用傳回之 **Win32_Service** 物件的 **Delete** 方法 `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="203f8-123">The second command uses the **Delete** method of the **Win32_Service** objects that `Get-CimInstance` returns.</span></span>

## <span data-ttu-id="203f8-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="203f8-124">PARAMETERS</span></span>

### <span data-ttu-id="203f8-125">-BinaryPathName</span><span class="sxs-lookup"><span data-stu-id="203f8-125">-BinaryPathName</span></span>

<span data-ttu-id="203f8-126">指定服務的可執行檔路徑。</span><span class="sxs-lookup"><span data-stu-id="203f8-126">Specifies the path of the executable file for the service.</span></span> <span data-ttu-id="203f8-127">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="203f8-127">This parameter is required.</span></span>

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

### <span data-ttu-id="203f8-128">-Credential</span><span class="sxs-lookup"><span data-stu-id="203f8-128">-Credential</span></span>

<span data-ttu-id="203f8-129">將服務所使用的帳戶指定為 [服務登入帳戶](/windows/desktop/ad/about-service-logon-accounts)。</span><span class="sxs-lookup"><span data-stu-id="203f8-129">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="203f8-130">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="203f8-130">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="203f8-131">如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="203f8-131">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="203f8-132">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="203f8-132">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="203f8-133">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="203f8-133">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="203f8-134">-DependsOn</span><span class="sxs-lookup"><span data-stu-id="203f8-134">-DependsOn</span></span>

<span data-ttu-id="203f8-135">指定新服務所依存之其他服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="203f8-135">Specifies the names of other services upon which the new service depends.</span></span> <span data-ttu-id="203f8-136">若要輸入多個服務名稱，請使用逗號來分隔名稱。</span><span class="sxs-lookup"><span data-stu-id="203f8-136">To enter multiple service names, use a comma to separate the names.</span></span>

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

### <span data-ttu-id="203f8-137">-Description</span><span class="sxs-lookup"><span data-stu-id="203f8-137">-Description</span></span>

<span data-ttu-id="203f8-138">指定服務的描述。</span><span class="sxs-lookup"><span data-stu-id="203f8-138">Specifies a description of the service.</span></span>

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

### <span data-ttu-id="203f8-139">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="203f8-139">-DisplayName</span></span>

<span data-ttu-id="203f8-140">指定服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="203f8-140">Specifies a display name for the service.</span></span>

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

### <span data-ttu-id="203f8-141">-Name</span><span class="sxs-lookup"><span data-stu-id="203f8-141">-Name</span></span>

<span data-ttu-id="203f8-142">指定服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="203f8-142">Specifies the name of the service.</span></span>
<span data-ttu-id="203f8-143">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="203f8-143">This parameter is required.</span></span>

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

### <span data-ttu-id="203f8-144">-StartupType</span><span class="sxs-lookup"><span data-stu-id="203f8-144">-StartupType</span></span>

<span data-ttu-id="203f8-145">設定服務的啟動類型。</span><span class="sxs-lookup"><span data-stu-id="203f8-145">Sets the startup type of the service.</span></span> <span data-ttu-id="203f8-146">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="203f8-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="203f8-147">**自動** -服務會在系統啟動時啟動或由作業系統啟動。</span><span class="sxs-lookup"><span data-stu-id="203f8-147">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="203f8-148">如果自動啟動的服務依賴手動啟動的服務，以手動方式啟動的服務也會在系統啟動時自動啟動。</span><span class="sxs-lookup"><span data-stu-id="203f8-148">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="203f8-149">**停用** -服務已停用，且無法由使用者或應用程式啟動。</span><span class="sxs-lookup"><span data-stu-id="203f8-149">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="203f8-150">**手動** -此服務只會由使用者以手動方式啟動，使用服務控制管理員或由應用程式啟動。</span><span class="sxs-lookup"><span data-stu-id="203f8-150">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>
- <span data-ttu-id="203f8-151">**開機** -表示該服務是由系統載入器啟動的設備磁碟機。</span><span class="sxs-lookup"><span data-stu-id="203f8-151">**Boot** - Indicates that the service is a device driver started by the system loader.</span></span> <span data-ttu-id="203f8-152">這個值僅適用於裝置驅動程式。</span><span class="sxs-lookup"><span data-stu-id="203f8-152">This value is valid only for device drivers.</span></span>
- <span data-ttu-id="203f8-153">**系統** -表示服務是由 ' IOInitSystem ( # A1 ' 函式啟動的設備磁碟機。</span><span class="sxs-lookup"><span data-stu-id="203f8-153">**System** - Indicates that the service is a device driver started by the 'IOInitSystem()' function.</span></span> <span data-ttu-id="203f8-154">這個值僅適用於裝置驅動程式。</span><span class="sxs-lookup"><span data-stu-id="203f8-154">This value is valid only for device drivers.</span></span>

 <span data-ttu-id="203f8-155">預設值為 [ **自動** ]。</span><span class="sxs-lookup"><span data-stu-id="203f8-155">The default value is **Automatic** .</span></span>

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

### <span data-ttu-id="203f8-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="203f8-156">-Confirm</span></span>

<span data-ttu-id="203f8-157">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="203f8-157">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="203f8-158">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="203f8-158">-WhatIf</span></span>

<span data-ttu-id="203f8-159">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="203f8-159">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="203f8-160">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="203f8-160">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="203f8-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="203f8-161">CommonParameters</span></span>

<span data-ttu-id="203f8-162">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="203f8-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="203f8-163">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="203f8-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="203f8-164">輸入</span><span class="sxs-lookup"><span data-stu-id="203f8-164">INPUTS</span></span>

### <span data-ttu-id="203f8-165">無</span><span class="sxs-lookup"><span data-stu-id="203f8-165">None</span></span>

<span data-ttu-id="203f8-166">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="203f8-166">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="203f8-167">輸出</span><span class="sxs-lookup"><span data-stu-id="203f8-167">OUTPUTS</span></span>

### <span data-ttu-id="203f8-168">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="203f8-168">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="203f8-169">此 Cmdlet 會傳回代表新服務的物件。</span><span class="sxs-lookup"><span data-stu-id="203f8-169">This cmdlet returns an object that represents the new service.</span></span>

## <span data-ttu-id="203f8-170">注意</span><span class="sxs-lookup"><span data-stu-id="203f8-170">NOTES</span></span>

<span data-ttu-id="203f8-171">若要在 Windows Vista 和更新版本的 Windows 作業系統上執行此 Cmdlet，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="203f8-171">To run this cmdlet on Windows Vista and later versions of the Windows operating system, start PowerShell by using the Run as administrator option.</span></span>

<span data-ttu-id="203f8-172">若要刪除服務，請使用 Sc.exe，或使用 `Get-CimInstance` Cmdlet 取得代表服務的 **Win32_Service** 物件，然後使用 **delete** 方法來刪除服務。</span><span class="sxs-lookup"><span data-stu-id="203f8-172">To delete a service, use Sc.exe, or use the `Get-CimInstance` cmdlet to get the **Win32_Service** object that represents the service and then use the **Delete** method to delete the service.</span></span> <span data-ttu-id="203f8-173">傳回的物件沒有 `Get-Service` delete 方法。</span><span class="sxs-lookup"><span data-stu-id="203f8-173">The object that `Get-Service` returns does not have a delete method.</span></span>

## <span data-ttu-id="203f8-174">相關連結</span><span class="sxs-lookup"><span data-stu-id="203f8-174">RELATED LINKS</span></span>

[<span data-ttu-id="203f8-175">Get-Service</span><span class="sxs-lookup"><span data-stu-id="203f8-175">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="203f8-176">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="203f8-176">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="203f8-177">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="203f8-177">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="203f8-178">Set-Service</span><span class="sxs-lookup"><span data-stu-id="203f8-178">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="203f8-179">Start-Service</span><span class="sxs-lookup"><span data-stu-id="203f8-179">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="203f8-180">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="203f8-180">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="203f8-181">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="203f8-181">Suspend-Service</span></span>](Suspend-Service.md)
