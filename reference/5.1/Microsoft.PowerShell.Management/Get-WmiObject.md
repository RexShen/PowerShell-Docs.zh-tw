---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WmiObject
ms.openlocfilehash: ed759ff3d0dd35cd55f9dac5a2d76e36eac4dc6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203983"
---
# <span data-ttu-id="5e39d-103">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="5e39d-103">Get-WmiObject</span></span>

## <span data-ttu-id="5e39d-104">概要</span><span class="sxs-lookup"><span data-stu-id="5e39d-104">SYNOPSIS</span></span>
<span data-ttu-id="5e39d-105">取得 Windows Management Instrumentation (WMI) 類別的執行個體，或可用類別的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5e39d-105">Gets instances of Windows Management Instrumentation (WMI) classes or information about the available classes.</span></span>

## <span data-ttu-id="5e39d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5e39d-106">SYNTAX</span></span>

### <span data-ttu-id="5e39d-107">查詢 (預設) </span><span class="sxs-lookup"><span data-stu-id="5e39d-107">query (Default)</span></span>

```
Get-WmiObject [-Class] <String> [[-Property] <String[]>] [-Filter <String>] [-Amended] [-DirectRead]
 [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="5e39d-108">list</span><span class="sxs-lookup"><span data-stu-id="5e39d-108">list</span></span>

```
Get-WmiObject [[-Class] <String>] [-Recurse] [-Amended] [-List] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="5e39d-109">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="5e39d-109">WQLQuery</span></span>

```
Get-WmiObject [-Amended] [-DirectRead] -Query <String> [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="5e39d-110">Class - 類別</span><span class="sxs-lookup"><span data-stu-id="5e39d-110">class</span></span>

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="5e39d-111">path</span><span class="sxs-lookup"><span data-stu-id="5e39d-111">path</span></span>

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

## <span data-ttu-id="5e39d-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5e39d-112">DESCRIPTION</span></span>

<span data-ttu-id="5e39d-113">從 PowerShell 3.0 開始，此 Cmdlet 已被取代 `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="5e39d-113">Starting in PowerShell 3.0, this cmdlet has been superseded by `Get-CimInstance`.</span></span>

<span data-ttu-id="5e39d-114">`Get-WmiObject`Cmdlet 會取得 wmi 類別的實例或可用 wmi 類別的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5e39d-114">The `Get-WmiObject` cmdlet gets instances of WMI classes or information about the available WMI classes.</span></span> <span data-ttu-id="5e39d-115">若要指定遠端電腦，請使用 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="5e39d-115">To specify a remote computer, use the **ComputerName** parameter.</span></span> <span data-ttu-id="5e39d-116">若指定 **List** 參數，此 Cmdlet 會取得在指定命名空間內可用的 WMI 類別相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5e39d-116">If the **List** parameter is specified, the cmdlet gets information about the WMI classes that are available in a specified namespace.</span></span> <span data-ttu-id="5e39d-117">若指定 **Query** 參數，此 Cmdlet 會執行 WMI 查詢語言 (WQL) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5e39d-117">If the **Query** parameter is specified, the cmdlet runs a WMI query language (WQL) statement.</span></span>

<span data-ttu-id="5e39d-118">`Get-WmiObject`Cmdlet 不會使用 Windows PowerShell 遠端執行遠端作業。</span><span class="sxs-lookup"><span data-stu-id="5e39d-118">The `Get-WmiObject` cmdlet does not use Windows PowerShell remoting to perform remote operations.</span></span>
<span data-ttu-id="5e39d-119">您可以使用 Cmdlet 的 **ComputerName** 參數， `Get-WmiObject` 即使您的電腦不符合 Windows PowerShell 遠端處理的需求或未在 Windows PowerShell 中設定遠端功能。</span><span class="sxs-lookup"><span data-stu-id="5e39d-119">You can use the **ComputerName** parameter of the `Get-WmiObject` cmdlet even if your computer does not meet the requirements for Windows PowerShell remoting or is not configured for remoting in Windows PowerShell.</span></span>

<span data-ttu-id="5e39d-120">從 Windows PowerShell 3.0 開始，傳回之物件的 **__Server** 屬性會 `Get-WmiObject` 有 **PSComputerName** 的別名。</span><span class="sxs-lookup"><span data-stu-id="5e39d-120">Beginning in Windows PowerShell 3.0, the **__Server** property of the object that `Get-WmiObject` returns has a **PSComputerName** alias.</span></span> <span data-ttu-id="5e39d-121">這樣比較容易在輸出和報告中包含來源電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="5e39d-121">This makes it easier to include the source computer name in output and reports.</span></span>

## <span data-ttu-id="5e39d-122">範例</span><span class="sxs-lookup"><span data-stu-id="5e39d-122">EXAMPLES</span></span>

