---
title: 使用 WMI
description: PowerShell 一開始便有可搭配 WMI 使用的 Cmdlet。
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 243685efa1f976ddb46a0d0efc4ed0635844606d
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438289"
---
# <a name="chapter-7---working-with-wmi"></a><span data-ttu-id="d12b2-103">第 7 章 - 使用 WMI</span><span class="sxs-lookup"><span data-stu-id="d12b2-103">Chapter 7 - Working with WMI</span></span>

## <a name="wmi-and-cim"></a><span data-ttu-id="d12b2-104">WMI 和 CIM</span><span class="sxs-lookup"><span data-stu-id="d12b2-104">WMI and CIM</span></span>

<span data-ttu-id="d12b2-105">PowerShell 預設隨附用於與其他技術 (例如 Windows Management Instrumentation (WMI)) 搭配使用的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d12b2-105">PowerShell ships by default with cmdlets for working with other technologies such as Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="d12b2-106">PowerShell 中存在數個原生 WMI Cmdlet，而不需安裝任何額外的軟體或模組。</span><span class="sxs-lookup"><span data-stu-id="d12b2-106">There are several native WMI cmdlets that exist in PowerShell without having to install any additional software or modules.</span></span>

<span data-ttu-id="d12b2-107">PowerShell 一開始便有可搭配 WMI 使用的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d12b2-107">PowerShell has had cmdlets for working with WMI since the beginning.</span></span> <span data-ttu-id="d12b2-108">`Get-Command` 可以用來判斷 PowerShell 中有哪些 WMI Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d12b2-108">`Get-Command` can be used to determine what WMI cmdlets exist in PowerShell.</span></span> <span data-ttu-id="d12b2-109">下列結果來自執行 PowerShell 5.1 版的 Windows 10 實驗室環境電腦。</span><span class="sxs-lookup"><span data-stu-id="d12b2-109">The following results are from my Windows 10 lab environment computer that is running PowerShell version 5.1.</span></span> <span data-ttu-id="d12b2-110">根據您正在執行的 PowerShell 版本，您的結果可能會有所不同。</span><span class="sxs-lookup"><span data-stu-id="d12b2-110">Your results may differ depending on what PowerShell version you're running.</span></span>

```powershell
Get-Command -Noun WMI*
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-WmiObject                                      3.1.0.0    Microsof...
Cmdlet          Invoke-WmiMethod                                   3.1.0.0    Microsof...
Cmdlet          Register-WmiEvent                                  3.1.0.0    Microsof...
Cmdlet          Remove-WmiObject                                   3.1.0.0    Microsof...
Cmdlet          Set-WmiInstance                                    3.1.0.0    Microsof...
```

<span data-ttu-id="d12b2-111">通用訊息模型 (CIM) Cmdlet 是在 PowerShell 3.0 版中推出。</span><span class="sxs-lookup"><span data-stu-id="d12b2-111">Common Information Model (CIM) cmdlets were introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="d12b2-112">CIM Cmdlet 的設計是要同時在 Windows 和非 Windows 電腦上使用。</span><span class="sxs-lookup"><span data-stu-id="d12b2-112">The CIM cmdlets are designed so they can be used on both Windows and non-Windows machines.</span></span> <span data-ttu-id="d12b2-113">WMI Cmdlet 已淘汰，因此我的建議是使用 CIM Cmdlet，而不是較舊的 WMI Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d12b2-113">The WMI cmdlets are deprecated so my recommendation is to use the CIM cmdlets instead of the older WMI ones.</span></span>

<span data-ttu-id="d12b2-114">CIM Cmdlet 全都包含在模組中。</span><span class="sxs-lookup"><span data-stu-id="d12b2-114">The CIM cmdlets are all contained within a module.</span></span> <span data-ttu-id="d12b2-115">若要取得 CIM Cmdlet 的清單，請使用 `Get-Command` 搭配 **Module** 參數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d12b2-115">To obtain a list of the CIM cmdlets, use `Get-Command` with the **Module** parameter as shown in the following example.</span></span>

