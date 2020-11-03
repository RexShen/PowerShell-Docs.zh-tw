---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pstransportoption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSTransportOption
ms.openlocfilehash: 7b7734c60a6a13d86f398418aeefce932e91a363
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205443"
---
# <span data-ttu-id="c53d8-103">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="c53d8-103">New-PSTransportOption</span></span>

## <span data-ttu-id="c53d8-104">概要</span><span class="sxs-lookup"><span data-stu-id="c53d8-104">SYNOPSIS</span></span>
<span data-ttu-id="c53d8-105">建立包含工作階段設定之進階選項的物件。</span><span class="sxs-lookup"><span data-stu-id="c53d8-105">Creates an object that contains advanced options for a session configuration.</span></span>

## <span data-ttu-id="c53d8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c53d8-106">SYNTAX</span></span>

```
New-PSTransportOption [-MaxIdleTimeoutSec <Int32>] [-ProcessIdleTimeoutSec <Int32>] [-MaxSessions <Int32>]
 [-MaxConcurrentCommandsPerSession <Int32>] [-MaxSessionsPerUser <Int32>] [-MaxMemoryPerSessionMB <Int32>]
 [-MaxProcessesPerSession <Int32>] [-MaxConcurrentUsers <Int32>] [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [<CommonParameters>]
```

## <span data-ttu-id="c53d8-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c53d8-107">DESCRIPTION</span></span>

<span data-ttu-id="c53d8-108">**New-PSTransportOption** Cmdlet 建立包含工作階段設定之傳輸選項的物件。</span><span class="sxs-lookup"><span data-stu-id="c53d8-108">The **New-PSTransportOption** cmdlet creates an object that contains transport options for session configurations.</span></span>
<span data-ttu-id="c53d8-109">您可以使用該物件做為建立或變更工作階段設定之 Cmdlet 的 *TransportOption* 參數值，例如 Register-PSSessionConfiguration 和 Set-PSSessionConfiguration Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c53d8-109">You can use the object as the value of the *TransportOption* parameter of cmdlets that create or change a session configuration, such as the Register-PSSessionConfiguration and Set-PSSessionConfiguration cmdlets.</span></span>

<span data-ttu-id="c53d8-110">您也可以透過編輯工作階段設定屬性的 WSMan: 磁碟機的值來變更傳輸選項設定。</span><span class="sxs-lookup"><span data-stu-id="c53d8-110">You can also change the transport option settings by editing the values of the session configuration properties in the WSMan: drive.</span></span>
<span data-ttu-id="c53d8-111">如需詳細資訊，請參閱＜WSMan 提供者＞。</span><span class="sxs-lookup"><span data-stu-id="c53d8-111">For more information, see WSMan Provider.</span></span>

<span data-ttu-id="c53d8-112">會話設定選項代表伺服器端上設定的會話值，或是遠端連線的接收端。</span><span class="sxs-lookup"><span data-stu-id="c53d8-112">The session configuration options represent the session values set on the server-side, or receiving end of a remote connection.</span></span>
<span data-ttu-id="c53d8-113">用戶端或連接結束時，可以在建立會話時，或者用戶端與會話中斷連線或重新連接時，設定會話選項值。</span><span class="sxs-lookup"><span data-stu-id="c53d8-113">The client-side, or sending end of the connection, can set session option values when the session is created, or when the client disconnects from or reconnects to the session.</span></span>
<span data-ttu-id="c53d8-114">除非另有說明，否則當設定值衝突時，用戶端值的優先順序較高。</span><span class="sxs-lookup"><span data-stu-id="c53d8-114">Unless stated otherwise, when the setting values conflict, the client-side values take precedence.</span></span>
<span data-ttu-id="c53d8-115">不過，用戶端值不能違反工作階段設定中設定的最大值與配額。</span><span class="sxs-lookup"><span data-stu-id="c53d8-115">However, the client-side values cannot violate maximum values and quotas set in the session configuration.</span></span>

