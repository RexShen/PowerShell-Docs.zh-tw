---
title: 安裝 Windows PowerShell SDK
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: da1b3dbb8a599aee2cdbab9115aedcab0b4c78c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082476"
---
# <a name="installing-the-windows-powershell-sdk"></a>安裝 Windows PowerShell SDK

適用於：Windows PowerShell 2.0, Windows PowerShell 3.0

下列主題說明如何在不同版本的 Windows 上安裝 PowerShell SDK。

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>安裝適用於 Windows 8 及 Windows Server 2012 的 Windows PowerShell 3.0 SDK

Windows 8 及 Windows Server 2012 會自動安裝 Windows PowerShell 3.0。 您也可以下載並安裝 Windows PowerShell 3.0 的參考組件，當做 Windows 8 SDK 的一部分。 這些組件可讓您撰寫 Windows PowerShell 3.0 的 Cmdlet、提供者和主機程式。 當您安裝 Windows SDK for Windows 8 時，Windows PowerShell 組件會自動安裝在參考組件資料夾中：\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0。 如需詳細資訊，請參閱 Windows 8 SDK 下載網站。 開發中心也會提供 Windows PowerShell 程式碼範例。
如需詳細資訊，請參閱開發人員中心網站上的桌面程式碼範例頁面。

此外，包含多個程式碼範例的 Windows PowerShell 3.0 與 Windows PowerShell 2.0 SDK 相容。 如需如何下載 Windows PowerShell 2.0 SDK 的詳細資訊，請參閱以下內容。 (請注意，雖然 2.0 程式碼範例與 Windows 8 和 Windows PowerShell 3.0 相容，但 Windows 8 平台無法安裝 Windows PowerShell 2.0。)

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>安裝適用於 Windows 7 及 Windows Server 2008 R2 的 Windows PowerShell 3.0 SDK

Windows 7 及 Windows Server 2008 R2 會自動安裝 PowerShell 2.0。 您也可以在這些系統上安裝 PowerShell 3.0。 （如需詳細資訊，請參閱安裝 Windows PowerShell。）。 如上所述，您也可以在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows 8 SDK。

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>安裝適用於 Windows 7、Vista、XP、Server 2003 及 Server 2008 的 Windows PowerShell 2.0 SDK

Windows PowerShell 2.0 SDK 提供撰寫 Cmdlet、提供者和主控應用程式所需的參考組件，並提供作為開始撰寫程式碼的起點 C# 範例程式碼。

若要安裝此 SDK，請參閱 Windows PowerShell 2.0 SDK。

### <a name="reference-assemblies"></a>參考組件

參考組件預設會安裝在下列位置： c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0。

> [!NOTE]
>
> 針對 Windows PowerShell 2.0 組件編譯的程式碼無法載入到 Windows PowerShell 1.0 安裝中。 不過，針對 Windows PowerShell 1.0 組件編譯的程式碼可以載入至 Windows PowerShell 2.0 安裝。


### <a name="samples"></a>範例

根據預設，程式碼範例會安裝在下列位置：C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\. 以下各節提供每個範例之用途的簡要說明。

#### <a name="cmdlet-samples"></a>Cmdlet 範例

- GetProcessSample01-示範如何撰寫簡易的 cmdlet 可取得在本機電腦上的所有處理程序。
- GetProcessSample02-示範如何將參數新增至 cmdlet。 此 Cmdlet 會採用一或多個處理序名稱，並傳回相符的處理序。
- GetProcessSample03-示範如何新增可接受來自管線的輸入參數。
- GetProcessSample04-示範如何處理非終止錯誤。
- GetProcessSample05-示範如何顯示一份指定的處理序。
- SelectObject-示範如何寫入篩選器，以選取特定的物件。
- SelectString-示範如何搜尋指定模式的檔案。
- StopProcessSample01-示範如何實作 PassThru 參數，以及如何對 ShouldProcess 及 ShouldContinue 方法的呼叫來要求使用者意見反應。 他們想要強制 cmdlet 傳回物件時，使用者可以指定 PassThru 參數
- StopProcessSample02-示範如何停止特定處理序。
- StopProcessSample03-示範如何宣告參數的別名，以及如何支援萬用字元。
- StopProcessSample04-示範如何宣告參數集，此 cmdlet 會作為輸入，以及如何指定預設參數設定為使用的物件。

