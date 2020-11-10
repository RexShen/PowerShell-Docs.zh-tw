---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionOption
ms.openlocfilehash: 566091a53941cd122a10aa2bcb45cddfb1f40cc4
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388615"
---
# <span data-ttu-id="09270-103">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="09270-103">New-PSSessionOption</span></span>

## <span data-ttu-id="09270-104">概要</span><span class="sxs-lookup"><span data-stu-id="09270-104">SYNOPSIS</span></span>
<span data-ttu-id="09270-105">建立包含 PSSession 之進階選項的物件。</span><span class="sxs-lookup"><span data-stu-id="09270-105">Creates an object that contains advanced options for a PSSession.</span></span>

## <span data-ttu-id="09270-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="09270-106">SYNTAX</span></span>

```
New-PSSessionOption [-MaximumRedirection <Int32>] [-NoCompression] [-NoMachineProfile] [-Culture <CultureInfo>]
 [-UICulture <CultureInfo>] [-MaximumReceivedDataSizePerCommand <Int32>] [-MaximumReceivedObjectSize <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-MaxConnectionRetryCount <Int32>]
 [-ApplicationArguments <PSPrimitiveDictionary>] [-OpenTimeout <Int32>] [-CancelTimeout <Int32>]
 [-IdleTimeout <Int32>] [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <AuthenticationMechanism>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [-IncludePortInSPN] [<CommonParameters>]
```

## <span data-ttu-id="09270-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="09270-107">DESCRIPTION</span></span>

<span data-ttu-id="09270-108">`New-PSSessionOption`Cmdlet 會建立一個物件，其中包含使用者管理的會話 ( **PSSession** ) 的 advanced 選項。</span><span class="sxs-lookup"><span data-stu-id="09270-108">The `New-PSSessionOption` cmdlet creates an object that contains advanced options for a user-managed session ( **PSSession** ).</span></span> <span data-ttu-id="09270-109">您可以使用物件作為建立 **PSSession** 之 Cmdlet 的 **SessionOption** 參數值，例如 `New-PSSession` 、 `Enter-PSSession` 和 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="09270-109">You can use the object as the value of the **SessionOption** parameter of cmdlets that create a **PSSession** , such as `New-PSSession`, `Enter-PSSession`, and `Invoke-Command`.</span></span>

<span data-ttu-id="09270-110">如果沒有參數，會 `New-PSSessionOption` 產生包含所有選項之預設值的物件。</span><span class="sxs-lookup"><span data-stu-id="09270-110">Without parameters, `New-PSSessionOption` generates an object that contains the default values for all of the options.</span></span> <span data-ttu-id="09270-111">因為所有屬性都可以編輯，所以您可以使用產生的物件作為範本，然後為您的企業建立標準選項物件。</span><span class="sxs-lookup"><span data-stu-id="09270-111">Because all of the properties can be edited, you can use the resulting object as a template, and create standard option objects for your enterprise.</span></span>

<span data-ttu-id="09270-112">您也可以在喜好設定變數中儲存會話選項物件 `$PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="09270-112">You can also save a session option object in the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="09270-113">此變數的值會替工作階段選項建立新的預設值。</span><span class="sxs-lookup"><span data-stu-id="09270-113">The values of this variable establish new default values for the session options.</span></span> <span data-ttu-id="09270-114">在沒有為工作階段設定任何工作階段選項時，它們就會生效，而且它們的優先順序高於在工作階段設定中設定的選項，但是您可以透過在建立工作階段的 Cmdlet 中，指定工作階段選項或工作階段選項物件來覆寫它們。</span><span class="sxs-lookup"><span data-stu-id="09270-114">They effective when no session options are set for the session and they take precedence over options set in the session configuration, but you can override them by specifying session options or a session option object in a cmdlet that creates a session.</span></span> <span data-ttu-id="09270-115">如需喜好設定變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="09270-115">For more information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="09270-116">當您在建立工作階段的 Cmdlet 中使用工作階段選項物件時，工作階段選項值的優先順序高於在 $PSSessionOption 喜好設定變數和工作階段設定中設定的工作階段預設值。</span><span class="sxs-lookup"><span data-stu-id="09270-116">When you use a session option object in a cmdlet that creates a session, the session option values take precedence over default values for sessions set in the $PSSessionOption preference variable and in the session configuration.</span></span> <span data-ttu-id="09270-117">不過，它們的優先順序不會高於工作階段設定中設定的最大值、配額或限制。</span><span class="sxs-lookup"><span data-stu-id="09270-117">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span> <span data-ttu-id="09270-118">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="09270-118">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="09270-119">範例</span><span class="sxs-lookup"><span data-stu-id="09270-119">EXAMPLES</span></span>

### <span data-ttu-id="09270-120">範例1：建立預設會話選項</span><span class="sxs-lookup"><span data-stu-id="09270-120">Example 1: Create a default session option</span></span>

<span data-ttu-id="09270-121">此命令會建立具有所有預設值的會話選項物件。</span><span class="sxs-lookup"><span data-stu-id="09270-121">This command creates a session option object that has all of the default values.</span></span>

```powershell
New-PSSessionOption
```

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

### <span data-ttu-id="09270-122">範例2：使用會話選項物件設定會話</span><span class="sxs-lookup"><span data-stu-id="09270-122">Example 2: Configure a session by using a session option object</span></span>

<span data-ttu-id="09270-123">此範例說明如何使用工作階段選項物件設定工作階段。</span><span class="sxs-lookup"><span data-stu-id="09270-123">This example shows how to use a session option object to configure a session.</span></span>

```powershell
$pso = New-PSSessionOption -Culture "fr-fr" -MaximumReceivedObjectSize 10MB
New-PSSession -ComputerName Server01 -SessionOption $pso
```

<span data-ttu-id="09270-124">第一個命令會建立新的會話選項物件，並將它儲存在變數的值中 `$pso` 。</span><span class="sxs-lookup"><span data-stu-id="09270-124">The first command creates a new session option object and saves it in the value of the `$pso` variable.</span></span> <span data-ttu-id="09270-125">第二個命令會使用 `New-PSSession` Cmdlet 在 Server01 遠端電腦上建立會話。</span><span class="sxs-lookup"><span data-stu-id="09270-125">The second command uses the `New-PSSession` cmdlet to create a session on the Server01 remote computer.</span></span> <span data-ttu-id="09270-126">此命令會使用變數值中的 session 選項物件 `$pso` 做為命令的 **SessionOption** 參數值。</span><span class="sxs-lookup"><span data-stu-id="09270-126">The command uses the session option object in the value of the `$pso` variable as the value of the **SessionOption** parameter of the command.</span></span>

### <span data-ttu-id="09270-127">範例3：啟動互動式會話</span><span class="sxs-lookup"><span data-stu-id="09270-127">Example 3: Start an interactive session</span></span>

<span data-ttu-id="09270-128">此命令會使用 `Enter-PSSession` Cmdlet 來啟動 Server01 電腦的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="09270-128">This command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

```powershell
Enter-PSSession -ComputerName Server01 -SessionOption (New-PSSessionOption -NoEncryption -NoCompression)
```

<span data-ttu-id="09270-129">**SessionOption** 參數的值是 `New-PSSessionOption` 具有 **nocompression** 和 **NoCompression** 參數的命令。</span><span class="sxs-lookup"><span data-stu-id="09270-129">The value of the **SessionOption** parameter is a `New-PSSessionOption` command that has the **NoEncryption** and **NoCompression** parameters.</span></span>

<span data-ttu-id="09270-130">此 `New-PSSessionOption` 命令會以括弧括住，以確保它會在命令之前執行 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="09270-130">The `New-PSSessionOption` command is enclosed in parentheses to make sure that it runs before the `Enter-PSSession` command.</span></span>

### <span data-ttu-id="09270-131">範例4：修改會話選項物件</span><span class="sxs-lookup"><span data-stu-id="09270-131">Example 4: Modify a session option object</span></span>

<span data-ttu-id="09270-132">這個範例示範您可以修改會話選項物件。</span><span class="sxs-lookup"><span data-stu-id="09270-132">This example demonstrates that you can modify the session option object.</span></span> <span data-ttu-id="09270-133">所有屬性皆具有讀取/寫入值。</span><span class="sxs-lookup"><span data-stu-id="09270-133">All properties have read/write values.</span></span>

```powershell
$a = New-PSSessionOption
$a.OpenTimeout
```

```Output
Days              : 0
Hours             : 0
Minutes           : 3
Seconds           : 0
Milliseconds      : 0
Ticks             : 1800000000
TotalDays         : 0.00208333333333333
TotalHours        : 0.05
TotalMinutes      : 3
TotalSeconds      : 180
TotalMilliseconds : 180000
```

```powershell
$a.UICulture = (Get-UICulture)
$a.OpenTimeout = (New-Timespan -Minutes 4)
$a.MaximumConnectionRedirectionCount = 1
$a
```

```Output
MaximumConnectionRedirectionCount : 1
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         : en-US
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:04:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