### <span data-ttu-id="5e39d-123">範例1：取得本機電腦上的處理常式</span><span class="sxs-lookup"><span data-stu-id="5e39d-123">Example 1: Get processes on the local computer</span></span>

<span data-ttu-id="5e39d-124">這個範例會取得本機電腦上的處理常式。</span><span class="sxs-lookup"><span data-stu-id="5e39d-124">This example get the processes on the local computer.</span></span>

```powershell
Get-WmiObject -Class Win32_Process
```

### <span data-ttu-id="5e39d-125">範例2：取得遠端電腦上的服務</span><span class="sxs-lookup"><span data-stu-id="5e39d-125">Example 2: Gets services on a remote computer</span></span>

<span data-ttu-id="5e39d-126">此範例會取得遠端電腦上的服務。</span><span class="sxs-lookup"><span data-stu-id="5e39d-126">This example gets the services on a remote computer.</span></span> <span data-ttu-id="5e39d-127">**ComputerName** 參數指定遠端電腦的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="5e39d-127">The **ComputerName** parameter specifies the IP address of a remote computer.</span></span> <span data-ttu-id="5e39d-128">根據預設，目前的使用者帳戶必須是遠端電腦上 **Administrators** 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="5e39d-128">By default, the current user account must be a member of the **Administrators** group on the remote computer.</span></span>

```powershell
Get-WmiObject -Class Win32_Service -ComputerName 10.1.4.62
```

### <span data-ttu-id="5e39d-129">範例3：取得本機電腦的根或預設命名空間中的 WMI 類別</span><span class="sxs-lookup"><span data-stu-id="5e39d-129">Example 3: Get WMI classes in the root or default namespace of the local computer</span></span>

<span data-ttu-id="5e39d-130">這個範例會取得本機電腦的根或預設命名空間中的 WMI 類別。</span><span class="sxs-lookup"><span data-stu-id="5e39d-130">This example gets the WMI classes in the root or default namespace of the local computer.</span></span>

```powershell
Get-WmiObject -Namespace "root/default" -List
```

### <span data-ttu-id="5e39d-131">範例4：在多部電腦上取得命名服務</span><span class="sxs-lookup"><span data-stu-id="5e39d-131">Example 4: Get a named service on multiple computers</span></span>

<span data-ttu-id="5e39d-132">這個範例會取得 **ComputerName** 參數值所指定電腦上的 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="5e39d-132">This example gets the WinRM service on the computers specified by the value of the **ComputerName** parameter.</span></span>

```powershell
Get-WmiObject -Query "select * from win32_service where name='WinRM'" -ComputerName Server01, Server02 |
  Format-List -Property PSComputerName, Name, ExitCode, Name, ProcessID, StartMode, State, Status
```

```Output
PSComputerName : SERVER01
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 844
StartMode      : Auto
State          : Running
Status         : OK

PSComputerName : SERVER02
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 932
StartMode      : Auto
State          : Running
Status         : OK
```

<span data-ttu-id="5e39d-133">管線運算子 (|) 將輸出傳送至 `Format-List` Cmdlet，此 Cmdlet 會將 **PSComputerName** 屬性新增至預設輸出。</span><span class="sxs-lookup"><span data-stu-id="5e39d-133">A pipeline operator (|) sends the output to the `Format-List` cmdlet, which adds the **PSComputerName** property to the default output.</span></span> <span data-ttu-id="5e39d-134">**PSComputerName** 是傳回之物件的 **__Server** 屬性的別名 `Get-WmiObject` 。</span><span class="sxs-lookup"><span data-stu-id="5e39d-134">**PSComputerName** is an alias of the **__Server** property of the objects that `Get-WmiObject` returns.</span></span> <span data-ttu-id="5e39d-135">此別名是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="5e39d-135">This alias was introduced in PowerShell 3.0.</span></span>

### <span data-ttu-id="5e39d-136">範例5：停止遠端電腦上的服務</span><span class="sxs-lookup"><span data-stu-id="5e39d-136">Example 5: Stop a service on a remote computer</span></span>

<span data-ttu-id="5e39d-137">此範例會停止遠端電腦上的 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="5e39d-137">This example stops the WinRM service on a remote computer.</span></span> <span data-ttu-id="5e39d-138">`Get-WmiObject` 取得 Server01 上 WinRM 服務物件的實例。</span><span class="sxs-lookup"><span data-stu-id="5e39d-138">`Get-WmiObject` gets the instance of the WinRM service object on Server01.</span></span> <span data-ttu-id="5e39d-139">然後，它會在該物件上叫用 **Win32_Service** WMI 類別的 **StopService** 方法。</span><span class="sxs-lookup"><span data-stu-id="5e39d-139">Then, it invokes the **StopService** method of the **Win32_Service** WMI class on that object.</span></span>