```powershell
Get-Command -Module CimCmdlets
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Export-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Get-CimAssociatedInstance                          1.0.0.0    CimCmdlets
Cmdlet          Get-CimClass                                       1.0.0.0    CimCmdlets
Cmdlet          Get-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          Get-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          Import-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Invoke-CimMethod                                   1.0.0.0    CimCmdlets
Cmdlet          New-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          New-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          New-CimSessionOption                               1.0.0.0    CimCmdlets
Cmdlet          Register-CimIndicationEvent                        1.0.0.0    CimCmdlets
Cmdlet          Remove-CimInstance                                 1.0.0.0    CimCmdlets
Cmdlet          Remove-CimSession                                  1.0.0.0    CimCmdlets
Cmdlet          Set-CimInstance                                    1.0.0.0    CimCmdlets
```

<span data-ttu-id="d12b2-116">CIM Cmdlet 仍然可讓您使用 WMI，因此當有人說「我使用 PowerShell CIM Cmdlet 查詢 WMI 時...」，請不要感到困惑</span><span class="sxs-lookup"><span data-stu-id="d12b2-116">The CIM cmdlets still allow you to work with WMI so don't be confused when someone makes the statement "When I query WMI with the PowerShell CIM cmdlets..."</span></span>

<span data-ttu-id="d12b2-117">如先前所述，WMI 是 PowerShell 中的個別技術，而您只是使用 CIM Cmdlet 來存取 WMI。</span><span class="sxs-lookup"><span data-stu-id="d12b2-117">As I previously mentioned, WMI is a separate technology from PowerShell and you're just using the CIM cmdlets for accessing WMI.</span></span> <span data-ttu-id="d12b2-118">您可能會發現使用 WMI 查詢語言 (WQL) 來查詢 WMI 的舊 VBScript，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d12b2-118">You may find an old VBScript that uses WMI Query Language (WQL) to query WMI such as in the following example.</span></span>

```vb
strComputer = "."
Set objWMIService = GetObject("winmgmts:" _
    & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\cimv2")

Set colBIOS = objWMIService.ExecQuery _
    ("Select * from Win32_BIOS")

For each objBIOS in colBIOS
    Wscript.Echo "Manufacturer: " & objBIOS.Manufacturer
    Wscript.Echo "Name: " & objBIOS.Name
    Wscript.Echo "Serial Number: " & objBIOS.SerialNumber
    Wscript.Echo "SMBIOS Version: " & objBIOS.SMBIOSBIOSVersion
    Wscript.Echo "Version: " & objBIOS.Version
Next
```

<span data-ttu-id="d12b2-119">您可以從該 VBScript 取得 WQL 查詢，並在不進行任何修改的情況下，將它與 `Get-CimInstance` Cmdlet 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="d12b2-119">You can take the WQL query from that VBScript and use it with the `Get-CimInstance` cmdlet without any modifications.</span></span>

```powershell
Get-CimInstance -Query 'Select * from Win32_BIOS'
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

<span data-ttu-id="d12b2-120">這並非我一般使用 PowerShell 查詢 WMI 的方式。</span><span class="sxs-lookup"><span data-stu-id="d12b2-120">That's not how I typically query WMI with PowerShell.</span></span> <span data-ttu-id="d12b2-121">但它的確可行，並可讓您輕鬆將現有的 VBScript 遷移至 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d12b2-121">But it does work and allows you to easily migrate existing VBScripts to PowerShell.</span></span> <span data-ttu-id="d12b2-122">當我開始撰寫一行程式碼來查詢 WMI 時，我會使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="d12b2-122">When I start out writing a one-liner to query WMI, I use the following syntax.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

<span data-ttu-id="d12b2-123">如果我只想要序號，我可以將輸出以管線傳送至 `Select-Object`，並只指定  **SerialNumber** 屬性。</span><span class="sxs-lookup"><span data-stu-id="d12b2-123">If I only want the serial number, I can pipe the output to `Select-Object` and specify only the **SerialNumber** property.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS | Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="d12b2-124">根據預設，有數個在幕後擷取的屬性從未使用過。</span><span class="sxs-lookup"><span data-stu-id="d12b2-124">By default, there are several properties that are retrieved behind the scenes that are never used.</span></span>
<span data-ttu-id="d12b2-125">在本機電腦上查詢 WMI 時，可能差別不大。</span><span class="sxs-lookup"><span data-stu-id="d12b2-125">It may not matter much when querying WMI on the local computer.</span></span> <span data-ttu-id="d12b2-126">可是當您開始查詢遠端電腦，不只是傳回該資訊需要額外的處理時間，還有在網路上提取非必要資訊的額外時間。</span><span class="sxs-lookup"><span data-stu-id="d12b2-126">But once you start querying remote computers, it's not only additional processing time to return that information, but also additional unnecessary information to have to pull across the network.</span></span> <span data-ttu-id="d12b2-127">`Get-CimInstance` 具有 **Property** 參數，會限制擷取的資訊。</span><span class="sxs-lookup"><span data-stu-id="d12b2-127">`Get-CimInstance` has a **Property** parameter that limits the information that's retrieved.</span></span> <span data-ttu-id="d12b2-128">這可讓查詢 WMI 更有效率。</span><span class="sxs-lookup"><span data-stu-id="d12b2-128">This makes the query to WMI more efficient.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="d12b2-129">先前的結果傳回了物件。</span><span class="sxs-lookup"><span data-stu-id="d12b2-129">The previous results returned an object.</span></span> <span data-ttu-id="d12b2-130">若要傳回簡單字串，請使用 **ExpandProperty** 參數。</span><span class="sxs-lookup"><span data-stu-id="d12b2-130">To return a simple string, use the **ExpandProperty** parameter.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -ExpandProperty SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="d12b2-131">您也可以使用虛線樣式的語法來傳回簡單的字串。</span><span class="sxs-lookup"><span data-stu-id="d12b2-131">You could also use the dotted style of syntax to return a simple string.</span></span> <span data-ttu-id="d12b2-132">這使得您不需要以管線傳送至 `Select-Object`。</span><span class="sxs-lookup"><span data-stu-id="d12b2-132">This eliminates the need to pipe to `Select-Object`.</span></span>

```powershell
(Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber).SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

