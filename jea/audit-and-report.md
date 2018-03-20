---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea,powershell,安全性"
title: "JEA 上的稽核和報告"
ms.openlocfilehash: 57148bc3753bdd751bfa21fc3198aca3f8654849
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="91376-103">JEA 上的稽核和報告</span><span class="sxs-lookup"><span data-stu-id="91376-103">Auditing and Reporting on JEA</span></span>

> <span data-ttu-id="91376-104">適用對象：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="91376-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="91376-105">部署 JEA 之後，您會想要定期稽核 JEA 設定。</span><span class="sxs-lookup"><span data-stu-id="91376-105">After you've deployed JEA, you will want to regularly audit the JEA configuration.</span></span>
<span data-ttu-id="91376-106">這有助於您評估正確的人員是否具有 JEA 端點的存取權，以及他們的指派角色是否仍然適當。</span><span class="sxs-lookup"><span data-stu-id="91376-106">This will help you assess if the correct people have access to the JEA endpoint and if their assigned roles are still appropriate.</span></span>

<span data-ttu-id="91376-107">本主題說明您可以稽核 JEA 端點的各種方式。</span><span class="sxs-lookup"><span data-stu-id="91376-107">This topic describes the various ways you can audit a JEA endpoint.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="91376-108">在電腦上尋找已註冊的 JEA 工作階段</span><span class="sxs-lookup"><span data-stu-id="91376-108">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="91376-109">若要檢查哪些 JEA 工作階段已在電腦上註冊，請使用 [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="91376-109">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="91376-110">端點的有效權限詳列於 "Permission" 屬性。</span><span class="sxs-lookup"><span data-stu-id="91376-110">The effective rights for the endpoint are listed in the "Permission" property.</span></span>
<span data-ttu-id="91376-111">這些使用者有權連接到 JEA 端點，但他們能存取哪些角色 (乃至於命令) 則由用來註冊端點的[工作階段設定檔](session-configurations.md)中的 "RoleDefinitions" 欄位決定。</span><span class="sxs-lookup"><span data-stu-id="91376-111">These users have the right to connect to the JEA endpoint, but which roles (and, by extension, commands) they have access to is determined by the "RoleDefinitions" field in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span>

<span data-ttu-id="91376-112">您可以展開 "RoleDefinitions" 屬性中的資料來評估已註冊的 JEA 端點中的角色對應。</span><span class="sxs-lookup"><span data-stu-id="91376-112">You can evaluate the role mappings in a registered JEA endpoint by expanding the data in the "RoleDefinitions" property.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="91376-113">在電腦上尋找可用的角色功能</span><span class="sxs-lookup"><span data-stu-id="91376-113">Find available role capabilities on the machine</span></span>

<span data-ttu-id="91376-114">角色功能檔案將只會在它們儲存於有效 PowerShell 模組內的 "RoleCapabilities" 資料夾時才會被 JEA 使用。</span><span class="sxs-lookup"><span data-stu-id="91376-114">Role capability files will only be used by JEA if they are stored in a "RoleCapabilities" folder inside a valid PowerShell module.</span></span>
<span data-ttu-id="91376-115">您可以搜尋可用模組清單，以在電腦上尋找所有可用的角色功能。</span><span class="sxs-lookup"><span data-stu-id="91376-115">You can find all role capabilities available on a computer by searching the list of available modules.</span></span>

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> <span data-ttu-id="91376-116">如果多個角色功能共用相同的名稱，則此函式的結果順序不一定是角色功能的選取順序。</span><span class="sxs-lookup"><span data-stu-id="91376-116">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="91376-117">檢查特定使用者的有效權限</span><span class="sxs-lookup"><span data-stu-id="91376-117">Check effective rights for a specific user</span></span>

<span data-ttu-id="91376-118">一旦您設定好 JEA 端點，便可以檢查哪些命令可供特定使用者在 JEA 工作階段中使用。</span><span class="sxs-lookup"><span data-stu-id="91376-118">Once you have set up a JEA endpoint, you may want to check which commands are available to a specific user in a JEA session.</span></span>
<span data-ttu-id="91376-119">您可以使用 [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) 列舉所有適用於使用者的命令，如果他們要使用其目前群組成員資格來啟動 JEA 工作階段。</span><span class="sxs-lookup"><span data-stu-id="91376-119">You can use [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) to enumerate all of the commands applicable to a user if they were to start a JEA session with their current group memberships.</span></span>
<span data-ttu-id="91376-120">`Get-PSSessionCapability` 的輸出會與指定使用者在 JEA 工作階段中執行 `Get-Command -CommandType All` 的輸出相同。</span><span class="sxs-lookup"><span data-stu-id="91376-120">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="91376-121">如果您的使用者不是會授與額外 JEA 權限之群組的永久成員，這個 Cmdlet 可能不會反映這些額外的權限。</span><span class="sxs-lookup"><span data-stu-id="91376-121">If your users are not permanent members of groups which would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span>
<span data-ttu-id="91376-122">使用 Just-in-Time 特殊權限的存取管理系統來允許使用者暫時屬於某個安全性群組時，通常會是如此。</span><span class="sxs-lookup"><span data-stu-id="91376-122">This is typically the case when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span>
<span data-ttu-id="91376-123">請務必仔細評估使用者與角色的對應，以及每個角色的內容，以確保使用者只能夠存取成功執行其工作所需的最少命令。</span><span class="sxs-lookup"><span data-stu-id="91376-123">Always carefully evaluate the mapping of users to roles and the contents of each role to ensure users are only getting access to the least amount of commands needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="91376-124">PowerShell 事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="91376-124">PowerShell event logs</span></span>

<span data-ttu-id="91376-125">如果您已在系統上啟用模組和/或指令碼區塊記錄，將可在 Windows 事件記錄檔中，找到使用者在其 JEA 工作階段中執行之每個命令的事件。</span><span class="sxs-lookup"><span data-stu-id="91376-125">If you enabled module and/or script block logging on the system, you will be able to find events in the Windows event logs for each command a user ran in their JEA sessions.</span></span>
<span data-ttu-id="91376-126">若要尋找這些事件，請開啟 Windows 事件檢視器、瀏覽至 [Microsoft-Windows-PowerShell/Operational] 事件記錄檔，然後尋找事件識別碼為 **4104** 的事件。</span><span class="sxs-lookup"><span data-stu-id="91376-126">To find these events, open the Windows Event Viewer, navigate to the **Microsoft-Windows-PowerShell/Operational** event log, and look for events with event ID **4104**.</span></span>

<span data-ttu-id="91376-127">每個事件記錄檔項目會包含命令執行所在工作階段的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="91376-127">Each event log entry will include information about the session in which the command was run.</span></span>
<span data-ttu-id="91376-128">對於 JEA 工作階段，這包含 **ConnectedUser** 的重要資訊，它是建立 JEA 工作階段的實際使用者，也包含 **RunAsUser** 的重要資訊，這會識別 JEA 用來執行命令的帳戶。</span><span class="sxs-lookup"><span data-stu-id="91376-128">For JEA sessions, this includes important information about the **ConnectedUser**, which is the actual user who created the JEA session, as well as the **RunAsUser** which identifies the account JEA used to execute the command.</span></span>
<span data-ttu-id="91376-129">應用程式事件記錄檔會顯示 RunAsUser 正在進行的變更，因此啟用文字記錄或模組/指令碼記錄十分重要，如此才能從特定命令引動過程回溯到使用者。</span><span class="sxs-lookup"><span data-stu-id="91376-129">Application event logs will show changes being made by the RunAsUser, so having transcripts or module/script logging enabled is crucial to be able to trace a specific command invocation back to a user.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="91376-130">應用程式事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="91376-130">Application event logs</span></span>

<span data-ttu-id="91376-131">當您在與外部應用程式或服務互動的 JEA 工作階段中執行命令時，這些應用程式可能會將事件記錄到自己的事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="91376-131">When you run a command in a JEA session that interacts with an external application or service, those applications may log events to their own event logs.</span></span>
<span data-ttu-id="91376-132">不同於 PowerShell 記錄檔和文字記錄，其他記錄機制不會擷取 JEA 工作階段的連線使用者，而只會記錄虛擬執行身分使用者或群組受管理的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="91376-132">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the connected user of the JEA session, and will instead only log the virtual run-as user or group managed service account.</span></span>
<span data-ttu-id="91376-133">若要判斷誰執行命令，您必須參考[工作階段文字記錄](#session-transcripts)，或相互關聯 PowerShell 事件記錄檔與應用程式事件記錄檔中顯示的時間和使用者。</span><span class="sxs-lookup"><span data-stu-id="91376-133">In order to determine who ran the command, you will need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="91376-134">WinRM 記錄檔也可協助您相互關聯應用程式事件記錄檔中的執行身分使用者與連線使用者。</span><span class="sxs-lookup"><span data-stu-id="91376-134">The WinRM log can also help you correlate run as users in an application event log with the connecting user.</span></span>
<span data-ttu-id="91376-135">**Microsoft-Windows-Windows 遠端管理/作業**記錄檔中的事件識別碼 **193** 會記錄每次建立 JEA 工作階段時，連線使用者與執行身分使用者的安全性識別碼 (SID) 和帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="91376-135">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user every time a JEA session is created.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="91376-136">工作階段文字記錄</span><span class="sxs-lookup"><span data-stu-id="91376-136">Session transcripts</span></span>

<span data-ttu-id="91376-137">如果您已設定 JEA 為每個使用者工作階段建立文字記錄，每個使用者動作的文字副本將儲存在指定的資料夾。</span><span class="sxs-lookup"><span data-stu-id="91376-137">If you configured JEA to create a transcript for each user session, a text copy of every user's actions will be stored in the specified folder.</span></span>

<span data-ttu-id="91376-138">若要尋找所有文字記錄目錄，請以系統管理員身分在設定了 JEA 的電腦上執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="91376-138">To find all transcript directories, run the following command as an administrator on the computer configured with JEA:</span></span>

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="91376-139">每份文字記錄開頭為工作階段的啟動時間、連線到工作階段的使用者，以及指派給他們的 JEA 身分識別等資訊。</span><span class="sxs-lookup"><span data-stu-id="91376-139">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="91376-140">在文字記錄的本文中，會記錄使用者叫用之每個命令的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="91376-140">In the body of the transcript, information is logged about each command the user invoked.</span></span>
<span data-ttu-id="91376-141">因為針對 PowerShell 遠端轉換命令的方式，使用者所執行命令的正確語法無法在 JEA 工作階段中取得，但是您仍可以判斷所執行的有效命令。</span><span class="sxs-lookup"><span data-stu-id="91376-141">The exact syntax of the command the user ran is unavailable in JEA sessions due to the way commands are transformed for PowerShell remoting, however you can still determine the effective command that was executed.</span></span>
<span data-ttu-id="91376-142">以下是範例文字記錄程式碼片段，來自在 JEA 工作階段中執行 `Get-Service Dns` 的使用者：</span><span class="sxs-lookup"><span data-stu-id="91376-142">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="91376-143">對於使用者執行的每個命令，會寫入一列 "CommandInvocation"，描述使用者叫用的 Cmdlet 或函式。</span><span class="sxs-lookup"><span data-stu-id="91376-143">For each command a user runs, a "CommandInvocation" line will be written, describing the cmdlet or function the user invoked.</span></span>
<span data-ttu-id="91376-144">ParameterBindings 接在每個 CommandInvocation 之後，告訴您與命令一起提供的每個參數和值。</span><span class="sxs-lookup"><span data-stu-id="91376-144">ParameterBindings follow each CommandInvocation to tell you about each parameter and value that was supplied with the command.</span></span>
<span data-ttu-id="91376-145">在上述範例中，您可以看到針對 "Get-Service" Cmdlet 提供 "Name" 參數 "Dns" 值。</span><span class="sxs-lookup"><span data-stu-id="91376-145">In the above example, you can see that the parameter "Name" was supplied the value "Dns" for the "Get-Service" cmdlet.</span></span>

<span data-ttu-id="91376-146">每個命令的輸出也會觸發 CommandInvocation，通常為 Out-Default。</span><span class="sxs-lookup"><span data-stu-id="91376-146">The output of each command will also trigger a CommandInvocation, usually to Out-Default.</span></span> <span data-ttu-id="91376-147">Out-Default 的 InputObject 是由命令傳回的 PowerShell 物件。</span><span class="sxs-lookup"><span data-stu-id="91376-147">The InputObject of Out-Default is the PowerShell object returned from the command.</span></span>
<span data-ttu-id="91376-148">物件的詳細資料會列印在下面幾行，密切模擬使用者會看到的情況。</span><span class="sxs-lookup"><span data-stu-id="91376-148">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="91376-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91376-149">See also</span></span>

- [<span data-ttu-id="91376-150">在 JEA 工作階段中稽核使用者動作</span><span class="sxs-lookup"><span data-stu-id="91376-150">Audit user actions in a JEA session</span></span>](audit-and-report.md)
- [<span data-ttu-id="91376-151">*PowerShell ♥ 藍色小組*安全性部落格文章</span><span class="sxs-lookup"><span data-stu-id="91376-151">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

