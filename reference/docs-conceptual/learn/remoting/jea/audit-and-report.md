---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: JEA 上的稽核和報告
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "70017789"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="fd0d7-103">JEA 上的稽核和報告</span><span class="sxs-lookup"><span data-stu-id="fd0d7-103">Auditing and Reporting on JEA</span></span>

<span data-ttu-id="fd0d7-104">部署 JEA 之後，您需要定期稽核 JEA 設定。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-104">After you've deployed JEA, you need to regularly audit the JEA configuration.</span></span> <span data-ttu-id="fd0d7-105">稽核有助於您評估正確的人員是否具有 JEA 端點存取權，以及他們的指派角色是否仍然適當。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-105">Auditing helps you assess that the correct people have access to the JEA endpoint and their assigned roles are still appropriate.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="fd0d7-106">在電腦上尋找已註冊的 JEA 工作階段</span><span class="sxs-lookup"><span data-stu-id="fd0d7-106">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="fd0d7-107">若要檢查哪些 JEA 工作階段已在電腦上註冊，請使用 [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-107">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="fd0d7-108">端點的有效權限列於 **Permission** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-108">The effective rights for the endpoint are listed in the **Permission** property.</span></span> <span data-ttu-id="fd0d7-109">這些使用者有權連線至 JEA 端點。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-109">These users have the right to connect to the JEA endpoint.</span></span> <span data-ttu-id="fd0d7-110">但是，他們能存取哪些角色和命令則由用來註冊端點之[工作階段設定檔](session-configurations.md)中的 **RoleDefinitions** 欄位決定。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-110">However, the roles and commands they have access to is determined by the **RoleDefinitions** property in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span> <span data-ttu-id="fd0d7-111">展開 **RoleDefinitions** 屬性中的資料，以評估已註冊的 JEA 端點中角色對應。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-111">Expand the **RoleDefinitions** property to evaluate the role mappings in a registered JEA endpoint.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="fd0d7-112">在電腦上尋找可用的角色功能</span><span class="sxs-lookup"><span data-stu-id="fd0d7-112">Find available role capabilities on the machine</span></span>

<span data-ttu-id="fd0d7-113">JEA 會從儲存在 PowerShell 模組內 **RoleCapabilities** 資料夾的 `.psrc` 檔案中取得角色功能。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-113">JEA gets role capabilities from the `.psrc` files stored in the **RoleCapabilities** folder inside a PowerShell module.</span></span> <span data-ttu-id="fd0d7-114">下列函式會尋找電腦上所有可用的角色功能。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-114">The following function finds all role capabilities available on a computer.</span></span>

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
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> <span data-ttu-id="fd0d7-115">如果多個角色功能共用相同的名稱，則此函式的結果順序不一定是角色功能的選取順序。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-115">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="fd0d7-116">檢查特定使用者的有效權限</span><span class="sxs-lookup"><span data-stu-id="fd0d7-116">Check effective rights for a specific user</span></span>

<span data-ttu-id="fd0d7-117">[Get-pssessioncapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) Cmdlet 會根據使用者的群組成員資格，列舉 JEA 端點上的所有可用命令。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-117">The [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet enumerates all the commands available on a JEA endpoint based on a user's group memberships.</span></span>
<span data-ttu-id="fd0d7-118">`Get-PSSessionCapability` 的輸出會與指定使用者在 JEA 工作階段中執行 `Get-Command -CommandType All` 的輸出相同。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-118">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="fd0d7-119">如果您的使用者不是會授與額外 JEA 權限之群組的永久成員，則這個 Cmdlet 可能不會反映這些額外的權限。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-119">If your users aren't permanent members of groups that would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span> <span data-ttu-id="fd0d7-120">使用 Just-in-Time 特殊權限的存取管理系統來允許使用者暫時屬於某個安全性群組時，會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-120">This happens when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span> <span data-ttu-id="fd0d7-121">請仔細評估使用者與角色及功能的對應，以確保使用者僅具有成功完成工作所需的存取層級。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-121">Carefully evaluate the mapping of users to roles and capabilities to ensure that users only get the level of access needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="fd0d7-122">PowerShell 事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="fd0d7-122">PowerShell event logs</span></span>

<span data-ttu-id="fd0d7-123">如果您已在系統上啟用模組或指令碼區塊記錄，您可在 Windows 事件記錄檔中找到使用者在 JEA 工作階段中執行之每個命令的事件。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-123">If you enabled module or script block logging on the system, you can see events in the Windows event logs for each command a user runs in a JEA session.</span></span> <span data-ttu-id="fd0d7-124">若要尋找這些事件，請開啟 **Microsoft-Windows-PowerShell/Operational** 事件記錄檔，然後尋找事件識別碼為 **4104** 的事件。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-124">To find these events, open **Microsoft-Windows-PowerShell/Operational** event log and look for events with event ID **4104**.</span></span>

<span data-ttu-id="fd0d7-125">每個事件記錄檔項目會包含命令執行所在工作階段的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-125">Each event log entry includes information about the session in which the command was run.</span></span> <span data-ttu-id="fd0d7-126">針對 JEA 工作階段，事件包含 **ConnectedUser** 和 **RunAsUser** 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-126">For JEA sessions, the event includes information about the **ConnectedUser** and the **RunAsUser**.</span></span> <span data-ttu-id="fd0d7-127">**ConnectedUser** 是建立 JEA 工作階段的實際使用者。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-127">The **ConnectedUser** is the actual user who created the JEA session.</span></span> <span data-ttu-id="fd0d7-128">**RunAsUser** 用來執行命令的帳戶 JEA。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-128">The **RunAsUser** is the account JEA used to execute the command.</span></span>

<span data-ttu-id="fd0d7-129">應用程式事件記錄檔會顯示正在由 **RunAsUser** 進行的變更。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-129">Application event logs show changes being made by the **RunAsUser**.</span></span> <span data-ttu-id="fd0d7-130">因此必須啟用模組和指令碼記錄，才能將特定的命令引動過程追蹤回 **ConnectedUser**。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-130">So having module and script logging enabled is required to trace a specific command invocation back to the **ConnectedUser**.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="fd0d7-131">應用程式事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="fd0d7-131">Application event logs</span></span>

<span data-ttu-id="fd0d7-132">在與外部應用程式或服務互動之 JEA 工作階段中執行的命令，可能會將事件記錄至自己的事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-132">Commands run in a JEA session that interact with external applications or services may log events to their own event logs.</span></span> <span data-ttu-id="fd0d7-133">不同於 PowerShell 記錄檔和文字記錄，其他記錄機制不會擷取 JEA 工作階段的連線使用者。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-133">Unlike PowerShell logs and transcripts, other logging mechanisms don't capture the connected user of the JEA session.</span></span> <span data-ttu-id="fd0d7-134">反之，這些應用程式只會記錄虛擬執行身分使用者。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-134">Instead, those applications only log the virtual run-as user.</span></span>
<span data-ttu-id="fd0d7-135">若要判斷誰執行了命令，您必須參閱[工作階段文字記錄](#session-transcripts)，或相互關聯 PowerShell 事件記錄檔與應用程式事件記錄檔中顯示的時間和使用者。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-135">To determine who ran the command, you need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="fd0d7-136">WinRM 記錄檔也可協助您相互關聯應用程式事件記錄檔中的執行身分使用者與連線使用者。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-136">The WinRM log can also help you correlate run-as users to the connecting user in an application event log.</span></span> <span data-ttu-id="fd0d7-137">**Microsoft-Windows-Windows 遠端管理/作業**記錄檔中的事件識別碼 **193** 會針對每個新的 JEA 工作階段，記錄連線使用者與執行身分使用者的安全性識別碼 (SID) 和帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-137">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user for every new JEA session.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="fd0d7-138">工作階段文字記錄</span><span class="sxs-lookup"><span data-stu-id="fd0d7-138">Session transcripts</span></span>

<span data-ttu-id="fd0d7-139">如果您已設定 JEA 為每個使用者工作階段建立文字記錄，則每個使用者動作的文字副本將儲存在指定的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-139">If you configured JEA to create a transcript for each user session, a text copy of every user's actions are stored in the specified folder.</span></span>

<span data-ttu-id="fd0d7-140">下列命令 (以系統管理員身分) 會尋找所有文字記錄目錄。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-140">The following command (as an administrator) finds all transcript directories.</span></span>

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="fd0d7-141">每份文字記錄開頭為工作階段的啟動時間、連線到工作階段的使用者，以及指派給他們的 JEA 身分識別等資訊。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-141">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="fd0d7-142">文字記錄的本文包含使用者所叫用每個命令的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-142">The body of the transcript contains information about each command the user invoked.</span></span> <span data-ttu-id="fd0d7-143">因為命令針對 PowerShell 遠端轉換的方式，使用此命令的正確語法不適用於 JEA 工作階段。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-143">The exact syntax of the command used is unavailable in JEA sessions because of the way commands are transformed for PowerShell remoting.</span></span> <span data-ttu-id="fd0d7-144">不過，您仍可以判斷已執行的有效命令。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-144">However, you can still determine the effective command that was executed.</span></span> <span data-ttu-id="fd0d7-145">以下是範例文字記錄程式碼片段，來自在 JEA 工作階段中執行 `Get-Service Dns` 的使用者：</span><span class="sxs-lookup"><span data-stu-id="fd0d7-145">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="fd0d7-146">**CommandInvocation** 行是針對使用者執行的每個命令所撰寫。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-146">A **CommandInvocation** line is written for each command a user runs.</span></span> <span data-ttu-id="fd0d7-147">**ParameterBindings** 會記錄命令所提供的每個參數和值。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-147">**ParameterBindings** record each parameter and value supplied with the command.</span></span> <span data-ttu-id="fd0d7-148">在上述範例中，您可以看到參數 **Name** 以值 **Dns** 提供給 `Get-Service` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-148">In the previous example, you can see that the parameter **Name** was supplied the with value **Dns** for the `Get-Service` cmdlet.</span></span>

<span data-ttu-id="fd0d7-149">每個命令的輸出也會觸發 **CommandInvocation**，通常為 `Out-Default`。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-149">The output of each command also triggers a **CommandInvocation**, usually to `Out-Default`.</span></span> <span data-ttu-id="fd0d7-150">`Out-Default` 的 **InputObject** 是由命令傳回的 PowerShell 物件。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-150">The **InputObject** of `Out-Default` is the PowerShell object returned from the command.</span></span> <span data-ttu-id="fd0d7-151">物件的詳細資料會列印在下面幾行，密切模擬使用者會看到的情況。</span><span class="sxs-lookup"><span data-stu-id="fd0d7-151">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd0d7-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd0d7-152">See also</span></span>

[<span data-ttu-id="fd0d7-153">*PowerShell ♥ 藍色小組*安全性部落格文章</span><span class="sxs-lookup"><span data-stu-id="fd0d7-153">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
