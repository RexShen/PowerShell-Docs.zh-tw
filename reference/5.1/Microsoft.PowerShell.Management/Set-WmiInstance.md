---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-wmiinstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WmiInstance
ms.openlocfilehash: 03288a2ffbef416937b2c92a7d08a5aed49ffb43
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203492"
---
# <span data-ttu-id="a571c-103">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="a571c-103">Set-WmiInstance</span></span>

## <span data-ttu-id="a571c-104">概要</span><span class="sxs-lookup"><span data-stu-id="a571c-104">SYNOPSIS</span></span>
<span data-ttu-id="a571c-105">建立或更新現有 Windows Management Instrumentation (WMI) 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a571c-105">Creates or updates an instance of an existing Windows Management Instrumentation (WMI) class.</span></span>

## <span data-ttu-id="a571c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a571c-106">SYNTAX</span></span>

### <span data-ttu-id="a571c-107">class (預設值)</span><span class="sxs-lookup"><span data-stu-id="a571c-107">class (Default)</span></span>

```
Set-WmiInstance [-Class] <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a571c-108">物件 (object)</span><span class="sxs-lookup"><span data-stu-id="a571c-108">object</span></span>

```
Set-WmiInstance -InputObject <ManagementObject> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a571c-109">path</span><span class="sxs-lookup"><span data-stu-id="a571c-109">path</span></span>

```
Set-WmiInstance -Path <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a571c-110">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="a571c-110">WQLQuery</span></span>

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a571c-111">查詢</span><span class="sxs-lookup"><span data-stu-id="a571c-111">query</span></span>

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a571c-112">list</span><span class="sxs-lookup"><span data-stu-id="a571c-112">list</span></span>

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a571c-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a571c-113">DESCRIPTION</span></span>
<span data-ttu-id="a571c-114">`Set-WmiInstance`Cmdlet 會建立或更新現有 Windows Management Instrumentation (WMI) 類別的實例。</span><span class="sxs-lookup"><span data-stu-id="a571c-114">The `Set-WmiInstance` cmdlet creates or updates an instance of an existing Windows Management Instrumentation (WMI) class.</span></span>
<span data-ttu-id="a571c-115">建立或更新的執行個體會寫入 WMI 存放庫中。</span><span class="sxs-lookup"><span data-stu-id="a571c-115">The created or updated instance is written to the WMI repository.</span></span>

<span data-ttu-id="a571c-116">已導入 Windows PowerShell 3.0 的新 CIM Cmdlet 可執行與 WMI Cmdlet 相同的工作。</span><span class="sxs-lookup"><span data-stu-id="a571c-116">New CIM cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span>
<span data-ttu-id="a571c-117">CIM Cmdlet 符合 WS-Management (WSMan) 標準，以及通用訊息模型 (CIM) standard。</span><span class="sxs-lookup"><span data-stu-id="a571c-117">The CIM cmdlets comply with WS-Management (WSMan) standards and with the Common Information Model (CIM) standard.</span></span>
<span data-ttu-id="a571c-118">這可讓 Cmdlet 使用相同的技術來管理 Windows 電腦和執行其他作業系統的電腦。</span><span class="sxs-lookup"><span data-stu-id="a571c-118">this enables cmdlets to use the same techniques to manage Windows-based computers and those running other operating systems.</span></span>
<span data-ttu-id="a571c-119">請 `Set-WmiInstance` 考慮使用 [CimInstance](/powershell/module/cimcmdlets/set-ciminstance) 或 [CimInstance](/powershell/module/cimcmdlets/new-ciminstance) Cmdlet，而不是使用。</span><span class="sxs-lookup"><span data-stu-id="a571c-119">Instead of using `Set-WmiInstance`, consider using the [Set-CimInstance](/powershell/module/cimcmdlets/set-ciminstance) or [New-CimInstance](/powershell/module/cimcmdlets/new-ciminstance) cmdlets.</span></span>

## <span data-ttu-id="a571c-120">範例</span><span class="sxs-lookup"><span data-stu-id="a571c-120">EXAMPLES</span></span>

### <span data-ttu-id="a571c-121">範例1：設定 WMI 記錄層級</span><span class="sxs-lookup"><span data-stu-id="a571c-121">Example 1: Set WMI logging level</span></span>

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2}
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
```