## <a name="query-remote-computers-with-the-cim-cmdlets"></a><span data-ttu-id="d12b2-133">使用 CIM Cmdlet 查詢遠端電腦</span><span class="sxs-lookup"><span data-stu-id="d12b2-133">Query Remote Computers with the CIM cmdlets</span></span>

<span data-ttu-id="d12b2-134">我仍以屬於網域使用者的本機系統管理員身分執行 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d12b2-134">I'm still running PowerShell as a local admin who is a domain user.</span></span> <span data-ttu-id="d12b2-135">當我嘗試使用 `Get-CimInstance` Cmdlet 從遠端電腦查詢資訊時，收到拒絕存取錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="d12b2-135">When I try to query information from a remote computer using the `Get-CimInstance` cmdlet, I receive an access denied error message.</span></span>

```powershell
Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
```

```Output
Get-CimInstance : Access is denied.
At line:1 char:1
+ Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
+ ``````````````````````````````````````````````````````~~
    + CategoryInfo          : PermissionDenied: (root\cimv2:Win32_BIOS:String) [Get-CimI
   nstance], CimException
    + FullyQualifiedErrorId : HRESULT 0x80070005,Microsoft.Management.Infrastructure.Cim
   Cmdlets.GetCimInstanceCommand
    + PSComputerName        : dc01
```

<span data-ttu-id="d12b2-136">許多人對於 PowerShell 有安全性疑慮，但事實上，您在 PowerShell 中的權限與在 GUI 中完全相同。</span><span class="sxs-lookup"><span data-stu-id="d12b2-136">Many people have security concerns when it comes to PowerShell, but the truth is you have exactly the same permissions in PowerShell as you do in the GUI.</span></span> <span data-ttu-id="d12b2-137">不會更多也不會更少。</span><span class="sxs-lookup"><span data-stu-id="d12b2-137">No more and no less.</span></span> <span data-ttu-id="d12b2-138">上一個範例中的問題是，執行 PowerShell 的使用者沒有從 DC01 伺服器查詢 WMI 資訊的權限。</span><span class="sxs-lookup"><span data-stu-id="d12b2-138">The problem in the previous example is that the user running PowerShell doesn't have rights to query WMI information from the DC01 server.</span></span> <span data-ttu-id="d12b2-139">我可以以網域系統管理員的身分重新啟動 PowerShell，因為 `Get-CimInstance` 沒有 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="d12b2-139">I could relaunch PowerShell as a domain administrator since `Get-CimInstance` doesn't have a **Credential** parameter.</span></span> <span data-ttu-id="d12b2-140">但相信我，這不是個好主意，因為這麼一來，從 PowerShell 執行的任何項目都會以網域系統管理員的身分執行。從安全性的觀點來看，視情況而定，這可能會有危險。</span><span class="sxs-lookup"><span data-stu-id="d12b2-140">But, trust me, that isn't a good idea because then anything that I run from PowerShell would be running as a domain admin. That could be dangerous from a security standpoint depending on the situation.</span></span>

