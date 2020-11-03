---
description: 提供關於 Windows Management Instrumentation (WMI) 和 Windows PowerShell 的背景資訊。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI_Cmdlets
ms.openlocfilehash: c2099c005cedf64e9621d66d6757419320c9b43e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207883"
---
# <a name="about-wmi-cmdlets"></a>關於 WMI Cmdlet

## <a name="short-description"></a>簡短描述

提供關於 Windows Management Instrumentation (WMI) 和 Windows PowerShell 的背景資訊。

## <a name="long-description"></a>詳細描述

本主題提供 WMI 技術、Windows PowerShell 的 WMI Cmdlet、wmi 型遠端、WMI 加速器和 WMI 疑難排解的相關資訊。 本主題也提供 WMI 的詳細資訊連結。

### <a name="about-wmi"></a>關於 WMI

Windows Management Instrumentation (WMI) 是 Microsoft 在 Web 架構企業管理 (WBEM) 方面的實作，這是一種開發標準技術的業界措施，用於存取企業環境中的管理資訊。 WMI 使用通用訊息模型 (CIM) 業界標準來代表系統、應用程式、網路、裝置和其他受管理元件。 CIM 由分散式管理任務推動小組 (DMTF) 開發與維護。 您可以使用 WMI 來管理本機和遠端電腦。 例如，您可以使用 WMI 來執行下列作業：

- 在遠端電腦上啟動處理常式。
- 從遠端重新開機電腦。
- 取得安裝在本機或遠端電腦上的應用程式清單。
- 查詢本機或遠端電腦上的 Windows 事件記錄檔。

### <a name="the-wmi-cmdlets-for-windows-powershell"></a>適用于 WINDOWS POWERSHELL 的 WMI CMDLET

Windows PowerShell 會透過一組可在 Windows PowerShell 中使用的 Cmdlet 來執行 WMI 功能。 您可以使用這些 Cmdlet 來完成管理本機和遠端電腦所需的端對端工作。

包含下列 WMI Cmdlet。

|Cmdlet           |描述                                   |
|-----------------|----------------------------------------------|
|Get-WmiObject    |取得 WMI 類別或資訊的實例  |
|                 |關於可用的類別。                  |
|Invoke-WmiMethod |呼叫 WMI 方法。                            |
|Register-WmiEvent|訂閱 WMI 事件。                    |
|Remove-WmiObject |刪除 WMI 類別和執行個體。            |
|Set-WmiInstance  |建立或修改 WMI 類別的執行個體。 |

### <a name="sample-commands"></a>範例命令
下列命令會顯示本機電腦的 BIOS 資訊。

```powershell
C:\PS> get-wmiobject win32_bios | format-list *
```

下列命令會顯示三部遠端電腦的 WinRM 服務相關資訊。

```powershell
$wql = "select * from win32_service where name='WinRM'"
get-wmiobject -query $wql -computername server01, server01, server03
```

下列更複雜的命令會結束程式的所有實例。

```powershell
C:\PS> notepad.exe
C:\PS> $wql = "select * from win32_process where name='notepad.exe'"
C:\PS> $np = get-wmiobject -query $wql
C:\PS> $np | remove-wmiobject
```

### <a name="wmi-based-remoting"></a>以 WMI 為基礎的遠端

雖然透過 WMI 管理本機系統的能力很有説明，但它是讓 WMI 成為強大系統管理工具的遠端功能。 WMI 會使用 Microsoft 的分散式元件物件模型 (DCOM) 來連接和管理系統。 您可能必須設定某些系統以允許 DCOM 連線。
防火牆設定和鎖定的 DCOM 許可權可以封鎖 WMI 從遠端管理系統的能力。

### <a name="wmi-type-accelerators"></a>WMI 類型加速器

Windows PowerShell 包含 WMI 類型加速器。 這些 WMI 類型加速器 (快捷方式，) 可讓您更直接存取 WMI 物件，而非以非類型加速器的方法允許。

WMI 支援下列類型加速器：

[WMISEARCHER]-用來搜尋 WMI 物件的快捷方式。

[WMICLASS]-存取類別之靜態屬性和方法的快捷方式。

[WMI]-取得類別的單一實例的快捷方式。

