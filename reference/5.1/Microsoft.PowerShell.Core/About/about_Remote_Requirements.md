---
description: 描述在 PowerShell 中執行遠端命令的系統需求與設定需求。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Requirements
ms.openlocfilehash: 63971aeaa92eb10a745f2a02e0c7cf00dbf65d8f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207920"
---
# <a name="about-remote-requirements"></a>關於遠端需求

## <a name="short-description"></a>簡短描述

描述在 PowerShell 中執行遠端命令的系統需求與設定需求。

## <a name="long-description"></a>詳細描述

本主題說明在 PowerShell 中建立遠端連線和執行遠端命令的系統需求、使用者需求和資源需求。 它也提供設定遠端作業的指示。

注意：許多 Cmdlet (包括 Get-help、>get-wmiobject、get-help、Get-EventLog 和 Get-WinEvent Cmdlet) 從遠端電腦取得物件，方法是使用 Microsoft .NET Framework 方法來取出物件。 它們不會使用 PowerShell 遠端基礎結構。 本檔中的需求不適用於這些 Cmdlet。

若要尋找具有 ComputerName 參數但未使用 Windows PowerShell 遠端功能的 Cmdlet，請閱讀 Cmdlet 的 ComputerName 參數描述。

## <a name="system-requirements"></a>系統需求

若要在 Windows PowerShell 3.0 上執行遠端會話，本機和遠端電腦必須具有下列各項：

- Windows PowerShell 3.0 或更新版本
- Microsoft .NET Framework 4 或更新版本
- Windows 遠端管理3。0

若要在 Windows PowerShell 2.0 上執行遠端會話，本機和遠端電腦必須具有下列各項：

- Windows PowerShell 2.0 或更新版本
- Microsoft .NET Framework 2.0 或更新版本
- Windows 遠端管理2。0

您可以在執行 Windows PowerShell 2.0 和 Windows PowerShell 3.0 的電腦之間建立遠端會話。 不過，只有當兩部電腦都在執行 Windows PowerShell 3.0 時，才可使用在 Windows PowerShell 3.0 上執行的功能，例如中斷連線和重新連線至會話的能力。

若要尋找已安裝之 PowerShell 版本的版本號碼，請使用 $PSVersionTable 自動變數。

Windows 8、Windows Server 2012 和更新版本的 Windows 作業系統包含 Windows 遠端管理 (WinRM) 3.0 和 Microsoft .NET Framework 4。 舊版作業系統的 Windows Management Framework 3.0 包含 WinRM 3.0。 如果電腦沒有必要的 WinRM 版本或 Microsoft .NET Framework，則安裝會失敗。

## <a name="user-permissions"></a>使用者權限

若要建立遠端會話並執行遠端命令，預設的使用者必須是遠端電腦上 Administrators 群組的成員，或是提供系統管理員的認證。 否則命令會失敗。

在遠端電腦上建立會話和執行命令所需的許可權 (或本機電腦上的遠端會話) 是由會話設定 (也稱為「端點」 ) 在會話連線的遠端電腦上。 具體而言，會話設定上的安全描述項會決定誰可以存取會話設定，以及誰可以使用它來連接。

預設會話設定的安全描述項、Microsoft.powershell32 和 Microsoft. 工作流程，只允許存取 Administrators 群組成員的許可權。

如果目前的使用者沒有使用會話設定的許可權，則執行命令的命令 (（使用暫時性會話) 或在遠端電腦上建立持續性會話）將會失敗。 使用者可以使用 Cmdlet 的 ConfigurationName 參數來建立會話，以選取不同的會話設定（如果有的話）。

電腦上 Administrators 群組的成員可以藉由變更預設會話設定的安全描述項，以及建立具有不同安全描述項的新會話設定，來判斷誰有權從遠端連線到電腦。

如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](about_Session_Configurations.md)。

## <a name="windows-network-locations"></a>WINDOWS 網路位置

從 Windows PowerShell 3.0 開始，Enable-PSRemoting Cmdlet 可以在私人、網域及公用網路上的用戶端和伺服器版本的 Windows 上啟用遠端功能。

在具有私人和網域網路的 Windows server 版本上，Enable-PSRemoting Cmdlet 會建立允許不受限制的遠端存取的防火牆規則。 它也會針對公用網路建立防火牆規則，以允許從相同本機子網的電腦進行遠端存取。 此本機子網防火牆規則預設會在公用網路上的 Windows server 版本上啟用，但 Enable-PSRemoting 會在變更或刪除時重新套用規則。

在具有私人和網域網路的 Windows 用戶端版本上，根據預設，Enable-PSRemoting Cmdlet 會建立允許不受限制的遠端存取的防火牆規則。

若要在用戶端版本的 Windows 上啟用具有公用網路的遠端功能，請使用 Enable-PSRemoting Cmdlet 的 SkipNetworkProfileCheck 參數。 它會建立防火牆規則，只允許來自相同本機子網的電腦進行遠端存取。