<span data-ttu-id="d12b2-141">使用最低權限原則時，我會使用 **Credential** 參數 (如果命令有的話)，以每一命令為基礎的方式，提高權限為我的網域系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="d12b2-141">Using the principle of least privilege, I elevate to my domain admin account on a per command basis using the **Credential** parameter, if a command has one.</span></span> <span data-ttu-id="d12b2-142">`Get-CimInstance` 沒有 **Credential** 參數，因此此案例中的解決方案是先建立 **CimSession**。</span><span class="sxs-lookup"><span data-stu-id="d12b2-142">`Get-CimInstance` doesn't have a **Credential** parameter so the solution in this scenario is to create a **CimSession** first.</span></span> <span data-ttu-id="d12b2-143">然後我使用 **CimSession**，而不是電腦名稱來查詢遠端電腦上的 WMI。</span><span class="sxs-lookup"><span data-stu-id="d12b2-143">Then I use the **CimSession** instead of a computer name to query WMI on the remote computer.</span></span>

```powershell
$CimSession = New-CimSession -ComputerName dc01 -Credential (Get-Credential)
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

<span data-ttu-id="d12b2-144">CIM 工作階段儲存在名為 `$CimSession` 的變數中。</span><span class="sxs-lookup"><span data-stu-id="d12b2-144">The CIM session was stored in a variable named `$CimSession`.</span></span> <span data-ttu-id="d12b2-145">請注意，我也在括弧中指定了 `Get-Credential` Cmdlet，使得它會先執行，並提示我輸入替代認證，之後再建立新的工作階段。</span><span class="sxs-lookup"><span data-stu-id="d12b2-145">Notice that I also specified the `Get-Credential` cmdlet in parentheses so that it executes first, prompting me for alternate credentials, before creating the new session.</span></span> <span data-ttu-id="d12b2-146">我將在本章稍後說明指定替代認證的另一個更有效率的方式，但請務必在讓它變得更複雜之前，先了解此基本概念。</span><span class="sxs-lookup"><span data-stu-id="d12b2-146">I'll show you another more efficient way to specify alternate credentials later in this chapter, but it's important to understand this basic concept before making it more complicated.</span></span>

<span data-ttu-id="d12b2-147">先前範例中所建立的 CIM 工作階段現在可以與 `Get-CimInstance` Cmdlet 搭配使用，以從遠端電腦上的 WMI 查詢 BIOS 資訊。</span><span class="sxs-lookup"><span data-stu-id="d12b2-147">The CIM session created in the previous example can now be used with the `Get-CimInstance` cmdlet to query the BIOS information from WMI on the remote computer.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01
```

<span data-ttu-id="d12b2-148">使用 CIM 工作階段而不只是指定電腦名稱有幾個額外的優點。</span><span class="sxs-lookup"><span data-stu-id="d12b2-148">There are several additional benefits to using CIM sessions instead of just specifying a computer name.</span></span> <span data-ttu-id="d12b2-149">對相同電腦執行多個查詢時，使用 CIM 工作階段較針對每個查詢使用電腦名稱更有效率。</span><span class="sxs-lookup"><span data-stu-id="d12b2-149">When running multiple queries to the same computer, using a CIM session is more efficient than using the computer name for each query.</span></span> <span data-ttu-id="d12b2-150">建立 CIM 工作階段只會設定連線一次。</span><span class="sxs-lookup"><span data-stu-id="d12b2-150">Creating a CIM session only sets up the connection once.</span></span>
<span data-ttu-id="d12b2-151">然後，多個查詢會使用該相同工作階段來擷取資訊。</span><span class="sxs-lookup"><span data-stu-id="d12b2-151">Then, multiple queries use that same session to retrieve information.</span></span> <span data-ttu-id="d12b2-152">使用電腦名稱需要 Cmdlet 來設定及卸載與每個個別查詢的連線。</span><span class="sxs-lookup"><span data-stu-id="d12b2-152">Using the computer name requires the cmdlets to set up and tear down the connection with each individual query.</span></span>