<span data-ttu-id="a571c-122">這個命令會將 WMI 記錄層級設定為 2。</span><span class="sxs-lookup"><span data-stu-id="a571c-122">This command sets the WMI logging level to 2.</span></span>
<span data-ttu-id="a571c-123">此命令會在引數參數中傳遞要設定的屬性，並將值一起視為值組。</span><span class="sxs-lookup"><span data-stu-id="a571c-123">The command passes the property to be set and the value, together considered a value pair, in the argument parameter.</span></span>
<span data-ttu-id="a571c-124">此參數接受一個由 @{property = value} 建構所定義的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="a571c-124">The parameter takes a hash table that is defined by the @{property = value} construction.</span></span>
<span data-ttu-id="a571c-125">傳回的類別資訊會反映新的值。</span><span class="sxs-lookup"><span data-stu-id="a571c-125">The class information that is returned reflects the new value.</span></span>

### <span data-ttu-id="a571c-126">範例2：建立環境變數及其值</span><span class="sxs-lookup"><span data-stu-id="a571c-126">Example 2: Create an environment variable and its value</span></span>

```
PS C:\> Set-WmiInstance -Class win32_environment -Argument @{Name="testvar";VariableValue="testvalue";UserName="<SYSTEM>"}
__GENUS          : 2
__CLASS          : Win32_Environment
__SUPERCLASS     : CIM_SystemResource
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Environment.Name="testvar",UserName="<SYSTEM>"
__PROPERTY_COUNT : 8
__DERIVATION     : {CIM_SystemResource, CIM_LogicalElement, CIM_ManagedSystemElement}
__SERVER         : SYSTEM01
__NAMESPACE      : root\cimv2
__PATH           : \\SYSTEM01\root\cimv2:Win32_Environment.Name="testvar",UserName="<SYSTEM>"
Caption          : <SYSTEM>\testvar
Description      : <SYSTEM>\testvar
InstallDate      :
Name             : testvar
Status           : OK
SystemVariable   : True
UserName         : <SYSTEM>
VariableValue    : testvalue
```

<span data-ttu-id="a571c-127">此命令會建立 testvar 環境變數，其值為 testvalue。</span><span class="sxs-lookup"><span data-stu-id="a571c-127">This command creates the testvar environment variable that has the value testvalue.</span></span>
<span data-ttu-id="a571c-128">它是藉由建立 **Win32_Environment** WMI 類別的新實例來完成這項工作。</span><span class="sxs-lookup"><span data-stu-id="a571c-128">It does this by creating a new instance of the **Win32_Environment** WMI class.</span></span>
<span data-ttu-id="a571c-129">此操作需要適當的認證，而且您可能必須重新開機 Windows PowerShell，才能看到新的環境變數。</span><span class="sxs-lookup"><span data-stu-id="a571c-129">This operation requires appropriate credentials and that you may have to restart Windows PowerShell to see the new environment variable.</span></span>