<span data-ttu-id="c53d8-116">如果沒有參數， **>new-pstransportoption** 會產生一個傳輸選項物件，其所有選項都有 null 值。</span><span class="sxs-lookup"><span data-stu-id="c53d8-116">Without parameters, **New-PSTransportOption** generates a transport option object that has null values for all of the options.</span></span>
<span data-ttu-id="c53d8-117">如果您省略參數，該參數代表的物件屬性就會是 Null 值。</span><span class="sxs-lookup"><span data-stu-id="c53d8-117">If you omit a parameter, the object has a null value for the property that the parameter represents.</span></span>
<span data-ttu-id="c53d8-118">Null 值不會影響會話設定。</span><span class="sxs-lookup"><span data-stu-id="c53d8-118">A null value does not affect the session configuration.</span></span>

<span data-ttu-id="c53d8-119">如需工作階段選項的詳細資訊，請參閱 New-PSSessionOption。</span><span class="sxs-lookup"><span data-stu-id="c53d8-119">For more information about session options, see New-PSSessionOption.</span></span>
<span data-ttu-id="c53d8-120">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="c53d8-120">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="c53d8-121">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="c53d8-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="c53d8-122">範例</span><span class="sxs-lookup"><span data-stu-id="c53d8-122">EXAMPLES</span></span>

### <span data-ttu-id="c53d8-123">範例1：產生預設傳輸選項</span><span class="sxs-lookup"><span data-stu-id="c53d8-123">Example 1: Generate a default transport option</span></span>

```powershell
New-PSTransportOption
```

```Output
ProcessIdleTimeoutSec           :
MaxIdleTimeoutSec               :
MaxSessions                     :
MaxConcurrentCommandsPerSession :
MaxSessionsPerUser              :
MaxMemoryPerSessionMB           :
MaxProcessesPerSession          :
MaxConcurrentUsers              :
IdleTimeoutSec                  :
OutputBufferingMode             :
```

<span data-ttu-id="c53d8-124">此命令會執行不含參數的 **新 >new-pstransportoption** 。</span><span class="sxs-lookup"><span data-stu-id="c53d8-124">This command runs the **New-PSTransportOption** without parameters.</span></span>
<span data-ttu-id="c53d8-125">輸出顯示此 Cmdlet 會產生所有屬性都是 null 值的傳輸選項物件。</span><span class="sxs-lookup"><span data-stu-id="c53d8-125">The output shows that the cmdlet generates a transport option object that has null values for all properties.</span></span>

### <span data-ttu-id="c53d8-126">範例2：取得會話設定選項</span><span class="sxs-lookup"><span data-stu-id="c53d8-126">Example 2: Get session configuration options</span></span>

<span data-ttu-id="c53d8-127">此範例示範如何使用傳輸選項物件設定會話設定選項。</span><span class="sxs-lookup"><span data-stu-id="c53d8-127">This example shows how to use a transport options object to set session configuration options.</span></span>

```powershell
$t = New-PSTransportOption -MaxSessions 40
Register-PSSessionConfiguration -Name ITTasks -TransportOption $t
Get-PSSessionConfiguration -Name ITTasks | Format-List -Property *
```

```Output
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITTasks
MaxConcurrentCommandsPerShell : 1000
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 40
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 2
Name                          : ITTasks
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
Enabled                       : True
MaxShellsPerUser              : 25
Permission                    :
```

<span data-ttu-id="c53d8-128">第一個命令使用 **New-PSTransportOption** Cmdlet 建立一個傳輸選項物件，它會儲存在 $t 變數中。</span><span class="sxs-lookup"><span data-stu-id="c53d8-128">The first command uses the **New-PSTransportOption** cmdlet to create a transport options object, which it saves in the $t variable.</span></span> <span data-ttu-id="c53d8-129">命令使用 *MaxSessions* 參數將工作階段數目上限增加為 40。</span><span class="sxs-lookup"><span data-stu-id="c53d8-129">The command uses the *MaxSessions* parameter to increase the maximum number of sessions to 40.</span></span>

<span data-ttu-id="c53d8-130">第二個命令使用 **Register-PSSessionConfiguration** Cmdlet 建立 ITTasks 工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="c53d8-130">The second command uses the **Register-PSSessionConfiguration** cmdlet create the ITTasks session configuration.</span></span> <span data-ttu-id="c53d8-131">命令使用 *TransportOption* 參數指定 $t 變數中的傳輸選項物件。</span><span class="sxs-lookup"><span data-stu-id="c53d8-131">The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.</span></span>

