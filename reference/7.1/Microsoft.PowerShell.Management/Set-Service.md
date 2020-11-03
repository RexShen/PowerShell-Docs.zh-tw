---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: 9881dccb78aab973cc6031e28308bbdd27b4da57
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205224"
---
# <span data-ttu-id="63542-103">Set-Service</span><span class="sxs-lookup"><span data-stu-id="63542-103">Set-Service</span></span>

## <span data-ttu-id="63542-104">概要</span><span class="sxs-lookup"><span data-stu-id="63542-104">SYNOPSIS</span></span>
<span data-ttu-id="63542-105">啟動、停止並擱置服務，然後變更其屬性。</span><span class="sxs-lookup"><span data-stu-id="63542-105">Starts, stops, and suspends a service, and changes its properties.</span></span>

## <span data-ttu-id="63542-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="63542-106">SYNTAX</span></span>

### <span data-ttu-id="63542-107">Name (預設值)</span><span class="sxs-lookup"><span data-stu-id="63542-107">Name (Default)</span></span>

```
Set-Service [-Name] <String> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-Status <String>]
 [-SecurityDescriptorSddl <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="63542-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="63542-108">InputObject</span></span>

```
Set-Service [-InputObject] <ServiceController> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-SecurityDescriptorSddl <String>]
 [-Status <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="63542-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="63542-109">DESCRIPTION</span></span>

<span data-ttu-id="63542-110">此 `Set-Service` Cmdlet 會變更服務的屬性，例如 **Status** 、 **Description** 、 **DisplayName** 和 **StartupType** 。</span><span class="sxs-lookup"><span data-stu-id="63542-110">The `Set-Service` cmdlet changes the properties of a service such as the **Status** , **Description** , **DisplayName** , and **StartupType** .</span></span> <span data-ttu-id="63542-111">`Set-Service` 可以啟動、停止、暫停或暫停服務。</span><span class="sxs-lookup"><span data-stu-id="63542-111">`Set-Service` can start, stop, suspend, or pause a service.</span></span> <span data-ttu-id="63542-112">若要識別服務，請輸入其服務名稱或提交服務物件。</span><span class="sxs-lookup"><span data-stu-id="63542-112">To identify a service, enter its service name or submit a service object.</span></span> <span data-ttu-id="63542-113">或者，將服務名稱或服務物件沿著管線向下傳送至 `Set-Service` 。</span><span class="sxs-lookup"><span data-stu-id="63542-113">Or, send a service name or service object down the pipeline to `Set-Service`.</span></span>

## <span data-ttu-id="63542-114">範例</span><span class="sxs-lookup"><span data-stu-id="63542-114">EXAMPLES</span></span>

### <span data-ttu-id="63542-115">範例1：變更顯示名稱</span><span class="sxs-lookup"><span data-stu-id="63542-115">Example 1: Change a display name</span></span>

<span data-ttu-id="63542-116">在此範例中，服務的顯示名稱已變更。</span><span class="sxs-lookup"><span data-stu-id="63542-116">In this example, a service's display name is changed.</span></span> <span data-ttu-id="63542-117">若要查看原始顯示名稱，請使用 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="63542-117">To view the original display name, use `Get-Service`.</span></span>

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

<span data-ttu-id="63542-118">`Set-Service` 使用 **Name** 參數來指定服務的名稱 **LanmanWorkstation** 。</span><span class="sxs-lookup"><span data-stu-id="63542-118">`Set-Service` uses the **Name** parameter to specify the service's name, **LanmanWorkstation** .</span></span> <span data-ttu-id="63542-119">**DisplayName** 參數指定新的顯示名稱 [ **LanMan 工作站** ]。</span><span class="sxs-lookup"><span data-stu-id="63542-119">The **DisplayName** parameter specifies the new display name, **LanMan Workstation** .</span></span>

### <span data-ttu-id="63542-120">範例2：變更服務的啟動類型</span><span class="sxs-lookup"><span data-stu-id="63542-120">Example 2: Change the startup type of services</span></span>

<span data-ttu-id="63542-121">此範例顯示如何變更服務的啟動類型。</span><span class="sxs-lookup"><span data-stu-id="63542-121">This example shows how to change a service's startup type.</span></span>

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

<span data-ttu-id="63542-122">`Set-Service` 使用 **Name** 參數來指定服務的名稱（ **BITS** ）。</span><span class="sxs-lookup"><span data-stu-id="63542-122">`Set-Service` uses the **Name** parameter to specify the service's name, **BITS** .</span></span> <span data-ttu-id="63542-123">**StartupType** 參數會將服務設定為 **自動** 。</span><span class="sxs-lookup"><span data-stu-id="63542-123">The **StartupType** parameter sets the service to **Automatic** .</span></span>

<span data-ttu-id="63542-124">`Get-Service` 使用 **Name** 參數來指定 **BITS** 服務，並將物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="63542-124">`Get-Service` uses the **Name** parameter to specify the **BITS** service and sends the object down the pipeline.</span></span> <span data-ttu-id="63542-125">`Select-Object` 使用 **Property** 參數來顯示 **BITS** 服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="63542-125">`Select-Object` uses the **Property** parameter to display the **BITS** service's status.</span></span>

### <span data-ttu-id="63542-126">範例3：變更服務的描述</span><span class="sxs-lookup"><span data-stu-id="63542-126">Example 3: Change the description of a service</span></span>

<span data-ttu-id="63542-127">此範例會變更 BITS 服務的描述，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="63542-127">This example changes the BITS service's description and displays the result.</span></span>

<span data-ttu-id="63542-128">`Get-CimInstance`使用 Cmdlet 的原因是它會傳回包含服務 **描述** 的 **Win32_Service** 物件。</span><span class="sxs-lookup"><span data-stu-id="63542-128">The `Get-CimInstance` cmdlet is used because it returns a **Win32_Service** object that includes the service's **Description** .</span></span>

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

<span data-ttu-id="63542-129">`Get-CimInstance` 將物件向下傳送至管線， `Format-List` 並顯示服務的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="63542-129">`Get-CimInstance` sends the object down the pipeline to `Format-List` and displays the service's name and description.</span></span> <span data-ttu-id="63542-130">為了進行比較，此命令會在更新描述之前和之後執行。</span><span class="sxs-lookup"><span data-stu-id="63542-130">For comparison purposes, the command is run before and after the description is updated.</span></span>

<span data-ttu-id="63542-131">`Set-Service` 使用 **Name** 參數來指定 **BITS** 服務。</span><span class="sxs-lookup"><span data-stu-id="63542-131">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="63542-132">**Description** 參數會指定服務描述的更新文字。</span><span class="sxs-lookup"><span data-stu-id="63542-132">The **Description** parameter specifies the updated text for the services' description.</span></span>

### <span data-ttu-id="63542-133">範例4：啟動服務</span><span class="sxs-lookup"><span data-stu-id="63542-133">Example 4: Start a service</span></span>

<span data-ttu-id="63542-134">在此範例中，會啟動服務。</span><span class="sxs-lookup"><span data-stu-id="63542-134">In this example, a service is started.</span></span>

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

<span data-ttu-id="63542-135">`Set-Service` 使用 **Name** 參數來指定服務 **WinRM** 。</span><span class="sxs-lookup"><span data-stu-id="63542-135">`Set-Service` uses the **Name** parameter to specify the service, **WinRM** .</span></span> <span data-ttu-id="63542-136">**Status** 參數會使用執行的 **值來** 啟動服務。</span><span class="sxs-lookup"><span data-stu-id="63542-136">The **Status** parameter uses the value **Running** to start the service.</span></span> <span data-ttu-id="63542-137">**PassThru** 參數會輸出顯示結果的 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="63542-137">The **PassThru** parameter outputs a **ServiceController** object that displays the results.</span></span>

### <span data-ttu-id="63542-138">範例5：暫止服務</span><span class="sxs-lookup"><span data-stu-id="63542-138">Example 5: Suspend a service</span></span>

<span data-ttu-id="63542-139">此範例會使用管線來暫停至服務。</span><span class="sxs-lookup"><span data-stu-id="63542-139">This example uses the pipeline to pause to service.</span></span>

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

<span data-ttu-id="63542-140">`Get-Service` 使用 **Name** 參數來指定 **排程** 服務，然後將物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="63542-140">`Get-Service` uses the **Name** parameter to specify the **Schedule** service, and sends the object down the pipeline.</span></span> <span data-ttu-id="63542-141">`Set-Service` 使用 **Status** 參數將服務設定為 **暫停** 。</span><span class="sxs-lookup"><span data-stu-id="63542-141">`Set-Service` uses the **Status** parameter to set the service to **Paused** .</span></span>

### <span data-ttu-id="63542-142">範例6：停止服務</span><span class="sxs-lookup"><span data-stu-id="63542-142">Example 6: Stop a service</span></span>

<span data-ttu-id="63542-143">此範例會使用變數來停止服務。</span><span class="sxs-lookup"><span data-stu-id="63542-143">This example uses a variable to stop a service.</span></span>

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

<span data-ttu-id="63542-144">`Get-Service` 使用 **Name** 參數來指定服務（ **Schedule** ）。</span><span class="sxs-lookup"><span data-stu-id="63542-144">`Get-Service` uses the **Name** parameter to specify the service, **Schedule** .</span></span> <span data-ttu-id="63542-145">物件會儲存在變數中 `$S` 。</span><span class="sxs-lookup"><span data-stu-id="63542-145">The object is stored in the variable, `$S`.</span></span> <span data-ttu-id="63542-146">`Set-Service` 使用 **InputObject** 參數並指定儲存的物件 `$S` 。</span><span class="sxs-lookup"><span data-stu-id="63542-146">`Set-Service` uses the **InputObject** parameter and specifies the object stored `$S`.</span></span> <span data-ttu-id="63542-147">**Status** 參數會將服務設定為「 **已停止** 」。</span><span class="sxs-lookup"><span data-stu-id="63542-147">The **Status** parameter sets the service to **Stopped** .</span></span>

### <span data-ttu-id="63542-148">範例7：停止遠端系統上的服務</span><span class="sxs-lookup"><span data-stu-id="63542-148">Example 7: Stop a service on a remote system</span></span>

<span data-ttu-id="63542-149">此範例會停止遠端電腦上的服務。</span><span class="sxs-lookup"><span data-stu-id="63542-149">This example stops a service on a remote computer.</span></span>
<span data-ttu-id="63542-150">如需詳細資訊，請參閱 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="63542-150">For more information, see [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```powershell
$Cred = Get-Credential
$S = Get-Service -Name Schedule
Invoke-Command -ComputerName server01.contoso.com -Credential $Cred -ScriptBlock {
  Set-Service -InputObject $S -Status Stopped
}
```

<span data-ttu-id="63542-151">`Get-Credential` 提示輸入使用者名稱和密碼，並將認證儲存在 `$Cred` 變數中。</span><span class="sxs-lookup"><span data-stu-id="63542-151">`Get-Credential` prompts for a username and password, and stores the credentials in the `$Cred` variable.</span></span> <span data-ttu-id="63542-152">`Get-Service` 使用 **Name** 參數來指定 **排程** 服務。</span><span class="sxs-lookup"><span data-stu-id="63542-152">`Get-Service` uses the **Name** parameter to specify the **Schedule** service.</span></span> <span data-ttu-id="63542-153">物件會儲存在變數中 `$S` 。</span><span class="sxs-lookup"><span data-stu-id="63542-153">The object is stored in the variable, `$S`.</span></span>

<span data-ttu-id="63542-154">`Invoke-Command` 使用 **ComputerName** 參數來指定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="63542-154">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer.</span></span> <span data-ttu-id="63542-155">**Credential** 參數使用 `$Cred` 變數來登入電腦。</span><span class="sxs-lookup"><span data-stu-id="63542-155">The **Credential** parameter uses the `$Cred` variable to sign on to the computer.</span></span> <span data-ttu-id="63542-156">**ScriptBlock** 會呼叫 `Set-Service` 。</span><span class="sxs-lookup"><span data-stu-id="63542-156">The **ScriptBlock** calls `Set-Service`.</span></span> <span data-ttu-id="63542-157">**InputObject** 參數會指定儲存的服務物件 `$S` 。</span><span class="sxs-lookup"><span data-stu-id="63542-157">The **InputObject** parameter specifies the service object stored `$S`.</span></span> <span data-ttu-id="63542-158">**Status** 參數會將服務設定為「 **已停止** 」。</span><span class="sxs-lookup"><span data-stu-id="63542-158">The **Status** parameter sets the service to **Stopped** .</span></span>

### <span data-ttu-id="63542-159">範例8：變更服務的認證</span><span class="sxs-lookup"><span data-stu-id="63542-159">Example 8: Change credential of a service</span></span>

<span data-ttu-id="63542-160">此範例會變更用來管理服務的認證。</span><span class="sxs-lookup"><span data-stu-id="63542-160">This example changes the credentials that are used to manage a service.</span></span>

```powershell
$credential = Get-Credential
Set-Service -Name Schedule -Credential $credential
```

<span data-ttu-id="63542-161">`Get-Credential` 提示輸入使用者名稱和密碼，並將認證儲存在 `$credential` 變數中。</span><span class="sxs-lookup"><span data-stu-id="63542-161">`Get-Credential` prompts for a username and password, and stores the credentials in the `$credential` variable.</span></span> <span data-ttu-id="63542-162">`Set-Service` 使用 **Name** 參數來指定 **排程** 服務。</span><span class="sxs-lookup"><span data-stu-id="63542-162">`Set-Service` uses the **Name** parameter to specify the **Schedule** service.</span></span> <span data-ttu-id="63542-163">**Credential** 參數會使用 `$credential` 變數，並更新 **排程** 服務。</span><span class="sxs-lookup"><span data-stu-id="63542-163">The **Credential** parameter uses the `$credential` variable and updates the **Schedule** service.</span></span>

### <span data-ttu-id="63542-164">範例9：變更服務的 SecurityDescriptor</span><span class="sxs-lookup"><span data-stu-id="63542-164">Example 9: Change the SecurityDescriptor of a service</span></span>

<span data-ttu-id="63542-165">此範例會變更服務的 **SecurityDescriptor** 。</span><span class="sxs-lookup"><span data-stu-id="63542-165">This example changes a service's **SecurityDescriptor** .</span></span>

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
Set-Service -Name "BITS" -SecurityDescriptorSddl $SDDL
```

<span data-ttu-id="63542-166">**SecurityDescriptor** 會儲存在變數中 `$SDDL` 。</span><span class="sxs-lookup"><span data-stu-id="63542-166">The **SecurityDescriptor** is stored in the `$SDDL` variable.</span></span> <span data-ttu-id="63542-167">`Set-Service` 使用 **Name** 參數來指定 **BITS** 服務。</span><span class="sxs-lookup"><span data-stu-id="63542-167">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="63542-168">**SecurityDescriptorSddl** 參數會使用 `$SDDL` 來變更 **BITS** 服務的 **SecurityDescriptor** 。</span><span class="sxs-lookup"><span data-stu-id="63542-168">The **SecurityDescriptorSddl** parameter uses `$SDDL` to change the **SecurityDescriptor** for the **BITS** service.</span></span>

## <span data-ttu-id="63542-169">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="63542-169">PARAMETERS</span></span>

### <span data-ttu-id="63542-170">-Confirm</span><span class="sxs-lookup"><span data-stu-id="63542-170">-Confirm</span></span>

<span data-ttu-id="63542-171">在執行之前提示您確認 `Set-Service` 。</span><span class="sxs-lookup"><span data-stu-id="63542-171">Prompts you for confirmation before running `Set-Service`.</span></span>

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

### <span data-ttu-id="63542-172">-Credential</span><span class="sxs-lookup"><span data-stu-id="63542-172">-Credential</span></span>

<span data-ttu-id="63542-173">將服務所使用的帳戶指定為 [服務登入帳戶](/windows/desktop/ad/about-service-logon-accounts)。</span><span class="sxs-lookup"><span data-stu-id="63542-173">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="63542-174">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="63542-174">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="63542-175">如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="63542-175">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="63542-176">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="63542-176">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="63542-177">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="63542-177">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

<span data-ttu-id="63542-178">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="63542-178">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="63542-179">-Description</span><span class="sxs-lookup"><span data-stu-id="63542-179">-Description</span></span>

<span data-ttu-id="63542-180">指定服務的新描述。</span><span class="sxs-lookup"><span data-stu-id="63542-180">Specifies a new description for the service.</span></span>

<span data-ttu-id="63542-181">服務描述會顯示在 [ **電腦管理]、[服務** ] 中。</span><span class="sxs-lookup"><span data-stu-id="63542-181">The service description appears in **Computer Management, Services** .</span></span> <span data-ttu-id="63542-182">**描述** 不是 `Get-Service` **ServiceController** 物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="63542-182">The **Description** isn't a property of the `Get-Service` **ServiceController** object.</span></span> <span data-ttu-id="63542-183">若要查看服務描述，請使用傳回 `Get-CimInstance` 代表服務的 **Win32_Service** 物件。</span><span class="sxs-lookup"><span data-stu-id="63542-183">To see the service description, use `Get-CimInstance` that returns a **Win32_Service** object that represents the service.</span></span>

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

### <span data-ttu-id="63542-184">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="63542-184">-DisplayName</span></span>

<span data-ttu-id="63542-185">指定服務的新顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="63542-185">Specifies a new display name for the service.</span></span>

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

### <span data-ttu-id="63542-186">-Force</span><span class="sxs-lookup"><span data-stu-id="63542-186">-Force</span></span>

<span data-ttu-id="63542-187">指定服務的停止模式。</span><span class="sxs-lookup"><span data-stu-id="63542-187">Specifies the Stop mode of the service.</span></span> <span data-ttu-id="63542-188">只有在使用時，此參數才有效 `-Status Stopped` 。</span><span class="sxs-lookup"><span data-stu-id="63542-188">This parameter only works when `-Status Stopped` is used.</span></span> <span data-ttu-id="63542-189">啟用時， `Set-Service` 會在目標服務停止之前停止相依的服務。</span><span class="sxs-lookup"><span data-stu-id="63542-189">If enabled, `Set-Service` stops the dependent services before the target service is stopped.</span></span> <span data-ttu-id="63542-190">根據預設，當其他執行中的服務相依于目標服務時，就會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="63542-190">By default, exceptions are raised when other running services depend on the target service.</span></span>

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

### <span data-ttu-id="63542-191">-InputObject</span><span class="sxs-lookup"><span data-stu-id="63542-191">-InputObject</span></span>

<span data-ttu-id="63542-192">指定代表要變更之服務的 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="63542-192">Specifies a **ServiceController** object that represents the service to change.</span></span> <span data-ttu-id="63542-193">輸入包含物件的變數，或輸入可取得物件的命令或運算式，例如 `Get-Service` 命令。</span><span class="sxs-lookup"><span data-stu-id="63542-193">Enter a variable that contains the object, or type a command or expression that gets the object, such as a `Get-Service` command.</span></span> <span data-ttu-id="63542-194">您可以使用管線將服務物件傳送至 `Set-Service` 。</span><span class="sxs-lookup"><span data-stu-id="63542-194">You can use the pipeline to send a service object to `Set-Service`.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="63542-195">-Name</span><span class="sxs-lookup"><span data-stu-id="63542-195">-Name</span></span>

<span data-ttu-id="63542-196">指定要變更之服務的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="63542-196">Specifies the service name of the service to be changed.</span></span> <span data-ttu-id="63542-197">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="63542-197">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="63542-198">您可以使用管線將服務名稱傳送至 `Set-Service` 。</span><span class="sxs-lookup"><span data-stu-id="63542-198">You can use the pipeline to send a service name to `Set-Service`.</span></span>

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

### <span data-ttu-id="63542-199">-PassThru</span><span class="sxs-lookup"><span data-stu-id="63542-199">-PassThru</span></span>

<span data-ttu-id="63542-200">傳回代表已變更之服務的 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="63542-200">Returns a **ServiceController** object that represents the services that were changed.</span></span> <span data-ttu-id="63542-201">依預設， `Set-Service` 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="63542-201">By default, `Set-Service` doesn't generate any output.</span></span>

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

### <span data-ttu-id="63542-202">-StartupType</span><span class="sxs-lookup"><span data-stu-id="63542-202">-StartupType</span></span>

<span data-ttu-id="63542-203">指定服務的啟動模式。</span><span class="sxs-lookup"><span data-stu-id="63542-203">Specifies the start mode of the service.</span></span>

<span data-ttu-id="63542-204">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="63542-204">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="63542-205">**自動** -服務會在系統啟動時啟動或由作業系統啟動。</span><span class="sxs-lookup"><span data-stu-id="63542-205">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="63542-206">如果自動啟動的服務依賴手動啟動的服務，以手動方式啟動的服務也會在系統啟動時自動啟動。</span><span class="sxs-lookup"><span data-stu-id="63542-206">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="63542-207">**AutomaticDelayedStart** -在系統開機之後不久就會開始。</span><span class="sxs-lookup"><span data-stu-id="63542-207">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="63542-208">**停用** -服務已停用，且無法由使用者或應用程式啟動。</span><span class="sxs-lookup"><span data-stu-id="63542-208">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="63542-209">**InvalidValue** -沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="63542-209">**InvalidValue** - Has no effect.</span></span> <span data-ttu-id="63542-210">此 Cmdlet 不會傳回錯誤，但服務的 StartupType 不會變更。</span><span class="sxs-lookup"><span data-stu-id="63542-210">The cmdlet does not return an error but the StartupType of the service is not changed.</span></span>
- <span data-ttu-id="63542-211">**手動** -此服務只會由使用者以手動方式啟動，使用服務控制管理員或由應用程式啟動。</span><span class="sxs-lookup"><span data-stu-id="63542-211">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ServiceStartupType
Parameter Sets: (All)
Aliases: StartMode, SM, ST, StartType
Accepted values: Automatic, AutomaticDelayedStart, Disabled, InvalidValue, Manual

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="63542-212">-Status</span><span class="sxs-lookup"><span data-stu-id="63542-212">-Status</span></span>

<span data-ttu-id="63542-213">指定服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="63542-213">Specifies the status for the service.</span></span>

<span data-ttu-id="63542-214">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="63542-214">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="63542-215">已 **暫停** 。</span><span class="sxs-lookup"><span data-stu-id="63542-215">**Paused** .</span></span> <span data-ttu-id="63542-216">暫停服務。</span><span class="sxs-lookup"><span data-stu-id="63542-216">Suspends the service.</span></span>
- <span data-ttu-id="63542-217">**正在** 執行。</span><span class="sxs-lookup"><span data-stu-id="63542-217">**Running** .</span></span> <span data-ttu-id="63542-218">啟動服務。</span><span class="sxs-lookup"><span data-stu-id="63542-218">Starts the service.</span></span>
- <span data-ttu-id="63542-219">**已停止** 。</span><span class="sxs-lookup"><span data-stu-id="63542-219">**Stopped** .</span></span> <span data-ttu-id="63542-220">停止服務。</span><span class="sxs-lookup"><span data-stu-id="63542-220">Stops the service.</span></span>

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

### <span data-ttu-id="63542-221">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="63542-221">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="63542-222">以 **Sddl** 格式指定服務的 **SecurityDescriptor** 。</span><span class="sxs-lookup"><span data-stu-id="63542-222">Specifies the **SecurityDescriptor** for the service in **Sddl** format.</span></span>

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

### <span data-ttu-id="63542-223">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="63542-223">-WhatIf</span></span>

<span data-ttu-id="63542-224">顯示執行時所發生 `Set-Service` 的情況。</span><span class="sxs-lookup"><span data-stu-id="63542-224">Shows what would happen if `Set-Service` runs.</span></span> <span data-ttu-id="63542-225">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="63542-225">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="63542-226">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="63542-226">CommonParameters</span></span>

<span data-ttu-id="63542-227">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="63542-227">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="63542-228">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="63542-228">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="63542-229">輸入</span><span class="sxs-lookup"><span data-stu-id="63542-229">INPUTS</span></span>

### <span data-ttu-id="63542-230">System.ServiceProcess.ServiceController、System.String</span><span class="sxs-lookup"><span data-stu-id="63542-230">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="63542-231">您可以使用管線將服務物件或包含服務名稱的字串傳送至 `Set-Service` 。</span><span class="sxs-lookup"><span data-stu-id="63542-231">You can use the pipeline to send a service object or a string that contains a service name to `Set-Service`.</span></span>

## <span data-ttu-id="63542-232">輸出</span><span class="sxs-lookup"><span data-stu-id="63542-232">OUTPUTS</span></span>

### <span data-ttu-id="63542-233">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="63542-233">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="63542-234">依預設， `Set-Service` 不會傳回任何物件。</span><span class="sxs-lookup"><span data-stu-id="63542-234">By default, `Set-Service` doesn't return any objects.</span></span> <span data-ttu-id="63542-235">使用 **PassThru** 參數輸出 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="63542-235">Use the **PassThru** parameter to output a **ServiceController** object.</span></span>

## <span data-ttu-id="63542-236">注意</span><span class="sxs-lookup"><span data-stu-id="63542-236">NOTES</span></span>

<span data-ttu-id="63542-237">`Set-Service` 需要較高的許可權。</span><span class="sxs-lookup"><span data-stu-id="63542-237">`Set-Service` requires elevated permissions.</span></span> <span data-ttu-id="63542-238">使用 [ **以系統管理員身分執行** ] 選項。</span><span class="sxs-lookup"><span data-stu-id="63542-238">Use the **Run as administrator** option.</span></span>

<span data-ttu-id="63542-239">`Set-Service` 只有在目前的使用者有權管理服務時，才能控制服務。</span><span class="sxs-lookup"><span data-stu-id="63542-239">`Set-Service` can only control services when the current user has permissions to manage services.</span></span> <span data-ttu-id="63542-240">如果命令無法正確運作，您可能沒有必要的許可權。</span><span class="sxs-lookup"><span data-stu-id="63542-240">If a command doesn't work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="63542-241">若要尋找服務的服務名稱或顯示名稱，請使用 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="63542-241">To find a service's service name or display name, use `Get-Service`.</span></span> <span data-ttu-id="63542-242">服務名稱是在 [ **名稱** ] 資料行中，而顯示名稱則是在 [ **DisplayName** ] 欄位中。</span><span class="sxs-lookup"><span data-stu-id="63542-242">The service names are in the **Name** column and the display names are in the **DisplayName** column.</span></span>

## <span data-ttu-id="63542-243">相關連結</span><span class="sxs-lookup"><span data-stu-id="63542-243">RELATED LINKS</span></span>

[<span data-ttu-id="63542-244">Get-Service</span><span class="sxs-lookup"><span data-stu-id="63542-244">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="63542-245">New-Service</span><span class="sxs-lookup"><span data-stu-id="63542-245">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="63542-246">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="63542-246">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="63542-247">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="63542-247">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="63542-248">Start-Service</span><span class="sxs-lookup"><span data-stu-id="63542-248">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="63542-249">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="63542-249">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="63542-250">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="63542-250">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="63542-251">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="63542-251">Remove-Service</span></span>](Remove-Service.md)