若要移除公用網路上的本機子網限制，並允許從用戶端和伺服器版本的 Windows 上的所有位置進行遠端存取，請使用 NetSecurity 模組中的 Set-NetFirewallRule Cmdlet。 執行下列命令：

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

在 Windows PowerShell 2.0 中，在伺服器版本的 Windows 上，Enable-PSRemoting 會建立允許在所有網路上進行遠端存取的防火牆規則。

在 Windows PowerShell 2.0 中，在用戶端版本的 Windows 上，Enable-PSRemoting 只會在私人和網域網路上建立防火牆規則。 如果網路位置是公用的，Enable-PSRemoting 會失敗。

## <a name="run-as-administrator"></a>以系統管理員身分執行

下列遠端操作需要系統管理員許可權：

- 建立本機電腦的遠端連線。 這通常稱為「回送」案例。

- 管理本機電腦上的會話設定。

- 在本機電腦上進行 WS-Management 設定的查看與變更。 這些是 WSMAN：磁片磁碟機的 LocalHost 節點中的設定。

若要執行這些工作，您必須使用 [以系統管理員身分執行] 選項啟動 PowerShell，即使您是本機電腦上 Administrators 群組的成員也一樣。

在 Windows 7 和 Windows Server 2008 R2 中，使用 [以系統管理員身分執行] 選項開始 Windows PowerShell：

1. 依序按一下 [開始]、[所有程式]、[附屬應用程式]，然後按一下 Windows PowerShell 資料夾。
2. 在 [Windows PowerShell] 上按一下滑鼠右鍵，然後按一下 [以系統管理員身分執行]。

若要使用 [以系統管理員身分執行] 選項開始 Windows PowerShell：

1. 按一下 [開始]，按一下 [所有程式]，然後按一下 Windows PowerShell 資料夾。
2. 在 [Windows PowerShell] 上按一下滑鼠右鍵，然後按一下 [以系統管理員身分執行]。

[以系統管理員身分執行] 選項也適用于 Windows PowerShell 的其他 Windows 檔案總管專案，包括快捷方式。 只要以滑鼠右鍵按一下專案，然後按一下 [以系統管理員身分執行]。

當您從另一個程式（例如 Cmd.exe）開始 Windows PowerShell 時，請使用 [以系統管理員身分執行] 選項來啟動程式。

## <a name="how-to-configure-your-computer-for-remoting"></a>如何設定您的電腦以進行遠端處理

執行所有支援的 Windows 版本的電腦可以在 PowerShell 中建立遠端連線並執行遠端命令，而不需要進行任何設定。 不過，若要接收連線，並允許使用者建立本機和遠端使用者管理的 PowerShell 會話 ( "Pssession" ) 並在本機電腦上執行命令，您必須在電腦上啟用 PowerShell 遠端功能。

Windows server 2012 和更新版本的 Windows Server 預設會啟用 PowerShell 遠端功能。 如果設定已變更，您可以執行 Enable-PSRemoting Cmdlet 來還原預設設定。

在所有其他支援的 Windows 版本上，您必須執行 Enable-PSRemoting Cmdlet 以啟用 PowerShell 遠端功能。

WinRM 服務支援 PowerShell 的遠端功能，也就是 Microsoft 管理 Web Services for Management (WS-MANAGEMENT) 通訊協定。 當您啟用 PowerShell 遠端功能時，您會變更 WS-Management 的預設設定，並新增可讓使用者連線至 WS-MANAGEMENT 的系統組態。

若要將 PowerShell 設定為接收遠端命令：

1. 使用 [以系統管理員身分執行] 選項啟動 PowerShell。
2. 在命令提示字元中，輸入：`Enable-PSRemoting`

若要確認是否已正確設定遠端，請執行如下命令的測試命令，這會在本機電腦上建立遠端會話。

```powershell
New-PSSession
```

如果已正確設定遠端，此命令會在本機電腦上建立會話，並傳回代表會話的物件。 輸出應類似下列範例輸出：

```output
Id Name        ComputerName    State    ConfigurationName
-- ----        ------------    -----    -----
1  Session1    localhost       Opened   Microsoft.PowerShell
```

如果命令失敗，如需協助，請參閱 [about_Remote_Troubleshooting](about_Remote_Troubleshooting.md)。

## <a name="understand-policies"></a>瞭解原則

當您從遠端工作時，您會使用兩個 PowerShell 實例，一個在本機電腦上，另一個位於遠端電腦上。 因此，您的工作會受到 Windows 原則和本機電腦和遠端電腦上的 PowerShell 原則影響。

一般情況下，在您連接之前，以及在建立連線之前，本機電腦上的原則都會生效。 當您使用此連接時，遠端電腦上的原則會生效。

## <a name="see-also"></a>另請參閱

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[about_PSSessions](about_PSSessions.md)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