<span data-ttu-id="c53d8-132">第三個命令會使用 Get-PSSessionConfiguration Cmdlet 來取得 ITTasks 會話設定，並使用 Format-List Cmdlet 將會話設定物件的所有屬性顯示在清單中。</span><span class="sxs-lookup"><span data-stu-id="c53d8-132">The third command uses the Get-PSSessionConfiguration cmdlet to get the ITTasks session configurations and the Format-List cmdlet to display all of the properties of the session configuration object in a list.</span></span> <span data-ttu-id="c53d8-133">輸出顯示工作階段設定的 **MaxShells** 屬性值為 40。</span><span class="sxs-lookup"><span data-stu-id="c53d8-133">The output shows that the value of the **MaxShells** property of the session configuration is 40.</span></span>

### <span data-ttu-id="c53d8-134">範例3：設定傳輸選項</span><span class="sxs-lookup"><span data-stu-id="c53d8-134">Example 3: Setting a transport option</span></span>

<span data-ttu-id="c53d8-135">此命令示範在工作階段設定中設定傳輸選項對使用工作階段設定的工作階段的效果。</span><span class="sxs-lookup"><span data-stu-id="c53d8-135">This command shows the effect of setting a transport option in a session configuration on the sessions that use the session configuration.</span></span>

```powershell
$t = New-PSTransportOption -IdleTimeoutSec 3600
Set-PSSessionConfiguration -Name ITTasks -TransportOption $t
$s = New-PSSession -Name MyITTasks -ConfigurationName ITTasks
$s | Format-List -Property *
```

```Output
State                  : Opened
IdleTimeout            : 3600000
OutputBufferingMode    : Block
ComputerName           : localhost
ConfigurationName      : ITTasks
InstanceId             : 4110c3f5-68ea-40fa-9bbf-04a433dbb02d
Id                     : 1
Name                   : MyITTasks
Availability           : Available
ApplicationPrivateData : {PSVersionTable}
Runspace               : System.Management.Automation.RemoteRunspace
```

<span data-ttu-id="c53d8-136">第一個命令使用 **New-PSTransportOption** Cmdlet 建立傳輸選項物件。</span><span class="sxs-lookup"><span data-stu-id="c53d8-136">The first command uses the **New-PSTransportOption** cmdlet to create a transport option object.</span></span> <span data-ttu-id="c53d8-137">命令使用 *IdleTimeoutSec* 參數設定物件的 **IdleTimeoutSec** 屬性值為 1 小時 (3600 秒)。</span><span class="sxs-lookup"><span data-stu-id="c53d8-137">The command uses the *IdleTimeoutSec* parameter to set the **IdleTimeoutSec** property value of the object to one hour (3600 seconds).</span></span> <span data-ttu-id="c53d8-138">命令會將傳輸選項物件儲存在 $t 變數中。</span><span class="sxs-lookup"><span data-stu-id="c53d8-138">The command saves the transport objects object in the $t variable.</span></span>

<span data-ttu-id="c53d8-139">第二個命令使用 Set-PSSessionConfiguration Cmdlet 來變更 ITTasks 會話設定的傳輸選項。</span><span class="sxs-lookup"><span data-stu-id="c53d8-139">The second command uses the Set-PSSessionConfiguration cmdlet to change the transport options of the ITTasks session configuration.</span></span> <span data-ttu-id="c53d8-140">命令使用 *TransportOption* 參數指定 $t 變數中的傳輸選項物件。</span><span class="sxs-lookup"><span data-stu-id="c53d8-140">The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.</span></span>