<span data-ttu-id="09270-134">請使用此方法為您的企業建立標準工作階段物件，然後用它來針對特定用途建立自訂版本。</span><span class="sxs-lookup"><span data-stu-id="09270-134">Use this method to create a standard session object for your enterprise, and then create customized versions of it for particular uses.</span></span>

### <span data-ttu-id="09270-135">範例5：建立喜好設定變數</span><span class="sxs-lookup"><span data-stu-id="09270-135">Example 5: Create a preference variable</span></span>

<span data-ttu-id="09270-136">此命令會建立 `$PSSessionOption` 喜好設定變數。</span><span class="sxs-lookup"><span data-stu-id="09270-136">This command creates a `$PSSessionOption` preference variable.</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -OpenTimeOut 120000
```

<span data-ttu-id="09270-137">當 `$PSSessionOption` 喜好設定變數發生在會話中時，它會在使用 `New-PSSession` 、 `Enter-PSSession` 和 Cmdlet 建立的會話中，建立選項的預設值 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="09270-137">When the `$PSSessionOption` preference variable occurs in the session, it establishes default values for options in the sessions that are created by using the `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="09270-138">若要讓 `$PSSessionOption` 變數在所有會話中都可使用，請將它新增至您的 powershell 會話和 powershell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="09270-138">To make the `$PSSessionOption` variable available in all sessions, add it to your PowerShell session and to your PowerShell profile.</span></span>

