---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 處理軟體安裝
ms.openlocfilehash: f3023d8819d6cdcc9f55befcfedb21e6ff9d282c
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996115"
---
# <a name="working-with-software-installations"></a>處理軟體安裝

設計成使用 Windows Installer 的應用程式可以透過 WMI 的 **Win32_Product** 類別存取，但並非所有現今使用的應用程式都使用 Windows Installer。
使用替代安裝常式的應用程式通常不受 Windows Installer 管理。
處理那些應用程式的特定技術視安裝程式軟體與應用程式開發人員的決定而定。 例如，透過將應用程式檔案複製到電腦上資料夾來安裝的應用程式，通常無法使用這裡討論的技術來管理。 您可以使用[處理檔案與資料夾](Working-with-Files-and-Folders.md)一節中所討論的技術，將這些應用程式當成檔案與資料夾來管理。

> [!CAUTION]
> **Win32_Product** 類別未針對查詢最佳化。 使用萬用字元篩選條件的查詢，會造成 WMI 使用 MSI 提供者來列舉所有已安裝產品，然後依序剖析完整清單來處理篩選條件。 這也會起始已安裝套件的一致性檢查，驗證並修復安裝。 驗證是緩慢的程序，而且可能會導致事件記錄檔中有錯誤。 如需詳細資訊，請參閱[知識庫文章 974524](https://support.microsoft.com/help/974524) \(英文\)。

## <a name="listing-windows-installer-applications"></a>列出 Windows Installer 應用程式

若要列出在本機或遠端系統上使用 Windows Installer 安裝的應用程式，請使用下列簡單的 WMI 查詢：

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)"
```

```Output
Name             Caption                   Vendor                    Version       IdentifyingNumber
----             -------                   ------                    -------       -----------------
Microsoft .NET … Microsoft .NET Core Runt… Microsoft Corporation     16.84.26919   {BEB59D04-C6DD-4926-AFE…
```

若要在螢幕上顯示 **Win32_Product** 物件的所有屬性，請使用格式設定 Cmdlet (例如 `Format-List` Cmdlet) 的 **Properties** 參數，加上 `*` (全部) 值。

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.5 (x64)
Version               : 16.84.26919
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.5 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.5 (x64)
IdentifyingNumber     : {BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20181105
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}v16.84.26919\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\4f97a771.msi
PackageCache          : C:\WINDOWS\Installer\4f97a771.msi
PackageCode           : {9A271A10-039D-49EA-8D24-043D91B9F915}
PackageName           : dotnet-runtime-2.1.5-win-x64.msi
ProductID             :
RegCompany            :
RegOwner              :
Transforms            :
URLInfoAbout          :
URLUpdateInfo         :
WordCount             : 0
PSComputerName        :
CimClass              : root/cimv2:Win32_Product
CimInstanceProperties : {Caption, Description, IdentifyingNumber, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

或者，您可以使用 `Get-CimInstance`**Filter** 參數，以只選取 Microsoft .NET 2.0 執行階段。 **Filter** 參數的值使用 WMI 查詢語言 (WQL) 語法，而不是 Windows PowerShell 語法。 例如：

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property *
```

若只要列出您感興趣的屬性，請使用格式設定 Cmdlet 的 **Property** 參數來列出想要的屬性。

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.5 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\4f97a771.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a>列出所有可解除安裝應用程式

因為大部分的標準應用程式會向 Windows 登錄解除安裝程式，所以我們可以透過在 Windows 登錄中尋找這些應用程式，以在本機處理它們。 沒有方式保證能找出系統上的每個應用程式。 不過，在下列登錄機碼中找出在 [新增或移除程式]  中顯示清單的所有程式是可能的：

第 1 課：建立 Windows Azure 儲存體物件`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`。

我們可以檢查此機碼來尋找應用程式。 為了讓您更輕鬆地檢視 Uninstall 機碼，我們可以將 PowerShell 磁碟機對應至此登錄位置：

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

我們現在有了名為 "Uninstall:" 的磁碟機，它可以用來快速又方便地尋找應用程式安裝。 我們可以透過計算 Uninstall:PowerShell 磁碟機：

```powershell
(Get-ChildItem -Path Uninstall:).Count
```

```Output
459
```

我們可以使用各種技術來進一步搜尋此應用程式清單，首先是 `Get-ChildItem`。 若要取得應用程式清單並將它們儲存在 `$UninstallableApplications` 變數中，請使用下列命令：

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

若要顯示 Uninstall 下登錄機碼中登錄項目的值，請使用登錄機碼的 GetValue 方法。 方法的值是登錄項目的名稱。

例如，若要尋找 Uninstall 機碼中應用程式的顯示名稱，請使用下列命令：

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

這些值並不保證是唯一的。 在下列範例中，有兩個已安裝項目顯示為 "Windows Media Encoder 9 Series"：

```powershell
$UninstallableApplications | Where-Object -FilterScript {
  $_.GetValue("DisplayName") -eq "Microsoft Silverlight"
}
```

```Output
    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name                           Property
----                           --------
{89F4137D-6C26-4A84-BDB8-2E5A4 AuthorizedCDFPrefix :
BB71E00}                       Comments            :
                               Contact             :
                               DisplayVersion      : 5.1.50918.0
                               HelpLink            : https://go.microsoft.com/fwlink/?LinkID=91955
                               HelpTelephone       :
                               InstallDate         : 20190115
                               InstallLocation     : C:\Program Files\Microsoft Silverlight\
                               InstallSource       : c:\ef64c54526db9c34cd477c103e68a254\
                               ModifyPath          : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               NoModify            : 1
                               NoRepair            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 236432
                               UninstallString     : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 5
                               VersionMinor        : 1
                               WindowsInstaller    : 1
                               Version             : 84002534
                               Language            : 1033
                               DisplayName         : Microsoft Silverlight
                               sEstimatedSize2     : 79214
```

## <a name="installing-applications"></a>安裝應用程式

您可以在遠端或本機使用 **Win32_Product** 類別來安裝 Windows Installer 封裝。

> [!NOTE]
> 若要安裝應用程式，您必須使用 [以系統管理員身分執行] 選項來啟動 PowerShell。

進行遠端安裝時，請使用通用命名慣例 (UNC) 網路路徑來指定 .msi 套件的路徑，因為 WMI 子系統不了解 PowerShell 路徑。 例如，若要在遠端電腦 PC01 上安裝位於網路共用 `\\AppServ\dsp` 中的 NewPackage.msi 套件，請在 PowerShell 提示字元輸入下列命令：

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

不使用 Windows Installer 技術的應用程式可能會有適用於自動化部署的應用程式專屬方法。 請檢查應用程式的文件或洽詢應用程式廠商的支援系統。

## <a name="removing-applications"></a>移除應用程式

使用 PowerShell 移除 Windows Installer 套件的方法，與安裝套件的方法大致相同。 以下是範例，其中根據封裝的名稱選取要解除安裝的封裝；在某些情況下，使用 **IdentifyingNumber** 來篩選可能會比較容易：

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

即使是在本機上要移除其他應用程式，有時候也不太容易。 我們可以透過擷取 **UninstallString** 屬性，來尋找這些應用程式的命令列解除安裝字串。
此方法可用於 Windows Installer 應用程式，以及出現在 Uninstall 機碼下的舊版程式：

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

您也可以使用顯示名稱來篩選輸出：

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

不過，這些字串在未經修改之前，可能無法直接用於 PowerShell 提示字元。

## <a name="upgrading-windows-installer-applications"></a>升級 Windows Installer 應用程式

若要升級應用程式，您需要知道應用程式的名稱，以及應用程式升級套件的路徑。 有了該資訊之後，您就可以使用單一的 PowerShell 命令升級應用程式：

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