<span data-ttu-id="d12b2-153">`Get-CimInstance` Cmdlet 預設會使用 WSMan 通訊協定，這表示遠端電腦需要 PowerShell 3.0 或更高版本才能連線。</span><span class="sxs-lookup"><span data-stu-id="d12b2-153">The `Get-CimInstance` cmdlet uses the WSMan protocol by default, which means the remote computer needs PowerShell version 3.0 or higher to connect.</span></span> <span data-ttu-id="d12b2-154">它實際上不是很重要的 PowerShell 版本，而是堆疊版本。</span><span class="sxs-lookup"><span data-stu-id="d12b2-154">It's actually not the PowerShell version that matters, it's the stack version.</span></span> <span data-ttu-id="d12b2-155">您可以使用 `Test-WSMan` Cmdlet 來判斷堆疊版本。</span><span class="sxs-lookup"><span data-stu-id="d12b2-155">The stack version can be determined using the `Test-WSMan` cmdlet.</span></span>
<span data-ttu-id="d12b2-156">它必須是 3.0 版。</span><span class="sxs-lookup"><span data-stu-id="d12b2-156">It needs to be version 3.0.</span></span> <span data-ttu-id="d12b2-157">這是您會在 PowerShell 3.0 版和更新版本中找到的版本。</span><span class="sxs-lookup"><span data-stu-id="d12b2-157">That's the version you'll find with PowerShell version 3.0 and higher.</span></span>

```powershell
Test-WSMan -ComputerName dc01
```

```Output
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd
ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd
ProductVendor   : Microsoft Corporation
ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 3.0
```

<span data-ttu-id="d12b2-158">較舊的 WMI Cmdlet 會使用與舊版 Windows 相容的 DCOM 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="d12b2-158">The older WMI cmdlets use the DCOM protocol, which is compatible with older versions of Windows.</span></span> <span data-ttu-id="d12b2-159">但在較新版本的 Windows 上，防火牆通常會封鎖 DCOM。</span><span class="sxs-lookup"><span data-stu-id="d12b2-159">But DCOM is typically blocked by the firewall on newer versions of Windows.</span></span> <span data-ttu-id="d12b2-160">`New-CimSessionOption` Cmdlet 可讓您建立 DCOM 通訊協定連線，以與 `New-CimSession` 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="d12b2-160">The `New-CimSessionOption` cmdlet allows you to create a DCOM protocol connection for use with `New-CimSession`.</span></span> <span data-ttu-id="d12b2-161">這麼做會允許使用 `Get-CimInstance` Cmdlet 來與舊版 Windows (最舊為 Windows Server 2000) 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="d12b2-161">This allows the `Get-CimInstance` cmdlet to be used to communicate with versions of Windows as old as Windows Server 2000.</span></span> <span data-ttu-id="d12b2-162">這也表示在使用 `Get-CimInstance` Cmdlet 搭配設定為使用 DCOM 通訊協定的 CimSession 時，遠端電腦上不需要有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d12b2-162">This also means that PowerShell is not required on the remote computer when using the `Get-CimInstance` cmdlet with a CimSession that's configured to use the DCOM protocol.</span></span>

<span data-ttu-id="d12b2-163">使用 `New-CimSessionOption` Cmdlet 建立 DCOM 通訊協定選項，並將其儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="d12b2-163">Create the DCOM protocol option using the `New-CimSessionOption` cmdlet and store it in a variable.</span></span>

```powershell
$DCOM = New-CimSessionOption -Protocol Dcom
```

<span data-ttu-id="d12b2-164">為了提高效率，您可以將您的網域系統管理員或提高權限的認證儲存在變數中，這樣您就不需要針對每個命令持續輸入它們。</span><span class="sxs-lookup"><span data-stu-id="d12b2-164">For efficiency, you can store your domain administrator or elevated credentials in a variable so you don't have to constantly enter them for each command.</span></span>

