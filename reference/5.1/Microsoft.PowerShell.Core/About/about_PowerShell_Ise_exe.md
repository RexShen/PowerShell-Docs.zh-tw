---
description: 說明如何使用 PowerShell_Ise.exe 命令列工具。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_ise_exe?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Ise_exe
ms.openlocfilehash: c7500eb6d8586b9dca568edc4e805c577e94bec4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207956"
---
# <a name="about-powershell-iseexe"></a>關於 PowerShell Ise.exe

## <a name="short-description"></a>簡短描述

說明如何使用 PowerShell_Ise.exe 命令列工具。

## <a name="long-description"></a>詳細描述

PowerShell_Ise.exe 啟動 Windows PowerShell 整合式腳本環境 (ISE) 會話。 您可以在 Cmd.exe 和 Windows PowerShell 中執行它。

若要執行 PowerShell_ISE.exe，請輸入 PowerShell_ISE.exe、PowerShell_ISE 或 ISE。

## <a name="syntax"></a>SYNTAX

```
PowerShell_Ise[.exe]
PowerShell_ISE[.exe]
ISE[.exe]
[-File]<FilePath[]> [-NoProfile] [-MTA]
-Help | ? | -? | /? Displays the syntax and describes the command-line switches.
```

## <a name="parameters"></a>PARAMETERS

### <a name="-file"></a>-File

在 Windows PowerShell ISE 中開啟指定的檔案。 參數名稱 ( "-File" ) 是選擇性的。 若要列出一個以上的檔案，請輸入一個以引號括住的文字字串。 使用逗號來分隔字串內的檔案名。

例如：

PowerShell_ISE-File "File1.ps1，File2.ps1，File3.xml"。

Windows PowerShell 中允許檔案名之間的空格，但其他程式可能無法正確地解讀，例如 Cmd.exe。

您可以使用這個參數來開啟任何文字檔，包括 Windows PowerShell 腳本檔案和 XML 檔案。

### <a name="-mta"></a>-Mta

使用多執行緒的單元開始 Windows PowerShell ISE。 此參數是在 Windows PowerShell 3.0 引進。 單一執行緒的單元 (STA) 為預設值。

### <a name="-noprofile"></a>-NoProfile

不會執行 Windows PowerShell 設定檔。 根據預設，Windows PowerShell 設定檔會在每個會話中執行。

當您要撰寫共用內容（例如，將在具有不同設定檔的系統上執行的函式和腳本）時，建議使用此參數。
如需詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。

### <a name="-help---"></a>-Help-?,/？

顯示 PowerShell_ISE.exe 的說明。

## <a name="examples"></a>範例

這些命令會啟動 Windows PowerShell ISE。 這些命令是相等的，可以交換使用。

```
PS C:> PowerShell_ISE.exe
PS C:> PowerShell_ISE
PS C:> ISE
```

這些命令會在 Windows PowerShell ISE 中開啟 Get-Profile.ps1 腳本。
這些命令是相等的，可以交換使用。

```
PS C:> PowerShell_ISE.exe -File .\Get-Profile.ps1
PS C:> ISE -File .\Get-Profile.ps1
PS C:> ISE .\Get-Profile.ps1
```

此命令會在 Windows PowerShell ISE 中開啟 Get-Backups.ps1 和 Get-BackupInstance.ps1 腳本。 若要開啟一個以上的檔案，請使用逗號來分隔檔案名，並以引號括住整個檔案名。

```
PS C:> ISE -File ".\Get-Backups.ps1,Get-BackupInstance.ps1"
```

此命令會 Windows PowerShell ISE 沒有設定檔的情況下啟動。

```
PS C:> ISE -NoProfile
```

此命令會取得 PowerShell_ISE.exe 的說明。

```
PS C:> ISE -help
```

## <a name="see-also"></a>另請參閱

[about_PowerShell.exe](about_PowerShell_exe.md)

[about_Windows_PowerShell_ISE](about_Windows_PowerShell_ISE.md)

[Windows PowerShell 整合式指令碼環境 (ISE)](/powershell/scripting/windows-powershell/ise/introducing-the-windows-powershell-ise)