```powershell
(Get-WmiObject -Class Win32_Service -Filter "name='WinRM'" -ComputerName Server01).StopService()
```

<span data-ttu-id="5e39d-140">這相當於使用 `Stop-Service` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5e39d-140">This is equivalent to using the `Stop-Service` cmdlet.</span></span>

### <span data-ttu-id="5e39d-141">範例6：取得本機電腦上的 BIOS</span><span class="sxs-lookup"><span data-stu-id="5e39d-141">Example 6: Get the BIOS on the local computer</span></span>

<span data-ttu-id="5e39d-142">此範例會從本機電腦取得 BIOS 資訊。</span><span class="sxs-lookup"><span data-stu-id="5e39d-142">This example gets the BIOS information from the local computer.</span></span> <span data-ttu-id="5e39d-143">Cmdlet 的 **Property** 參數 `Format-List` 是用來顯示清單中傳回之物件的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="5e39d-143">The **Property** parameter of the `Format-List` cmdlet is used to display all properties of the returned object in a list.</span></span> <span data-ttu-id="5e39d-144">依預設，只 `Types.ps1xml` 會顯示設定檔中定義的屬性子集。</span><span class="sxs-lookup"><span data-stu-id="5e39d-144">By default, only the subset of properties defined in the `Types.ps1xml` configuration file are displayed.</span></span>

```powershell
Get-WmiObject -Class Win32_Bios | Format-List -Property *
```

```Output
Status                : OK
Name                  : Phoenix ROM BIOS PLUS Version 1.10 A05
Caption               : Phoenix ROM BIOS PLUS Version 1.10 A05
SMBIOSPresent         : True
__GENUS               : 2
__CLASS               : Win32_BIOS
__SUPERCLASS          : CIM_BIOSElement
__DYNASTY             : CIM_ManagedSystemElement
__RELPATH             : Win32_BIOS.Name="Phoenix ROM BIOS PLUS Version 1.10
__PROPERTY_COUNT      : 27
__DERIVATION          : {CIM_BIOSElement, CIM_SoftwareElement, CIM_LogicalElement,
__SERVER              : Server01
__NAMESPACE           : root\cimv2
__PATH                : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
BiosCharacteristics   : {7, 9, 10, 11...}
BIOSVersion           : {DELL   - 15, Phoenix ROM BIOS PLUS Version 1.10 A05}
BuildNumber           :
CodeSet               :
CurrentLanguage       : en|US|iso8859-1
Description           : Phoenix ROM BIOS PLUS Version 1.10 A05
IdentificationCode    :
InstallableLanguages  : 1
InstallDate           :
LanguageEdition       :
ListOfLanguages       : {en|US|iso8859-1}
Manufacturer          : Dell Inc.
OtherTargetOS         :
PrimaryBIOS           : True
ReleaseDate           : 20101103000000.000000+000
SerialNumber          : 8VDM9P1
SMBIOSBIOSVersion     : A05
SMBIOSMajorVersion    : 2
SMBIOSMinorVersion    : 6
SoftwareElementID     : Phoenix ROM BIOS PLUS Version 1.10 A05
SoftwareElementState  : 3
TargetOperatingSystem : 0
Version               : DELL   - 15
Scope                 : System.Management.ManagementScope
Path                  : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
Options               : System.Management.ObjectGetOptions
ClassPath             : \\JUNE-PC\root\cimv2:Win32_BIOS
Properties            : {BiosCharacteristics, BIOSVersion, BuildNumber, Caption...}
SystemProperties      : {__GENUS, __CLASS, __SUPERCLASS, __DYNASTY...}
Qualifiers            : {dynamic, Locale, provider, UUID}
Site                  :
Container             :
```

### <span data-ttu-id="5e39d-145">範例7：取得遠端電腦上的服務</span><span class="sxs-lookup"><span data-stu-id="5e39d-145">Example 7: Get the services on a remote computer</span></span>

<span data-ttu-id="5e39d-146">此範例會使用 Cmdlet 的 **Credential** 參數 `Get-WmiObject` 來取得遠端電腦上的服務。</span><span class="sxs-lookup"><span data-stu-id="5e39d-146">This example uses the **Credential** parameter of the `Get-WmiObject` cmdlet to get the services on a remote computer.</span></span> <span data-ttu-id="5e39d-147">**Credential** 參數的值是使用者帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="5e39d-147">The value of the **Credential** parameter is a user account name.</span></span> <span data-ttu-id="5e39d-148">使用者會被提示輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="5e39d-148">The user is prompted for a password.</span></span>

```powershell
Get-WmiObject Win32_Service -Credential FABRIKAM\administrator -ComputerName Fabrikam
```

