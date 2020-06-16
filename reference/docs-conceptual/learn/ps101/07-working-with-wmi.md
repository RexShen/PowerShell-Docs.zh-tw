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
# <a name="chapter-7---working-with-wmi"></a>第 7 章 - 使用 WMI

## <a name="wmi-and-cim"></a>WMI 和 CIM

PowerShell 預設隨附用於與其他技術 (例如 Windows Management Instrumentation (WMI)) 搭配使用的 Cmdlet。 PowerShell 中存在數個原生 WMI Cmdlet，而不需安裝任何額外的軟體或模組。

PowerShell 一開始便有可搭配 WMI 使用的 Cmdlet。 `Get-Command` 可以用來判斷 PowerShell 中有哪些 WMI Cmdlet。 下列結果來自執行 PowerShell 5.1 版的 Windows 10 實驗室環境電腦。 根據您正在執行的 PowerShell 版本，您的結果可能會有所不同。

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

通用訊息模型 (CIM) Cmdlet 是在 PowerShell 3.0 版中推出。 CIM Cmdlet 的設計是要同時在 Windows 和非 Windows 電腦上使用。 WMI Cmdlet 已淘汰，因此我的建議是使用 CIM Cmdlet，而不是較舊的 WMI Cmdlet。

CIM Cmdlet 全都包含在模組中。 若要取得 CIM Cmdlet 的清單，請使用 `Get-Command` 搭配 **Module** 參數，如下列範例所示。

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

CIM Cmdlet 仍然可讓您使用 WMI，因此當有人說「我使用 PowerShell CIM Cmdlet 查詢 WMI 時...」，請不要感到困惑

如先前所述，WMI 是 PowerShell 中的個別技術，而您只是使用 CIM Cmdlet 來存取 WMI。 您可能會發現使用 WMI 查詢語言 (WQL) 來查詢 WMI 的舊 VBScript，如下列範例所示。

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

您可以從該 VBScript 取得 WQL 查詢，並在不進行任何修改的情況下，將它與 `Get-CimInstance` Cmdlet 搭配使用。

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

這並非我一般使用 PowerShell 查詢 WMI 的方式。 但它的確可行，並可讓您輕鬆將現有的 VBScript 遷移至 PowerShell。 當我開始撰寫一行程式碼來查詢 WMI 時，我會使用下列語法。

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

如果我只想要序號，我可以將輸出以管線傳送至 `Select-Object`，並只指定  **SerialNumber** 屬性。

```powershell
Get-CimInstance -ClassName Win32_BIOS | Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

根據預設，有數個在幕後擷取的屬性從未使用過。
在本機電腦上查詢 WMI 時，可能差別不大。 可是當您開始查詢遠端電腦，不只是傳回該資訊需要額外的處理時間，還有在網路上提取非必要資訊的額外時間。 `Get-CimInstance` 具有 **Property** 參數，會限制擷取的資訊。 這可讓查詢 WMI 更有效率。

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

先前的結果傳回了物件。 若要傳回簡單字串，請使用 **ExpandProperty** 參數。

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -ExpandProperty SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

您也可以使用虛線樣式的語法來傳回簡單的字串。 這使得您不需要以管線傳送至 `Select-Object`。

```powershell
(Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber).SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

## <a name="query-remote-computers-with-the-cim-cmdlets"></a>使用 CIM Cmdlet 查詢遠端電腦

我仍以屬於網域使用者的本機系統管理員身分執行 PowerShell。 當我嘗試使用 `Get-CimInstance` Cmdlet 從遠端電腦查詢資訊時，收到拒絕存取錯誤訊息。

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

許多人對於 PowerShell 有安全性疑慮，但事實上，您在 PowerShell 中的權限與在 GUI 中完全相同。 不會更多也不會更少。 上一個範例中的問題是，執行 PowerShell 的使用者沒有從 DC01 伺服器查詢 WMI 資訊的權限。 我可以以網域系統管理員的身分重新啟動 PowerShell，因為 `Get-CimInstance` 沒有 **Credential** 參數。 但相信我，這不是個好主意，因為這麼一來，從 PowerShell 執行的任何項目都會以網域系統管理員的身分執行。從安全性的觀點來看，視情況而定，這可能會有危險。

使用最低權限原則時，我會使用 **Credential** 參數 (如果命令有的話)，以每一命令為基礎的方式，提高權限為我的網域系統管理員帳戶。 `Get-CimInstance` 沒有 **Credential** 參數，因此此案例中的解決方案是先建立 **CimSession**。 然後我使用 **CimSession**，而不是電腦名稱來查詢遠端電腦上的 WMI。

