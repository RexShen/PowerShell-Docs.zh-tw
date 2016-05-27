---
title:  處理軟體安裝
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
---

# 處理軟體安裝
設計成使用 Windows Installer 的應用程式可以透過 WMI 的 **Win32\_Product** 類別存取，但並非所有現今使用的應用程式都使用 Windows Installer。 因為 Windows Installer 對處理可安裝的應用程式提供最廣泛的標準技術，我們主要將著重在那些應用程式。 使用替代安裝常式的應用程式通常不受 Windows Installer 管理。 處理那些應用程式的特定技術將視安裝程式軟體與應用程式開發人員的決定而定。

> [!NOTE]
> 透過將應用程式檔案複製到電腦來安裝的應用程式通常無法使用這裡討論的技術來管理。 您可以使用＜處理檔案與資料夾＞一節中所討論的技術，將這些應用程式當成檔案與資料夾來管理。

### 列出 Windows Installer 應用程式
若要列出在本機或遠端系統上使用 Windows Installer 安裝的應用程式，請使用下列簡單的 WMI 查詢：

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

若要在螢幕上顯示 Win32_Product 物件的所有屬性，請使用格式化 Cmdlet (例如 Format-List Cmdlet) 的 Properties 參數，加上 * (全部) 值。

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *
Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

或者，您可以使用 **Get-WmiObject Filter** 參數來只選取 Microsoft .NET Framework 2.0。 因為此命令中使用的篩選器是 WMI 篩選器，所以它使用 WMI 查詢語言 (WQL) 語法，而不是 Windows PowerShell 語法。 而是：

```
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

請注意，WQL 查詢經常使用在 Windows PowerShell 中有特殊意義的字元，例如空格或等號。 基於此原因，最好一律將 Filter 參數的值用引號括住。 您也可以使用 Windows PowerShell 的逸出字元倒引號 (\`)，但這麼做可能無法改善可讀性。 下列命令相當於先前的命令且傳回相同的結果，但它使用倒引號來逸出特殊字元，而不是將整個篩選字串用引號括住。

```
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

若只要列出您感興趣的屬性，請使用格式化 Cmdlet 的 Property 參數來列出想要的屬性。

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

最後，如果只要尋找已安裝應用程式的名稱，使用簡單的 **Format-Wide** 陳述式可簡化輸出：

```
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

雖然我們現在有數種方式可查看使用 Windows Installer 安裝的應用程式，但我們還沒有考慮其他應用程式。 因為大部分的標準應用程式會向 Windows 登錄其解除安裝程式，所以我們可以透過在 Windows 登錄中尋找這些應用程式，以在本機處理它們。

### 列出所有可解除安裝應用程式
雖然沒有方法可以保證找出系統上所有應用程式，但可以尋找 [新增或移除程式] 對話方塊顯示之清單中的所有程式。 [新增或移除程式] 會在下列登錄機碼中尋找這些應用程式：

**HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.

我們也可以檢查此機碼來尋找應用程式。 為了讓您更輕鬆地檢視 Uninstall 機碼，我們可以將 Windows PowerShell 磁碟機對應至此登錄位置：

```
PS>    

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> **HKLM:** 磁碟機已對應到 **HKEY\_LOCAL\_MACHINE** 的根目錄，因此我們在指向 Uninstall 機碼的路徑中使用該磁碟機。 除了 **HKLM:** 之外，我們可以使用 **HKLM** 或 **HKEY\_LOCAL\_MACHINE** 其中之一指定登錄路徑。 使用現有登錄磁碟機的好處是可以使用 Tab 鍵自動完成來填入機碼名稱，因此我們不需要手動輸入。

我們現在有了名為 "Uninstall" 的磁碟機，它可以用來快速又方便地尋找應用程式安裝。 我們可以計算 Uninstall: Windows PowerShell 磁碟機中的登錄機碼數目，找出安裝的應用程式數目：

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

我們可以使用各種不同的技術來進一步搜尋此應用程式清單，首先是 **Get-ChildItem**。 若要取得應用程式清單並將它們儲存在 **$UninstallableApplications** 變數中，請使用下列命令：

```
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> 為了清楚說明，在這裡我們使用冗長的變數名稱。 在實際使用時，就沒有必要使用長名稱。 雖然您可以使用 Tab 鍵自動完成輸入變數名稱，但您也可以為了加快速度使用 1 至 2 個字元的名稱。 較長的描述性名稱在您開發重複使用的程式碼時最有幫助。

若要顯示 Uninstall 下登錄機碼中登錄項目的值，請使用登錄機碼的 GetValue 方法。 方法的值是登錄項目的名稱。

例如，若要尋找 Uninstall 機碼中應用程式的顯示名稱，請使用下列命令：

```
PS> Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue("DisplayName") }
```

這些值並不保證是唯一的。 在下列範例中，有兩個已安裝項目顯示為 "Windows Media Encoder 9 Series"：

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

### 安裝應用程式
您可以在遠端或本機使用 **Win32\_Product** 類別來安裝 Windows Installer 封裝。

> [!NOTE] 在 Windows Vista、Windows Server 2008 與更新版本的 Windows 中，您必須使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell 才能安裝應用程式。

進行遠端安裝時，請使用通用命名慣例 (UNC) 網路路徑來指定 .msi 套件的路徑，因為 WMI 子系統不了解 Windows PowerShell 路徑。 例如，若要安裝位於遠端電腦 PC01 上網路共用 \\\\AppServ\\dsp 中的 NewPackage.msi 封裝，請在 Windows PowerShell 提示字元輸入下列命令：

```
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq "Win32_Product"}).Install(\\AppSrv\dsp\NewPackage.msi)
```

不使用 Windows Installer 技術的應用程式可能會有應用程式專屬，且適用於自動化部署的方法。 若要判斷是否有自動化部署的方法，請檢查應用程式的文件或洽詢應用程式廠商的支援系統。 在某些情況下，即使應用程式廠商沒有特別將應用程式設計成自動化安裝，但安裝程式軟體製造商可能會有一些自動化技術。

### 移除應用程式
使用 Windows PowerShell 移除 Windows Installer 套件的方法，與安裝套件的方法大致相同。 以下是範例，其中根據封裝的名稱選取要解除安裝的封裝；在某些情況下，使用 **IdentifyingNumber** 來篩選可能會比較容易：

```
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

即使是在本機上要移除其他應用程式，有時候也不太容易。 我們可以透過擷取 **UninstallString** 屬性，來尋找這些應用程式的命令列解除安裝字串。 此方法可用於 Windows Installer 應用程式，以及出現在 Uninstall 機碼下的舊版程式：

```
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue("UninstallString") }
```

您也可以使用顯示名稱來篩選輸出：

```
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -like "Win*"} | ForEach-Object -Process { $_.GetValue("UninstallString") }
```

不過，這些字串在未經修改之前，可能無法直接用於 Windows PowerShell 提示字元。

### 升級 Windows Installer 應用程式
若要升級應用程式，您需要知道應用程式的名稱，以及應用程式升級套件的路徑。 有了該資訊之後，您就可以使用單一的 Windows PowerShell 命令升級應用程式：

```
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```



<!--HONumber=May16_HO2-->


