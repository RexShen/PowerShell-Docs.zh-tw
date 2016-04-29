---
title: 變更電腦狀態
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
---
# 變更電腦狀態
若要在 Windows PowerShell 中重設電腦，請使用標準命令列工具或 WMI 類別。 雖然您使用 Windows PowerShell 只是為了執行工具，但是了解如何在 Windows PowerShell 中變更電腦的電源狀態，描述了有關在 Windows PowerShell 中使用外部工具的一些重要詳細資訊。

### 鎖定電腦
透過可用的標準工具直接鎖定電腦的唯一方式，是呼叫 **user32.dll** 中的 **LockWorkstation()** 函式：

```
rundll32.exe user32.dll,LockWorkStation
```

此命令會立即鎖定工作站。 它使用執行 Windows DLL (並儲存其程式庫以供重複使用) 的 *rundll32.exe*，來執行 Windows 管理函式程式庫 user32.dll。

如果您在啟用 [快速切換使用者] 時鎖定工作站 (例如在 Windows XP 上)，電腦會顯示在使用者登入畫面，而不是啟動目前使用者的螢幕保護裝置。

若要關閉終端機伺服器上的特定工作階段，請使用 **tsshutdn.exe** 命令列工具。

### 登出目前的工作階段
您可以使用幾項不同的技術，來登出本機系統上的工作階段。 最簡單的方式是使用遠端桌面/終端機服務命令列工具 **logoff.exe** (如需詳細資訊，請在 Windows PowerShell 命令提示字元中，輸入 **logoff /?**)。 若要登出目前使用中的工作階段，請輸入 **logoff** 且不加引數。

您也可以使用 **shutdown.exe** 工具搭配其登出選項︰

```
shutdown.exe -l
```

第三個選項是使用 WMI。 Win32_OperatingSystem 類別具有 Win32Shutdown 方法。 叫用方法加上 0 旗標會起始登出︰

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

如需詳細資訊，以及尋找 Win32Shutdown 方法的其他函式，請參閱 MSDN 中的＜Win32Shutdown Method of the Win32_OperatingSystem Class＞(Win32_OperatingSystem 類別的 Win32Shutdown 方法)。

### 關閉或重新啟動電腦
關閉並重新啟動電腦通常是相同類型的工作。 用來關閉電腦的工具通常也會用來重新啟動電腦，反之亦然。 從 Windows PowerShell 重新啟動電腦有兩個直接的作法。 使用 Tsshutdn.exe 或 Shutdown.exe 加上適當的引數。 您可以從 **tsshutdn.exe /?** 或 **shutdown.exe /?** 取得詳細的使用方式資訊。

您也可以直接從 Windows PowerShell 使用 **Win32_OperatingSystem**，來執行關閉和重新啟動作業。

若要關閉電腦，請使用 Win32Shutdown 方法加上 **1** 旗標。

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(1)
```

若要重新啟動電腦，請使用 Win32Shutdown 方法加上 **2** 旗標。

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(2)
```



<!--HONumber=Apr16_HO1-->


