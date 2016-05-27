---
title:  建立 .NET 和 COM 物件 New Object 
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  2057b113-efeb-465e-8b44-da2f20dbf603
---

# 建立 .NET 和 COM 物件 (New-Object)
您可以透過具有 .NET Framework 和 COM 介面的軟體元件，來執行許多系統管理工作。 Windows PowerShell 可讓您使用這些元件，因此您不再僅限於使用 Cmdlet 執行工作。 Windows PowerShell 的初始版本中有許多 Cmdlet 無法對遠端電腦執行。 我們將示範如何從 Windows PowerShell 直接使用 .NET Framework **System.Diagnostics.EventLog** 類別，以克服管理事件記錄檔時的這項限制。

### 使用 New-Object 存取事件記錄檔
.NET Framework 類別庫包含名為 **System.Diagnostics.EventLog** 的類別，可用來管理事件記錄檔。 您可以使用 **New-Object** Cmdlet 搭配 **TypeName** 參數，建立 .NET Framework 類別的新執行個體。 例如，下列命令會建立事件記錄檔參考：

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

雖然此命令已建立 EventLog 類別的執行個體，但是該執行個體不會包含任何資料。 這是因為我們並未指定特定事件記錄檔。 如何取得實際事件記錄檔？

#### 搭配使用建構函式和 New-Object
若要參考特定事件記錄檔，您需要指定記錄檔的名稱。 **New-Object** 具有 **ArgumentList** 參數。 物件的特殊啟動方法會使用您以值傳遞給這個參數的引數。 該方法稱為*建構函式*，因為它可用來建構物件。 例如，若要取得應用程式記錄檔參考，您會將字串 'Application' 指定為引數︰

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> 由於大部分的 .NET Framework 核心類別都包含在 System 命名空間中，因此如果 Windows PowerShell 找不到您指定之 typename 的相符項目，就會自動嘗試尋找您在 System 命名空間中指定的類別。 這表示您可以指定 Diagnostics.EventLog，而不是 System.Diagnostics.EventLog。

#### 將物件儲存在變數中
您可能想要儲存物件參考，以便在目前的殼層中使用。 雖然 Windows PowerShell 可讓您執行許多管線工作，因而降低變數的需要，但是有時將物件參考儲存在變數中，可以更方便管理這些物件。

Windows PowerShell 可讓您建立基本上為具名物件的變數。 任何有效的 Windows PowerShell 命令輸出都能儲存在變數中。 變數名稱一律會以 $ 開頭。 如果您想要將應用程式記錄檔參考儲存在名為 $AppLog 的變數中，請輸入變數的名稱，後面接著等號，然後輸入用來建立應用程式記錄檔物件的命令︰

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

如果您接著輸入 $AppLog，您可以看到它包含了應用程式記錄檔︰

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

#### 使用 New-Object 存取遠端事件記錄檔
上一節所使用的命令是以本機電腦為目標；**Get-EventLog** Cmdlet 可以執行該作業。 若要存取遠端電腦上的應用程式記錄檔，您必須同時提供記錄檔名稱和電腦名稱 (或 IP 位址) 作為引數。

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

將事件記錄檔參考儲存在 $RemoteAppLog 變數之後，可對其執行哪些工作？

#### 使用物件方法清除事件記錄檔
物件通常具有可呼叫以執行工作的方法。 您可以使用 **Get-Member**，顯示與物件相關聯的方法。 下列命令和選取的輸出顯示 EventLog 類別的一些方法︰

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

**Clear()** 方法可用來清除事件記錄檔。 呼叫方法時，您必須一律在方法名稱後面加上括弧，即使方法不需要引數亦然。 這可讓 Windows PowerShell 在此方法與具有相同名稱的潛在屬性之間進行區別。 輸入下列命令呼叫 **Clear** 方法︰

```
PS> $RemoteAppLog.Clear()
```

輸入下列命令顯示記錄檔。 您會看到事件記錄檔已清除，現在有 0 個而不是 262 個項目：

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

### 使用 New-Object 建立 COM 物件
您可以使用 **New-Object** 來處理元件物件模型 (COM) 元件。 元件範圍從 Windows Script Host (WSH) 隨附的各種程式庫，到安裝在大多數系統上的 ActiveX 應用程式 (例如 Internet Explorer)。

**New-Object** 使用 .NET Framework 執行階段可呼叫包裝函式來建立 COM 物件，因此與呼叫 COM 物件時具有相同的 .NET Framework 限制。 若要建立 COM 物件，您需要指定 **ComObject** 參數，並提供所要使用之 COM 類別的程式設計識別碼 (或 *ProgID*)。 COM 使用限制及判斷系統上可用 ProgID 的完整探討不在本使用者指南的討論範圍內，但 WSH 等環境中的大部分已知物件都可以在 Windows PowerShell 中使用。

您可以透過指定下列 ProgID 來建立 WSH 物件︰**WScript.Shell**、**WScript.Network**、**Scripting.Dictionary** 和 **Scripting.FileSystemObject**。 下列命令會建立這些物件：