[WMISEARCHER] 是 ManagementObjectSearcher 的型別加速器。 它可以採用字串的函式來建立搜尋，讓您可以在上執行 GET ( # A1。

例如：

```powershell
PS> $s = [WmiSearcher]'Select * from Win32_Process where Handlecount > 1000'
PS> $s.Get() |sort handlecount |ft handlecount,__path,name -auto

count  __PATH                                              name
-----  ------                                              ----
1105   \\SERVER01\root\cimv2:Win32_Process.Handle="3724"   PowerShell...
1132   \\SERVER01\root\cimv2:Win32_Process.Handle="1388"   winlogon.exe
1495   \\SERVER01\root\cimv2:Win32_Process.Handle="2852"   iexplore.exe
1699   \\SERVER01\root\cimv2:Win32_Process.Handle="1204"   OUTLOOK.EXE
1719   \\SERVER01\root\cimv2:Win32_Process.Handle="1912"   iexplore.exe
2579   \\SERVER01\root\cimv2:Win32_Process.Handle="1768"   svchost.exe
```

[WMICLASS] 是 ManagementClass 的型別加速器。 這個字串的函式會接受 WMI 類別的本機或絕對 WMI 路徑，並傳回系結至該類別的物件。

例如：

```powershell
PS> $c = [WMICLASS]"root\cimv2:WIn32_Process"
PS> $c |fl *
Name             : Win32_Process
__GENUS          : 1
__CLASS          : Win32_Process
__SUPERCLASS     : CIM_Process
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Process
__PROPERTY_COUNT : 45
__DERIVATION     : {CIM_Process, CIM_LogicalElement,
                   CIM_ManagedSystemElement}
__SERVER         : SERVER01
__NAMESPACE      : ROOT\cimv2
__PATH           : \\SERVER01\ROOT\cimv2:Win32_Process
```

[WMI] 是 System.management.managementobject 的型別加速器。 這個字串的函式會接受 WMI 實例的本機或絕對 WMI 路徑，並傳回系結至該實例的物件。

例如：

```powershell
PS> $p = [WMI]'\\SERVER01\root\cimv2:Win32_Process.Handle="1204"'
PS> $p.Name
OUTLOOK.EXE
```

### <a name="wmi-troubleshooting"></a>WMI 疑難排解

下列問題是當您嘗試連接到遠端電腦時，可能發生的最常見問題。

問題1：遠端電腦不在線上。

如果電腦離線，您將無法使用 WMI 連接到電腦。
您可能會收到下列錯誤訊息：

```
Remote server machine does not exist or is unavailable
```

如果您收到此錯誤訊息，請確認電腦已上線。 嘗試 ping 遠端電腦。

問題2：您在遠端電腦上沒有本機系統管理員許可權。

若要從遠端使用 WMI，您必須擁有遠端電腦的本機系統管理員許可權。 如果沒有這麼做，就會拒絕存取該電腦。

若要驗證命名空間安全性：

1. 按一下 [開始]，以滑鼠右鍵按一下我的電腦，然後按一下 [管理]。
2. 在 [電腦管理] 中，展開 [服務和應用程式]，以滑鼠右鍵按一下 [WMI 控制]，然後按一下 [內容]
3. 在 [WMI 控制項屬性] 對話方塊中，按一下 [[安全性] 索引標籤]。

問題3：防火牆正在封鎖對遠端電腦的存取。

WMI 使用 DCOM (分散式 COM) 和 RPC (遠端程序呼叫) 通訊協定來跨越網路。 根據預設，許多防火牆會封鎖 DCOM 和 RPC 流量。 如果您的防火牆封鎖這些通訊協定，連接將會失敗。 例如，Microsoft Windows XP Service Pack 2 中的 Windows 防火牆是設定成自動封鎖所有未經要求的網路流量，包括 DCOM 和 WMI。 在其預設設定中，Windows 防火牆會拒絕傳入的 WMI 要求，且您會收到下列錯誤訊息：

```
Remote server machine does not exist or is unavailable
```

## <a name="see-also"></a>另請參閱

[關於 WMI](/windows/win32/wmisdk/about-wmi)

[WMI 疑難排解](/windows/win32/wmisdk/wmi-troubleshooting) \(英文\)

[Get-WmiObject](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[Invoke-WmiMethod](xref:Microsoft.PowerShell.Management.Invoke-WmiMethod)

[Register-WmiEvent](xref:Microsoft.PowerShell.Management.Register-WmiEvent)

[Remove-WmiObject](xref:Microsoft.PowerShell.Management.Remove-WmiObject)

[Set-WmiInstance](xref:Microsoft.PowerShell.Management.Set-WmiInstance)
