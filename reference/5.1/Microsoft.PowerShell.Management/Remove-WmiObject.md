---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WmiObject
ms.openlocfilehash: 287eb02e7de2f4182e0ecfd7f6b6a7cafb66969e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203559"
---
# <span data-ttu-id="4f3ef-103">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="4f3ef-103">Remove-WmiObject</span></span>

## <span data-ttu-id="4f3ef-104">概要</span><span class="sxs-lookup"><span data-stu-id="4f3ef-104">SYNOPSIS</span></span>
<span data-ttu-id="4f3ef-105">刪除現有 Windows Management Instrumentation (WMI) 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-105">Deletes an instance of an existing Windows Management Instrumentation (WMI) class.</span></span>

## <span data-ttu-id="4f3ef-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4f3ef-106">SYNTAX</span></span>

### <span data-ttu-id="4f3ef-107">class (預設值)</span><span class="sxs-lookup"><span data-stu-id="4f3ef-107">class (Default)</span></span>

```
Remove-WmiObject [-Class] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4f3ef-108">物件 (object)</span><span class="sxs-lookup"><span data-stu-id="4f3ef-108">object</span></span>

```
Remove-WmiObject -InputObject <ManagementObject> [-AsJob] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="4f3ef-109">path</span><span class="sxs-lookup"><span data-stu-id="4f3ef-109">path</span></span>