```
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

雖然這些類別的大部分功能都可以利用 Windows PowerShell 的其他方式提供，但針對建立捷徑等一些工作，使用 WSH 類別還是比較容易進行。

### 使用 WScript.Shell 建立桌面捷徑
您可以透過 COM 物件快速執行的一項工作就是建立捷徑。 假設您想要在桌面上建立捷徑，以連結到 Windows PowerShell 的主資料夾。 您必須先建立 **WScript.Shell** 的參考，我們將儲存在名為 **$WshShell** 的變數中：

```
$WshShell = New-Object -ComObject WScript.Shell
```

Get-Member 可用於 COM 物件，因此您可以輸入下列命令瀏覽物件成員︰

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

**Get-Member** 具有選擇性 **InputObject** 參數，您可以改用此參數提供輸入而不是傳送到 **Get-Member**。 如果您改用命令 **Get-Member -InputObject $WshShell**，會得到如上所示的相同輸出。 如果您使用 **InputObject**，它會將其引數視為單一項目。 這表示如果您在變數中有數個物件，**Get-Member** 會將其視為物件的陣列。 例如：

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

**WScript.Shell CreateShortcut** 方法接受單一引數，也就是要建立的捷徑檔案路徑。 我們可以輸入桌面的完整路徑，但還有更簡單的方法。 桌面通常會以目前使用者的主資料夾內名為 [桌面] 的資料夾來表示。 Windows PowerShell 有一個包含此資料夾路徑的變數 **$Home**。 我們可以使用此變數指定主資料夾的路徑，然後加入 [桌面] 資料夾的名稱及要建立的捷徑名稱，請輸入︰

```
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

當您使用類似雙引號內的變數名稱時，Windows PowerShell 會嘗試取代為相符的值。 如果您使用單引號，Windows PowerShell 不會嘗試取代變數值。 例如，嘗試輸入下列命令：

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

我們現在有一個名為 **$lnk** 的變數，其中包含新的捷徑參考。 如果您想要查看其成員，您可以將其傳送到 **Get-Member**。 以下的輸出顯示完成建立捷徑所需使用的成員︰

<pre>PS> $lnk | Get-Member TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b} Name             MemberType   Definition ----             ----------   ---------- ...Save             Method       void Save () ...TargetPath       Property     string TargetPath () {get} {set} ...</pre>

我們需要指定 Windows PowerShell 的應用程式資料夾 **TargetPath**，然後再呼叫 **Save** 方法來儲存捷徑 **$lnk**。 Windows PowerShell 應用程式資料夾路徑儲存在變數 **$PSHome** 中，因此我們可以輸入下列命令來執行此作業︰

<pre>$lnk.TargetPath = $PSHome $lnk.Save()</pre>

### 從 Windows PowerShell 使用 Internet Explorer
許多應用程式 (包括 Microsoft Office 系列應用程式和 Internet Explorer) 都可以透過 COM 自動化。 Internet Explorer 說明一些與使用 COM 應用程式相關的典型技術和問題。

您可以指定 Internet Explorer ProgID **InternetExplorer.Application** 來建立 Internet Explorer 執行個體：

```
$ie = New-Object -ComObject InternetExplorer.Application
```

此命令會啟動但不會顯示 Internet Explorer。 如果您輸入 Get-Process，您可以看到名為 iexplore 的處理序正在執行。 事實上，如果您結束 Windows PowerShell，該處理序會繼續執行。 您必須重新啟動電腦或使用工作管理員等工具，才能結束 iexplore 處理序。

> [!NOTE]
> 以個別處理序啟動的 COM 物件通常稱為*ActiveX 可執行檔*，啟動時不一定會顯示使用者介面視窗。 像是 Internet Explorer，如果建立但未顯示視窗，通常會將焦點移至 Windows 桌面，而您必須顯示視窗才能與其互動。

您可以輸入 **$ie | Get-Member**，以檢視 Internet Explorer 的內容和方法。 若要看到 Internet Explorer 視窗，請輸入下列命令將 Visible 屬性設定為 $true︰

```
$ie.Visible = $true
```

您接著可以使用 Navigate 方法巡覽至特定網址︰

```
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

透過 Internet Explorer 物件模型的其他成員，您可以從網頁擷取文字內容。 下列命令會顯示目前網頁內文中的 HTML 文字 ︰

```
$ie.Document.Body.InnerText
```

若要從 PowerShell 關閉 Internet Explorer，請呼叫其 Quit() 方法︰

```
$ie.Quit()
```

這會強制關閉。 $Ie 變數雖然仍會顯示為 COM 物件，但已不再包含有效的參考。 如果您嘗試使用，您會收到自動化錯誤︰

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

您可以使用 $ie = $null 等命令移除其餘參考，或輸入下列命令完全移除變數︰

```
Remove-Variable ie
```

> [!NOTE]
> 當您移除 ActiveX 可執行檔參考時，ActiveX 可執行檔會結束或繼續執行，並沒有通用標準。 根據應用程式是否顯示、其中是否正在執行編輯的文件，甚至是根據 Windows PowerShell 是否仍在執行等情況，應用程式可能結束，也可能不會結束。 因此，您應該針對要在 Windows PowerShell 中使用的每個 ActiveX 可執行檔，測試其終止行為。

### 取得 .NET Framework 包裝之 COM 物件的相關警告
在某些情況下，COM 物件可能會有相關聯的 .NET Framework *執行階段可呼叫包裝函式* (或 RCW)，**New-Object** 將會使用此包裝函式。 因為 RCW 的行為可能與一般 COM 物件的行為不同，所以 **New-Object** 提供了 **Strict** 參數，以警告您 RCW 的存取。 如果您指定 **Strict** 參數，然後建立使用 RCW 的 COM 物件，您會收到警告訊息︰

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

雖然物件仍會建立，但您會收到警告，指出該物件不是標準 COM 物件。



<!--HONumber=May16_HO2-->