<span data-ttu-id="09270-139">如需喜好設定變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="09270-139">For more information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>
<span data-ttu-id="09270-140">如需設定檔的詳細資訊，請參閱 [about_Profiles](About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="09270-140">For more information about profiles, see [about_Profiles](About/about_Profiles.md).</span></span>

### <span data-ttu-id="09270-141">範例6：滿足遠端會話設定的需求</span><span class="sxs-lookup"><span data-stu-id="09270-141">Example 6: Fulfill the requirements for a remote session configuration</span></span>

<span data-ttu-id="09270-142">此範例說明如何使用 **SessionOption** 物件來滿足遠端工作階段設定的要求。</span><span class="sxs-lookup"><span data-stu-id="09270-142">This example shows how to use a **SessionOption** object to fulfill the requirements for a remote session configuration.</span></span>

```powershell
$skipCN = New-PSSessionOption -SkipCNCheck
New-PSSession -ComputerName 171.09.21.207 -UseSSL -Credential Domain01\User01 -SessionOption $SkipCN
```

<span data-ttu-id="09270-143">第一個命令會使用 `New-PSSessionOption` Cmdlet 來建立具有 **SkipCNCheck** 屬性的會話選項物件。</span><span class="sxs-lookup"><span data-stu-id="09270-143">The first command uses the `New-PSSessionOption` cmdlet to create a session option object that has the **SkipCNCheck** property.</span></span> <span data-ttu-id="09270-144">此命令會將產生的會話物件儲存在 `$skipCN` 變數中。</span><span class="sxs-lookup"><span data-stu-id="09270-144">The command saves the resulting session object in the `$skipCN` variable.</span></span>

<span data-ttu-id="09270-145">第二個命令會使用 `New-PSSession` Cmdlet 在遠端電腦上建立新的會話。</span><span class="sxs-lookup"><span data-stu-id="09270-145">The second command uses the `New-PSSession` cmdlet to create a new session on a remote computer.</span></span> <span data-ttu-id="09270-146">`$skipCN`檢查變數會在 **SessionOption** 參數的值中使用。</span><span class="sxs-lookup"><span data-stu-id="09270-146">The `$skipCN` check variable is used in the value of the **SessionOption** parameter.</span></span>

<span data-ttu-id="09270-147">因為電腦是透過其 IP 位址來識別，所以 **ComputerName** 參數的值不符合用於安全通訊端層 (SSL) 之憑證中的任何一般名稱。</span><span class="sxs-lookup"><span data-stu-id="09270-147">Because the computer is identified by its IP address, the value of the **ComputerName** parameter does not match any of the common names in the certificate that is used for Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="09270-148">因此，需要 **SkipCNCheck** 選項。</span><span class="sxs-lookup"><span data-stu-id="09270-148">As a result, the **SkipCNCheck** option is required.</span></span>

### <span data-ttu-id="09270-149">範例7：讓引數可供遠端會話使用</span><span class="sxs-lookup"><span data-stu-id="09270-149">Example 7: Make arguments available to a remote session</span></span>

<span data-ttu-id="09270-150">此範例示範如何使用 Cmdlet 的 **ApplicationArguments** 參數 `New-PSSessionOption` ，讓其他資料可供遠端會話使用。</span><span class="sxs-lookup"><span data-stu-id="09270-150">This example shows how to use the **ApplicationArguments** parameter of the `New-PSSessionOption` cmdlet to make additional data available to the remote session.</span></span>

```powershell
$team = @{Team="IT"; Use="Testing"}
$TeamOption = New-PSSessionOption -ApplicationArguments $team
$s = New-PSSession -ComputerName Server01 -SessionOption $TeamOption
Invoke-Command -Session $s {$PSSenderInfo.ApplicationArguments}
```

```Output
Name                 Value
----                 -----
Team                 IT
Use                  Testing
PSVersionTable       {CLRVersion, BuildVersion, PSVersion, WSManStackVersion...}
```

```powershell
Invoke-Command -Session $s {
  if ($PSSenderInfo.ApplicationArguments.Use -ne "Testing") {
    .\logFiles.ps1
  }
  else {
    "Just testing."
  }
}
```

```Output
Just testing.
```

<span data-ttu-id="09270-151">第一個命令會建立包含兩個索引鍵（ **Team** 和 **Use** ）的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="09270-151">The first command creates a hash table with two keys, **Team** and **Use**.</span></span> <span data-ttu-id="09270-152">此命令會將雜湊表儲存在 `$team` 變數中。</span><span class="sxs-lookup"><span data-stu-id="09270-152">The command saves the hash table in the `$team` variable.</span></span> <span data-ttu-id="09270-153">如需雜湊表的相關詳細資訊，請參閱 [about_Hash_Tables](about/about_Hash_Tables.md)。</span><span class="sxs-lookup"><span data-stu-id="09270-153">For more information about hash tables, see [about_Hash_Tables](about/about_Hash_Tables.md).</span></span>

<span data-ttu-id="09270-154">接下來， `New-PSSessionOption` 使用 **ApplicationArguments** 參數的 Cmdlet 會建立儲存在變數中的會話選項物件 `$team` 。</span><span class="sxs-lookup"><span data-stu-id="09270-154">Next, the `New-PSSessionOption` cmdlet, using the **ApplicationArguments** parameter, creates a session option object saved in the `$team` variable.</span></span> <span data-ttu-id="09270-155">當 `New-PSSessionOption` 建立會話選項物件時，它會自動將 **ApplicationArguments** 參數值中的雜湊表轉換成基本字典，以便將資料可靠地傳輸至遠端會話。</span><span class="sxs-lookup"><span data-stu-id="09270-155">When `New-PSSessionOption` creates the session option object, it automatically converts the hash table in the value of the **ApplicationArguments** parameter to a primitive dictionary so the data can be reliably transmitted to the remote session.</span></span>

<span data-ttu-id="09270-156">`New-PSSession`Cmdlet 會啟動 Server01 電腦上的會話。</span><span class="sxs-lookup"><span data-stu-id="09270-156">The `New-PSSession` cmdlet starts a session on the Server01 computer.</span></span> <span data-ttu-id="09270-157">它會使用 **SessionOption** 參數將選項包含在變數中 `$teamOption` 。</span><span class="sxs-lookup"><span data-stu-id="09270-157">It uses the **SessionOption** parameter to include the options in the `$teamOption` variable.</span></span>

<span data-ttu-id="09270-158">此 `Invoke-Command` Cmdlet 會示範變數中的資料 `$team` 可供遠端會話中的命令使用。</span><span class="sxs-lookup"><span data-stu-id="09270-158">The `Invoke-Command` cmdlet demonstrates that the data in the `$team` variable is available to commands in the remote session.</span></span> <span data-ttu-id="09270-159">資料會出現在自動變數的 **ApplicationArguments** 屬性中 `$PSSenderInfo` 。</span><span class="sxs-lookup"><span data-stu-id="09270-159">The data appears in the **ApplicationArguments** property of the `$PSSenderInfo` automatic variable.</span></span>

<span data-ttu-id="09270-160">最後 `Invoke-Command` 會顯示如何使用資料。</span><span class="sxs-lookup"><span data-stu-id="09270-160">The final `Invoke-Command` shows how the data might be used.</span></span>

## <span data-ttu-id="09270-161">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="09270-161">PARAMETERS</span></span>

### <span data-ttu-id="09270-162">-ApplicationArguments</span><span class="sxs-lookup"><span data-stu-id="09270-162">-ApplicationArguments</span></span>

<span data-ttu-id="09270-163">指定傳送至遠端工作階段的基本字典。</span><span class="sxs-lookup"><span data-stu-id="09270-163">Specifies a primitive dictionary that is sent to the remote session.</span></span> <span data-ttu-id="09270-164">遠端會話中的命令和腳本（包括會話設定中的啟動腳本）可以在自動變數的 **ApplicationArguments** 屬性中找到此字典 `$PSSenderInfo` 。</span><span class="sxs-lookup"><span data-stu-id="09270-164">Commands and scripts in the remote session, including startup scripts in the session configuration, can find this dictionary in the **ApplicationArguments** property of the `$PSSenderInfo` automatic variable.</span></span> <span data-ttu-id="09270-165">您可以使用此參數將資料傳送至遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="09270-165">You can use this parameter to send data to the remote session.</span></span>

<span data-ttu-id="09270-166">如需詳細資訊，請參閱 [about_Hash_Tables](about/about_Hash_Tables.md)、 [about_Session_Configurations](About/about_Session_Configurations.md)和 [about_Automatic_Variables](about/about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="09270-166">For more information, see [about_Hash_Tables](about/about_Hash_Tables.md), [about_Session_Configurations](About/about_Session_Configurations.md), and [about_Automatic_Variables](about/about_Automatic_Variables.md).</span></span>

```yaml
Type: System.Management.Automation.PSPrimitiveDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09270-167">-CancelTimeout</span><span class="sxs-lookup"><span data-stu-id="09270-167">-CancelTimeout</span></span>

<span data-ttu-id="09270-168">判斷 PowerShell 等候取消作業 (CTRL + C) 在結束之前完成的時間。</span><span class="sxs-lookup"><span data-stu-id="09270-168">Determines how long PowerShell waits for a cancel operation (CTRL+C) to finish before ending it.</span></span>
<span data-ttu-id="09270-169">輸入以毫秒為單位的值。</span><span class="sxs-lookup"><span data-stu-id="09270-169">Enter a value in milliseconds.</span></span>

<span data-ttu-id="09270-170">預設值為 60000 (一分鐘)。</span><span class="sxs-lookup"><span data-stu-id="09270-170">The default value is 60000 (one minute).</span></span> <span data-ttu-id="09270-171">值為 0 (零) 表示無逾時；命令會無限期繼續執行。</span><span class="sxs-lookup"><span data-stu-id="09270-171">A value of 0 (zero) means no time-out; the command continues indefinitely.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: CancelTimeoutMSec

Required: False
Position: Named
Default value: 60000
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09270-172">-Culture</span><span class="sxs-lookup"><span data-stu-id="09270-172">-Culture</span></span>

<span data-ttu-id="09270-173">指定要用於工作階段的文化特性。</span><span class="sxs-lookup"><span data-stu-id="09270-173">Specifies the culture to use for the session.</span></span> <span data-ttu-id="09270-174">以格式輸入文化特性名稱 `<languagecode2>-<country/regioncode2>` (例如 `ja-JP`) 、包含 **cultureinfo** 物件的變數，或可取得 **cultureinfo** 物件的命令。</span><span class="sxs-lookup"><span data-stu-id="09270-174">Enter a culture name in `<languagecode2>-<country/regioncode2>` format (like `ja-JP`), a variable that contains a **CultureInfo** object, or a command that gets a **CultureInfo** object.</span></span>

<span data-ttu-id="09270-175">預設值為 `$Null` ，而在作業系統中設定的文化特性會在會話中使用。</span><span class="sxs-lookup"><span data-stu-id="09270-175">The default value is `$Null`, and the culture that is set in the operating system is used in the session.</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09270-176">-IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="09270-176">-IdleTimeout</span></span>

<span data-ttu-id="09270-177">決定當遠端電腦未收到來自本機電腦的任何通訊時，會話保持開啟的時間長度。</span><span class="sxs-lookup"><span data-stu-id="09270-177">Determines how long the session stays open if the remote computer does not receive any communication from the local computer.</span></span> <span data-ttu-id="09270-178">這包括了信號信號。</span><span class="sxs-lookup"><span data-stu-id="09270-178">This includes the heartbeat signal.</span></span> <span data-ttu-id="09270-179">當間隔時間過期時，工作階段就會關閉。</span><span class="sxs-lookup"><span data-stu-id="09270-179">When the interval expires, the session closes.</span></span>

<span data-ttu-id="09270-180">如果您想要中斷連線並重新連線到會話，閒置的超時值是很重要的。</span><span class="sxs-lookup"><span data-stu-id="09270-180">The idle time-out value is of significant importance if you intend to disconnect and reconnect to a session.</span></span> <span data-ttu-id="09270-181">您只能在工作階段尚未逾時時重新連線。</span><span class="sxs-lookup"><span data-stu-id="09270-181">You can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="09270-182">輸入以毫秒為單位的值。</span><span class="sxs-lookup"><span data-stu-id="09270-182">Enter a value in milliseconds.</span></span> <span data-ttu-id="09270-183">最小值為 60000 (1 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="09270-183">The minimum value is 60000 (1 minute).</span></span> <span data-ttu-id="09270-184">最大值為工作階段設定之 **MaxIdleTimeoutms** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="09270-184">The maximum is the value of the **MaxIdleTimeoutms** property of the session configuration.</span></span> <span data-ttu-id="09270-185">預設值-1 不會設定閒置的超時時間。</span><span class="sxs-lookup"><span data-stu-id="09270-185">The default value, -1, does not set an idle time-out.</span></span>

<span data-ttu-id="09270-186">會話會使用會話選項中設定的空閒超時時間（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="09270-186">The session uses the idle time-out that is set in the session options, if any.</span></span> <span data-ttu-id="09270-187">如果未設定 (-1) ，會話就會使用會話設定的 **IdleTimeoutMs** 屬性值或 WSMan shell 超時值 (`WSMan:\<ComputerName>\Shell\IdleTimeout`) （以最短者為准）。</span><span class="sxs-lookup"><span data-stu-id="09270-187">If none is set (-1), the session uses the value of the **IdleTimeoutMs** property of the session configuration or the WSMan shell time-out value (`WSMan:\<ComputerName>\Shell\IdleTimeout`), whichever is shortest.</span></span>

<span data-ttu-id="09270-188">如果工作階段選項中設定的閒置逾時超出工作階段設定之 **MaxIdleTimeoutMs** 屬性的值，建立工作階段的命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="09270-188">If the idle timeout set in the session options exceeds the value of the **MaxIdleTimeoutMs** property of the session configuration, the command to create a session fails.</span></span>

<span data-ttu-id="09270-189">**預設的** **IdleTimeoutMs** 值為7200000毫秒 (2 小時) 。</span><span class="sxs-lookup"><span data-stu-id="09270-189">The **IdleTimeoutMs** value of the default **Microsoft.PowerShell** session configuration is 7200000 milliseconds (2 hours).</span></span> <span data-ttu-id="09270-190">其 **MaxIdleTimeoutMs** 值為2147483647毫秒 (\> 24 天) 。</span><span class="sxs-lookup"><span data-stu-id="09270-190">Its **MaxIdleTimeoutMs** value is 2147483647 milliseconds (\>24 days).</span></span> <span data-ttu-id="09270-191">WSMan shell 空閒超時 () 的預設值 `WSMan:\<ComputerName>\Shell\IdleTimeout` 為7200000毫秒 (2 小時) 。</span><span class="sxs-lookup"><span data-stu-id="09270-191">The default value of the WSMan shell idle time-out (`WSMan:\<ComputerName>\Shell\IdleTimeout`) is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="09270-192">從會話中斷連線或重新連線至會話時，會話的閒置超時值也可以變更。</span><span class="sxs-lookup"><span data-stu-id="09270-192">The idle time-out value of a session can also be changed when disconnecting from a session or reconnecting to a session.</span></span> <span data-ttu-id="09270-193">如需詳細資訊，請參閱 `Disconnect-PSSession` 和 `Connect-PSSession`。</span><span class="sxs-lookup"><span data-stu-id="09270-193">For more information, see `Disconnect-PSSession` and `Connect-PSSession`.</span></span>

<span data-ttu-id="09270-194">在 Windows PowerShell 2.0 中， **IdleTimeout** 參數的預設值為 240000 (4 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="09270-194">In Windows PowerShell 2.0, the default value of the **IdleTimeout** parameter is 240000 (4 minutes).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: IdleTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09270-195">-IncludePortInSPN</span><span class="sxs-lookup"><span data-stu-id="09270-195">-IncludePortInSPN</span></span>

<span data-ttu-id="09270-196">在服務主體名稱中包含通訊埠編號 (SPN) 用於 Kerberos 驗證，例如 `HTTP://<ComputerName>:5985` 。</span><span class="sxs-lookup"><span data-stu-id="09270-196">Includes the port number in the Service Principal Name (SPN) used for Kerberos authentication, for example, `HTTP://<ComputerName>:5985`.</span></span> <span data-ttu-id="09270-197">此選項允許使用非預設 SPN 的用戶端，向使用 Kerberos 驗證的遠端電腦進行驗證。</span><span class="sxs-lookup"><span data-stu-id="09270-197">This option allows a client that uses a non-default SPN to authenticate against a remote computer that uses Kerberos authentication.</span></span>

<span data-ttu-id="09270-198">此選項是針對支援 Kerberos 驗證的多項服務在不同使用者帳戶底下執行的企業所設計。</span><span class="sxs-lookup"><span data-stu-id="09270-198">The option is designed for enterprises where multiple services that support Kerberos authentication are running under different user accounts.</span></span> <span data-ttu-id="09270-199">例如，允許 Kerberos 驗證的 IIS 應用程式可能需要將預設 SPN 註冊至與電腦帳戶不同的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="09270-199">For example, an IIS application that allows for Kerberos authentication can require the default SPN to be registered to a user account that differs from the computer account.</span></span> <span data-ttu-id="09270-200">在這種情況下，PowerShell 遠端處理無法使用 Kerberos 進行驗證，因為它需要已向電腦帳戶註冊的 SPN。</span><span class="sxs-lookup"><span data-stu-id="09270-200">In such cases, PowerShell remoting cannot use Kerberos to authenticate because it requires an SPN that is registered to the computer account.</span></span> <span data-ttu-id="09270-201">若要解決這個問題，系統管理員可以建立不同的 Spn，例如使用 **Setspn.exe** 註冊到不同的使用者帳戶，並可透過在 SPN 中包含埠號碼來區分它們。</span><span class="sxs-lookup"><span data-stu-id="09270-201">To resolve this problem, administrators can create different SPNs, such as by using **Setspn.exe** , that are registered to different user accounts and can distinguish between them by including the port number in the SPN.</span></span>

<span data-ttu-id="09270-202">如需詳細資訊，請參閱 [Setspn 總覽](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10))。</span><span class="sxs-lookup"><span data-stu-id="09270-202">For more information, see [Setspn Overview](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).</span></span>

<span data-ttu-id="09270-203">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="09270-203">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="09270-204">-MaxConnectionRetryCount</span><span class="sxs-lookup"><span data-stu-id="09270-204">-MaxConnectionRetryCount</span></span>

<span data-ttu-id="09270-205">指定當目前的嘗試因網路問題而失敗時，PowerShell 嘗試連接至目的電腦的次數。</span><span class="sxs-lookup"><span data-stu-id="09270-205">Specifies the number of times that PowerShell attempts to make a connection to a target machine if the current attempt fails due to network issues.</span></span> <span data-ttu-id="09270-206">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="09270-206">The default value is 5.</span></span>

<span data-ttu-id="09270-207">已針對 PowerShell 5.0 版新增此參數。</span><span class="sxs-lookup"><span data-stu-id="09270-207">This parameter was added for PowerShell version 5.0.</span></span>

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

### <span data-ttu-id="09270-208">-MaximumReceivedDataSizePerCommand</span><span class="sxs-lookup"><span data-stu-id="09270-208">-MaximumReceivedDataSizePerCommand</span></span>

<span data-ttu-id="09270-209">指定本機電腦可以在單一命令中從遠端電腦收到的位元組數上限。</span><span class="sxs-lookup"><span data-stu-id="09270-209">Specifies the maximum number of bytes that the local computer can receive from the remote computer in a single command.</span></span> <span data-ttu-id="09270-210">輸入以位元組為單位的值。</span><span class="sxs-lookup"><span data-stu-id="09270-210">Enter a value in bytes.</span></span> <span data-ttu-id="09270-211">依照預設，並沒有資料大小限制。</span><span class="sxs-lookup"><span data-stu-id="09270-211">By default, there is no data size limit.</span></span>

<span data-ttu-id="09270-212">此選項是為了保護用戶端電腦上的資源而設計。</span><span class="sxs-lookup"><span data-stu-id="09270-212">This option is designed to protect the resources on the client computer.</span></span>

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

### <span data-ttu-id="09270-213">-MaximumReceivedObjectSize</span><span class="sxs-lookup"><span data-stu-id="09270-213">-MaximumReceivedObjectSize</span></span>

<span data-ttu-id="09270-214">指定本機電腦可從遠端電腦接收之物件的大小上限。</span><span class="sxs-lookup"><span data-stu-id="09270-214">Specifies the maximum size of an object that the local computer can receive from the remote computer.</span></span> <span data-ttu-id="09270-215">此選項是為了保護用戶端電腦上的資源而設計。</span><span class="sxs-lookup"><span data-stu-id="09270-215">This option is designed to protect the resources on the client computer.</span></span> <span data-ttu-id="09270-216">輸入以位元組為單位的值。</span><span class="sxs-lookup"><span data-stu-id="09270-216">Enter a value in bytes.</span></span>

<span data-ttu-id="09270-217">在 Windows PowerShell 2.0 中，如果您省略此參數，就不會有物件大小限制。</span><span class="sxs-lookup"><span data-stu-id="09270-217">In Windows PowerShell 2.0, if you omit this parameter, there is no object size limit.</span></span> <span data-ttu-id="09270-218">從 Windows PowerShell 3.0 開始，如果您省略此參數，預設值為 200 MB。</span><span class="sxs-lookup"><span data-stu-id="09270-218">Beginning in Windows PowerShell 3.0, if you omit this parameter, the default value is 200 MB.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 200 MB
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09270-219">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="09270-219">-MaximumRedirection</span></span>

<span data-ttu-id="09270-220">判斷在連接失敗之前，PowerShell 將連接重新導向至替代統一資源識別項 (URI) 的次數。</span><span class="sxs-lookup"><span data-stu-id="09270-220">Determines how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="09270-221">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="09270-221">The default value is 5.</span></span> <span data-ttu-id="09270-222">值為 0 (零) 將禁止所有重新導向。</span><span class="sxs-lookup"><span data-stu-id="09270-222">A value of 0 (zero) prevents all redirection.</span></span>

<span data-ttu-id="09270-223">只有在建立會話的命令中使用 **AllowRedirection** 參數時，會話中才會使用此選項。</span><span class="sxs-lookup"><span data-stu-id="09270-223">This option is used in the session only when the **AllowRedirection** parameter is used in the command that creates the session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09270-224">-NoCompression</span><span class="sxs-lookup"><span data-stu-id="09270-224">-NoCompression</span></span>

<span data-ttu-id="09270-225">關閉工作階段中的封包壓縮。</span><span class="sxs-lookup"><span data-stu-id="09270-225">Turns off packet compression in the session.</span></span> <span data-ttu-id="09270-226">壓縮會使用更多處理器週期，但是它可以加快傳輸速度。</span><span class="sxs-lookup"><span data-stu-id="09270-226">Compression uses more processor cycles, but it makes transmission faster.</span></span>

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

### <span data-ttu-id="09270-227">-NoEncryption</span><span class="sxs-lookup"><span data-stu-id="09270-227">-NoEncryption</span></span>

<span data-ttu-id="09270-228">關閉資料加密。</span><span class="sxs-lookup"><span data-stu-id="09270-228">Turns off data encryption.</span></span>

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

### <span data-ttu-id="09270-229">-NoMachineProfile</span><span class="sxs-lookup"><span data-stu-id="09270-229">-NoMachineProfile</span></span>

<span data-ttu-id="09270-230">避免載入使用者的 Windows 使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="09270-230">Prevents loading the user's Windows user profile.</span></span> <span data-ttu-id="09270-231">如此一來，可能可以更快速地建立工作階段，但是工作階段中將沒有使用者特定登錄設定、像是環境變數這樣的項目以及憑證可用。</span><span class="sxs-lookup"><span data-stu-id="09270-231">As a result, the session might be created faster, but user-specific registry settings, items such as environment variables, and certificates are not available in the session.</span></span>

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

### <span data-ttu-id="09270-232">-OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="09270-232">-OpenTimeout</span></span>

<span data-ttu-id="09270-233">決定用戶端電腦等待建立工作階段連線的時間。</span><span class="sxs-lookup"><span data-stu-id="09270-233">Determines how long the client computer waits for the session connection to be established.</span></span> <span data-ttu-id="09270-234">當間隔時間過期時，建立連線的命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="09270-234">When the interval expires, the command to establish the connection fails.</span></span> <span data-ttu-id="09270-235">輸入以毫秒為單位的值。</span><span class="sxs-lookup"><span data-stu-id="09270-235">Enter a value in milliseconds.</span></span>

<span data-ttu-id="09270-236">預設值為 180000 (3 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="09270-236">The default value is 180000 (3 minutes).</span></span> <span data-ttu-id="09270-237">值為 0 (零) 表示無逾時；命令會無限期繼續執行。</span><span class="sxs-lookup"><span data-stu-id="09270-237">A value of 0 (zero) means no time-out; the command continues indefinitely.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OpenTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09270-238">-OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="09270-238">-OperationTimeout</span></span>

<span data-ttu-id="09270-239">決定工作階段中任何操作可以執行的最長時間。</span><span class="sxs-lookup"><span data-stu-id="09270-239">Determines the maximum time that any operation in the session can run.</span></span> <span data-ttu-id="09270-240">當間隔時間過期時，操作就會失敗</span><span class="sxs-lookup"><span data-stu-id="09270-240">When the interval expires, the operation fails.</span></span> <span data-ttu-id="09270-241">輸入以毫秒為單位的值。</span><span class="sxs-lookup"><span data-stu-id="09270-241">Enter a value in milliseconds.</span></span>

<span data-ttu-id="09270-242">預設值為 180000 (3 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="09270-242">The default value is 180000 (3 minutes).</span></span> <span data-ttu-id="09270-243">值為 0 (零) 表示無逾時；操作會無限期繼續執行。</span><span class="sxs-lookup"><span data-stu-id="09270-243">A value of 0 (zero) means no time-out; the operation continues indefinitely.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09270-244">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="09270-244">-OutputBufferingMode</span></span>

<span data-ttu-id="09270-245">決定在輸出緩衝區已滿時，在中斷連線的工作階段中管理命令輸出的方式。</span><span class="sxs-lookup"><span data-stu-id="09270-245">Determines how command output is managed in disconnected sessions when the output buffer becomes full.</span></span>

<span data-ttu-id="09270-246">如果工作階段或工作階段設定中沒有設定輸出緩衝處理模式，預設值為 **Block** 。</span><span class="sxs-lookup"><span data-stu-id="09270-246">If the output buffering mode is not set in the session or in the session configuration, the default value is **Block**.</span></span> <span data-ttu-id="09270-247">使用者也可以在中斷連線工作階段時變更輸出緩衝處理模式。</span><span class="sxs-lookup"><span data-stu-id="09270-247">Users can also change the output buffering mode when disconnecting the session.</span></span>

<span data-ttu-id="09270-248">如果您省略此參數，會話選項物件之 **OutputBufferingMode** 的值為 None。</span><span class="sxs-lookup"><span data-stu-id="09270-248">If you omit this parameter, the value of the **OutputBufferingMode** of the session option object is None.</span></span> <span data-ttu-id="09270-249">**Block** 或 **Drop** 的值會覆寫工作階段設定中所設定的輸出緩衝模式傳輸選項。</span><span class="sxs-lookup"><span data-stu-id="09270-249">A value of **Block** or **Drop** overrides the output buffering mode transport option set in the session configuration.</span></span> <span data-ttu-id="09270-250">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="09270-250">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="09270-251">區塊。</span><span class="sxs-lookup"><span data-stu-id="09270-251">Block.</span></span> <span data-ttu-id="09270-252">當輸出緩衝區已滿時，會暫停執行直到清除緩衝區為止。</span><span class="sxs-lookup"><span data-stu-id="09270-252">When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="09270-253">Drop：</span><span class="sxs-lookup"><span data-stu-id="09270-253">Drop.</span></span> <span data-ttu-id="09270-254">當輸出緩衝區已滿時，會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="09270-254">When the output buffer is full, execution continues.</span></span> <span data-ttu-id="09270-255">儲存新的輸出時，會捨棄最舊的輸出。</span><span class="sxs-lookup"><span data-stu-id="09270-255">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="09270-256">無。</span><span class="sxs-lookup"><span data-stu-id="09270-256">None.</span></span> <span data-ttu-id="09270-257">未指定輸出緩衝模式。</span><span class="sxs-lookup"><span data-stu-id="09270-257">No output buffering mode is specified.</span></span>

<span data-ttu-id="09270-258">如需輸出緩衝模式傳輸選項的詳細資訊，請參閱 `New-PSTransportOption` 。</span><span class="sxs-lookup"><span data-stu-id="09270-258">For more information about the output buffering mode transport option, see `New-PSTransportOption`.</span></span>

<span data-ttu-id="09270-259">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="09270-259">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09270-260">-ProxyAccessType</span><span class="sxs-lookup"><span data-stu-id="09270-260">-ProxyAccessType</span></span>

<span data-ttu-id="09270-261">決定使用哪一項機制來解析主機名稱。</span><span class="sxs-lookup"><span data-stu-id="09270-261">Determines which mechanism is used to resolve the host name.</span></span> <span data-ttu-id="09270-262">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="09270-262">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="09270-263">IEConfig</span><span class="sxs-lookup"><span data-stu-id="09270-263">IEConfig</span></span>
- <span data-ttu-id="09270-264">WinHttpConfig</span><span class="sxs-lookup"><span data-stu-id="09270-264">WinHttpConfig</span></span>
- <span data-ttu-id="09270-265">AutoDetect</span><span class="sxs-lookup"><span data-stu-id="09270-265">AutoDetect</span></span>
- <span data-ttu-id="09270-266">NoProxyServer</span><span class="sxs-lookup"><span data-stu-id="09270-266">NoProxyServer</span></span>
- <span data-ttu-id="09270-267">無</span><span class="sxs-lookup"><span data-stu-id="09270-267">None</span></span>

<span data-ttu-id="09270-268">預設值為 None。</span><span class="sxs-lookup"><span data-stu-id="09270-268">The default value is None.</span></span>

<span data-ttu-id="09270-269">如需此參數值的詳細資訊，請參閱 [System.management.automation.remoting.proxyaccesstype 列舉](/dotnet/api/system.management.automation.remoting.proxyaccesstype)。</span><span class="sxs-lookup"><span data-stu-id="09270-269">For information about the values of this parameter, see [ProxyAccessType Enumeration](/dotnet/api/system.management.automation.remoting.proxyaccesstype).</span></span>

```yaml
Type: System.Management.Automation.Remoting.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: None, IEConfig, WinHttpConfig, AutoDetect, NoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09270-270">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="09270-270">-ProxyAuthentication</span></span>

<span data-ttu-id="09270-271">指定用於 Proxy 解析的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="09270-271">Specifies the authentication method that is used for proxy resolution.</span></span> <span data-ttu-id="09270-272">此參數可接受的值包括： **基本** 、 **摘要** 和 **協商** 。</span><span class="sxs-lookup"><span data-stu-id="09270-272">The acceptable values for this parameter are: **Basic** , **Digest** , and **Negotiate**.</span></span> <span data-ttu-id="09270-273">預設值為 **Negotiate** 。</span><span class="sxs-lookup"><span data-stu-id="09270-273">The default value is **Negotiate**.</span></span>

<span data-ttu-id="09270-274">如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="09270-274">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Negotiate
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09270-275">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="09270-275">-ProxyCredential</span></span>

<span data-ttu-id="09270-276">指定要用於 Proxy 驗證的認證。</span><span class="sxs-lookup"><span data-stu-id="09270-276">Specifies the credentials to use for proxy authentication.</span></span> <span data-ttu-id="09270-277">輸入包含 **pscredential** 物件的變數，或輸入可取得 **pscredential** 物件的命令，例如 `Get-Credential` 命令。</span><span class="sxs-lookup"><span data-stu-id="09270-277">Enter a variable that contains a **PSCredential** object or a command that gets a **PSCredential** object, such as a `Get-Credential` command.</span></span> <span data-ttu-id="09270-278">如果未設定選項，就不會指定任何認證。</span><span class="sxs-lookup"><span data-stu-id="09270-278">If this option is not set, no credentials are specified.</span></span>

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

### <span data-ttu-id="09270-279">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="09270-279">-SkipCACheck</span></span>

<span data-ttu-id="09270-280">指定透過 HTTPS 連線時，用戶端不會驗證伺服器憑證是否由受信任的憑證授權單位單位 (CA) 簽署。</span><span class="sxs-lookup"><span data-stu-id="09270-280">Specifies that when it connects over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>

<span data-ttu-id="09270-281">請只在透過其他機制讓遠端電腦成為受信任的電腦時才使用此選項，例如當遠端電腦屬於受到實體防護及隔離之網路的一部分，或當遠端電腦在 WinRM 設定中列示為受信任的主機時。</span><span class="sxs-lookup"><span data-stu-id="09270-281">Use this option only when the remote computer is trusted by using another mechanism, such as when the remote computer is part of a network that is physically secure and isolated or when the remote computer is listed as a trusted host in a WinRM configuration.</span></span>

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

### <span data-ttu-id="09270-282">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="09270-282">-SkipCNCheck</span></span>

<span data-ttu-id="09270-283">指定伺服器的憑證一般名稱 (CN) 不需要與伺服器的主機名稱相符。</span><span class="sxs-lookup"><span data-stu-id="09270-283">Specifies that the certificate common name (CN) of the server does not have to match the host name of the server.</span></span> <span data-ttu-id="09270-284">此選項只有在使用 HTTPS 通訊協定的遠端操作中才會使用。</span><span class="sxs-lookup"><span data-stu-id="09270-284">This option is used only in remote operations that use the HTTPS protocol.</span></span>

<span data-ttu-id="09270-285">請只針對受信任的電腦使用此選項。</span><span class="sxs-lookup"><span data-stu-id="09270-285">Use this option only for trusted computers.</span></span>

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

### <span data-ttu-id="09270-286">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="09270-286">-SkipRevocationCheck</span></span>

<span data-ttu-id="09270-287">不驗證伺服器憑證的撤銷狀態。</span><span class="sxs-lookup"><span data-stu-id="09270-287">Does not validate the revocation status of the server certificate.</span></span>

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

### <span data-ttu-id="09270-288">-UICulture</span><span class="sxs-lookup"><span data-stu-id="09270-288">-UICulture</span></span>

<span data-ttu-id="09270-289">指定要用於工作階段的 UI 文化特性。</span><span class="sxs-lookup"><span data-stu-id="09270-289">Specifies the UI culture to use for the session.</span></span>

<span data-ttu-id="09270-290">有效值包括：</span><span class="sxs-lookup"><span data-stu-id="09270-290">Valid values include:</span></span>

- <span data-ttu-id="09270-291">格式的文化特性名稱 `<languagecode2>-<country/regioncode2>` ，例如 `ja-JP`</span><span class="sxs-lookup"><span data-stu-id="09270-291">A culture name in `<languagecode2>-<country/regioncode2>` format, such as `ja-JP`</span></span>
- <span data-ttu-id="09270-292">包含 **CultureInfo** 物件的變數</span><span class="sxs-lookup"><span data-stu-id="09270-292">A variable that contains a **CultureInfo** object</span></span>
- <span data-ttu-id="09270-293">取得 **CultureInfo** 物件的命令，例如 `Get-Culture`</span><span class="sxs-lookup"><span data-stu-id="09270-293">A command that gets a **CultureInfo** object, such as `Get-Culture`</span></span>

<span data-ttu-id="09270-294">預設值為 `$null` ，而且會話中會使用建立會話時在作業系統中設定的 UI 文化特性。</span><span class="sxs-lookup"><span data-stu-id="09270-294">The default value is `$null`, and the UI culture that is set in the operating system when the session is created is used in the session.</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09270-295">-UseUTF16</span><span class="sxs-lookup"><span data-stu-id="09270-295">-UseUTF16</span></span>

<span data-ttu-id="09270-296">指出此 Cmdlet 會將 UTF16 格式的要求編碼，而不是 UTF8 格式。</span><span class="sxs-lookup"><span data-stu-id="09270-296">Indicates that this cmdlet encodes the request in UTF16 format instead of UTF8 format.</span></span>

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

### <span data-ttu-id="09270-297">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="09270-297">CommonParameters</span></span>

<span data-ttu-id="09270-298">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="09270-298">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="09270-299">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="09270-299">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="09270-300">輸入</span><span class="sxs-lookup"><span data-stu-id="09270-300">INPUTS</span></span>

### <span data-ttu-id="09270-301">無</span><span class="sxs-lookup"><span data-stu-id="09270-301">None</span></span>

<span data-ttu-id="09270-302">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="09270-302">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="09270-303">輸出</span><span class="sxs-lookup"><span data-stu-id="09270-303">OUTPUTS</span></span>

### <span data-ttu-id="09270-304">PSSessionOption （管理）</span><span class="sxs-lookup"><span data-stu-id="09270-304">System.Management.Automation.Remoting.PSSessionOption</span></span>

## <span data-ttu-id="09270-305">注意</span><span class="sxs-lookup"><span data-stu-id="09270-305">NOTES</span></span>

<span data-ttu-id="09270-306">如果命令中沒有使用 **SessionOption** 參數來建立 **PSSession** ，則會話選項是由喜好設定變數的屬性值 `$PSSessionOption` （如果已設定）來決定。</span><span class="sxs-lookup"><span data-stu-id="09270-306">If the **SessionOption** parameter is not used in a command to create a **PSSession** , the session options are determined by the property values of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="09270-307">如需變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="09270-307">For more information about the `$PSSessionOption` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="09270-308">工作階段設定物件的屬性取決於工作階段設定所設定的選項，以及這些選項的值。</span><span class="sxs-lookup"><span data-stu-id="09270-308">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="09270-309">此外，使用工作階段設定檔的工作階段設定會有額外的屬性。</span><span class="sxs-lookup"><span data-stu-id="09270-309">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="09270-310">相關連結</span><span class="sxs-lookup"><span data-stu-id="09270-310">RELATED LINKS</span></span>

[<span data-ttu-id="09270-311">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="09270-311">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="09270-312">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="09270-312">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="09270-313">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="09270-313">New-PSSession</span></span>](New-PSSession.md)