<span data-ttu-id="c53d8-141">第三個命令使用 New-PSSession Cmdlet 在本機電腦上建立 MyITTasks 會話。</span><span class="sxs-lookup"><span data-stu-id="c53d8-141">The third command uses the New-PSSession cmdlet to create the MyITTasks session on the local computer.</span></span> <span data-ttu-id="c53d8-142">命令使用 **ConfigurationName** 屬性指定 ITTasks 工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="c53d8-142">The command uses the **ConfigurationName** property to specify the ITTasks session configuration.</span></span> <span data-ttu-id="c53d8-143">命令會將會話儲存在 $s 變數中。請注意，此命令不會使用 **新的-PSSession** 的 *SessionOption* 參數來設定會話的自訂空閒超時時間。</span><span class="sxs-lookup"><span data-stu-id="c53d8-143">The command saves the session in the $s variable.Notice that the command does not use the *SessionOption* parameter of **New-PSSession** to set a custom idle time-out for the session.</span></span> <span data-ttu-id="c53d8-144">如果有的話，在會話選項中設定的閒置超時值將會優先于會話設定中的閒置超時設定。</span><span class="sxs-lookup"><span data-stu-id="c53d8-144">If it did, the idle time-out value set in the session option would take precedence over the idle time-out set in the session configuration.</span></span>

<span data-ttu-id="c53d8-145">第四個命令使用 Format-List Cmdlet，在清單中顯示 $s 變數中會話的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="c53d8-145">The fourth command uses the Format-List cmdlet to display all properties of the session in the $s variable in a list.</span></span> <span data-ttu-id="c53d8-146">輸出顯示會話的閒置時間已達一小時， (360000 毫秒) 。</span><span class="sxs-lookup"><span data-stu-id="c53d8-146">The output shows that the session has an idle time-out of one hour (360,000 milliseconds).</span></span>

## <span data-ttu-id="c53d8-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c53d8-147">PARAMETERS</span></span>

### <span data-ttu-id="c53d8-148">-IdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="c53d8-148">-IdleTimeoutSec</span></span>

<span data-ttu-id="c53d8-149">決定在遠端電腦未收到來自本機電腦的任何通訊時，每個會話保持開啟的時間長度。</span><span class="sxs-lookup"><span data-stu-id="c53d8-149">Determines how long each session stays open if the remote computer does not receive any communication from the local computer.</span></span>
<span data-ttu-id="c53d8-150">這包括了信號信號。</span><span class="sxs-lookup"><span data-stu-id="c53d8-150">This includes the heartbeat signal.</span></span>
<span data-ttu-id="c53d8-151">當間隔時間過期時，工作階段就會關閉。</span><span class="sxs-lookup"><span data-stu-id="c53d8-151">When the interval expires, the session closes.</span></span>

<span data-ttu-id="c53d8-152">當使用者想要中斷連線並重新連線至會話時，空閒超時值相當重要。</span><span class="sxs-lookup"><span data-stu-id="c53d8-152">The idle time-out value is of significant importance when the user intends to disconnect and reconnect to a session.</span></span>
<span data-ttu-id="c53d8-153">只有當工作階段尚未逾時時，使用者才可以重新連線。</span><span class="sxs-lookup"><span data-stu-id="c53d8-153">The user can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="c53d8-154">*IdleTimeoutSec* 參數對應工作階段設定的 **IdleTimeoutMs** 屬性。</span><span class="sxs-lookup"><span data-stu-id="c53d8-154">The *IdleTimeoutSec* parameter corresponds to the **IdleTimeoutMs** property of a session configuration.</span></span>