> [!NOTE]
> <span data-ttu-id="5e39d-149">以本機電腦為目標時，無法使用認證。</span><span class="sxs-lookup"><span data-stu-id="5e39d-149">Credentials cannot be used when targeting the local computer.</span></span>

## <span data-ttu-id="5e39d-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5e39d-150">PARAMETERS</span></span>

### <span data-ttu-id="5e39d-151">-已修改</span><span class="sxs-lookup"><span data-stu-id="5e39d-151">-Amended</span></span>

<span data-ttu-id="5e39d-152">取得或設定一個值，該值會指示從 WMI 傳回的物件是否該包含修改過的資訊。</span><span class="sxs-lookup"><span data-stu-id="5e39d-152">Gets or sets a value that indicates whether the objects that are returned from WMI should contain amended information.</span></span> <span data-ttu-id="5e39d-153">一般而言，修改的資訊是可當地語系化的資訊，例如附加至 WMI 物件的物件和屬性描述。</span><span class="sxs-lookup"><span data-stu-id="5e39d-153">Typically, amended information is localizable information, such as object and property descriptions, that is attached to the WMI object.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e39d-154">-AsJob</span><span class="sxs-lookup"><span data-stu-id="5e39d-154">-AsJob</span></span>

<span data-ttu-id="5e39d-155">以背景工作方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="5e39d-155">Runs the command as a background job.</span></span> <span data-ttu-id="5e39d-156">使用此參數執行需要很長時間才能完成的命令。</span><span class="sxs-lookup"><span data-stu-id="5e39d-156">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="5e39d-157">使用 **AsJob** 參數時，此命令會傳回代表背景工作的物件，然後顯示命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="5e39d-157">When you use the **AsJob** parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span> <span data-ttu-id="5e39d-158">工作完成後，您可以繼續在工作階段中工作。</span><span class="sxs-lookup"><span data-stu-id="5e39d-158">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="5e39d-159">如果 `Get-WmiObject` 在遠端電腦上使用，則會在本機電腦上建立工作，而來自遠端電腦的結果則會自動傳回到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="5e39d-159">If `Get-WmiObject` is used on a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="5e39d-160">若要管理工作，請使用包含 Job Cmdlet 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5e39d-160">To manage the job, use the cmdlets that contain the Job cmdlets.</span></span> <span data-ttu-id="5e39d-161">若要取得工作結果，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5e39d-161">To get the job results, use the `Receive-Job` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="5e39d-162">若要將這個參數與遠端電腦搭配使用，則本機電腦和遠端電腦必須針對遠端執行功能做設定。</span><span class="sxs-lookup"><span data-stu-id="5e39d-162">To use this parameter with remote computers, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="5e39d-163">此外，您必須使用 Windows Vista 和更新版之 Windows 中的 [以系統管理員身分執行] 選項來啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="5e39d-163">Additionally, you must start Windows PowerShell by using the "Run as administrator" option in Windows Vista and later versions of Windows.</span></span> <span data-ttu-id="5e39d-164">如需詳細資訊，請參閱[about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e39d-164">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="5e39d-165">如需 Windows PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md) 和 [about_Remote_Jobs](../Microsoft.PowerShell.Core/about/about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="5e39d-165">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/about/about_Remote_Jobs.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e39d-166">-Authentication</span><span class="sxs-lookup"><span data-stu-id="5e39d-166">-Authentication</span></span>

<span data-ttu-id="5e39d-167">指定要與 WMI 連線搭配使用的驗證等級。</span><span class="sxs-lookup"><span data-stu-id="5e39d-167">Specifies the authentication level to be used with the WMI connection.</span></span>
<span data-ttu-id="5e39d-168">有效值為：</span><span class="sxs-lookup"><span data-stu-id="5e39d-168">Valid values are:</span></span>

- <span data-ttu-id="5e39d-169">-1：Unchanged</span><span class="sxs-lookup"><span data-stu-id="5e39d-169">-1: Unchanged</span></span>
- <span data-ttu-id="5e39d-170">0：Default</span><span class="sxs-lookup"><span data-stu-id="5e39d-170">0: Default</span></span>
- <span data-ttu-id="5e39d-171">1：None (不執行驗證。)</span><span class="sxs-lookup"><span data-stu-id="5e39d-171">1: None (No authentication in performed.)</span></span>
- <span data-ttu-id="5e39d-172">2：Connect (只有當用戶端與應用程式建立關係時，才執行驗證。)</span><span class="sxs-lookup"><span data-stu-id="5e39d-172">2: Connect (Authentication is performed only when the client establishes a relationship with the application.)</span></span>
- <span data-ttu-id="5e39d-173">3：Call (只有在每次呼叫的開始並當應用程式接收要求時，才執行驗證。)</span><span class="sxs-lookup"><span data-stu-id="5e39d-173">3: Call (Authentication is performed only at the beginning of each call when the application receives the request.)</span></span>
- <span data-ttu-id="5e39d-174">4：Packet (在從用戶端接收的所有資料上執行驗證。)</span><span class="sxs-lookup"><span data-stu-id="5e39d-174">4: Packet (Authentication is performed on all the data that is received from the client.)</span></span>
- <span data-ttu-id="5e39d-175">5： PacketIntegrity (在用戶端和應用程式之間傳送的所有資料都會經過驗證和驗證。 ) </span><span class="sxs-lookup"><span data-stu-id="5e39d-175">5: PacketIntegrity (All the data that is transferred between the client and the application is authenticated and verified.)</span></span>
- <span data-ttu-id="5e39d-176">6：PacketPrivacy (使用其他驗證等級的屬性，並加密所有資料。)</span><span class="sxs-lookup"><span data-stu-id="5e39d-176">6: PacketPrivacy (The properties of the other authentication levels are used, and all the data is encrypted.)</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e39d-177">-Authority</span><span class="sxs-lookup"><span data-stu-id="5e39d-177">-Authority</span></span>

<span data-ttu-id="5e39d-178">指定用來驗證 WMI 連線的授權單位。</span><span class="sxs-lookup"><span data-stu-id="5e39d-178">Specifies the authority to use to authenticate the WMI connection.</span></span> <span data-ttu-id="5e39d-179">您可以指定標準 NTLM 或 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="5e39d-179">You can specify standard NTLM or Kerberos authentication.</span></span> <span data-ttu-id="5e39d-180">若要使用 NTLM，請將授權單位設定為 `ntlmdomain:<DomainName>` ，其中會 `<DomainName>` 識別有效的 NTLM 功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="5e39d-180">To use NTLM, set the authority setting to `ntlmdomain:<DomainName>`, where `<DomainName>` identifies a valid NTLM domain name.</span></span> <span data-ttu-id="5e39d-181">若要使用 Kerberos，請指定 `kerberos:<DomainName>\<ServerName>` 。</span><span class="sxs-lookup"><span data-stu-id="5e39d-181">To use Kerberos, specify `kerberos:<DomainName>\<ServerName>`.</span></span> <span data-ttu-id="5e39d-182">當您連線到本機電腦時，不能包含授權單位設定。</span><span class="sxs-lookup"><span data-stu-id="5e39d-182">You cannot include the authority setting when you connect to the local computer.</span></span>

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

### <span data-ttu-id="5e39d-183">-Class</span><span class="sxs-lookup"><span data-stu-id="5e39d-183">-Class</span></span>

<span data-ttu-id="5e39d-184">指定 WMI 類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="5e39d-184">Specifies the name of a WMI class.</span></span> <span data-ttu-id="5e39d-185">使用此參數時，Cmdlet 會抓取 WMI 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5e39d-185">When this parameter is used, the cmdlet retrieves instances of the WMI class.</span></span>

```yaml
Type: System.String
Parameter Sets: query, list
Aliases: ClassName

Required: True (query), False (list)
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e39d-186">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="5e39d-186">-ComputerName</span></span>

<span data-ttu-id="5e39d-187">指定管理操作的目標電腦。</span><span class="sxs-lookup"><span data-stu-id="5e39d-187">Specifies the target computer for the management operation.</span></span> <span data-ttu-id="5e39d-188">輸入 (FQDN) 、NetBIOS 名稱或 IP 位址的完整功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="5e39d-188">Enter a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="5e39d-189">當遠端電腦與本機電腦位於不同網域，則必須使用完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="5e39d-189">When the remote computer is in a different domain than the local computer, the fully qualified domain name is required.</span></span>

<span data-ttu-id="5e39d-190">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="5e39d-190">The default is the local computer.</span></span> <span data-ttu-id="5e39d-191">若要指定本機電腦 (例如在一份電腦名稱清單中)，請使用 "localhost"、本機電腦名稱或句點 (.)。</span><span class="sxs-lookup"><span data-stu-id="5e39d-191">To specify the local computer, such as in a list of computer names, use "localhost", the local computer name, or a dot (.).</span></span>

<span data-ttu-id="5e39d-192">此參數不必依賴使用 WS-Management 的 Windows PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="5e39d-192">This parameter does not rely on Windows PowerShell remoting, which uses WS-Management.</span></span> <span data-ttu-id="5e39d-193">**ComputerName** `Get-WmiObject` 即使您的電腦未設定為執行遠端命令 WS-Management，您也可以使用 ComputerName 參數。</span><span class="sxs-lookup"><span data-stu-id="5e39d-193">You can use the **ComputerName** parameter of `Get-WmiObject` even if your computer is not configured to run WS-Management remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e39d-194">-Credential</span><span class="sxs-lookup"><span data-stu-id="5e39d-194">-Credential</span></span>

<span data-ttu-id="5e39d-195">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="5e39d-195">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="5e39d-196">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="5e39d-196">The default is the current user.</span></span> <span data-ttu-id="5e39d-197">輸入使用者名稱，例如 "User01"、"Domain01\User01" 或 User@Contoso.com 。</span><span class="sxs-lookup"><span data-stu-id="5e39d-197">Type a user name, such as "User01", "Domain01\User01", or User@Contoso.com.</span></span> <span data-ttu-id="5e39d-198">或者，輸入 **PSCredential** 物件，例如 Cmdlet 所傳回的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="5e39d-198">Or, enter a **PSCredential** object, such as an object that is returned by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="5e39d-199">當您輸入使用者名稱時，會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="5e39d-199">When you type a user name, you are prompted for a password.</span></span> <span data-ttu-id="5e39d-200">以本機電腦為目標時，無法使用認證。</span><span class="sxs-lookup"><span data-stu-id="5e39d-200">Credentials cannot be used when targeting the local computer.</span></span>

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

### <span data-ttu-id="5e39d-201">-DirectRead</span><span class="sxs-lookup"><span data-stu-id="5e39d-201">-DirectRead</span></span>

<span data-ttu-id="5e39d-202">指定是否不論其基底類別或衍生類別，都針對指定類別要求直接存取 WMI 提供者。</span><span class="sxs-lookup"><span data-stu-id="5e39d-202">Specifies whether direct access to the WMI provider is requested for the specified class without any regard to its base class or to its derived classes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: query, WQLQuery
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e39d-203">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="5e39d-203">-EnableAllPrivileges</span></span>

<span data-ttu-id="5e39d-204">在命令進行 WMI 呼叫之前，先啟用目前使用者的所有權限。</span><span class="sxs-lookup"><span data-stu-id="5e39d-204">Enables all the privileges of the current user before the command makes the WMI call.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e39d-205">-Filter</span><span class="sxs-lookup"><span data-stu-id="5e39d-205">-Filter</span></span>

<span data-ttu-id="5e39d-206">指定 **Where** 子句做為篩選。</span><span class="sxs-lookup"><span data-stu-id="5e39d-206">Specifies a **Where** clause to use as a filter.</span></span> <span data-ttu-id="5e39d-207">使用 WMI 查詢語言 (WQL) 的語法。</span><span class="sxs-lookup"><span data-stu-id="5e39d-207">Uses the syntax of the WMI Query Language (WQL).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e39d-208">不要在參數值中包含 **Where** 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="5e39d-208">Do not include the **Where** keyword in the value of the parameter.</span></span> <span data-ttu-id="5e39d-209">例如，下列命令只會傳回具有 'c:' **DeviceID** 的邏輯磁碟，以及具有名稱 'WinRM' 且沒有使用 **Where** 關鍵字的服務。</span><span class="sxs-lookup"><span data-stu-id="5e39d-209">For example, the following commands return only the logical disks that have a **DeviceID** of 'c:' and services that have the name 'WinRM' without using the **Where** keyword.</span></span>

`Get-WmiObject Win32_LogicalDisk -filter "DeviceID = 'c:' "`

`Get-WmiObject win32_service -filter "name='WinRM'"`

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e39d-210">-Impersonation</span><span class="sxs-lookup"><span data-stu-id="5e39d-210">-Impersonation</span></span>

<span data-ttu-id="5e39d-211">指定要使用的模擬等級。</span><span class="sxs-lookup"><span data-stu-id="5e39d-211">Specifies the impersonation level to use.</span></span>

<span data-ttu-id="5e39d-212">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="5e39d-212">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5e39d-213">0：預設值。</span><span class="sxs-lookup"><span data-stu-id="5e39d-213">0: Default.</span></span> <span data-ttu-id="5e39d-214">讀取本機登錄以取得預設的模擬層級。</span><span class="sxs-lookup"><span data-stu-id="5e39d-214">Reads the local registry for the default impersonation level.</span></span> <span data-ttu-id="5e39d-215">預設值通常會設定為 [模擬 **]。**</span><span class="sxs-lookup"><span data-stu-id="5e39d-215">The default is usually set to **Impersonate** .</span></span>
- <span data-ttu-id="5e39d-216">1： Anonymous。</span><span class="sxs-lookup"><span data-stu-id="5e39d-216">1: Anonymous.</span></span> <span data-ttu-id="5e39d-217">隱藏呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="5e39d-217">Hides the credentials of the caller.</span></span>
- <span data-ttu-id="5e39d-218">2：識別。</span><span class="sxs-lookup"><span data-stu-id="5e39d-218">2: Identify.</span></span> <span data-ttu-id="5e39d-219">允許物件查詢呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="5e39d-219">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="5e39d-220">3：模擬。</span><span class="sxs-lookup"><span data-stu-id="5e39d-220">3: Impersonate.</span></span> <span data-ttu-id="5e39d-221">允許物件使用呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="5e39d-221">Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="5e39d-222">4：委派。</span><span class="sxs-lookup"><span data-stu-id="5e39d-222">4: Delegate.</span></span> <span data-ttu-id="5e39d-223">允許物件許可其他物件使用呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="5e39d-223">Allows objects to permit other objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e39d-224">-List</span><span class="sxs-lookup"><span data-stu-id="5e39d-224">-List</span></span>

<span data-ttu-id="5e39d-225">取得 WMI 存放庫命名空間 (由 **Namespace** 參數指定) 中 WMI 類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="5e39d-225">Gets the names of the WMI classes in the WMI repository namespace that is specified by the **Namespace** parameter.</span></span>

<span data-ttu-id="5e39d-226">如果您指定 **List** 參數，而不是 **命名空間** 參數，則 `Get-WmiObject` 預設會使用 **Root\Cimv2** 命名空間。</span><span class="sxs-lookup"><span data-stu-id="5e39d-226">If you specify the **List** parameter, but not the **Namespace** parameter, `Get-WmiObject` uses the **Root\Cimv2** namespace by default.</span></span> <span data-ttu-id="5e39d-227">此 Cmdlet 不會使用登錄機碼中的 **預設命名空間** 登錄專案 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WBEM\Scripting` 來決定預設的命名空間。</span><span class="sxs-lookup"><span data-stu-id="5e39d-227">This cmdlet does not use the **Default Namespace** registry entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WBEM\Scripting` registry key to determine the default namespace.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e39d-228">-Locale</span><span class="sxs-lookup"><span data-stu-id="5e39d-228">-Locale</span></span>

<span data-ttu-id="5e39d-229">指定 WMI 物件的慣用地區設定。</span><span class="sxs-lookup"><span data-stu-id="5e39d-229">Specifies the preferred locale for WMI objects.</span></span>
<span data-ttu-id="5e39d-230">輸入 MS_\<LCID\> 格式的值。</span><span class="sxs-lookup"><span data-stu-id="5e39d-230">Enter a value in MS_\<LCID\> format.</span></span>

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

### <span data-ttu-id="5e39d-231">-Namespace</span><span class="sxs-lookup"><span data-stu-id="5e39d-231">-Namespace</span></span>

<span data-ttu-id="5e39d-232">搭配 **Class** 參數使用時， **Namespace** 參數會指定 WMI 存放庫命名空間 (指定的 WMI 類別所在)。</span><span class="sxs-lookup"><span data-stu-id="5e39d-232">When used with the **Class** parameter, the **Namespace** parameter specifies the WMI repository namespace where the specified WMI class is located.</span></span> <span data-ttu-id="5e39d-233">搭配 **List** 參數使用時，它會指定收集 WMI 類別資訊的命名空間。</span><span class="sxs-lookup"><span data-stu-id="5e39d-233">When used with the **List** parameter, it specifies the namespace from which to gather WMI class information.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e39d-234">-Property</span><span class="sxs-lookup"><span data-stu-id="5e39d-234">-Property</span></span>

<span data-ttu-id="5e39d-235">指定此 Cmdlet 從中取得資訊的 WMI 類別屬性。</span><span class="sxs-lookup"><span data-stu-id="5e39d-235">Specifies the WMI class properties that this cmdlet gets information from.</span></span> <span data-ttu-id="5e39d-236">輸入屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="5e39d-236">Enter the property names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: query
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e39d-237">-Query</span><span class="sxs-lookup"><span data-stu-id="5e39d-237">-Query</span></span>

<span data-ttu-id="5e39d-238">執行指定的 WMI 查詢語言 (WQL) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5e39d-238">Runs the specified WMI Query Language (WQL) statement.</span></span> <span data-ttu-id="5e39d-239">這個參數不支援事件查詢。</span><span class="sxs-lookup"><span data-stu-id="5e39d-239">This parameter does not support event queries.</span></span>

```yaml
Type: System.String
Parameter Sets: WQLQuery
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e39d-240">-Recurse</span><span class="sxs-lookup"><span data-stu-id="5e39d-240">-Recurse</span></span>

<span data-ttu-id="5e39d-241">在目前的命名空間及所有其他命名空間，搜尋 **Class** 參數所指定的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="5e39d-241">Searches the current namespace and all other namespaces for the class name that is specified by the **Class** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e39d-242">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="5e39d-242">-ThrottleLimit</span></span>

<span data-ttu-id="5e39d-243">指定 WMI 作業能同時執行的數目上限。</span><span class="sxs-lookup"><span data-stu-id="5e39d-243">Specifies the maximum number of WMI operations that can be executed simultaneously.</span></span> <span data-ttu-id="5e39d-244">只有當命令中使用 **AsJob** 參數時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="5e39d-244">This parameter is valid only when the **AsJob** parameter is used in the command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e39d-245">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5e39d-245">CommonParameters</span></span>

<span data-ttu-id="5e39d-246">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5e39d-246">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5e39d-247">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="5e39d-247">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5e39d-248">輸入</span><span class="sxs-lookup"><span data-stu-id="5e39d-248">INPUTS</span></span>

### <span data-ttu-id="5e39d-249">無</span><span class="sxs-lookup"><span data-stu-id="5e39d-249">None</span></span>

<span data-ttu-id="5e39d-250">您無法透過管道傳送輸入 `Get-WmiObject` 。</span><span class="sxs-lookup"><span data-stu-id="5e39d-250">You cannot pipe input to `Get-WmiObject`.</span></span>

## <span data-ttu-id="5e39d-251">輸出</span><span class="sxs-lookup"><span data-stu-id="5e39d-251">OUTPUTS</span></span>

### <span data-ttu-id="5e39d-252">PSObject 或 System.management.automation.remotingjob。</span><span class="sxs-lookup"><span data-stu-id="5e39d-252">PSObject or System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="5e39d-253">使用 **AsJob** 參數時，此 Cmdlet 會傳回工作物件。</span><span class="sxs-lookup"><span data-stu-id="5e39d-253">When you use the **AsJob** parameter, the cmdlet returns a job object.</span></span> <span data-ttu-id="5e39d-254">否則，傳回的物件 `Get-WmiObject` 取決於 **類別** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="5e39d-254">Otherwise, the object that `Get-WmiObject` returns depends on the value of the **Class** parameter.</span></span>

## <span data-ttu-id="5e39d-255">注意</span><span class="sxs-lookup"><span data-stu-id="5e39d-255">NOTES</span></span>

<span data-ttu-id="5e39d-256">若要在遠端電腦存取 WMI 資訊，執行 Cmdlet 的帳戶必須是遠端電腦上本機 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="5e39d-256">To access WMI information on a remote computer, the cmdlet must run under an account that is a member of the local administrators group on the remote computer.</span></span> <span data-ttu-id="5e39d-257">或者，可以變更遠端存放庫的 WMI 命名空間上的預設存取控制，來授與其他帳戶存取權限。</span><span class="sxs-lookup"><span data-stu-id="5e39d-257">Or, the default access control on the WMI namespace of the remote repository can be changed to give access rights to other accounts.</span></span>

<span data-ttu-id="5e39d-258">預設只會顯示 WMI 類別的某些屬性。</span><span class="sxs-lookup"><span data-stu-id="5e39d-258">Only some of the properties of each WMI class are displayed by default.</span></span> <span data-ttu-id="5e39d-259">每個 WMI 類別會顯示的屬性集指定於 Types.ps1xml 設定檔中。</span><span class="sxs-lookup"><span data-stu-id="5e39d-259">The set of properties that is displayed for each WMI class is specified in the Types.ps1xml configuration file.</span></span> <span data-ttu-id="5e39d-260">若要取得 WMI 物件的所有屬性，請使用 `Get-Member` 或 `Format-List` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5e39d-260">To get all properties of a WMI object, use the `Get-Member` or `Format-List` cmdlets.</span></span>

## <span data-ttu-id="5e39d-261">相關連結</span><span class="sxs-lookup"><span data-stu-id="5e39d-261">RELATED LINKS</span></span>

[<span data-ttu-id="5e39d-262">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="5e39d-262">Invoke-WmiMethod</span></span>](Invoke-WmiMethod.md)

[<span data-ttu-id="5e39d-263">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="5e39d-263">Remove-WmiObject</span></span>](Remove-WmiObject.md)

[<span data-ttu-id="5e39d-264">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="5e39d-264">Set-WmiInstance</span></span>](Set-WmiInstance.md)

[<span data-ttu-id="5e39d-265">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="5e39d-265">Get-WSManInstance</span></span>](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[<span data-ttu-id="5e39d-266">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="5e39d-266">Invoke-WSManAction</span></span>](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[<span data-ttu-id="5e39d-267">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="5e39d-267">New-WSManInstance</span></span>](../Microsoft.WsMan.Management/New-WSManInstance.md)

[<span data-ttu-id="5e39d-268">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="5e39d-268">Remove-WSManInstance</span></span>](../Microsoft.WsMan.Management/Remove-WSManInstance.md)