#### <a name="remoting-samples"></a>遠端範例

- RemoteRunspace01-示範如何建立用來建立遠端連線的遠端 runspace。
- RemoteRunspacePool01-示範如何建構遠端 runspace 集區以及如何使用此集區同時執行多個命令。
- Serialization01-示範如何查看現有的.NET 類別，並確定所選的公用屬性，這個類別的資訊會保留於序列化/還原序列化。
- Serialization02-示範如何查看現有的.NET 類別，並確定此類別的執行個體的資訊會保留於序列化/還原序列化時的資訊不適用於類別的公用屬性。
- Serialization03-示範如何查看現有的.NET 類別，並確定此類別和衍生類別的執行個體都會還原序列化 （解除凍結） 成實際.NET 物件。

#### <a name="event-samples"></a>事件範例

- Event01-示範如何透過衍生自 ObjectEventRegistrationBase 建立事件註冊 cmdlet。
- Event02-示範如何為了示範如何接收遠端電腦所產生的 Windows PowerShell 事件的通知。 它會使用透過 Runspace 類別公開的 PSEventReceived 事件。

#### <a name="hosting-application-samples"></a>主控應用程式範例

- Runspace01-示範如何使用 PowerShell 類別來執行`Get-Process`cmdlet 以同步方式。
`Get-Process` Cmdlet 會傳回每個處理序在本機電腦上執行的處理程序物件。
- Runspace02-示範如何使用 PowerShell 類別來執行`Get-Process`和`Sort-Object`cmdlet 以同步方式。 `Get-Process` Cmdlet 會傳回每個處理序在本機電腦上執行的處理程序物件和`Sort-Object`排序根據 Id 屬性的物件。 這些命令的結果會顯示使用 DataGridView 控制項中。
- Runspace03-示範如何使用 PowerShell 類別來執行指令碼，以同步方式，以及如何處理非終止錯誤。 指令碼會接收處理序名稱的清單，然後擷取這些處理序。 指令碼的結果會顯示在主控台視窗中，包括執行指令碼時所產生的任何非終止錯誤在內。
- Runspace04-示範如何使用 PowerShell 類別來執行命令，以及如何攔截終止執行命令時，所擲回錯誤。 執行了兩個命令，而最後一個命令傳遞了無效的參數引數。 如此便不會傳回任何物件，且會擲回終止錯誤。
- Runspace05-示範如何使嵌入式管理單元的 cmdlet 可在 runspace 開啟時，將嵌入式管理單元加入 InitialSessionState 物件。 嵌入式管理單元提供 Get-proc cmdlet （GetProcessSample01 範例所定義） 所使用的 PowerShell 物件以同步方式執行。
- Runspace06-示範如何將模組加入 InitialSessionState 物件，以便在 runspace 開啟時載入的模組。 模組提供 Get-proc cmdlet （GetProcessSample02 範例所定義） 所使用的 PowerShell 物件以同步方式執行。
- Runspace07-示範如何建立 runspace，並使用該 runspace，若要使用的 PowerShell 物件，以同步方式執行兩個 cmdlet。
- Runspace08-示範如何將命令和引數新增至 PowerShell 物件的管線以及如何以同步方式執行命令。
- Runspace09-示範如何將指令碼新增至 PowerShell 物件的管線以及如何以非同步方式執行指令碼。 事件為用來處理指令碼的輸出。
- Runspace10-示範如何建立預設初始工作階段狀態、 如何將 cmdlet 新增至 InitialSessionState、 如何建立使用初始工作階段狀態，runspace，以及如何執行此命令使用的 PowerShell 物件。
- Runspace11-示範如何使用 ProxyCommand 類別來建立 proxy 命令呼叫現有的 cmdlet，但會限制可用的參數集。 Proxy 命令接著會加入用來建立受限 Runspace 的初始工作階段狀態。 這表示使用者只能透過 Proxy 命令使用此 Cmdlet 的功能。
- PowerShell01-示範如何建立受限的 runspace 使用 InitialSessionState 物件。
- PowerShell02-示範如何使用 runspace 集區同時執行多個命令。

