---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 變更電腦狀態
ms.openlocfilehash: 9278df55ba027134a61c8ed4e89b5b839d460b29
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736908"
---
# <a name="changing-computer-state"></a>變更電腦狀態

若要在 PowerShell 中重設電腦，請使用標準命令列工具、WMI 或 CIM 類別。
雖然您使用 PowerShell 只是為了執行工具，但是了解如何在 PowerShell 中變更電腦的電源狀態，描述了有關在 PowerShell 中使用外部工具的一些重要詳細資訊。

## <a name="locking-a-computer"></a>鎖定電腦

透過可用的標準工具直接鎖定電腦的唯一方式，是呼叫 **user32.dll** 中的 **LockWorkstation()** 函式：

```powershell
rundll32.exe user32.dll,LockWorkStation
```

此命令會立即鎖定工作站。 它使用執行 Windows DLL (並儲存其程式庫以供重複使用) 的 **rundll32.exe**，來執行 Windows 管理函式程式庫 `user32.dll`。

如果您在啟用 [快速切換使用者] 時鎖定工作站 (例如在 Windows XP 上)，電腦會顯示在使用者登入畫面，而不是啟動目前使用者的螢幕保護裝置。

若要關閉終端機伺服器上的特定工作階段，請使用 **tsshutdn.exe** 命令列工具。

## <a name="logging-off-the-current-session"></a>登出目前的工作階段

您可以使用幾項不同的技術，來登出本機系統上的工作階段。 最簡單的方式是使用遠端桌面/終端機服務命令列工具 **logoff.exe** (如需詳細資訊，請在 PowerShell 命令提示字元中，輸入 `logoff /?`)。 若要登出目前使用中的工作階段，請輸入 `logoff` 且不搭配引數。

您也可以使用 **shutdown.exe** 工具搭配其登出選項︰

```powershell
shutdown.exe -l
```

另一個選項是使用 WMI。 **Win32_OperatingSystem** 類別具有 **Shutdown** 方法。
叫用方法加上 0 旗標會起始登出︰

如需有關 **Shutdown** 方法的詳細資訊，請參閱 [Win32_OperatingSystem 類別的 Shutdown 方法](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)

```powershell
Get-CimInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a>關閉或重新啟動電腦

關閉並重新啟動電腦通常是相同類型的工作。 用來關閉電腦的工具通常也會用來重新啟動電腦，反之亦然。 有兩個從 PowerShell 重新啟動電腦的簡單選項。 使用 **tsshutdn.exe** 或 **shutdown.exe** 搭配適當的引數。 您可以從 `tsshutdn.exe /?` 或 `shutdown.exe /?` 取得詳細的使用方式資訊。

您也可以直接從 PowerShell 執行關閉和重新啟動作業。

若要關閉電腦，請使用 Stop-Computer 命令

```powershell
Stop-Computer
```

若要重新啟動作業系統，請使用 Restart-Computer 命令

```powershell
Restart-Computer
```

若要強制立即重新啟動電腦，請使用 -Force 參數。

```powershell
Restart-Computer -Force
```