```
Remove-WmiObject -Path <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4f3ef-110">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="4f3ef-110">WQLQuery</span></span>

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="4f3ef-111">查詢</span><span class="sxs-lookup"><span data-stu-id="4f3ef-111">query</span></span>

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="4f3ef-112">list</span><span class="sxs-lookup"><span data-stu-id="4f3ef-112">list</span></span>

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="4f3ef-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4f3ef-113">DESCRIPTION</span></span>
<span data-ttu-id="4f3ef-114">**>get-wmiobject** 指令程式會刪除現有 WINDOWS MANAGEMENT INSTRUMENTATION (WMI) 類別的實例。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-114">The **Remove-WmiObject** cmdlet deletes an instance of an existing Windows Management Instrumentation (WMI)class.</span></span>

## <span data-ttu-id="4f3ef-115">範例</span><span class="sxs-lookup"><span data-stu-id="4f3ef-115">EXAMPLES</span></span>

### <span data-ttu-id="4f3ef-116">範例1：關閉 Win32 進程的所有實例</span><span class="sxs-lookup"><span data-stu-id="4f3ef-116">Example 1: Close all instances of a Win32 process</span></span>

```
PS C:\> notepad
PS C:\> $np = Get-WmiObject -Query "select * from win32_process where name='notepad.exe'"
PS C:\> $np | Remove-WmiObject
```

<span data-ttu-id="4f3ef-117">這個範例會關閉 Notepad.exe 的所有實例。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-117">This example closes all the instances of Notepad.exe.</span></span>

<span data-ttu-id="4f3ef-118">第一個命令會啟動一個「記事本」執行個體。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-118">The first command starts an instance of Notepad.</span></span>

<span data-ttu-id="4f3ef-119">第二個命令會使用 Get-WmiObject Cmdlet 來取出對應至 Notepad.exe 的 Win32_Process 實例，然後將它們儲存在 $np 變數中。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-119">The second command uses the Get-WmiObject cmdlet to retrieve the instances of the Win32_Process that correspond to Notepad.exe, and then stores them in the $np variable.</span></span>

<span data-ttu-id="4f3ef-120">第三個命令會將 $np 變數中的物件傳遞至 **>get-wmiobject** ，以刪除 Notepad.exe 的所有實例。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-120">The third command passes the object in the $np variable to **Remove-WmiObject** , which deletes all the instances of Notepad.exe.</span></span>

### <span data-ttu-id="4f3ef-121">範例2：刪除資料夾</span><span class="sxs-lookup"><span data-stu-id="4f3ef-121">Example 2: Delete a folder</span></span>

```
PS C:\> $a = Get-WMIObject -Query "Select * From Win32_Directory Where Name ='C:\\Test'"
PS C:\> $a | Remove-WMIObject
```

<span data-ttu-id="4f3ef-122">此命令會刪除 C:\Test 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-122">This command deletes the C:\Test folder.</span></span>

<span data-ttu-id="4f3ef-123">第一個命令會使用 **>get-wmiobject** 來查詢 C:\Test 資料夾，然後將物件儲存在 $a 變數中。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-123">The first command uses **Get-WMIObject** to query for the C:\Test folder, and then stores the object in the $a variable.</span></span>

<span data-ttu-id="4f3ef-124">第二個命令會以管線將 $a 變數傳送至 **>get-wmiobject** ，以刪除資料夾。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-124">The second command pipes the $a variable to **Remove-WMIObject** , which deletes the folder.</span></span>

## <span data-ttu-id="4f3ef-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4f3ef-125">PARAMETERS</span></span>

### <span data-ttu-id="4f3ef-126">-AsJob</span><span class="sxs-lookup"><span data-stu-id="4f3ef-126">-AsJob</span></span>
<span data-ttu-id="4f3ef-127">指出此 Cmdlet 會以背景工作的形式執行。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-127">Indicates that this cmdlet run as a background job.</span></span>
<span data-ttu-id="4f3ef-128">使用此參數執行需要很長時間才能完成的命令。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-128">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="4f3ef-129">已導入 Windows PowerShell 3.0 的新 CIM Cmdlet 可執行與 WMI Cmdlet 相同的工作。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-129">New CIM cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span>
<span data-ttu-id="4f3ef-130">CIM Cmdlet 符合 WS-Management (WSMan) 標準以及通用訊息模型 (CIM) 標準，可讓 Cmdlet 使用相同的技術來管理執行 Windows 作業系統的電腦，以及執行其他作業系統的電腦。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-130">The CIM cmdlets comply with WS-Management (WSMan) standards and with the Common Information Model (CIM) standard, which enables the cmdlets to use the same techniques to manage computers that run the Windows operating system and those running other operating systems.</span></span>
<span data-ttu-id="4f3ef-131">請考慮使用 CimInstance 指令程式，而不是使用 **>get-wmiobject** https://go.microsoft.com/fwlink/?LinkId=227964 。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-131">Instead of using **Remove-WmiObject** , consider using the Remove-CimInstancehttps://go.microsoft.com/fwlink/?LinkId=227964 cmdlet.</span></span>

<span data-ttu-id="4f3ef-132">使用 *AsJob* 參數時，此命令會傳回代表背景工作的物件，然後顯示命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-132">When you use the *AsJob* parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span>
<span data-ttu-id="4f3ef-133">工作完成後，您可以繼續在工作階段中工作。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-133">You can continue to work in the session while the job finishes.</span></span>
<span data-ttu-id="4f3ef-134">如果對遠端電腦使用 **Remove-WmiObject** ，就會在本機電腦上建立工作，而來自遠端電腦的結果則會自動傳回到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-134">If **Remove-WmiObject** is used against a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="4f3ef-135">若要管理工作，請使用包含 **作業** 名詞 ( **工作 Cmdlet) 的 Cmdlet。**</span><span class="sxs-lookup"><span data-stu-id="4f3ef-135">To manage the job, use the cmdlets that contain the **Job** noun (the **Job** cmdlets).</span></span>
<span data-ttu-id="4f3ef-136">若要取得工作結果，請使用 Receive-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-136">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="4f3ef-137">若要將此參數用於遠端電腦，必須設定本機和遠端電腦以進行遠端處理。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-137">To use this parameter for remote computers, the local and remote computers must be configured for remoting.</span></span>
<span data-ttu-id="4f3ef-138">使用 [以系統管理員身分執行] 選項開始 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-138">Start Windows PowerShell by using the Run as administrator option.</span></span>
<span data-ttu-id="4f3ef-139">如需詳細資訊，請參閱 about_Remote_Requirements。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-139">For more information, see about_Remote_Requirements.</span></span>

<span data-ttu-id="4f3ef-140">如需有關 Windows PowerShell 背景工作的詳細資訊，請參閱 about_Jobs 和 about_Remote_Jobs。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-140">For more information about Windows PowerShell background jobs, see about_Jobs and about_Remote_Jobs.</span></span>

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

### <span data-ttu-id="4f3ef-141">-Authentication</span><span class="sxs-lookup"><span data-stu-id="4f3ef-141">-Authentication</span></span>
<span data-ttu-id="4f3ef-142">指定用於 WMI 連線的驗證層級。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-142">Specifies the authentication level to use for the WMI connection.</span></span>
<span data-ttu-id="4f3ef-143">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="4f3ef-143">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4f3ef-144">-1：未變更。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-144">-1: Unchanged.</span></span>
- <span data-ttu-id="4f3ef-145">0：預設值。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-145">0: Default.</span></span>
- <span data-ttu-id="4f3ef-146">1：無。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-146">1: None.</span></span>
<span data-ttu-id="4f3ef-147">未執行任何驗證。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-147">No authentication in performed.</span></span>
- <span data-ttu-id="4f3ef-148">2：連接。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-148">2: Connect.</span></span>
<span data-ttu-id="4f3ef-149">只有當用戶端與應用程式建立關聯性時，才會執行驗證。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-149">Authentication is performed only when the client establishes a relationship with the application.</span></span>
- <span data-ttu-id="4f3ef-150">3：呼叫。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-150">3: Call.</span></span>
<span data-ttu-id="4f3ef-151">只有當應用程式收到要求時，才會在每次呼叫開始時執行驗證。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-151">Authentication is performed only at the start of each call when the application receives the request.</span></span>
- <span data-ttu-id="4f3ef-152">4：封包。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-152">4: Packet.</span></span>
<span data-ttu-id="4f3ef-153">會在從用戶端接收的所有資料上執行驗證。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-153">Authentication is performed on all the data that is received from the client.</span></span>
- <span data-ttu-id="4f3ef-154">5： PacketIntegrity。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-154">5: PacketIntegrity.</span></span>
<span data-ttu-id="4f3ef-155">在用戶端與應用程式之間傳輸的所有資料都會經過驗證和驗證。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-155">All the data that is transferred between the client and the application is authenticated and verified.</span></span>
- <span data-ttu-id="4f3ef-156">6： PacketPrivacy。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-156">6: PacketPrivacy.</span></span>
<span data-ttu-id="4f3ef-157">系統會使用其他驗證層級的屬性，並加密所有資料。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-157">The properties of the other authentication levels are used, and all the data is encrypted.</span></span>

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

### <span data-ttu-id="4f3ef-158">-Authority</span><span class="sxs-lookup"><span data-stu-id="4f3ef-158">-Authority</span></span>
<span data-ttu-id="4f3ef-159">指定用來驗證 WMI 連線的授權單位。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-159">Specifies the authority to use to authenticate the WMI connection.</span></span>
<span data-ttu-id="4f3ef-160">您可以指定標準 NTLM 或 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-160">You can specify standard NTLM or Kerberos authentication.</span></span>
<span data-ttu-id="4f3ef-161">若要使用 NTLM，請將授權單位設定為 "ntlmdomain:\<DomainName\>"，其中 \<DomainName\> 識別有效的 NTLM 網域名稱。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-161">To use NTLM, set the authority setting to ntlmdomain:\<DomainName\>, where \<DomainName\> identifies a valid NTLM domain name.</span></span>
<span data-ttu-id="4f3ef-162">若要使用 Kerberos，請指定 kerberos： \<DomainName\> \\ \<ServerName\> 。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-162">To use Kerberos, specify kerberos:\<DomainName\>\\\<ServerName\>.</span></span>
<span data-ttu-id="4f3ef-163">當您連線到本機電腦時，不能包含授權單位設定。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-163">You cannot include the authority setting when you connect to the local computer.</span></span>

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

### <span data-ttu-id="4f3ef-164">-Class</span><span class="sxs-lookup"><span data-stu-id="4f3ef-164">-Class</span></span>
<span data-ttu-id="4f3ef-165">指定此 Cmdlet 刪除之 WMI 類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-165">Specifies the name of a WMI class that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="4f3ef-166">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="4f3ef-166">-ComputerName</span></span>
<span data-ttu-id="4f3ef-167">指定此 Cmdlet 執行所在的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-167">Specifies the name of the computer on which this cmdlet runs.</span></span>
<span data-ttu-id="4f3ef-168">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-168">The default is the local computer.</span></span>

<span data-ttu-id="4f3ef-169">請輸入一部或多部電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-169">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more computers.</span></span>
<span data-ttu-id="4f3ef-170">若要指定本機電腦，請輸入電腦名稱、句點 (.)，或者 localhost。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-170">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="4f3ef-171">此參數不必依賴 Windows PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-171">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="4f3ef-172">即使您的電腦未設定為執行遠端命令，您仍然可以使用 *ComputerName* 參數。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-172">You can use the *ComputerName* parameter even if your computer is not configured to run remote commands.</span></span>

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

### <span data-ttu-id="4f3ef-173">-Credential</span><span class="sxs-lookup"><span data-stu-id="4f3ef-173">-Credential</span></span>
<span data-ttu-id="4f3ef-174">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-174">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="4f3ef-175">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-175">The default is the current user.</span></span>

<span data-ttu-id="4f3ef-176">輸入使用者名稱，例如 User01 或 Domain01\User01，或輸入 **PSCredential** 物件，例如 Get-Credential Cmdlet 產生的物件。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-176">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="4f3ef-177">如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-177">If you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="4f3ef-178">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="4f3ef-178">-EnableAllPrivileges</span></span>
<span data-ttu-id="4f3ef-179">指出此 Cmdlet 會在進行 WMI 呼叫之前，先啟用目前使用者的擁有權限。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-179">Indicates that this cmdlet enables all the permissions of the current user before the command it makes the WMI call.</span></span>

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

### <span data-ttu-id="4f3ef-180">-Impersonation</span><span class="sxs-lookup"><span data-stu-id="4f3ef-180">-Impersonation</span></span>
<span data-ttu-id="4f3ef-181">指定要使用的模擬等級。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-181">Specifies the impersonation level to use.</span></span>
<span data-ttu-id="4f3ef-182">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="4f3ef-182">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4f3ef-183">0：預設值。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-183">0: Default.</span></span>
<span data-ttu-id="4f3ef-184">讀取預設模擬層級的本機登錄，通常設定為3：模擬。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-184">Reads the local registry for the default impersonation level, which is usually set to 3: Impersonate.</span></span>
- <span data-ttu-id="4f3ef-185">1： Anonymous。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-185">1: Anonymous.</span></span>
<span data-ttu-id="4f3ef-186">隱藏呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-186">Hides the credentials of the caller.</span></span>
- <span data-ttu-id="4f3ef-187">2：識別。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-187">2: Identify.</span></span>
<span data-ttu-id="4f3ef-188">允許物件查詢呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-188">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="4f3ef-189">3：模擬。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-189">3: Impersonate.</span></span>
<span data-ttu-id="4f3ef-190">允許物件使用呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-190">Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="4f3ef-191">4：委派。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-191">4: Delegate.</span></span>
<span data-ttu-id="4f3ef-192">允許物件許可其他物件使用呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-192">Allows objects to permit other objects to use the credentials of the caller.</span></span>

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

### <span data-ttu-id="4f3ef-193">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4f3ef-193">-InputObject</span></span>
<span data-ttu-id="4f3ef-194">指定要做為輸入使用的 **system.management.managementobject** 物件。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-194">Specifies a **ManagementObject** object to use as input.</span></span>
<span data-ttu-id="4f3ef-195">使用這個參數時，將會忽略所有其他參數。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-195">When this parameter is used, all other parameters are ignored.</span></span>

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

### <span data-ttu-id="4f3ef-196">-Locale</span><span class="sxs-lookup"><span data-stu-id="4f3ef-196">-Locale</span></span>
<span data-ttu-id="4f3ef-197">指定 WMI 物件的慣用地區設定。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-197">Specifies the preferred locale for WMI objects.</span></span>
<span data-ttu-id="4f3ef-198">*地區* 設定參數是以慣用順序指定為 MS_ 格式的陣列 \<LCID\> 。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-198">The *Locale* parameter is specified as an array in the MS_\<LCID\> format in the preferred order.</span></span>

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

### <span data-ttu-id="4f3ef-199">-Namespace</span><span class="sxs-lookup"><span data-stu-id="4f3ef-199">-Namespace</span></span>
<span data-ttu-id="4f3ef-200">指定當與 *類別* 參數搭配使用時，參考的 wmi 類別所在的 wmi 存放庫命名空間。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-200">Specifies the WMI repository namespace where the referenced WMI class is located when it is used with the *Class* parameter.</span></span>

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

### <span data-ttu-id="4f3ef-201">-Path</span><span class="sxs-lookup"><span data-stu-id="4f3ef-201">-Path</span></span>
<span data-ttu-id="4f3ef-202">指定 WMI 類別的 WMI 物件路徑，或指定要刪除之 WMI 類別執行個體的 WMI 物件路徑。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-202">Specifies the WMI object path of a WMI class, or specifies the WMI object path of an instance of a WMI class to delete.</span></span>

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

### <span data-ttu-id="4f3ef-203">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="4f3ef-203">-ThrottleLimit</span></span>
<span data-ttu-id="4f3ef-204">指定為執行此命令可建立的最大同時連線數。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-204">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="4f3ef-205">此參數會與 *AsJob* 參數一起使用。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-205">This parameter is used together with the *AsJob* parameter.</span></span>
<span data-ttu-id="4f3ef-206">節流限制僅適用於目前命令，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-206">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="4f3ef-207">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4f3ef-207">-Confirm</span></span>
<span data-ttu-id="4f3ef-208">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-208">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4f3ef-209">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4f3ef-209">-WhatIf</span></span>
<span data-ttu-id="4f3ef-210">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-210">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4f3ef-211">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-211">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4f3ef-212">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4f3ef-212">CommonParameters</span></span>
<span data-ttu-id="4f3ef-213">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-213">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4f3ef-214">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-214">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4f3ef-215">輸入</span><span class="sxs-lookup"><span data-stu-id="4f3ef-215">INPUTS</span></span>

### <span data-ttu-id="4f3ef-216">System.Management.ManagementObject</span><span class="sxs-lookup"><span data-stu-id="4f3ef-216">System.Management.ManagementObject</span></span>
<span data-ttu-id="4f3ef-217">您可以使用管線將管理物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-217">You can pipe a management object to this cmdlet.</span></span>

## <span data-ttu-id="4f3ef-218">輸出</span><span class="sxs-lookup"><span data-stu-id="4f3ef-218">OUTPUTS</span></span>

### <span data-ttu-id="4f3ef-219">None、System.management.automation.remotingjob、Automation。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-219">None, System.Management.Automation.RemotingJob</span></span>
<span data-ttu-id="4f3ef-220">如果您指定 *AsJob* 參數，此 Cmdlet 會傳回工作物件。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-220">This cmdlet returns a job object, if you specify the *AsJob* parameter.</span></span>
<span data-ttu-id="4f3ef-221">否則，它不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="4f3ef-221">Otherwise, it does not generate any output.</span></span>

## <span data-ttu-id="4f3ef-222">注意</span><span class="sxs-lookup"><span data-stu-id="4f3ef-222">NOTES</span></span>

## <span data-ttu-id="4f3ef-223">相關連結</span><span class="sxs-lookup"><span data-stu-id="4f3ef-223">RELATED LINKS</span></span>

[<span data-ttu-id="4f3ef-224">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="4f3ef-224">Get-WmiObject</span></span>](Get-WmiObject.md)

[<span data-ttu-id="4f3ef-225">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="4f3ef-225">Invoke-WmiMethod</span></span>](Invoke-WmiMethod.md)

[<span data-ttu-id="4f3ef-226">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="4f3ef-226">Set-WmiInstance</span></span>](Set-WmiInstance.md)
