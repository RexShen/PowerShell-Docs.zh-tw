---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 安裝 Windows PowerShell SDK
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: 830b054c2cf2b49d935d3d96b79effa7131f6db2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953560"
---
# <a name="installing-the-windows-powershell-sdk"></a>安裝 Windows PowerShell SDK

下列主題說明如何在不同版本的 Windows 上安裝 PowerShell SDK。

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>安裝適用於 Windows 8 及 Windows Server 2012 的 Windows PowerShell 3.0 SDK

Windows 8 及 Windows Server 2012 會自動安裝 Windows PowerShell 3.0。
您也可以下載並安裝 Windows PowerShell 3.0 的參考組件，當做 Windows 8 SDK 的一部分。
這些組件可讓您撰寫 Windows PowerShell 3.0 的 Cmdlet、提供者和主機程式。
當您安裝 Windows SDK for Windows 8 時，Windows PowerShell 組件會自動安裝在參考組件資料夾中：\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0。
如需詳細資訊，請參閱 [Windows 8 SDK 下載網站](http://msdn.microsoft.com/windows/hardware/hh852363.aspx)。
開發中心也會提供 Windows PowerShell 程式碼範例。
如需詳細資訊，請參閱[開發人員中心網站](http://code.msdn.microsoft.com/windowsdesktop/)的桌面程式碼範例頁面。

此外，包含多個程式碼範例的 Windows PowerShell 3.0 與 Windows PowerShell 2.0 SDK 相容。
如需如何下載 Windows PowerShell 2.0 SDK 的詳細資訊，請參閱以下內容。
(請注意，雖然 2.0 程式碼範例與 Windows 8 和 Windows PowerShell 3.0 相容，但 Windows 8 平台無法安裝 Windows PowerShell 2.0。)

##<a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>安裝適用於 Windows 7 及 Windows Server 2008 R2 的 Windows PowerShell 3.0 SDK

Windows 7 及 Windows Server 2008 R2 會自動安裝 PowerShell 2.0。
您也可以在這些系統上安裝 PowerShell 3.0。
(如需詳細資訊，請參閱[安裝 Windows PowerShell](Installing-Windows-PowerShell.md)。)
如上所述，您也可以在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows 8 SDK。

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>安裝適用於 Windows 7、Vista、XP、Server 2003 及 Server 2008 的 Windows PowerShell 2.0 SDK

Windows PowerShell 2.0 SDK 提供撰寫 Cmdlet、提供者和主控應用程式所需的參考組件，並提供作為開始撰寫程式碼的起點 C# 範例程式碼。

若要安裝此 SDK，請參閱 [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611)。

## <a name="reference-assemblies"></a>參考組件

參考組件預設會安裝在下列位置︰`c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`。

> **注意**：針對 Windows PowerShell 2.0 組件編譯的程式碼無法載入 Windows PowerShell 1.0 安裝。
>不過，針對 Windows PowerShell 1.0 組件編譯的程式碼可以載入至 Windows PowerShell 2.0 安裝。

## <a name="samples"></a>範例

程式碼範例預設會安裝在下列位置︰`C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`。

以下各節提供每個範例之用途的簡要說明。

## <a name="cmdlet-samples"></a>Cmdlet 範例
**GetProcessSample01**

示範如何撰寫簡易的 Cmdlet，進而取得本機電腦上的所有處理序。

**GetProcessSample02**

示範如何將參數新增至 Cmdlet。
此 Cmdlet 會採用一或多個處理序名稱，並傳回相符的處理序。

**GetProcessSample03**

示範如何新增可自管線接受輸入的參數。

**GetProcessSample04**

示範如何處理非終止錯誤。

**GetProcessSample05**

示範如何顯示指定的處理序清單。

**SelectObject**

示範如何撰寫篩選，進而僅選取特定的物件。

**SelectString**

示範如何搜尋指定模式的檔案。

**StopProcessSample01**

示範如何實作 *PassThru* 參數，以及如何透過呼叫 [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) 及 [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) 方法來要求使用者意見回應。
使用者會在想要強制 Cmdlet 傳回物件時指定 *PassThru* 參數。

**StopProcessSample02**

示範如何停止特定處理序。

**StopProcessSample03**

示範如何宣告參數的別名，以及如何支援萬用字元。

**StopProcessSample04**

示範如何宣告參數集 (Cmdlet 用作輸入的物件)，以及如何指定要使用的預設參數集。

## <a name="remoting-samples"></a>遠端範例

**RemoteRunspace01**

示範如何建立用來建立遠端連線的遠端 Runspace。

**RemoteRunspacePool01**

示範如何建構遠端 Runspace 集區，以及如何使用此集區同時執行多個命令。

**Serialization01**

示範如何查看現有的 .NET 類別，並確定此類別所選公用屬性的資訊會保留於序列化/還原序列化。

**Serialization02**

示範如何查看現有的 .NET 類別，並確定此類別的執行個體資訊會在無法於類別的公用屬性中使用時，保留於序列化/還原序列化。

**Serialization03**

示範如何查看現有的 .NET 類別，並確定此類別和衍生類別的執行個體都會還原序列化 (解除凍結) 成實際 .NET 物件。

## <a name="event-samples"></a>事件範例

**Event01**

示範如何透過衍生自 ObjectEventRegistrationBase 來建立事件註冊的 Cmdlet。

**Event02**

示範如何接收遠端電腦上所產生的 Windows PowerShell 事件的通知。
其會使用透過 [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) 類別公開的 PSEventReceived 事件。

## <a name="hosting-application-samples"></a>主控應用程式範例

**Runspace01**

示範如何使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 類別以同步執行 [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) Cmdlet。
[Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) Cmdlet 會為本機電腦上所執行的每個處理序傳回 [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) 物件。

**Runspace02**

示範如何使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 類別以同步執行 [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) 及 [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) Cmdlet。
[Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) Cmdlet 會為本機電腦上所執行的每個處理序傳回 [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) 物件，而 Sort-Object 會依據物件的 [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) 屬性排序物件。
這些命令的結果會透過使用 [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) 控制項來顯示。

**Runspace03**

示範如何使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 類別以同步執行指令碼，以及如何處理非終止錯誤。
指令碼會接收處理序名稱的清單，然後擷取這些處理序。
指令碼的結果會顯示在主控台視窗中，包括執行指令碼時所產生的任何非終止錯誤在內。

**Runspace04**

示範如何使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 類別來執行命令，以及如何捕捉執行命令時所擲回的終止錯誤。
執行了兩個命令，而最後一個命令傳遞了無效的參數引數。
如此便不會傳回任何物件，且會擲回終止錯誤。

**Runspace05**

示範如何將嵌入式管理單元新增至 [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) 物件，讓嵌入式管理單元的 Cmdlet 可在 Runspace 開啟時使用。
嵌入式管理單元提供 Get-Proc Cmdlet (由 [GetProcessSample01 範例](https://technet.microsoft.com/library/ff602028.aspx) 定義)，其透過使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 物件同步執行。

**Runspace06**

示範如何將模組新增至 [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) 物件，使模組在 Runspace 開啟時載入。
模組提供 Get-Proc Cmdlet (由 [GetProcessSample02 範例](https://technet.microsoft.com/library/ff602027.aspx) 定義)，其透過使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 物件同步執行。

**Runspace07**

示範如何建立 Runspace，並使用該 Runspace 透過 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 物件以同步執行兩個 Cmdlet。

**Runspace08**

示範如何將命令和引數新增至 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 物件的管線，以及如何同步執行命令。

**Runspace09**

示範如何將指令碼新增至 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 物件的管線，以及如何非同步地執行指令碼。
事件為用來處理指令碼的輸出。

**Runspace10**

示範如何建立預設初始工作階段狀態、如何將 Cmdlet 新增至 [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx)、如何建立使用初始工作階段狀態的 Runspace，以及如何使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) 物件執行此命令。

**Runspace11**

示範如何使用 [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) 類別來建立 Proxy 命令，該命令會呼叫現有的 Cmdlet，但會限制可用的參數集。
Proxy 命令接著會加入用來建立受限 Runspace 的初始工作階段狀態。
這表示使用者只能透過 Proxy 命令使用此 Cmdlet 的功能。

**PowerShell01**

示範如何使用 [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) 物件建立受限的 Runspace 。

**PowerShell02**

示範如何使用 Runspace 集區同時執行多個命令。

## <a name="host-samples"></a>主機範例

**Host01**

示範如何實作使用自訂主機的主應用程式。
在這個範例中，建立了使用自訂主機的 Runspace，然後使用 [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) API 執行呼叫 "exit" 的指令碼。
主應用程式會查看指令碼的輸出，並列印結果。

**Host02**

示範如何撰寫使用 Windows PowerShell 執行階段及自訂主機實作的主應用程式。
主應用程式會將主機的文化特性設定為德文、執行 [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) Cmdlet，並顯示您使用 pwrsh.exe 時會看到的結果，然後以德文列印目前的日期和時間。

**Host03**

示範如何建置互動式主控台主應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。

**Host04**

示範如何建置互動式主控台主應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。
這個主應用程式也支援顯示允許使用者指定多個選項的提示。

**Host05**

示範如何建置互動式主控台主應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。
這個主應用程式也支援使用 [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) 和 [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) Cmdlet 呼叫遠端電腦。

**Host06**

示範如何建置互動式主控台主應用程式，從命令列讀取命令、執行命令，然後在主控台顯示結果。
此外，這個範例會使用權杖化工具 API 指定使用者所輸入的文字色彩。

## <a name="provider-samples"></a>提供者範例

**AccessDBProviderSample01**

示範如何宣告直接衍生自 [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) 類別的提供者類別。
包含在此僅為完整性用途。

**AccessDBProviderSample02**

示範如何覆寫 [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) 和 [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) 方法來支援呼叫 New-PSDrive 和 Remove-PSDrive Cmdlet。
此範例中的提供者類別衍生自 [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) 類別。

**AccessDBProviderSample03**

示範如何覆寫 [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) 和 [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) 方法來支援呼叫 Get-Item 和 Set-Item Cmdlet。
此範例中的提供者類別衍生自 [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) 類別。

**AccessDBProviderSample04**

示範如何覆寫容器方法來支援呼叫 Copy-Item、Get-ChildItem、New-Item 和 Remove-Item Cmdlet。
當資料存放區包含容器項目時，就應該實作這些方法。
容器是常見父項目底下的一組子項目。
此範例中的提供者類別衍生自 [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) 類別。

**AccessDBProviderSample05**

示範如何覆寫容器方法來支援呼叫 Move-Item 及 Join-Path Cmdlet。
當使用者需要移動容器內的項目，而且資料存放區包含巢狀容器時，就應該實作這些方法。
此範例中的提供者類別衍生自 [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) 類別。

**AccessDBProviderSample06**

示範如何覆寫內容方法來支援呼叫 Clear-Content、Get-Content 及 Set-Content Cmdlet。
當使用者需要管理資料存放區的項目內容時，就應該實作這些方法。
此範例中的提供者類別衍生自 [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) 類別，且其會實作 [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) 介面。