```powershell
$CimSession = New-CimSession -ComputerName dc01 -Credential (Get-Credential)
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

CIM 工作階段儲存在名為 `$CimSession` 的變數中。 請注意，我也在括弧中指定了 `Get-Credential` Cmdlet，使得它會先執行，並提示我輸入替代認證，之後再建立新的工作階段。 我將在本章稍後說明指定替代認證的另一個更有效率的方式，但請務必在讓它變得更複雜之前，先了解此基本概念。

先前範例中所建立的 CIM 工作階段現在可以與 `Get-CimInstance` Cmdlet 搭配使用，以從遠端電腦上的 WMI 查詢 BIOS 資訊。

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

使用 CIM 工作階段而不只是指定電腦名稱有幾個額外的優點。 對相同電腦執行多個查詢時，使用 CIM 工作階段較針對每個查詢使用電腦名稱更有效率。 建立 CIM 工作階段只會設定連線一次。
然後，多個查詢會使用該相同工作階段來擷取資訊。 使用電腦名稱需要 Cmdlet 來設定及卸載與每個個別查詢的連線。

`Get-CimInstance` Cmdlet 預設會使用 WSMan 通訊協定，這表示遠端電腦需要 PowerShell 3.0 或更高版本才能連線。 它實際上不是很重要的 PowerShell 版本，而是堆疊版本。 您可以使用 `Test-WSMan` Cmdlet 來判斷堆疊版本。
它必須是 3.0 版。 這是您會在 PowerShell 3.0 版和更新版本中找到的版本。

```powershell
Test-WSMan -ComputerName dc01
```

```Output
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd
ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd
ProductVendor   : Microsoft Corporation
ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 3.0
```

較舊的 WMI Cmdlet 會使用與舊版 Windows 相容的 DCOM 通訊協定。 但在較新版本的 Windows 上，防火牆通常會封鎖 DCOM。 `New-CimSessionOption` Cmdlet 可讓您建立 DCOM 通訊協定連線，以與 `New-CimSession` 搭配使用。 這麼做會允許使用 `Get-CimInstance` Cmdlet 來與舊版 Windows (最舊為 Windows Server 2000) 進行通訊。 這也表示在使用 `Get-CimInstance` Cmdlet 搭配設定為使用 DCOM 通訊協定的 CimSession 時，遠端電腦上不需要有 PowerShell。

使用 `New-CimSessionOption` Cmdlet 建立 DCOM 通訊協定選項，並將其儲存在變數中。

```powershell
$DCOM = New-CimSessionOption -Protocol Dcom
```

為了提高效率，您可以將您的網域系統管理員或提高權限的認證儲存在變數中，這樣您就不需要針對每個命令持續輸入它們。

```powershell
$Cred = Get-Credential
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

我有一個名為 SQL03 的伺服器，其執行 Windows Server 2008 (非 R2)。 這是最新的 Windows Server 作業系統，預設不會安裝 PowerShell。

使用 DCOM 通訊協定建立與 SQL03 連線的 **CimSession**。

```powershell
$CimSession = New-CimSession -ComputerName sql03 -SessionOption $DCOM -Credential $Cred
```

請注意，在上一個命令中，這次我將名為 `$Cred` 的變數指定為 **Credential** 參數的值，而不需要再次手動輸入。

不論使用的基礎通訊協定為何，查詢的輸出都相同。

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

`Get-CimSession` Cmdlet 可用來查看目前連線的 **CimSessions**，以及它們所使用的通訊協定。

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

擷取並儲存先前建立的 **CimSessions** 在名為 `$CimSession` 的變數中。

```powershell
$CimSession = Get-CimSession
```

使用一個命令來查詢這兩部電腦，一個使用 WSMan 通訊協定，另一個則使用 DCOM。

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

我撰寫了許多關於 WMI 和 CIM Cmdlet 的部落格文章。 其中一個最實用的文章，就是關於我建立的一個函式，用來自動判斷是否應該使用 WSMan 或 DCOM，並自動設定 CIM 工作階段，而不必手動找出是哪一個。 該部落格文章的標題是：[用來建立對遠端電腦的 CimSessions 連線並後援至 DCOM 的 PowerShell 函式][] (英文)。

完成 CIM 工作階段時，您應該使用 `Remove-CimSession` Cmdlet 加以移除。 若要移除所有 CIM 工作階段，只需將 `Get-CimSession` 以管線傳送至 `Remove-CimSession`。

```powershell
Get-CimSession | Remove-CimSession
```

## <a name="summary"></a>摘要

在本章中，您已了解如何使用 PowerShell 在本機和遠端電腦上使用 WMI。 您也已了解如何利用 CIM Cmdlet，以透過 WSMan 或 DCOM 通訊協定來處理遠端電腦。

## <a name="review"></a>檢閱

1. WMI 和 CIM Cmdlet 有何差異？
1. 根據預設，`Get-CimInstance` Cmdlet 會使用哪個通訊協定？
1. 使用 CIM 工作階段，而非使用 `Get-CimInstance` 來指定電腦名稱有哪些優點？
1. 如何指定預設值以外的替代通訊協定，以與 `Get-CimInstance` 搭配使用？
1. 如何關閉或移除 CIM 工作階段？

## <a name="recommended-reading"></a>建議閱讀資料

- [about_WMI][]
- [about_WMI_Cmdlets][]
- [about_WQL][]
- [CimCmdlets 模組][]
- [影片：使用 CIM Cmdlet 和 CIM 工作階段][]

<!-- link references -->
[about_WMI]: /powershell/module/microsoft.powershell.core/about/about_wmi
[about_WMI_Cmdlets]: /powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets
[about_WQL]: /powershell/module/microsoft.powershell.core/about/about_wql
[CimCmdlets 模組]: /powershell/module/cimcmdlets/
[影片：使用 CIM Cmdlet 和 CIM 工作階段]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[用來建立對遠端電腦的 CimSessions 連線並後援至 DCOM 的 PowerShell 函式]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
