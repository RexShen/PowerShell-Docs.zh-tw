---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-wmimethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WmiMethod
ms.openlocfilehash: e9743488e86429e5cc3252162e51268a7978b79d
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "93205283"
---
# <span data-ttu-id="29afb-103">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="29afb-103">Invoke-WmiMethod</span></span>

## <span data-ttu-id="29afb-104">概要</span><span class="sxs-lookup"><span data-stu-id="29afb-104">SYNOPSIS</span></span>
<span data-ttu-id="29afb-105">呼叫 WMI 方法。</span><span class="sxs-lookup"><span data-stu-id="29afb-105">Calls WMI methods.</span></span>

## <span data-ttu-id="29afb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="29afb-106">SYNTAX</span></span>

### <span data-ttu-id="29afb-107">class (預設值)</span><span class="sxs-lookup"><span data-stu-id="29afb-107">class (Default)</span></span>

```
Invoke-WmiMethod [-Class] <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="29afb-108">物件 (object)</span><span class="sxs-lookup"><span data-stu-id="29afb-108">object</span></span>

```
Invoke-WmiMethod -InputObject <ManagementObject> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="29afb-109">path</span><span class="sxs-lookup"><span data-stu-id="29afb-109">path</span></span>

```
Invoke-WmiMethod -Path <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="29afb-110">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="29afb-110">WQLQuery</span></span>

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="29afb-111">查詢</span><span class="sxs-lookup"><span data-stu-id="29afb-111">query</span></span>

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="29afb-112">list</span><span class="sxs-lookup"><span data-stu-id="29afb-112">list</span></span>

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="29afb-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="29afb-113">DESCRIPTION</span></span>

<span data-ttu-id="29afb-114">`Invoke-WmiMethod`Cmdlet 會呼叫 WMI) 物件 (Windows Management Instrumentation 的方法。</span><span class="sxs-lookup"><span data-stu-id="29afb-114">The `Invoke-WmiMethod` cmdlet calls the methods of Windows Management Instrumentation (WMI) objects.</span></span>

<span data-ttu-id="29afb-115">在 Windows PowerShell 3.0 中引進的新通用訊息模型 (CIM) Cmdlet，會執行與 WMI Cmdlet 相同的工作。</span><span class="sxs-lookup"><span data-stu-id="29afb-115">New Common Information Model (CIM) cmdlets, introduced in Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span> <span data-ttu-id="29afb-116">CIM Cmdlet 符合 WS-Management (WSMan) 標準和 CIM 標準，可讓 Cmdlet 使用相同的技術來管理 Windows 電腦和執行其他作業系統的電腦。</span><span class="sxs-lookup"><span data-stu-id="29afb-116">The CIM cmdlets comply with WS-Management (WSMan) standards and with the CIM standard, which enables the cmdlets to use the same techniques to manage Windows computers and those running other operating systems.</span></span> <span data-ttu-id="29afb-117">請 `Invoke-WmiMethod` 考慮使用 [Invoke invoke-cimmethod](../cimcmdlets/invoke-cimmethod.md)，而不是使用。</span><span class="sxs-lookup"><span data-stu-id="29afb-117">Instead of using `Invoke-WmiMethod`, consider using [Invoke-CimMethod](../cimcmdlets/invoke-cimmethod.md).</span></span>

## <span data-ttu-id="29afb-118">範例</span><span class="sxs-lookup"><span data-stu-id="29afb-118">EXAMPLES</span></span>

### <span data-ttu-id="29afb-119">範例1：列出 WMI 物件的必要順序</span><span class="sxs-lookup"><span data-stu-id="29afb-119">Example 1: List the required order of WMI objects</span></span>

```powershell
([wmiclass]'Win32_Volume').GetMethodParameters('Format')
```

```Output
__GENUS           : 2
__CLASS           : __PARAMETERS
__SUPERCLASS      :
__DYNASTY         : __PARAMETERS
__RELPATH         :
__PROPERTY_COUNT  : 6
__DERIVATION      : {}
__SERVER          :
__NAMESPACE       :
__PATH            :
ClusterSize       : 0
EnableCompression : False
FileSystem        : NTFS
Label             :
QuickFormat       : False
Version           : 0
PSComputerName    :
```

<span data-ttu-id="29afb-120">此命令列出必要的物件順序。</span><span class="sxs-lookup"><span data-stu-id="29afb-120">This command lists the required order of the objects.</span></span> <span data-ttu-id="29afb-121">在 PowerShell 3.0 中叫用 WMI 不同於替代方法，且需要以特定順序輸入物件值。</span><span class="sxs-lookup"><span data-stu-id="29afb-121">To invoke WMI in PowerShell 3.0 differs from alternate methods, and requires that object values are entered in a specific order.</span></span>

### <span data-ttu-id="29afb-122">範例2：啟動應用程式的實例</span><span class="sxs-lookup"><span data-stu-id="29afb-122">Example 2: Start an instance of an application</span></span>

```powershell
([Wmiclass]'Win32_Process').GetMethodParameters('Create')
```

```Output
__GENUS                   : 2
__CLASS                   : __PARAMETERS
__SUPERCLASS              :
__DYNASTY                 : __PARAMETERS
__RELPATH                 :
__PROPERTY_COUNT          : 3
__DERIVATION              : {}
__SERVER                  :
__NAMESPACE               :
__PATH                    :
CommandLine               :
CurrentDirectory          :
ProcessStartupInformation :
PSComputerName            :
```

```powershell
Invoke-WmiMethod -Path win32_process -Name create -ArgumentList notepad.exe
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 2
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ProcessId        : 11312
ReturnValue      : 0
PSComputerName   :
```

<span data-ttu-id="29afb-123">此命令會藉由呼叫 Win32_Process 類別的方法，啟動「記事本」的實例 `Create` 。 **Win32_Process**</span><span class="sxs-lookup"><span data-stu-id="29afb-123">This command starts an instance of Notepad by calling the `Create` method of the **Win32_Process** class.</span></span>

<span data-ttu-id="29afb-124">**ReturnValue** 屬性會填入0，而 **ProcessId** 屬性則會填入整數 (下一個處理序識別碼) （如果命令已完成）。</span><span class="sxs-lookup"><span data-stu-id="29afb-124">The **ReturnValue** property is populated with a 0, and the **ProcessId** property is populated with an integer (the next process ID number) if the command is completed.</span></span>

### <span data-ttu-id="29afb-125">範例3：重新命名檔案</span><span class="sxs-lookup"><span data-stu-id="29afb-125">Example 3: Rename a file</span></span>

```powershell
Invoke-WmiMethod -Path "CIM_DataFile.Name='C:\scripts\test.txt'" -Name Rename -ArgumentList "C:\scripts\test_bu.txt"
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ReturnValue      : 0
```

<span data-ttu-id="29afb-126">此命令會重新命名檔案。</span><span class="sxs-lookup"><span data-stu-id="29afb-126">This command renames a file.</span></span> <span data-ttu-id="29afb-127">它會使用 **Path** 參數來參考 **CIM_DataFile** 類別的實例。</span><span class="sxs-lookup"><span data-stu-id="29afb-127">It uses the **Path** parameter to reference an instance of the **CIM_DataFile** class.</span></span> <span data-ttu-id="29afb-128">然後，它會將 Rename 方法套用至該特定執行個體。</span><span class="sxs-lookup"><span data-stu-id="29afb-128">Then, it applies the Rename method to that particular instance.</span></span>

<span data-ttu-id="29afb-129">如果命令完成， **ReturnValue** 屬性會填入0。</span><span class="sxs-lookup"><span data-stu-id="29afb-129">The **ReturnValue** property is populated with a 0 if the command is completed.</span></span>

### <span data-ttu-id="29afb-130">範例4：使用傳遞值陣列 `-ArgumentList`</span><span class="sxs-lookup"><span data-stu-id="29afb-130">Example 4: Passing an array of values using `-ArgumentList`</span></span>

<span data-ttu-id="29afb-131">使用後面接著值的物件陣列的範例 `$binSD` `$null` 。</span><span class="sxs-lookup"><span data-stu-id="29afb-131">An example using an array of objects `$binSD` followed by a `$null` value.</span></span>

```powershell
$acl = get-acl test.txt
$binSD = $acl.GetSecurityDescriptorBinaryForm()
Invoke-WmiMethod -class Win32_SecurityDescriptorHelper -Name BinarySDToSDDL -ArgumentList $binSD, $null
```

## <span data-ttu-id="29afb-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="29afb-132">PARAMETERS</span></span>

### <span data-ttu-id="29afb-133">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="29afb-133">-ArgumentList</span></span>

<span data-ttu-id="29afb-134">指定要傳送至呼叫之方法的參數。</span><span class="sxs-lookup"><span data-stu-id="29afb-134">Specifies the parameters to pass to the called method.</span></span> <span data-ttu-id="29afb-135">這個參數的值必須是物件的陣列，且必須以所呼叫方法所需的順序出現。</span><span class="sxs-lookup"><span data-stu-id="29afb-135">The value of this parameter must be an array of objects, and they must appear in the order required by the called method.</span></span> <span data-ttu-id="29afb-136">`Invoke-CimCommand`Cmdlet 沒有這些限制。</span><span class="sxs-lookup"><span data-stu-id="29afb-136">The `Invoke-CimCommand` cmdlet does not have these limitations.</span></span>

<span data-ttu-id="29afb-137">若要判斷列出這些物件的順序，請 `GetMethodParameters()` 在 WMI 類別上執行方法，如本主題結尾附近的範例1所示。</span><span class="sxs-lookup"><span data-stu-id="29afb-137">To determine the order in which to list those objects, run the `GetMethodParameters()` method on the WMI class, as illustrated in Example 1, near the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="29afb-138">如果第一個值是包含多個元素的陣列，則需要第二個值 $null。</span><span class="sxs-lookup"><span data-stu-id="29afb-138">If the first value is an array that contains more than one element, a second value of $null is required.</span></span> <span data-ttu-id="29afb-139">否則命令會產生錯誤，例如「無法將型別 'System.Byte' 的物件轉換為型別 'System.Array'」。</span><span class="sxs-lookup"><span data-stu-id="29afb-139">Otherwise, the command generates an error, such as "Unable to cast object of type 'System.Byte' to type 'System.Array'.".</span></span> <span data-ttu-id="29afb-140">請參閱上述的範例4。</span><span class="sxs-lookup"><span data-stu-id="29afb-140">See example 4 above.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: class, object, path
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="29afb-141">-AsJob</span><span class="sxs-lookup"><span data-stu-id="29afb-141">-AsJob</span></span>

<span data-ttu-id="29afb-142">指出此 Cmdlet 會以背景工作方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="29afb-142">Indicates that this cmdlet runs the command as a background job.</span></span> <span data-ttu-id="29afb-143">使用此參數執行需要很長時間才能完成的命令。</span><span class="sxs-lookup"><span data-stu-id="29afb-143">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="29afb-144">使用 **AsJob** 參數時，此命令會傳回代表背景工作的物件，然後顯示命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="29afb-144">When you use the **AsJob** parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span> <span data-ttu-id="29afb-145">工作完成後，您可以繼續在工作階段中工作。</span><span class="sxs-lookup"><span data-stu-id="29afb-145">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="29afb-146">如果 `Invoke-WmiMethod` 用於遠端電腦，則會在本機電腦上建立工作，而來自遠端電腦的結果則會自動傳回到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="29afb-146">If `Invoke-WmiMethod` is used against a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="29afb-147">若要管理工作，請使用包含 Job 名詞的 Cmdlet (各種 Job Cmdlet)。</span><span class="sxs-lookup"><span data-stu-id="29afb-147">To manage the job, use the cmdlets that contain the Job noun (the Job cmdlets).</span></span> <span data-ttu-id="29afb-148">若要取得工作結果，請使用 Receive-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="29afb-148">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="29afb-149">若要將這個參數與遠端電腦搭配使用，則本機電腦和遠端電腦必須針對遠端執行功能做設定。</span><span class="sxs-lookup"><span data-stu-id="29afb-149">To use this parameter with remote computers, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="29afb-150">此外，您必須使用 Windows Vista 和更新版本的 Windows 中的 [以系統管理員身分執行] 選項來啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="29afb-150">Additionally, you must start Windows PowerShell by using the Run as administrator option in Windows Vista and later versions of Windows.</span></span> <span data-ttu-id="29afb-151">如需詳細資訊，請參閱 about_Remote_Requirements。</span><span class="sxs-lookup"><span data-stu-id="29afb-151">For more information, see about_Remote_Requirements.</span></span>

<span data-ttu-id="29afb-152">如需有關 Windows PowerShell 背景工作的詳細資訊，請參閱 about_Jobs 和 about_Remote_Jobs。</span><span class="sxs-lookup"><span data-stu-id="29afb-152">For more information about Windows PowerShell background jobs, see about_Jobs and about_Remote_Jobs.</span></span>

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

### <span data-ttu-id="29afb-153">-Authentication</span><span class="sxs-lookup"><span data-stu-id="29afb-153">-Authentication</span></span>

<span data-ttu-id="29afb-154">指定要與 WMI 連線搭配使用的驗證等級。</span><span class="sxs-lookup"><span data-stu-id="29afb-154">Specifies the authentication level to be used with the WMI connection.</span></span> <span data-ttu-id="29afb-155">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="29afb-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="29afb-156">-1：Unchanged</span><span class="sxs-lookup"><span data-stu-id="29afb-156">-1: Unchanged</span></span>
- <span data-ttu-id="29afb-157">0：Default</span><span class="sxs-lookup"><span data-stu-id="29afb-157">0: Default</span></span>
- <span data-ttu-id="29afb-158">1：None (不執行驗證。)</span><span class="sxs-lookup"><span data-stu-id="29afb-158">1: None (No authentication in performed.)</span></span>
- <span data-ttu-id="29afb-159">2：Connect (只有當用戶端與應用程式建立關係時，才執行驗證。)</span><span class="sxs-lookup"><span data-stu-id="29afb-159">2: Connect (Authentication is performed only when the client establishes a relationship with the application.)</span></span>
- <span data-ttu-id="29afb-160">3：Call (只有在每次呼叫的開始並當應用程式接收要求時，才執行驗證。)</span><span class="sxs-lookup"><span data-stu-id="29afb-160">3: Call (Authentication is performed only at the beginning of each call when the application receives the request.)</span></span>
- <span data-ttu-id="29afb-161">4：Packet (在從用戶端接收的所有資料上執行驗證。)</span><span class="sxs-lookup"><span data-stu-id="29afb-161">4: Packet (Authentication is performed on all the data that is received from the client.)</span></span>
- <span data-ttu-id="29afb-162">5： PacketIntegrity (在用戶端和應用程式之間傳送的所有資料都會經過驗證和驗證。 ) </span><span class="sxs-lookup"><span data-stu-id="29afb-162">5: PacketIntegrity (All the data that is transferred between the client and the application is authenticated and verified.)</span></span>
- <span data-ttu-id="29afb-163">6：PacketPrivacy (使用其他驗證等級的屬性，並加密所有資料。)</span><span class="sxs-lookup"><span data-stu-id="29afb-163">6: PacketPrivacy (The properties of the other authentication levels are used, and all the data is encrypted.)</span></span>

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

### <span data-ttu-id="29afb-164">-Authority</span><span class="sxs-lookup"><span data-stu-id="29afb-164">-Authority</span></span>

<span data-ttu-id="29afb-165">指定用來驗證 WMI 連線的授權單位。</span><span class="sxs-lookup"><span data-stu-id="29afb-165">Specifies the authority to use to authenticate the WMI connection.</span></span> <span data-ttu-id="29afb-166">您可以指定標準 Windows NT LAN Manager (NTLM) 或 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="29afb-166">You can specify standard Windows NT LAN Manager (NTLM) or Kerberos authentication.</span></span> <span data-ttu-id="29afb-167">若要使用 NTLM，請將授權單位設定為 "ntlmdomain:\<DomainName\>"，其中 \<DomainName\> 識別有效的 NTLM 網域名稱。</span><span class="sxs-lookup"><span data-stu-id="29afb-167">To use NTLM, set the authority setting to ntlmdomain:\<DomainName\>, where \<DomainName\> identifies a valid NTLM domain name.</span></span> <span data-ttu-id="29afb-168">若要使用 Kerberos，請指定 kerberos:\<DomainName\ServerName\>。</span><span class="sxs-lookup"><span data-stu-id="29afb-168">To use Kerberos, specify kerberos:\<DomainName\ServerName\>.</span></span> <span data-ttu-id="29afb-169">當您連線到本機電腦時，不能包含授權單位設定。</span><span class="sxs-lookup"><span data-stu-id="29afb-169">You cannot include the authority setting when you connect to the local computer.</span></span>

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

### <span data-ttu-id="29afb-170">-Class</span><span class="sxs-lookup"><span data-stu-id="29afb-170">-Class</span></span>

<span data-ttu-id="29afb-171">指定包含要呼叫之靜態方法的 WMI 類別。</span><span class="sxs-lookup"><span data-stu-id="29afb-171">Specifies the WMI class that contains a static method to call.</span></span>

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

### <span data-ttu-id="29afb-172">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="29afb-172">-ComputerName</span></span>

<span data-ttu-id="29afb-173">以字串陣列指定此 Cmdlet 在其上執行命令的電腦。</span><span class="sxs-lookup"><span data-stu-id="29afb-173">Specifies, as a string array, the computers that this cmdlet runs the command on.</span></span> <span data-ttu-id="29afb-174">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="29afb-174">The default is the local computer.</span></span>

<span data-ttu-id="29afb-175">請輸入一部或多部電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="29afb-175">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more computers.</span></span> <span data-ttu-id="29afb-176">若要指定本機電腦，請輸入電腦名稱、句點 (.)，或者 localhost。</span><span class="sxs-lookup"><span data-stu-id="29afb-176">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="29afb-177">此參數不必依賴 Windows PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="29afb-177">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="29afb-178">即使您的電腦未設定為執行遠端命令，您仍然可以使用 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="29afb-178">You can use the **ComputerName** parameter even if your computer is not configured to run remote commands.</span></span>

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

### <span data-ttu-id="29afb-179">-Credential</span><span class="sxs-lookup"><span data-stu-id="29afb-179">-Credential</span></span>

<span data-ttu-id="29afb-180">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="29afb-180">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="29afb-181">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="29afb-181">The default is the current user.</span></span> <span data-ttu-id="29afb-182">輸入使用者名稱，例如 `User01` 、 `Domain01\User01` 或 `User@Contoso.com` 。</span><span class="sxs-lookup"><span data-stu-id="29afb-182">Type a user name, such as `User01`, `Domain01\User01`, or `User@Contoso.com`.</span></span> <span data-ttu-id="29afb-183">或者，輸入 **PSCredential** 物件，例如 Get-Credential Cmdlet 所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="29afb-183">Or, enter a **PSCredential** object, such as an object that is returned by the Get-Credential cmdlet.</span></span> <span data-ttu-id="29afb-184">當您輸入使用者名稱時，會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="29afb-184">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="29afb-185">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="29afb-185">-EnableAllPrivileges</span></span>

<span data-ttu-id="29afb-186">指出此 Cmdlet 會在命令進行 WMI 呼叫之前，先啟用目前使用者的擁有權限。</span><span class="sxs-lookup"><span data-stu-id="29afb-186">Indicates that this cmdlet enables all the privileges of the current user before the command makes the WMI call.</span></span>

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

### <span data-ttu-id="29afb-187">-Impersonation</span><span class="sxs-lookup"><span data-stu-id="29afb-187">-Impersonation</span></span>

<span data-ttu-id="29afb-188">指定要使用的模擬等級。</span><span class="sxs-lookup"><span data-stu-id="29afb-188">Specifies the impersonation level to use.</span></span> <span data-ttu-id="29afb-189">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="29afb-189">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="29afb-190">0：Default (讀取本機登錄以找出預設模擬等級，通常是設定為 "3：Impersonate"。)</span><span class="sxs-lookup"><span data-stu-id="29afb-190">0: Default (Reads the local registry for the default impersonation level, which is usually set to "3: Impersonate".)</span></span>
- <span data-ttu-id="29afb-191">1：Anonymous (隱藏呼叫端的認證。)</span><span class="sxs-lookup"><span data-stu-id="29afb-191">1: Anonymous (Hides the credentials of the caller.)</span></span>
- <span data-ttu-id="29afb-192">2：Identify (允許物件查詢呼叫端的認證。)</span><span class="sxs-lookup"><span data-stu-id="29afb-192">2: Identify (Allows objects to query the credentials of the caller.)</span></span>
- <span data-ttu-id="29afb-193">3：Impersonate (允許物件使用呼叫端的認證。)</span><span class="sxs-lookup"><span data-stu-id="29afb-193">3: Impersonate (Allows objects to use the credentials of the caller.)</span></span>
- <span data-ttu-id="29afb-194">4：Delegate (允許物件許可其他物件使用呼叫端的認證。)</span><span class="sxs-lookup"><span data-stu-id="29afb-194">4: Delegate (Allows objects to permit other objects to use the credentials of the caller.)</span></span>

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

### <span data-ttu-id="29afb-195">-InputObject</span><span class="sxs-lookup"><span data-stu-id="29afb-195">-InputObject</span></span>

<span data-ttu-id="29afb-196">指定要做為輸入使用的 **system.management.managementobject** 物件。</span><span class="sxs-lookup"><span data-stu-id="29afb-196">Specifies a **ManagementObject** object to use as input.</span></span> <span data-ttu-id="29afb-197">使用這個參數時，會忽略 **旗** 標和 **引數** 參數以外的所有其他參數。</span><span class="sxs-lookup"><span data-stu-id="29afb-197">When this parameter is used, all other parameters except the **Flag** and **Argument** parameters are ignored.</span></span>

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

### <span data-ttu-id="29afb-198">-Locale</span><span class="sxs-lookup"><span data-stu-id="29afb-198">-Locale</span></span>

<span data-ttu-id="29afb-199">指定 WMI 物件的慣用地區設定。</span><span class="sxs-lookup"><span data-stu-id="29afb-199">Specifies the preferred locale for WMI objects.</span></span> <span data-ttu-id="29afb-200">以慣用順序將 **地區** 設定參數的值指定為格式的陣列 `MS_<LCID>` 。</span><span class="sxs-lookup"><span data-stu-id="29afb-200">Specify the value of the **Locale** parameter as an array in the `MS_<LCID>` format in the preferred order.</span></span>

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

### <span data-ttu-id="29afb-201">-Name</span><span class="sxs-lookup"><span data-stu-id="29afb-201">-Name</span></span>

<span data-ttu-id="29afb-202">指定要叫用之方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="29afb-202">Specifies the name of the method to be invoked.</span></span> <span data-ttu-id="29afb-203">這是必要參數，不能是 null 或空白。</span><span class="sxs-lookup"><span data-stu-id="29afb-203">This parameter is mandatory and cannot be null or empty.</span></span>

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

### <span data-ttu-id="29afb-204">-Namespace</span><span class="sxs-lookup"><span data-stu-id="29afb-204">-Namespace</span></span>

<span data-ttu-id="29afb-205">與 **Class** 參數搭配使用時，此參數會指定參考的 wmi 類別或物件所在的 wmi 存放庫命名空間。</span><span class="sxs-lookup"><span data-stu-id="29afb-205">When used with the **Class** parameter, this parameter specifies the WMI repository namespace where the referenced WMI class or object is located.</span></span>

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

### <span data-ttu-id="29afb-206">-Path</span><span class="sxs-lookup"><span data-stu-id="29afb-206">-Path</span></span>

<span data-ttu-id="29afb-207">指定 WMI 類別的 WMI 物件路徑，或指定 WMI 類別之執行個體的 WMI 物件路徑。</span><span class="sxs-lookup"><span data-stu-id="29afb-207">Specifies the WMI object path of a WMI class, or specifies the WMI object path of an instance of a WMI class.</span></span> <span data-ttu-id="29afb-208">您指定的類別或實例必須包含 **Name** 參數中指定的方法。</span><span class="sxs-lookup"><span data-stu-id="29afb-208">The class or the instance that you specify must contain the method that is specified in the **Name** parameter.</span></span>

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

### <span data-ttu-id="29afb-209">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="29afb-209">-ThrottleLimit</span></span>

<span data-ttu-id="29afb-210">針對可同時執行的 WMI 作業數目指定節流值。</span><span class="sxs-lookup"><span data-stu-id="29afb-210">Specifies a throttle value for the number of WMI operations that can be executed simultaneously.</span></span>
<span data-ttu-id="29afb-211">此參數會與 **AsJob** 參數一起使用。</span><span class="sxs-lookup"><span data-stu-id="29afb-211">This parameter is used together with the **AsJob** parameter.</span></span> <span data-ttu-id="29afb-212">節流限制僅適用於目前命令，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="29afb-212">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="29afb-213">-Confirm</span><span class="sxs-lookup"><span data-stu-id="29afb-213">-Confirm</span></span>

<span data-ttu-id="29afb-214">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="29afb-214">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="29afb-215">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="29afb-215">-WhatIf</span></span>

<span data-ttu-id="29afb-216">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="29afb-216">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="29afb-217">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="29afb-217">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="29afb-218">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="29afb-218">CommonParameters</span></span>

<span data-ttu-id="29afb-219">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="29afb-219">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="29afb-220">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="29afb-220">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="29afb-221">輸入</span><span class="sxs-lookup"><span data-stu-id="29afb-221">INPUTS</span></span>

### <span data-ttu-id="29afb-222">無</span><span class="sxs-lookup"><span data-stu-id="29afb-222">None</span></span>

<span data-ttu-id="29afb-223">此 Cmdlet 不接受任何輸入。</span><span class="sxs-lookup"><span data-stu-id="29afb-223">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="29afb-224">輸出</span><span class="sxs-lookup"><span data-stu-id="29afb-224">OUTPUTS</span></span>

### <span data-ttu-id="29afb-225">無</span><span class="sxs-lookup"><span data-stu-id="29afb-225">None</span></span>

<span data-ttu-id="29afb-226">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="29afb-226">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="29afb-227">注意</span><span class="sxs-lookup"><span data-stu-id="29afb-227">NOTES</span></span>

## <span data-ttu-id="29afb-228">相關連結</span><span class="sxs-lookup"><span data-stu-id="29afb-228">RELATED LINKS</span></span>

[<span data-ttu-id="29afb-229">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="29afb-229">Get-WSManInstance</span></span>](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[<span data-ttu-id="29afb-230">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="29afb-230">Invoke-WSManAction</span></span>](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[<span data-ttu-id="29afb-231">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="29afb-231">New-WSManInstance</span></span>](../Microsoft.WsMan.Management/New-WSManInstance.md)

[<span data-ttu-id="29afb-232">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="29afb-232">Remove-WSManInstance</span></span>](../Microsoft.WsMan.Management/Remove-WSManInstance.md)

[<span data-ttu-id="29afb-233">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="29afb-233">Get-WmiObject</span></span>](Get-WmiObject.md)

[<span data-ttu-id="29afb-234">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="29afb-234">Remove-WmiObject</span></span>](Remove-WmiObject.md)

[<span data-ttu-id="29afb-235">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="29afb-235">Set-WmiInstance</span></span>](Set-WmiInstance.md)
