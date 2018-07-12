---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 安裝 Windows PowerShell SDK
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: fa876bac0c1afac24f93d11dd2e7ecfb1165cf5f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893533"
---
# <a name="installing-the-windows-powershell-sdk"></a>安裝 Windows PowerShell SDK

下列主題說明如何在不同版本的 Windows 上安裝 PowerShell SDK。

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>安裝適用於 Windows 8 及 Windows Server 2012 的 Windows PowerShell 3.0 SDK

Windows 8 及 Windows Server 2012 會自動安裝 Windows PowerShell 3.0。
您也可以下載並安裝 Windows PowerShell 3.0 的參考組件，當做 Windows 8 SDK 的一部分。
這些組件可讓您撰寫 Windows PowerShell 3.0 的 Cmdlet、提供者和主機程式。
當您安裝適用於 Windows 8 的 Windows SDK 時，Windows PowerShell 組件會自動安裝在參考組件資料夾中 (位於 `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0` 中)。
如需詳細資訊，請參閱 [Windows 8 SDK 下載網站](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive)。
開發中心也會提供 Windows PowerShell 程式碼範例。
如需詳細資訊，請參閱[開發人員中心網站](https://code.msdn.microsoft.com:443/windowsdesktop/)的桌面程式碼範例頁面。

此外，包含多個程式碼範例的 Windows PowerShell 3.0 與 Windows PowerShell 2.0 SDK 相容。
如需如何下載 Windows PowerShell 2.0 SDK 的詳細資訊，請參閱以下內容。
(請注意，雖然 2.0 程式碼範例與 Windows 8 和 Windows PowerShell 3.0 相容，但 Windows 8 平台無法安裝 Windows PowerShell 2.0。)

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>安裝適用於 Windows 7 及 Windows Server 2008 R2 的 Windows PowerShell 3.0 SDK

Windows 7 及 Windows Server 2008 R2 會自動安裝 PowerShell 2.0。
您也可以在這些系統上安裝 PowerShell 3.0。
(如需詳細資訊，請參閱[安裝 Windows PowerShell](Installing-Windows-PowerShell.md)。)
如上所述，您也可以在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows 8 SDK。

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>安裝適用於 Windows 7、Vista、XP、Server 2003 及 Server 2008 的 Windows PowerShell 2.0 SDK

Windows PowerShell 2.0 SDK 提供撰寫 Cmdlet、提供者和主控應用程式所需的參考組件，並提供作為開始撰寫程式碼的起點 C# 範例程式碼。

若要安裝此 SDK，請參閱 [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560)。

## <a name="reference-assemblies"></a>參考組件

參考組件預設會安裝在下列位置︰`c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`。

> [!NOTE] 
> 針對 Windows PowerShell 2.0 組件編譯的程式碼無法載入到 Windows PowerShell 1.0 安裝中。
> 不過，針對 Windows PowerShell 1.0 組件編譯的程式碼可以載入至 Windows PowerShell 2.0 安裝。

## <a name="samples"></a>範例

程式碼範例預設會安裝在下列位置︰`C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`。

以下各節提供每個範例之用途的簡要說明。

## <a name="cmdlet-samples"></a>Cmdlet 範例

### <a name="getprocesssample01"></a>GetProcessSample01

示範如何撰寫簡易的 Cmdlet，進而取得本機電腦上的所有處理序。

### <a name="getprocesssample02"></a>GetProcessSample02

示範如何將參數新增至 Cmdlet。
此 Cmdlet 會採用一或多個處理序名稱，並傳回相符的處理序。

### <a name="getprocesssample03"></a>GetProcessSample03

示範如何新增可自管線接受輸入的參數。

### <a name="getprocesssample04"></a>GetProcessSample04

示範如何處理非終止錯誤。

### <a name="getprocesssample05"></a>GetProcessSample05

示範如何顯示指定的處理序清單。

### <a name="selectobject"></a>SelectObject

示範如何撰寫篩選，進而僅選取特定的物件。

### <a name="selectstring"></a>SelectString

示範如何搜尋指定模式的檔案。

### <a name="stopprocesssample01"></a>StopProcessSample01

示範如何實作 *PassThru* 參數，以及如何透過呼叫 [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) 及 [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) 方法來要求使用者意見回應。
使用者會在想要強制 Cmdlet 傳回物件時指定 *PassThru* 參數。

### <a name="stopprocesssample02"></a>StopProcessSample02

示範如何停止特定處理序。

### <a name="stopprocesssample03"></a>StopProcessSample03

示範如何宣告參數的別名，以及如何支援萬用字元。

### <a name="stopprocesssample04"></a>StopProcessSample04

示範如何宣告參數集 (Cmdlet 用作輸入的物件)，以及如何指定要使用的預設參數集。

## <a name="remoting-samples"></a>遠端範例

### <a name="remoterunspace01"></a>RemoteRunspace01

示範如何建立用來建立遠端連線的遠端 Runspace。

### <a name="remoterunspacepool01"></a>RemoteRunspacePool01

示範如何建構遠端 Runspace 集區，以及如何使用此集區同時執行多個命令。

### <a name="serialization01"></a>Serialization01

示範如何查看現有的 .NET 類別，並確定此類別所選公用屬性的資訊會保留於序列化/還原序列化。

### <a name="serialization02"></a>Serialization02

示範如何查看現有的 .NET 類別，並確定此類別的執行個體資訊會在無法於類別的公用屬性中使用時，保留於序列化/還原序列化。

### <a name="serialization03"></a>Serialization03

示範如何查看現有的 .NET 類別，並確定此類別和衍生類別的執行個體都會還原序列化 (解除凍結) 成實際 .NET 物件。

## <a name="event-samples"></a>事件範例

### <a name="event01"></a>Event01

示範如何透過衍生自 ObjectEventRegistrationBase 來建立事件註冊的 Cmdlet。

### <a name="event02"></a>Event02

示範如何接收遠端電腦上所產生的 Windows PowerShell 事件的通知。
其會使用透過 [Runspace](/dotnet/api/system.management.automation.runspaces.runspace) 類別公開的 PSEventReceived 事件。

## <a name="hosting-application-samples"></a>主控應用程式範例

### <a name="runspace01"></a>Runspace01

示範如何使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 類別以同步執行 [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet。
[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet 會為本機電腦上所執行的每個處理序傳回 [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) 物件。

### <a name="runspace02"></a>Runspace02

示範如何使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 類別以同步執行 [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 及 [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) Cmdlet。
[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet 會為本機電腦上所執行的每個處理序傳回 [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) 物件，而 `Sort-Object` 會依據物件的 [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) 屬性排序物件。
這些命令的結果會透過使用 [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) 控制項來顯示。

### <a name="runspace03"></a>Runspace03

示範如何使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 類別以同步執行指令碼，以及如何處理非終止錯誤。
指令碼會接收處理序名稱的清單，然後擷取這些處理序。
指令碼的結果會顯示在主控台視窗中，包括執行指令碼時所產生的任何非終止錯誤在內。

### <a name="runspace04"></a>Runspace04

示範如何使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 類別來執行命令，以及如何捕捉執行命令時所擲回的終止錯誤。
執行了兩個命令，而最後一個命令傳遞了無效的參數引數。
如此便不會傳回任何物件，且會擲回終止錯誤。

### <a name="runspace05"></a>Runspace05

示範如何將嵌入式管理單元新增至 [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) 物件，讓嵌入式管理單元的 Cmdlet 可在 Runspace 開啟時使用。
嵌入式管理單元提供 Get-Proc Cmdlet (由 [GetProcessSample01 範例](https://technet.microsoft.com/library/ff602028.aspx) 定義)，其透過使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 物件同步執行。

### <a name="runspace06"></a>Runspace06

示範如何將模組新增至 [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) 物件，使模組在 Runspace 開啟時載入。
模組提供 Get-Proc Cmdlet (由 [GetProcessSample02 範例](https://technet.microsoft.com/library/ff602027.aspx) 定義)，其透過使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 物件同步執行。

### <a name="runspace07"></a>Runspace07

示範如何建立 Runspace，並使用該 Runspace 透過 [PowerShell](/dotnet/api/system.management.automation.powershell) 物件以同步執行兩個 Cmdlet。

### <a name="runspace08"></a>Runspace08

示範如何將命令和引數新增至 [PowerShell](/dotnet/api/system.management.automation.powershell) 物件的管線，以及如何同步執行命令。

### <a name="runspace09"></a>Runspace09

示範如何將指令碼新增至 [PowerShell](/dotnet/api/system.management.automation.powershell) 物件的管線，以及如何非同步地執行指令碼。
事件為用來處理指令碼的輸出。

### <a name="runspace10"></a>Runspace10

示範如何建立預設初始工作階段狀態、如何將 Cmdlet 新增至 [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate)、如何建立使用初始工作階段狀態的 Runspace，以及如何使用 [PowerShell](/dotnet/api/system.management.automation.powershell) 物件執行此命令。

### <a name="runspace11"></a>Runspace11

示範如何使用 [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) 類別來建立 Proxy 命令，該命令會呼叫現有的 Cmdlet，但會限制可用的參數集。
Proxy 命令接著會加入用來建立受限 Runspace 的初始工作階段狀態。
這表示使用者只能透過 Proxy 命令使用此 Cmdlet 的功能。

### <a name="powershell01"></a>PowerShell01

示範如何使用 [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) 物件建立受限的 Runspace 。

### <a name="powershell02"></a>PowerShell02

示範如何使用 Runspace 集區同時執行多個命令。

## <a name="host-samples"></a>主機範例

### <a name="host01"></a>Host01

示範如何實作使用自訂主機的主應用程式。
在這個範例中，建立了使用自訂主機的 Runspace，然後使用 [PowerShell](/dotnet/api/system.management.automation.powershell) API 執行呼叫 "exit" 的指令碼。
主應用程式會查看指令碼的輸出，並列印結果。

### <a name="host02"></a>Host02

示範如何撰寫使用 Windows PowerShell 執行階段及自訂主機實作的主應用程式。
主應用程式會將主機的文化特性設定為德文、執行 [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet，並顯示您使用 pwrsh.exe 時會看到的結果，然後以德文列印目前的日期和時間。

### <a name="host03"></a>Host03

示範如何建置互動式主控台主應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。

### <a name="host04"></a>Host04

示範如何建置互動式主控台主應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。
這個主應用程式也支援顯示允許使用者指定多個選項的提示。

### <a name="host05"></a>Host05

示範如何建置互動式主控台主應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。
這個主應用程式也支援使用 [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) 和 [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) Cmdlet 呼叫遠端電腦。

### <a name="host06"></a>Host06

示範如何建置互動式主控台主應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。
此外，這個範例會使用權杖化工具 API 指定使用者所輸入的文字色彩。

## <a name="provider-samples"></a>提供者範例

### <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

示範如何宣告直接衍生自 [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) 類別的提供者類別。
包含在此僅為完整性用途。

### <a name="accessdbprovidersample02"></a>AccessDBProviderSample02

示範如何覆寫 [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) 和 [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) 方法來支援對 `New-PSDrive` 和 `Remove-PSDrive` Cmdlet 的呼叫。
此範例中的提供者類別衍生自 [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) 類別。

### <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

示範如何覆寫 [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) 和 [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) 方法來支援對 `Get-Item` 和 `Set-Item` Cmdlet 的呼叫。
此範例中的提供者類別衍生自 [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) 類別。

### <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

示範如何覆寫容器方法來支援對 `Copy-Item`、`Get-ChildItem`、`New-Item` 和 `Remove-Item` Cmdlet 的呼叫。
當資料存放區包含容器項目時，就應該實作這些方法。
容器是常見父項目底下的一組子項目。
此範例中的提供者類別衍生自 [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) 類別。

### <a name="accessdbprovidersample05"></a>AccessDBProviderSample05

示範如何覆寫容器方法來支援對 `Move-Item` 和 `Join-Path` Cmdlet 的呼叫。
當使用者需要移動容器內的項目，而且資料存放區包含巢狀容器時，就應該實作這些方法。
此範例中的提供者類別衍生自 [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) 類別。

### <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

示範如何覆寫內容方法來支援對 `Clear-Content`、`Get-Content` 和 `Set-Content` Cmdlet 的呼叫。
當使用者需要管理資料存放區的項目內容時，就應該實作這些方法。
此範例中的提供者類別衍生自 [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) 類別，且其會實作 [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) 介面。