### <span data-ttu-id="a571c-130">範例3：設定數部遠端電腦的 WMI 記錄層級</span><span class="sxs-lookup"><span data-stu-id="a571c-130">Example 3: Set WMI logging level for several remote computers</span></span>

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2} -Computername "system01", "system02", "system03"
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
...
```

<span data-ttu-id="a571c-131">這個命令會將 WMI 記錄層級設定為 2。</span><span class="sxs-lookup"><span data-stu-id="a571c-131">This command sets the WMI logging level to 2.</span></span>
<span data-ttu-id="a571c-132">此命令會在引數參數中傳遞要設定的屬性，並將值一起視為值組。</span><span class="sxs-lookup"><span data-stu-id="a571c-132">The command passes the property to be set and the value, together considered a value pair, in the argument parameter.</span></span>
<span data-ttu-id="a571c-133">此參數接受一個由 @{property = value} 建構所定義的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="a571c-133">The parameter takes a hash table that is defined by the @{property = value} construction.</span></span>
<span data-ttu-id="a571c-134">傳回的類別資訊會反映新的值。</span><span class="sxs-lookup"><span data-stu-id="a571c-134">The returned class information reflects the new value.</span></span>

## <span data-ttu-id="a571c-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a571c-135">PARAMETERS</span></span>

### <span data-ttu-id="a571c-136">-Arguments</span><span class="sxs-lookup"><span data-stu-id="a571c-136">-Arguments</span></span>
<span data-ttu-id="a571c-137">指定要變更之屬性的名稱和該屬性的新值。</span><span class="sxs-lookup"><span data-stu-id="a571c-137">Specifies the name of the property to be changed and the new value for that property.</span></span>
<span data-ttu-id="a571c-138">名稱和值必須是成對的名稱和值。</span><span class="sxs-lookup"><span data-stu-id="a571c-138">The name and value must be a name-value pair.</span></span>
<span data-ttu-id="a571c-139">名稱/值組會以雜湊表的形式在命令列上傳遞。</span><span class="sxs-lookup"><span data-stu-id="a571c-139">The name-value pair is passed on the command line as a hash table.</span></span>
<span data-ttu-id="a571c-140">例如：</span><span class="sxs-lookup"><span data-stu-id="a571c-140">For example:</span></span>

`@{Setting1=1; Setting2=5; Setting3="test"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: class, object, path
Aliases: Args, Property

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a571c-141">-AsJob</span><span class="sxs-lookup"><span data-stu-id="a571c-141">-AsJob</span></span>
<span data-ttu-id="a571c-142">表示這個 cmdket 會以背景工作的形式執行。</span><span class="sxs-lookup"><span data-stu-id="a571c-142">Indicates that this cmdket runs as a background job.</span></span>
<span data-ttu-id="a571c-143">使用此參數執行需要很長時間才能完成的命令。</span><span class="sxs-lookup"><span data-stu-id="a571c-143">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="a571c-144">當您指定 *AsJob* 參數時，此命令會傳回代表背景工作的物件，然後顯示命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="a571c-144">When you specify the *AsJob* parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span>
<span data-ttu-id="a571c-145">工作完成後，您可以繼續在工作階段中工作。</span><span class="sxs-lookup"><span data-stu-id="a571c-145">You can continue to work in the session while the job finishes.</span></span>
<span data-ttu-id="a571c-146">如果遠端電腦使用 **set-wmiinstance** ，則會在本機電腦上建立工作，而來自遠端電腦的結果則會自動傳回到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="a571c-146">If **Set-WmiInstance** is used for a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="a571c-147">若要管理工作，請使用包含 **作業** 名詞 ( **工作 Cmdlet) 的 Cmdlet。**</span><span class="sxs-lookup"><span data-stu-id="a571c-147">To manage the job, use the cmdlets that contain the **Job** noun (the **Job** cmdlets).</span></span>
<span data-ttu-id="a571c-148">若要取得工作結果，請使用 Receive-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a571c-148">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="a571c-149">若要將這個參數與遠端電腦搭配使用，必須設定本機和遠端電腦以進行遠端處理。</span><span class="sxs-lookup"><span data-stu-id="a571c-149">To use this parameter together with remote computers, the local and remote computers must be configured for remoting.</span></span>
<span data-ttu-id="a571c-150">此外，您必須使用 Windows Vista 和更新版本的 Windows 作業系統中的 [以系統管理員身分執行] 選項來啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a571c-150">Additionally, you must start Windows PowerShell by using the Run as administrator option in Windows Vista and later versions of the Windows operating system.</span></span>
<span data-ttu-id="a571c-151">如需詳細資訊，請參閱 about_Remote_Requirements。</span><span class="sxs-lookup"><span data-stu-id="a571c-151">For more information, see about_Remote_Requirements.</span></span>

<span data-ttu-id="a571c-152">如需有關 Windows PowerShell 背景工作的詳細資訊，請參閱 about_Jobs 和 about_Remote_Jobs。</span><span class="sxs-lookup"><span data-stu-id="a571c-152">For more information about Windows PowerShell background jobs, see about_Jobs and about_Remote_Jobs.</span></span>

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

### <span data-ttu-id="a571c-153">-Authentication</span><span class="sxs-lookup"><span data-stu-id="a571c-153">-Authentication</span></span>
<span data-ttu-id="a571c-154">指定必須搭配 WMI 連接使用的驗證層級。</span><span class="sxs-lookup"><span data-stu-id="a571c-154">Specifies the authentication level that must be used with the WMI connection.</span></span>
<span data-ttu-id="a571c-155">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="a571c-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a571c-156">-1：未變更。</span><span class="sxs-lookup"><span data-stu-id="a571c-156">-1: Unchanged.</span></span>
- <span data-ttu-id="a571c-157">0：預設值。</span><span class="sxs-lookup"><span data-stu-id="a571c-157">0: Default.</span></span>
- <span data-ttu-id="a571c-158">1：無。</span><span class="sxs-lookup"><span data-stu-id="a571c-158">1: None.</span></span>
<span data-ttu-id="a571c-159">未執行任何驗證。</span><span class="sxs-lookup"><span data-stu-id="a571c-159">No authentication in performed.</span></span>
- <span data-ttu-id="a571c-160">2：連接。</span><span class="sxs-lookup"><span data-stu-id="a571c-160">2: Connect.</span></span>
<span data-ttu-id="a571c-161">只有當用戶端與應用程式建立關聯性時，才會執行驗證。</span><span class="sxs-lookup"><span data-stu-id="a571c-161">Authentication is performed only when the client establishes a relationship with the application.</span></span>
- <span data-ttu-id="a571c-162">3：呼叫。</span><span class="sxs-lookup"><span data-stu-id="a571c-162">3: Call.</span></span>
<span data-ttu-id="a571c-163">只有當應用程式收到要求時，才會在每次呼叫開始時執行驗證。</span><span class="sxs-lookup"><span data-stu-id="a571c-163">Authentication is performed only at the start of each call when the application receives the request.</span></span>
- <span data-ttu-id="a571c-164">4：封包。</span><span class="sxs-lookup"><span data-stu-id="a571c-164">4: Packet.</span></span>
<span data-ttu-id="a571c-165">會在從用戶端接收的所有資料上執行驗證。</span><span class="sxs-lookup"><span data-stu-id="a571c-165">Authentication is performed on all the data that is received from the client.</span></span>
- <span data-ttu-id="a571c-166">5： PacketIntegrity。</span><span class="sxs-lookup"><span data-stu-id="a571c-166">5: PacketIntegrity.</span></span>
<span data-ttu-id="a571c-167">在用戶端與應用程式之間傳輸的所有資料都會經過驗證和驗證。</span><span class="sxs-lookup"><span data-stu-id="a571c-167">All the data that is transferred between the client and the application is authenticated and verified.</span></span>
- <span data-ttu-id="a571c-168">6： PacketPrivacy。</span><span class="sxs-lookup"><span data-stu-id="a571c-168">6: PacketPrivacy.</span></span>
<span data-ttu-id="a571c-169">系統會使用其他驗證層級的屬性，並加密所有資料。</span><span class="sxs-lookup"><span data-stu-id="a571c-169">The properties of the other authentication levels are used, and all the data is encrypted.</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a571c-170">-Authority</span><span class="sxs-lookup"><span data-stu-id="a571c-170">-Authority</span></span>
<span data-ttu-id="a571c-171">指定用來驗證 WMI 連線的授權單位。</span><span class="sxs-lookup"><span data-stu-id="a571c-171">Specifies the authority to use to authenticate the WMI connection.</span></span>
<span data-ttu-id="a571c-172">您可以指定標準 NTLM 或 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="a571c-172">You can specify standard NTLM or Kerberos authentication.</span></span>
<span data-ttu-id="a571c-173">若要使用 NTLM，請將授權單位設定為 "ntlmdomain:\<DomainName\>"，其中 \<DomainName\> 識別有效的 NTLM 網域名稱。</span><span class="sxs-lookup"><span data-stu-id="a571c-173">To use NTLM, set the authority setting to ntlmdomain:\<DomainName\>, where \<DomainName\> identifies a valid NTLM domain name.</span></span>
<span data-ttu-id="a571c-174">若要使用 Kerberos，請指定 kerberos： \<DomainName\> \\ \<ServerName\> 。</span><span class="sxs-lookup"><span data-stu-id="a571c-174">To use Kerberos, specify kerberos:\<DomainName\>\\\<ServerName\>.</span></span>
<span data-ttu-id="a571c-175">當您連線到本機電腦時，不能包含授權單位設定。</span><span class="sxs-lookup"><span data-stu-id="a571c-175">You cannot include the authority setting when you connect to the local computer.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a571c-176">-Class</span><span class="sxs-lookup"><span data-stu-id="a571c-176">-Class</span></span>
<span data-ttu-id="a571c-177">指定 WMI 類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="a571c-177">Specifies the name of a WMI class.</span></span>

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a571c-178">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="a571c-178">-ComputerName</span></span>
<span data-ttu-id="a571c-179">指定此 Cmdlet 執行所在的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="a571c-179">Specifies the name of the computer on which this cmdlet runs.</span></span>
<span data-ttu-id="a571c-180">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="a571c-180">The default is the local computer.</span></span>

<span data-ttu-id="a571c-181">請輸入一部或多部電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="a571c-181">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more computers.</span></span>
<span data-ttu-id="a571c-182">若要指定本機電腦，請輸入電腦名稱、句點 (.)，或者 localhost。</span><span class="sxs-lookup"><span data-stu-id="a571c-182">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="a571c-183">此參數不必依賴 Windows PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="a571c-183">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="a571c-184">即使您的電腦未設定為執行遠端命令，您仍然可以使用 *ComputerName* 參數。</span><span class="sxs-lookup"><span data-stu-id="a571c-184">You can use the *ComputerName* parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: class, path, WQLQuery, query, list
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a571c-185">-Credential</span><span class="sxs-lookup"><span data-stu-id="a571c-185">-Credential</span></span>
<span data-ttu-id="a571c-186">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a571c-186">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="a571c-187">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="a571c-187">The default is the current user.</span></span>

<span data-ttu-id="a571c-188">輸入使用者名稱，例如 User01 或 Domain01\User01，或輸入 **PSCredential** 物件，例如 Get-Credential Cmdlet 產生的物件。</span><span class="sxs-lookup"><span data-stu-id="a571c-188">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="a571c-189">如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="a571c-189">If you type a user name, this cmdlet prompts for a password.</span></span>

<span data-ttu-id="a571c-190">隨 Windows PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="a571c-190">This parameter is not supported by any providers installed with parameter is not supported by any providers installed with Windows PowerShell.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a571c-191">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="a571c-191">-EnableAllPrivileges</span></span>
<span data-ttu-id="a571c-192">指出此 Cmdlet 會在進行 WMI 呼叫之前，先啟用目前使用者的擁有權限。</span><span class="sxs-lookup"><span data-stu-id="a571c-192">Indicates that this cmdlet enables all the permissions of the current user before the command it makes the WMI call.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a571c-193">-Impersonation</span><span class="sxs-lookup"><span data-stu-id="a571c-193">-Impersonation</span></span>
<span data-ttu-id="a571c-194">指定要使用的模擬等級。</span><span class="sxs-lookup"><span data-stu-id="a571c-194">Specifies the impersonation level to use.</span></span>
<span data-ttu-id="a571c-195">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="a571c-195">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a571c-196">0：預設值。</span><span class="sxs-lookup"><span data-stu-id="a571c-196">0: Default.</span></span>
<span data-ttu-id="a571c-197">讀取預設模擬層級的本機登錄，通常設定為3：模擬。</span><span class="sxs-lookup"><span data-stu-id="a571c-197">Reads the local registry for the default impersonation level, which is usually set to 3: Impersonate.</span></span>
- <span data-ttu-id="a571c-198">1： Anonymous。</span><span class="sxs-lookup"><span data-stu-id="a571c-198">1: Anonymous.</span></span>
<span data-ttu-id="a571c-199">隱藏呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="a571c-199">Hides the credentials of the caller.</span></span>
- <span data-ttu-id="a571c-200">2：識別。</span><span class="sxs-lookup"><span data-stu-id="a571c-200">2: Identify.</span></span>
<span data-ttu-id="a571c-201">允許物件查詢呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="a571c-201">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="a571c-202">3：模擬。</span><span class="sxs-lookup"><span data-stu-id="a571c-202">3: Impersonate.</span></span>
<span data-ttu-id="a571c-203">允許物件使用呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="a571c-203">Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="a571c-204">4：委派。</span><span class="sxs-lookup"><span data-stu-id="a571c-204">4: Delegate.</span></span>
<span data-ttu-id="a571c-205">允許物件許可其他物件使用呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="a571c-205">Allows objects to permit other objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a571c-206">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a571c-206">-InputObject</span></span>
<span data-ttu-id="a571c-207">指定要做為輸入使用的 **system.management.managementobject** 物件。</span><span class="sxs-lookup"><span data-stu-id="a571c-207">Specifies a **ManagementObject** object to use as input.</span></span>
<span data-ttu-id="a571c-208">使用這個參數時，會忽略所有其他參數（ *引數* 參數除外）。</span><span class="sxs-lookup"><span data-stu-id="a571c-208">When this parameter is used, all other parameters ,except the *Arguments* parameter, are ignored.</span></span>

```yaml
Type: System.Management.ManagementObject
Parameter Sets: object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a571c-209">-Locale</span><span class="sxs-lookup"><span data-stu-id="a571c-209">-Locale</span></span>
<span data-ttu-id="a571c-210">指定 WMI 物件的慣用地區設定。</span><span class="sxs-lookup"><span data-stu-id="a571c-210">Specifies the preferred locale for WMI objects.</span></span>
<span data-ttu-id="a571c-211">*地區* 設定參數是以慣用順序，以 MS_ 格式的陣列指定 \<LCID\> 。</span><span class="sxs-lookup"><span data-stu-id="a571c-211">The *Locale* parameter is specified in an array in the MS_\<LCID\> format in the preferred order.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a571c-212">-Namespace</span><span class="sxs-lookup"><span data-stu-id="a571c-212">-Namespace</span></span>
<span data-ttu-id="a571c-213">指定當與 *類別* 參數搭配使用時，參考的 wmi 類別所在的 wmi 存放庫命名空間。</span><span class="sxs-lookup"><span data-stu-id="a571c-213">Specifies the WMI repository namespace where the referenced WMI class is located when it is used with the *Class* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a571c-214">-Path</span><span class="sxs-lookup"><span data-stu-id="a571c-214">-Path</span></span>
<span data-ttu-id="a571c-215">指定您想要建立或更新之實例的 WMI 物件路徑。</span><span class="sxs-lookup"><span data-stu-id="a571c-215">Specifies a WMI object path of the instance that you want to create or update.</span></span>

```yaml
Type: System.String
Parameter Sets: path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a571c-216">-PutType</span><span class="sxs-lookup"><span data-stu-id="a571c-216">-PutType</span></span>
<span data-ttu-id="a571c-217">指出是否要建立或更新 WMI 實例。</span><span class="sxs-lookup"><span data-stu-id="a571c-217">Indicates whether to create or update the WMI instance.</span></span>
<span data-ttu-id="a571c-218">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="a571c-218">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a571c-219">UpdateOnly.</span><span class="sxs-lookup"><span data-stu-id="a571c-219">UpdateOnly.</span></span>
<span data-ttu-id="a571c-220">更新現有的 WMI 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a571c-220">Updates an existing WMI instance.</span></span>
- <span data-ttu-id="a571c-221">以.</span><span class="sxs-lookup"><span data-stu-id="a571c-221">CreateOnly.</span></span>
<span data-ttu-id="a571c-222">建立新的 WMI 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a571c-222">Creates a new WMI instance.</span></span>
- <span data-ttu-id="a571c-223">UpdateOrCreate.</span><span class="sxs-lookup"><span data-stu-id="a571c-223">UpdateOrCreate.</span></span>
<span data-ttu-id="a571c-224">如果 WMI 執行個體存在，就更新該執行個體，如果執行個體不存在，則建立新執行個體。</span><span class="sxs-lookup"><span data-stu-id="a571c-224">Updates the WMI instance if it exists or creates a new instance if an instance does not exist.</span></span>

```yaml
Type: System.Management.PutType
Parameter Sets: (All)
Aliases:
Accepted values: None, UpdateOnly, CreateOnly, UpdateOrCreate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a571c-225">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="a571c-225">-ThrottleLimit</span></span>
<span data-ttu-id="a571c-226">指定為執行此命令可建立的最大同時連線數。</span><span class="sxs-lookup"><span data-stu-id="a571c-226">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="a571c-227">此參數會與 *AsJob* 參數一起使用。</span><span class="sxs-lookup"><span data-stu-id="a571c-227">This parameter is used together with the *AsJob* parameter.</span></span>
<span data-ttu-id="a571c-228">節流限制僅適用於目前命令，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="a571c-228">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="a571c-229">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a571c-229">-Confirm</span></span>
<span data-ttu-id="a571c-230">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="a571c-230">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a571c-231">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a571c-231">-WhatIf</span></span>
<span data-ttu-id="a571c-232">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="a571c-232">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a571c-233">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="a571c-233">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a571c-234">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a571c-234">CommonParameters</span></span>
<span data-ttu-id="a571c-235">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a571c-235">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a571c-236">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a571c-236">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a571c-237">輸入</span><span class="sxs-lookup"><span data-stu-id="a571c-237">INPUTS</span></span>

### <span data-ttu-id="a571c-238">無</span><span class="sxs-lookup"><span data-stu-id="a571c-238">None</span></span>
<span data-ttu-id="a571c-239">此 Cmdlet 不接受輸入。</span><span class="sxs-lookup"><span data-stu-id="a571c-239">This cmdlet does not accept input.</span></span>

## <span data-ttu-id="a571c-240">輸出</span><span class="sxs-lookup"><span data-stu-id="a571c-240">OUTPUTS</span></span>

### <span data-ttu-id="a571c-241">無</span><span class="sxs-lookup"><span data-stu-id="a571c-241">None</span></span>
<span data-ttu-id="a571c-242">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="a571c-242">This cmdlet does not generate output.</span></span>

## <span data-ttu-id="a571c-243">注意</span><span class="sxs-lookup"><span data-stu-id="a571c-243">NOTES</span></span>

## <span data-ttu-id="a571c-244">相關連結</span><span class="sxs-lookup"><span data-stu-id="a571c-244">RELATED LINKS</span></span>

[<span data-ttu-id="a571c-245">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="a571c-245">Get-WmiObject</span></span>](Get-WmiObject.md)

[<span data-ttu-id="a571c-246">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="a571c-246">Invoke-WmiMethod</span></span>](Invoke-WmiMethod.md)

[<span data-ttu-id="a571c-247">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="a571c-247">Remove-WmiObject</span></span>](Remove-WmiObject.md)
