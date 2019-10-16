---
title: 安裝 Windows PowerShell SDK
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: da1b3dbb8a599aee2cdbab9115aedcab0b4c78c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367267"
---
# <a name="installing-the-windows-powershell-sdk"></a>安裝 Windows PowerShell SDK

適用于： Windows PowerShell 2.0、Windows PowerShell 3。0

下列主題說明如何在不同版本的 Windows 上安裝 PowerShell SDK。

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>安裝適用於 Windows 8 及 Windows Server 2012 的 Windows PowerShell 3.0 SDK

Windows 8 及 Windows Server 2012 會自動安裝 Windows PowerShell 3.0。 您也可以下載並安裝 Windows PowerShell 3.0 的參考組件，當做 Windows 8 SDK 的一部分。 這些組件可讓您撰寫 Windows PowerShell 3.0 的 Cmdlet、提供者和主機程式。 當您安裝 Windows SDK for Windows 8 時，Windows PowerShell 組件會自動安裝在參考組件資料夾中：\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0。 如需詳細資訊，請參閱 Windows 8 SDK 下載網站。 開發中心也會提供 Windows PowerShell 程式碼範例。
如需詳細資訊，請參閱開發人員中心網站上的桌面程式碼範例頁面。

此外，包含多個程式碼範例的 Windows PowerShell 3.0 與 Windows PowerShell 2.0 SDK 相容。 如需如何下載 Windows PowerShell 2.0 SDK 的詳細資訊，請參閱以下內容。 (請注意，雖然 2.0 程式碼範例與 Windows 8 和 Windows PowerShell 3.0 相容，但 Windows 8 平台無法安裝 Windows PowerShell 2.0。)

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>安裝適用於 Windows 7 及 Windows Server 2008 R2 的 Windows PowerShell 3.0 SDK

Windows 7 及 Windows Server 2008 R2 會自動安裝 PowerShell 2.0。 您也可以在這些系統上安裝 PowerShell 3.0。 （如需詳細資訊，請參閱安裝 Windows PowerShell）。 如上所述，您也可以在 Windows 7 和 Windows Server 2008 R2 上安裝 Windows 8 SDK。

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>安裝適用於 Windows 7、Vista、XP、Server 2003 及 Server 2008 的 Windows PowerShell 2.0 SDK

Windows PowerShell 2.0 SDK 提供撰寫 Cmdlet、提供者和主控應用程式所需的參考組件，並提供作為開始撰寫程式碼的起點 C# 範例程式碼。

若要安裝此 SDK，請參閱 Windows PowerShell 2.0 SDK。

### <a name="reference-assemblies"></a>參考組件

參考元件預設會安裝在下列位置： c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0。

> [!NOTE]
>
> 針對 Windows PowerShell 2.0 組件編譯的程式碼無法載入到 Windows PowerShell 1.0 安裝中。 不過，針對 Windows PowerShell 1.0 組件編譯的程式碼可以載入至 Windows PowerShell 2.0 安裝。


### <a name="samples"></a>範例

程式碼範例預設會安裝在下列位置： C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\。 以下各節提供每個範例之用途的簡要說明。

#### <a name="cmdlet-samples"></a>Cmdlet 範例

- GetProcessSample01-說明如何撰寫可取得本機電腦上所有處理常式的簡單 Cmdlet。
- GetProcessSample02-顯示如何將參數新增至 Cmdlet。 此 Cmdlet 會採用一或多個處理序名稱，並傳回相符的處理序。
- GetProcessSample03-說明如何新增可接受管線輸入的參數。
- GetProcessSample04-顯示如何處理非終止錯誤。
- GetProcessSample05-顯示如何顯示指定的進程清單。
- SelectObject-示範如何撰寫篩選來僅選取特定物件。
- SelectString-顯示如何搜尋指定模式的檔案。
- StopProcessSample01-顯示如何執行 PassThru 參數，以及如何藉由呼叫 ShouldProcess 和 ShouldContinue 方法來要求使用者意見反應。 當使用者想要強制 Cmdlet 傳回物件時，請指定 PassThru 參數，
- StopProcessSample02-顯示如何停止特定的進程。
- StopProcessSample03-顯示如何宣告參數的別名，以及如何支援萬用字元。
- StopProcessSample04-示範如何宣告參數集、Cmdlet 做為輸入的物件，以及如何指定要使用的預設參數集。

#### <a name="remoting-samples"></a>遠端範例

- RemoteRunspace01-說明如何建立用來建立遠端連線的遠端執行時間。
- RemoteRunspacePool01-示範如何建立遠端執行時間集區，以及如何使用此集區同時執行多個命令。
- Serialization01-示範如何查看現有的 .NET 類別，並確定已選取此類別之公用屬性的資訊會跨序列化/還原序列化進行保留。
- Serialization02-示範如何查看現有的 .NET 類別，並確定當此類別的公用屬性中未提供資訊時，會跨序列化/還原序列化，將此類別的實例中的資訊保留下來。
- Serialization03-顯示如何查看現有的 .NET 類別，並確定此類別和衍生類別的實例已還原序列化（解除凍結）為即時 .NET 物件。

#### <a name="event-samples"></a>事件範例

- Event01-示範如何藉由衍生自自 objecteventregistrationbase Cmdlet 來建立事件註冊的 Cmdlet。
- Event02-說明如何顯示在遠端電腦上產生的 Windows PowerShell 事件通知。 它會使用透過運行空間類別所公開的 PSEventReceived 事件。

#### <a name="hosting-application-samples"></a>主控應用程式範例