<span data-ttu-id="c53d8-155">輸入以秒為單位的值。</span><span class="sxs-lookup"><span data-stu-id="c53d8-155">Enter a value in seconds.</span></span>
<span data-ttu-id="c53d8-156">預設值為 7200 (2 小時)。</span><span class="sxs-lookup"><span data-stu-id="c53d8-156">The default value is 7200 (2 hours).</span></span>
<span data-ttu-id="c53d8-157">最小值為 60 (1 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="c53d8-157">The minimum value is 60 (1 minute).</span></span>
<span data-ttu-id="c53d8-158">最大值是 WSMan 設定中 Shell 物件的 **IdleTimeout** 屬性值 (`WSMan:\\\<ComputerName\>\Shell\IdleTimeout`) 。</span><span class="sxs-lookup"><span data-stu-id="c53d8-158">The maximum is the value of the **IdleTimeout** property of Shell objects in the WSMan configuration (`WSMan:\\\<ComputerName\>\Shell\IdleTimeout`).</span></span>
<span data-ttu-id="c53d8-159">預設值為 7200000 毫秒 (2 小時)。</span><span class="sxs-lookup"><span data-stu-id="c53d8-159">The default value is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="c53d8-160">如果在會話選項中與會話設定中設定了閒置的超時值，會話選項中設定的值會優先，但是它不能超過會話設定之 **MaxIdleTimeoutMs** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c53d8-160">If an idle time-out value is set in the session options and in the session configuration, value set in the session options takes precedence, but it cannot exceed the value of the **MaxIdleTimeoutMs** property of the session configuration.</span></span>
<span data-ttu-id="c53d8-161">若要設定 **MaxIdleTimeoutMs** 屬性的值，請使用 *MaxIdleTimeoutSec* 參數。</span><span class="sxs-lookup"><span data-stu-id="c53d8-161">To set the value of the **MaxIdleTimeoutMs** property, use the *MaxIdleTimeoutSec* parameter.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c53d8-162">-MaxConcurrentCommandsPerSession</span><span class="sxs-lookup"><span data-stu-id="c53d8-162">-MaxConcurrentCommandsPerSession</span></span>

<span data-ttu-id="c53d8-163">將每個會話中可同時執行的命令數目限制為指定的值。</span><span class="sxs-lookup"><span data-stu-id="c53d8-163">Limits the number of commands that can run at the same time in each session to the specified value.</span></span>
<span data-ttu-id="c53d8-164">預設值為 1000。</span><span class="sxs-lookup"><span data-stu-id="c53d8-164">The default value is 1000.</span></span>

<span data-ttu-id="c53d8-165">*MaxConcurrentCommandsPerSession* 參數會對應至工作階段設定的 **MaxConcurrentCommandsPerShell** 屬性。</span><span class="sxs-lookup"><span data-stu-id="c53d8-165">The *MaxConcurrentCommandsPerSession* parameter corresponds to the **MaxConcurrentCommandsPerShell** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c53d8-166">-MaxConcurrentUsers</span><span class="sxs-lookup"><span data-stu-id="c53d8-166">-MaxConcurrentUsers</span></span>

<span data-ttu-id="c53d8-167">將每個會話中可同時執行命令的使用者數目限制為指定的值。</span><span class="sxs-lookup"><span data-stu-id="c53d8-167">Limits the number of users who can run commands at the same time in each session to the specified value.</span></span>
<span data-ttu-id="c53d8-168">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="c53d8-168">The default value is 5.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c53d8-169">-MaxIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="c53d8-169">-MaxIdleTimeoutSec</span></span>

<span data-ttu-id="c53d8-170">將每個會話的閒置超時設定限制為指定的值。</span><span class="sxs-lookup"><span data-stu-id="c53d8-170">Limits the idle time-out set for each session to the specified value.</span></span>
<span data-ttu-id="c53d8-171">預設值為 \[Int\]::MaxValue (~25 天)。</span><span class="sxs-lookup"><span data-stu-id="c53d8-171">The default value is \[Int\]::MaxValue (~25 days).</span></span>

<span data-ttu-id="c53d8-172">當使用者想要中斷連線並重新連線至會話時，空閒超時值相當重要。</span><span class="sxs-lookup"><span data-stu-id="c53d8-172">The idle time-out value is of significant importance when the user intends to disconnect and reconnect to a session.</span></span>
<span data-ttu-id="c53d8-173">只有當工作階段尚未逾時時，使用者才可以重新連線。</span><span class="sxs-lookup"><span data-stu-id="c53d8-173">The user can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="c53d8-174">*MaxIdleTimeoutSec* 參數會對應到工作階段設定的 **MaxIdleTimeoutMs** 屬性。</span><span class="sxs-lookup"><span data-stu-id="c53d8-174">The *MaxIdleTimeoutSec* parameter corresponds to the **MaxIdleTimeoutMs** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c53d8-175">-MaxMemoryPerSessionMB</span><span class="sxs-lookup"><span data-stu-id="c53d8-175">-MaxMemoryPerSessionMB</span></span>

<span data-ttu-id="c53d8-176">限制每個工作階段所使用的記憶體為指定的值。</span><span class="sxs-lookup"><span data-stu-id="c53d8-176">Limits the memory used by each session to the specified value.</span></span>
<span data-ttu-id="c53d8-177">輸入以 MB 為單位的值。</span><span class="sxs-lookup"><span data-stu-id="c53d8-177">Enter a value in megabytes.</span></span>
<span data-ttu-id="c53d8-178">預設值為 1024 MB (1 GB)。</span><span class="sxs-lookup"><span data-stu-id="c53d8-178">The default value is 1024 megabytes (1 GB).</span></span>

<span data-ttu-id="c53d8-179">*MaxMemoryPerSessionMB* 參數會對應到工作階段設定的 **MaxMemoryPerShellMB** 屬性。</span><span class="sxs-lookup"><span data-stu-id="c53d8-179">The *MaxMemoryPerSessionMB* parameter corresponds to the **MaxMemoryPerShellMB** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c53d8-180">-MaxProcessesPerSession</span><span class="sxs-lookup"><span data-stu-id="c53d8-180">-MaxProcessesPerSession</span></span>

<span data-ttu-id="c53d8-181">限制每個工作階段中執行的處理程序數目為指定的值。</span><span class="sxs-lookup"><span data-stu-id="c53d8-181">Limits the number of processes running in each session to the specified value.</span></span>
<span data-ttu-id="c53d8-182">預設值為 15。</span><span class="sxs-lookup"><span data-stu-id="c53d8-182">The default value is 15.</span></span>

<span data-ttu-id="c53d8-183">*MaxProcessesPerSession* 參數會對應到工作階段設定的 **MaxProcessesPerShell** 屬性。</span><span class="sxs-lookup"><span data-stu-id="c53d8-183">The *MaxProcessesPerSession* parameter corresponds to the **MaxProcessesPerShell** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c53d8-184">-MaxSessions</span><span class="sxs-lookup"><span data-stu-id="c53d8-184">-MaxSessions</span></span>

<span data-ttu-id="c53d8-185">限制使用工作階段設定的工作階段數目。</span><span class="sxs-lookup"><span data-stu-id="c53d8-185">Limits the number of sessions that use the session configuration.</span></span>
<span data-ttu-id="c53d8-186">預設值為 25。</span><span class="sxs-lookup"><span data-stu-id="c53d8-186">The default value is 25.</span></span>

<span data-ttu-id="c53d8-187">*MaxSessions* 參數會對應到工作階段設定的 **MaxShells** 屬性。</span><span class="sxs-lookup"><span data-stu-id="c53d8-187">The *MaxSessions* parameter corresponds to the **MaxShells** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c53d8-188">-MaxSessionsPerUser</span><span class="sxs-lookup"><span data-stu-id="c53d8-188">-MaxSessionsPerUser</span></span>

<span data-ttu-id="c53d8-189">限制使用工作階段設定，並使用指定使用者的認證執行的工作階段數目為指定的值。</span><span class="sxs-lookup"><span data-stu-id="c53d8-189">Limits the number of sessions that use the session configuration and run with the credentials of a given user to the specified value.</span></span>
<span data-ttu-id="c53d8-190">預設值為 25。</span><span class="sxs-lookup"><span data-stu-id="c53d8-190">The default value is 25.</span></span>

<span data-ttu-id="c53d8-191">當您指定此值時，請考慮許多使用者可能使用「執行身分」使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="c53d8-191">When you specify this value, consider that many users might be using the credentials of a run as user.</span></span>

<span data-ttu-id="c53d8-192">*MaxSessionsPerUser* 參數會對應到工作階段設定的 **MaxShellsPerUser** 屬性。</span><span class="sxs-lookup"><span data-stu-id="c53d8-192">The *MaxSessionsPerUser* parameter corresponds to the **MaxShellsPerUser** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c53d8-193">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="c53d8-193">-OutputBufferingMode</span></span>

<span data-ttu-id="c53d8-194">決定在輸出緩衝區已滿時，在中斷連線的工作階段中管理命令輸出的方式。</span><span class="sxs-lookup"><span data-stu-id="c53d8-194">Determines how command output is managed in disconnected sessions when the output buffer becomes full.</span></span>
<span data-ttu-id="c53d8-195">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="c53d8-195">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c53d8-196">區塊。</span><span class="sxs-lookup"><span data-stu-id="c53d8-196">Block.</span></span>
<span data-ttu-id="c53d8-197">當輸出緩衝區已滿時，會暫停執行直到清除緩衝區為止。</span><span class="sxs-lookup"><span data-stu-id="c53d8-197">When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="c53d8-198">Drop：</span><span class="sxs-lookup"><span data-stu-id="c53d8-198">Drop.</span></span>
<span data-ttu-id="c53d8-199">當輸出緩衝區已滿時，會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="c53d8-199">When the output buffer is full, execution continues.</span></span>
<span data-ttu-id="c53d8-200">儲存新的輸出時，會捨棄最舊的輸出。</span><span class="sxs-lookup"><span data-stu-id="c53d8-200">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="c53d8-201">無。</span><span class="sxs-lookup"><span data-stu-id="c53d8-201">None.</span></span>
<span data-ttu-id="c53d8-202">未指定輸出緩衝模式。</span><span class="sxs-lookup"><span data-stu-id="c53d8-202">No output buffering mode is specified.</span></span>

<span data-ttu-id="c53d8-203">會話的 **OutputBufferingMode** 屬性預設值為 Block。</span><span class="sxs-lookup"><span data-stu-id="c53d8-203">The default value of the **OutputBufferingMode** property of sessions is Block.</span></span>

```yaml
Type: System.Nullable`1[System.Management.Automation.Runspaces.OutputBufferingMode]
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c53d8-204">-ProcessIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="c53d8-204">-ProcessIdleTimeoutSec</span></span>

<span data-ttu-id="c53d8-205">將每個主機進程的超時時間限制為指定的值。</span><span class="sxs-lookup"><span data-stu-id="c53d8-205">Limits the time-out for each host process to the specified value.</span></span>
<span data-ttu-id="c53d8-206">預設值為0，表示進程沒有超時值。</span><span class="sxs-lookup"><span data-stu-id="c53d8-206">The default value, 0, means that there is no time-out value for the process.</span></span>

<span data-ttu-id="c53d8-207">其他會話設定會有每個進程的超時值。</span><span class="sxs-lookup"><span data-stu-id="c53d8-207">Other session configurations have per-process time-out values.</span></span>
<span data-ttu-id="c53d8-208">例如， (8 小時) ，則 **工作流程** 會話設定的每個進程超時值為28800秒。</span><span class="sxs-lookup"><span data-stu-id="c53d8-208">For example, the **Microsoft.PowerShell.Workflow** session configuration has a per-process time-out value of 28800 seconds (8 hours).</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c53d8-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c53d8-209">CommonParameters</span></span>

<span data-ttu-id="c53d8-210">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c53d8-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c53d8-211">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c53d8-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c53d8-212">輸入</span><span class="sxs-lookup"><span data-stu-id="c53d8-212">INPUTS</span></span>

### <span data-ttu-id="c53d8-213">無</span><span class="sxs-lookup"><span data-stu-id="c53d8-213">None</span></span>

<span data-ttu-id="c53d8-214">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c53d8-214">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c53d8-215">輸出</span><span class="sxs-lookup"><span data-stu-id="c53d8-215">OUTPUTS</span></span>

### <span data-ttu-id="c53d8-216">Microsoft.PowerShell.Commands.WSManConfigurationOption</span><span class="sxs-lookup"><span data-stu-id="c53d8-216">Microsoft.PowerShell.Commands.WSManConfigurationOption</span></span>

## <span data-ttu-id="c53d8-217">注意</span><span class="sxs-lookup"><span data-stu-id="c53d8-217">NOTES</span></span>

- <span data-ttu-id="c53d8-218">工作階段設定物件的屬性取決於工作階段設定所設定的選項，以及這些選項的值。</span><span class="sxs-lookup"><span data-stu-id="c53d8-218">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="c53d8-219">此外，使用工作階段設定檔的工作階段設定會有額外的屬性。</span><span class="sxs-lookup"><span data-stu-id="c53d8-219">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="c53d8-220">相關連結</span><span class="sxs-lookup"><span data-stu-id="c53d8-220">RELATED LINKS</span></span>

[<span data-ttu-id="c53d8-221">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="c53d8-221">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="c53d8-222">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="c53d8-222">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="c53d8-223">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c53d8-223">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="c53d8-224">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c53d8-224">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

