---
title: PowerShell Core 中的 WS-Management (WSMan) 遠端處理
description: 使用 WSMan 在 PowerShell Core 中遠端
ms.date: 08/06/2018
ms.openlocfilehash: fdc4159279db28b8ee60bc0853e19512a1f9ec14
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501298"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a>PowerShell Core 中的 WS-Management (WSMan) 遠端處理

## <a name="instructions-to-create-a-remoting-endpoint"></a>建立遠端端點的指示

PowerShell Core for Windows 套件包含 `$PSHome` 中的 WinRM 外掛程式 (`pwrshplugin.dll`) 和安裝指令碼 (`Install-PowerShellRemoting.ps1`)。 這些檔案讓 PowerShell 在指定其端點時接受連入的 PowerShell 遠端連線。

### <a name="motivation"></a>動機

PowerShell 安裝可以使用 `New-PSSession` 和 `Enter-PSSession` 建立遠端電腦的 PowerShell 工作階段。 若要啟用它來接受連入的 PowerShell 遠端連線，使用者必須建立 WinRM 遠端端點。 這是使用者執行 Install-PowerShellRemoting.ps1 建立 WinRM 端點的明確加入案例。 將額外功能新增至 `Enable-PSRemoting` 以執行相同動作之前，安裝指令碼是短期解決方案。 如需詳細資料，請參閱問題 [#1193](https://github.com/PowerShell/PowerShell/issues/1193)。

### <a name="script-actions"></a>指令碼動作

指令碼

1. 在 `$env:windir\System32\PowerShell` 內建立外掛程式的目錄
1. 將 pwrshplugin.dll 複製至該位置
1. 產生設定檔
1. 使用 WinRM 註冊該外掛程式

### <a name="registration"></a>註冊

指令碼必須在系統管理員層級 PowerShell 工作階段內執行，並以兩種模式執行。

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a>透過其將註冊的 PowerShell 執行個體來執行

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a>另一個 PowerShell 執行個體代表其將註冊的執行個體來執行

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

例如：

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

> [!NOTE]
> 遠端註冊指令碼會重新啟動 WinRM。 所有現有的 PSRP 工作階段都會在執行指令碼之後立即終止。 若在遠端工作階段期間執行，指令碼會終止連線。

## <a name="how-to-connect-to-the-new-endpoint"></a>如何連線至新端點

指定 `-ConfigurationName "some endpoint name"`，以建立與新 PowerShell 端點的新 PowerShell 工作階段。 若要連線至上述範例中的 PowerShell 執行個體，請使用：

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

請注意，未指定 `-ConfigurationName` 的 `New-PSSession` 和 `Enter-PSSession` 引動過程將會以預設 PowerShell 端點 `microsoft.powershell` 為目標。