```powershell
$Cred = Get-Credential
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

<span data-ttu-id="d12b2-165">我有一個名為 SQL03 的伺服器，其執行 Windows Server 2008 (非 R2)。</span><span class="sxs-lookup"><span data-stu-id="d12b2-165">I have a server named SQL03 that runs Windows Server 2008 (non-R2).</span></span> <span data-ttu-id="d12b2-166">這是最新的 Windows Server 作業系統，預設不會安裝 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d12b2-166">It's the newest Windows Server operating system that doesn't have PowerShell installed by default.</span></span>

<span data-ttu-id="d12b2-167">使用 DCOM 通訊協定建立與 SQL03 連線的 **CimSession**。</span><span class="sxs-lookup"><span data-stu-id="d12b2-167">Create a **CimSession** to SQL03 using the DCOM protocol.</span></span>

```powershell
$CimSession = New-CimSession -ComputerName sql03 -SessionOption $DCOM -Credential $Cred
```

<span data-ttu-id="d12b2-168">請注意，在上一個命令中，這次我將名為 `$Cred` 的變數指定為 **Credential** 參數的值，而不需要再次手動輸入。</span><span class="sxs-lookup"><span data-stu-id="d12b2-168">Notice in the previous command, this time I specified the variable named `$Cred` as the value for the **Credential** parameter instead of having to enter them manually again.</span></span>

<span data-ttu-id="d12b2-169">不論使用的基礎通訊協定為何，查詢的輸出都相同。</span><span class="sxs-lookup"><span data-stu-id="d12b2-169">The output of the query is the same regardless of the underlying protocol being used.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

<span data-ttu-id="d12b2-170">`Get-CimSession` Cmdlet 可用來查看目前連線的 **CimSessions**，以及它們所使用的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="d12b2-170">The `Get-CimSession` cmdlet is used to see what **CimSessions** are currently connected and what protocols they're using.</span></span>

```powershell
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : 80742787-e38e-41b1-a7d7-fa1369cf1402
ComputerName : dc01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : 8fcabd81-43cf-4682-bd53-ccce1e24aecb
ComputerName : sql03
Protocol     : DCOM
```

<span data-ttu-id="d12b2-171">擷取並儲存先前建立的 **CimSessions** 在名為 `$CimSession` 的變數中。</span><span class="sxs-lookup"><span data-stu-id="d12b2-171">Retrieve and store both of the previously created **CimSessions** in a variable named `$CimSession`.</span></span>

```powershell
$CimSession = Get-CimSession
```

<span data-ttu-id="d12b2-172">使用一個命令來查詢這兩部電腦，一個使用 WSMan 通訊協定，另一個則使用 DCOM。</span><span class="sxs-lookup"><span data-stu-id="d12b2-172">Query both of the computers with one command, one using the WSMan protocol and the other one with DCOM.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01

SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

<span data-ttu-id="d12b2-173">我撰寫了許多關於 WMI 和 CIM Cmdlet 的部落格文章。</span><span class="sxs-lookup"><span data-stu-id="d12b2-173">I've written numerous blog articles about the WMI and CIM cmdlets.</span></span> <span data-ttu-id="d12b2-174">其中一個最實用的文章，就是關於我建立的一個函式，用來自動判斷是否應該使用 WSMan 或 DCOM，並自動設定 CIM 工作階段，而不必手動找出是哪一個。</span><span class="sxs-lookup"><span data-stu-id="d12b2-174">One of the most useful ones is about a function that I created to automatically determine if WSMan or DCOM should be used and set up the CIM session automatically without having to figure out which one manually.</span></span> <span data-ttu-id="d12b2-175">該部落格文章的標題是：[用來建立對遠端電腦的 CimSessions 連線並後援至 DCOM 的 PowerShell 函式][] (英文)。</span><span class="sxs-lookup"><span data-stu-id="d12b2-175">That blog article is titled [PowerShell Function to Create CimSessions to Remote Computers with Fallback to Dcom][].</span></span>

<span data-ttu-id="d12b2-176">完成 CIM 工作階段時，您應該使用 `Remove-CimSession` Cmdlet 加以移除。</span><span class="sxs-lookup"><span data-stu-id="d12b2-176">When you're finished with the CIM sessions, you should remove them with the `Remove-CimSession` cmdlet.</span></span> <span data-ttu-id="d12b2-177">若要移除所有 CIM 工作階段，只需將 `Get-CimSession` 以管線傳送至 `Remove-CimSession`。</span><span class="sxs-lookup"><span data-stu-id="d12b2-177">To remove all CIM sessions, simply pipe `Get-CimSession` to `Remove-CimSession`.</span></span>

```powershell
Get-CimSession | Remove-CimSession
```

## <a name="summary"></a><span data-ttu-id="d12b2-178">摘要</span><span class="sxs-lookup"><span data-stu-id="d12b2-178">Summary</span></span>

<span data-ttu-id="d12b2-179">在本章中，您已了解如何使用 PowerShell 在本機和遠端電腦上使用 WMI。</span><span class="sxs-lookup"><span data-stu-id="d12b2-179">In this chapter, you've learned about using PowerShell to work with WMI on both local and remote computers.</span></span> <span data-ttu-id="d12b2-180">您也已了解如何利用 CIM Cmdlet，以透過 WSMan 或 DCOM 通訊協定來處理遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="d12b2-180">You've also learned how to use the CIM cmdlets to work with remote computers with both the WSMan or DCOM protocol.</span></span>

## <a name="review"></a><span data-ttu-id="d12b2-181">檢閱</span><span class="sxs-lookup"><span data-stu-id="d12b2-181">Review</span></span>

1. <span data-ttu-id="d12b2-182">WMI 和 CIM Cmdlet 有何差異？</span><span class="sxs-lookup"><span data-stu-id="d12b2-182">What is the difference in the WMI and CIM cmdlets?</span></span>
1. <span data-ttu-id="d12b2-183">根據預設，`Get-CimInstance` Cmdlet 會使用哪個通訊協定？</span><span class="sxs-lookup"><span data-stu-id="d12b2-183">By default, what protocol does the `Get-CimInstance` cmdlet use?</span></span>
1. <span data-ttu-id="d12b2-184">使用 CIM 工作階段，而非使用 `Get-CimInstance` 來指定電腦名稱有哪些優點？</span><span class="sxs-lookup"><span data-stu-id="d12b2-184">What are some of the benefits of using a CIM session instead of specifying a computer name with `Get-CimInstance`?</span></span>
1. <span data-ttu-id="d12b2-185">如何指定預設值以外的替代通訊協定，以與 `Get-CimInstance` 搭配使用？</span><span class="sxs-lookup"><span data-stu-id="d12b2-185">How do you specify an alternate protocol other than the default one for use with `Get-CimInstance`?</span></span>
1. <span data-ttu-id="d12b2-186">如何關閉或移除 CIM 工作階段？</span><span class="sxs-lookup"><span data-stu-id="d12b2-186">How do you close or remove CIM sessions?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="d12b2-187">建議閱讀資料</span><span class="sxs-lookup"><span data-stu-id="d12b2-187">Recommended Reading</span></span>

- <span data-ttu-id="d12b2-188">[about_WMI][]</span><span class="sxs-lookup"><span data-stu-id="d12b2-188">[about_WMI][]</span></span>
- <span data-ttu-id="d12b2-189">[about_WMI_Cmdlets][]</span><span class="sxs-lookup"><span data-stu-id="d12b2-189">[about_WMI_Cmdlets][]</span></span>
- <span data-ttu-id="d12b2-190">[about_WQL][]</span><span class="sxs-lookup"><span data-stu-id="d12b2-190">[about_WQL][]</span></span>
- <span data-ttu-id="d12b2-191">[CimCmdlets 模組][]</span><span class="sxs-lookup"><span data-stu-id="d12b2-191">[CimCmdlets Module][]</span></span>
- <span data-ttu-id="d12b2-192">[影片：使用 CIM Cmdlet 和 CIM 工作階段][]</span><span class="sxs-lookup"><span data-stu-id="d12b2-192">[Video: Using CIM Cmdlets and CIM Sessions][]</span></span>

<!-- link references -->
[about_WMI]: /powershell/module/microsoft.powershell.core/about/about_wmi
[about_WMI_Cmdlets]: /powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets
[about_WQL]: /powershell/module/microsoft.powershell.core/about/about_wql
[CimCmdlets 模組]: /powershell/module/cimcmdlets/
[CimCmdlets Module]: /powershell/module/cimcmdlets/
[影片：使用 CIM Cmdlet 和 CIM 工作階段]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[Video: Using CIM Cmdlets and CIM Sessions]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[用來建立對遠端電腦的 CimSessions 連線並後援至 DCOM 的 PowerShell 函式]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
[PowerShell Function to Create CimSessions to Remote Computers with Fallback to Dcom]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