#### <a name="host-samples"></a>主機範例

- Host01-示範如何實作使用自訂主機的主機應用程式。 在這個範例中建立 runspace 中使用自訂主應用程式，和 PowerShell API 則用來執行的指令碼，呼叫"exit"。 主應用程式會查看指令碼的輸出，並列印結果。
- Host02-示範如何撰寫使用 Windows PowerShell 執行階段，以及自訂主機實作的主應用程式。 主應用程式設定主機的文化特性為德文、 執行`Get-Process`cmdlet，並顯示結果設定為您會看到它們以德文使用 pwrsh.exe，然後列印目前的日期和時間。
- Host03-示範如何建置互動式主控台主機應用程式，從命令列讀取命令、 執行命令，然後在主控台中顯示結果。
- Host04-示範如何建置互動式主控台主機應用程式，從命令列讀取命令、 執行命令，然後在主控台中顯示結果。 這個主應用程式也支援顯示允許使用者指定多個選項的提示。
- Host05-示範如何建置互動式主控台主機應用程式，從命令列讀取命令、 執行命令，然後在主控台中顯示結果。 這個主應用程式也支援呼叫遠端電腦使用`Enter-PsSession`和`Exit-PsSession`cmdlet。
- Host06-示範如何建置互動式主控台主機應用程式，從命令列讀取命令、 執行命令，然後在主控台中顯示結果。 此外，這個範例會使用權杖化工具 API 指定使用者所輸入的文字色彩。

#### <a name="provider-samples"></a>提供者範例

- AccessDBProviderSample01-示範如何宣告直接衍生自 CmdletProvider 類別的提供者類別。 包含在此僅為完整性用途。

- AccessDBProviderSample02-示範如何覆寫的 NewDrive 和 RemoveDrive 方法來支援呼叫`New-PSDrive`和`Remove-PSDrive`cmdlet。 在此範例中的提供者類別衍生自 DriveCmdletProvider 類別。

- AccessDBProviderSample03-示範如何覆寫的 GetItem 和 SetItem 方法來支援呼叫`Get-Item`和`Set-Item`cmdlet。 在此範例中的提供者類別衍生自 ItemCmdletProvider 類別。

- AccessDBProviderSample04-示範如何覆寫容器方法，以支援呼叫`Copy-Item`， `Get-ChildItem`， `New-Item`，和`Remove-Item`cmdlet。 當資料存放區包含容器項目時，就應該實作這些方法。 容器是常見父項目底下的一組子項目。 在此範例中的提供者類別衍生自 ItemCmdletProvider 類別。

- AccessDBProviderSample05-示範如何覆寫容器方法，以支援呼叫`Move-Item`和`Join-Path`cmdlet。 當使用者需要移動容器內的項目，而且資料存放區包含巢狀容器時，就應該實作這些方法。 在此範例中的提供者類別衍生自 NavigationCmdletProvider 類別。

- AccessDBProviderSample06-示範如何覆寫內容方法，以支援呼叫`Clear-Content`， `Get-Content`，和`Set-Content`cmdlet。 當使用者需要管理資料存放區的項目內容時，就應該實作這些方法。 在此範例中的提供者類別衍生自 NavigationCmdletProvider 類別，並實作 IContentCmdletProvider 介面。