- Runspace01-說明如何使用 PowerShell 類別以同步方式執行 `Get-Process` Cmdlet。
@No__t-0 Cmdlet 會針對在本機電腦上執行的每個進程傳回處理常式物件。
- Runspace02-示範如何使用 PowerShell 類別，以同步方式執行 `Get-Process` 和 @no__t 1 Cmdlet。 @No__t-0 Cmdlet 會針對在本機電腦上執行的每個進程傳回處理常式物件，而 `Sort-Object` 則會根據物件的 Id 屬性來排序這些物件。 這些命令的結果會使用 DataGridView 控制項來顯示。
- Runspace03-顯示如何使用 PowerShell 類別以同步方式執行腳本，以及如何處理非終止錯誤。 指令碼會接收處理序名稱的清單，然後擷取這些處理序。 指令碼的結果會顯示在主控台視窗中，包括執行指令碼時所產生的任何非終止錯誤在內。
- Runspace04-示範如何使用 PowerShell 類別來執行命令，以及如何攔截執行命令時所擲回的終止錯誤。 執行了兩個命令，而最後一個命令傳遞了無效的參數引數。 如此便不會傳回任何物件，且會擲回終止錯誤。
- Runspace05-說明如何將嵌入式管理單元新增至 InitialSessionState 物件，讓嵌入式管理單元的 Cmdlet 可在開啟執行時間時使用。 此嵌入式管理單元提供使用 PowerShell 物件，以同步方式執行的 GetProcessSample01 範例所定義的處理器指令程式。
- Runspace06-顯示如何將模組新增至 InitialSessionState 物件，以便在開啟執行時間時載入模組。 此模組提供使用 PowerShell 物件以同步方式執行的 GetProcessSample02 範例所定義的處理器指令程式。
- Runspace07-示範如何建立執行時間，然後使用該執行時間，透過 PowerShell 物件同步執行兩個 Cmdlet。
- Runspace08-說明如何將命令和引數新增至 PowerShell 物件的管線，以及如何同步執行命令。
- Runspace09-說明如何將腳本新增至 PowerShell 物件的管線，以及如何以非同步方式執行腳本。 事件為用來處理指令碼的輸出。
- Runspace10-說明如何建立預設初始會話狀態、如何將 Cmdlet 新增至 InitialSessionState、如何建立使用初始會話狀態的執行時間，以及如何使用 PowerShell 物件來執行命令。
- Runspace11-示範如何使用 ProxyCommand 類別來建立呼叫現有 Cmdlet 的 proxy 命令，但會限制可用的參數集合。 Proxy 命令接著會加入用來建立受限 Runspace 的初始工作階段狀態。 這表示使用者只能透過 Proxy 命令使用此 Cmdlet 的功能。
- PowerShell01-說明如何使用 InitialSessionState 物件建立受限的執行時間。
- PowerShell02-顯示如何使用執行時間集區同時執行多個命令。

#### <a name="host-samples"></a>主機範例

- Host01-顯示如何執行使用自訂主機的主應用程式。 在此範例中，會建立使用自訂主機的運行時，然後使用 PowerShell API 來執行呼叫 "exit" 的腳本。 主應用程式會查看指令碼的輸出，並列印結果。
- Host02-示範如何撰寫使用 Windows PowerShell 執行時間以及自訂主機執行的主應用程式。 主應用程式會將主機文化特性設定為德文、執行 `Get-Process` Cmdlet，並顯示結果，如同您使用 pwrsh 所看到的結果，然後以德文印出目前的資料和時間。
- Host03-說明如何建立互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後將結果顯示在主控台中。
- Host04-說明如何建立互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後將結果顯示在主控台中。 這個主應用程式也支援顯示允許使用者指定多個選項的提示。
- Host05-說明如何建立互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後將結果顯示在主控台中。 此主機應用程式也支援使用 `Enter-PsSession` 和 @no__t 1 Cmdlet 來呼叫遠端電腦。
- Host06-說明如何建立互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後將結果顯示在主控台中。 此外，這個範例會使用權杖化工具 API 指定使用者所輸入的文字色彩。

#### <a name="provider-samples"></a>提供者範例

- AccessDBProviderSample01-顯示如何宣告直接衍生自 CmdletProvider 類別的提供者類別。 包含在此僅為完整性用途。

- AccessDBProviderSample02-說明如何覆寫 NewDrive 和 RemoveDrive 方法，以支援對 `New-PSDrive` 和 @no__t 1 Cmdlet 的呼叫。 這個範例中的提供者類別衍生自 DriveCmdletProvider 類別。

- AccessDBProviderSample03-說明如何覆寫 GetItem 和 SetItem 方法，以支援對 `Get-Item` 和 @no__t 1 Cmdlet 的呼叫。 這個範例中的提供者類別衍生自 ItemCmdletProvider 類別。

- AccessDBProviderSample04-示範如何覆寫容器方法來支援對 `Copy-Item`、`Get-ChildItem`、`New-Item` 和 @no__t 3 Cmdlet 的呼叫。 當資料存放區包含容器項目時，就應該實作這些方法。 容器是常見父項目底下的一組子項目。 這個範例中的提供者類別衍生自 ItemCmdletProvider 類別。

- AccessDBProviderSample05-示範如何覆寫容器方法來支援對 `Move-Item` 和 @no__t 1 Cmdlet 的呼叫。 當使用者需要移動容器內的項目，而且資料存放區包含巢狀容器時，就應該實作這些方法。 這個範例中的提供者類別衍生自 NavigationCmdletProvider 類別。

- AccessDBProviderSample06-示範如何覆寫內容方法，以支援對 `Clear-Content`、`Get-Content` 和 @no__t 2 Cmdlet 的呼叫。 當使用者需要管理資料存放區的項目內容時，就應該實作這些方法。 這個範例中的提供者類別衍生自 NavigationCmdletProvider 類別，並會執行 IContentCmdletProvider 介面。
