---
ms.date: 12/05/2019
keywords: powershell,cmdlet
title: 啟動 Windows PowerShell
description: 此文章說明啟動各種 PowerShell 版本的方式。
ms.openlocfilehash: 47da7d85c9f7e6966a7f7e809c77979cd24cf129
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664028"
---
# <a name="starting-windows-powershell"></a>啟動 Windows PowerShell

Windows PowerShell 是指令碼引擎 `.DLL`，其會內嵌到多部主機中。 您將啟動的最常見主機為互動式命令列 `powershell.exe` 與互動式指令碼環境 `powershell_ise.exe`。

若要在 Windows Server&reg; 2012 R2、Windows&reg; 8.1、Windows Server 2012 與 Windows 8 上啟動 Windows PowerShell&reg;，請參閱 [Windows 中的常見管理工作與瀏覽](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11))。

## <a name="powershell-core-has-renamed-binary"></a>PowerShell Core 已重新命名二進位

PowerShell Core (稱為 PowerShell) 是開放原始碼的第 6 版和更高版本，且使用 .NET Core。 支援的版本適用於 Windows、macOS 和 Linux。

從 PowerShell 6 開始，PowerShell 二進位已針對 Windows 重新命名為 `pwsh.exe`，並針對 macOS 與 Linux 重新命名為 `pwsh`。 您可以使用 `pwsh-preview` 來啟動 PowerShell 預覽版本。 如需詳細資訊，請參閱 [PowerShell Core 6.0 的新功能](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe)和[關於 pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh)。

若要尋找 PowerShell 7 的 Cmdlet 參考和安裝文件，請使用下列連結：

| 文件 | 連結 |
| ----- | ----- |
| Cmdlet 參考 | [PowerShell 模組瀏覽器](/powershell/module/) |
| Windows 安裝 | [在 Windows 上安裝 PowerShell Core](/powershell/scripting/install/installing-powershell-core-on-windows) |
| macOS 安裝 | [在 macOS 上安裝 PowerShell Core](/powershell/scripting/install/installing-powershell-core-on-macos) |
| Linux 安裝 | [在 Linux 上安裝 PowerShell Core](/powershell/scripting/install/installing-powershell-core-on-linux) |

若要查看其他 PowerShell 版本的內容，請參閱[如何使用 PowerShell 文件](../how-to-use-docs.md)。

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>如何在舊版 Windows 上啟動 Windows PowerShell

此節說明如何在 Windows&reg; 7、Windows Server&reg; 2008 R2 與 Windows Server&reg; 2008 中，啟動 Windows PowerShell 與 Windows PowerShell 整合式指令碼環境 (ISE)。 同時也會說明如何在 Windows Server&reg; 2008 R2 與 Windows Server&reg; 2008 上的 Windows PowerShell 2.0 中，啟用 Windows PowerShell ISE 的選用功能。

使用下列任何方法來啟動已安裝的 Windows PowerShell 3.0 或 Windows PowerShell 4.0 版本 (適用時)。

#### <a name="from-the-start-menu"></a>從 [開始] 功能表

- 按一下 **[開始]** ，並輸入 **PowerShell** ，然後按一下 **[Windows PowerShell]** 。
- 從 **[開始]** 功能表中，依序按一下 **[開始]** 、 **[所有程式]** 、 **[附屬應用程式]** 、 **[Windows PowerShell]** 資料夾和 **[Windows PowerShell]** 。

#### <a name="at-the-command-prompt"></a>在命令提示字元中

在 **cmd.exe** 、Windows PowerShell 或 Windows PowerShell ISE 中，若要啟動 Windows PowerShell，請鍵入︰

```
PowerShell
```

您也可以使用 `powershell.exe` 程式的參數來自訂工作階段。 如需詳細資訊，請參閱 [PowerShell.exe 命令列說明](/powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_exe)。

#### <a name="with-administrative-privileges-run-as-administrator"></a>使用系統管理權限 (以系統管理員身分執行)

按一下 [開始]、輸入 **PowerShell** 、以滑鼠右鍵按一下 [Windows PowerShell]，然後按一下 [以系統管理員身分執行]。

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>如何在舊版 Windows 上啟動 Windows PowerShell ISE

使用下列任何方法來啟動 Windows PowerShell ISE。

#### <a name="from-the-start-menu"></a>從 [開始] 功能表

- 按一下 **[開始]** ，並輸入 **ISE** ，然後按一下 **[Windows PowerShell ISE]** 。
- 從 **[開始]** 功能表中，依序按一下 **[開始]** 、 **[所有程式]** 、 **[附屬應用程式]** 、 **[Windows PowerShell]** 資料夾和 **[Windows PowerShell ISE]** 。

#### <a name="at-the-command-prompt"></a>在命令提示字元中

在 `cmd.exe`、Windows PowerShell 或 Windows PowerShell ISE 中，若要啟動 Windows PowerShell，請輸入：

```
PowerShell_ISE
```

或

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>使用系統管理權限 (以系統管理員身分執行)

按一下 [開始]、輸入 **ISE** 、以滑鼠右鍵按一下 [Windows PowerShell ISE]，然後按一下 [以系統管理員身分執行]。

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>如何在舊版 Windows 上啟用 Windows PowerShell ISE

在 Windows PowerShell 4.0 和 Windows PowerShell 3.0 中，預設會在所有 Windows 版本上啟用 Windows PowerShell ISE。 如果尚未啟用，則 Windows Management Framework 4.0 或 Windows Management Framework 3.0 會將其啟用。

在 Windows PowerShell 2.0 中，預設會在 Windows 7 上啟用 Windows PowerShell ISE。 不過，在 Windows Server 2008 R2 和 Windows Server 2008 中，這是選擇性功能。

若要在 Windows Server 2008 R2 或 Windows Server 2008 上的 Windows PowerShell 2.0 中啟用 Windows PowerShell ISE，請使用下列程序。

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>啟用 Windows PowerShell 整合式指令碼環境 (ISE)

1. 啟動伺服器管理員。
2. 按一下 **[功能]** ，然後按一下 **[新增功能]** 。
3. 在 [選取功能] 中，按一下 [Windows PowerShell 整合式指令碼環境 (ISE)]。

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>啟動 32 位元版本的 Windows PowerShell

當您在 64 位元電腦上安裝 Windows PowerShell 時，除了 64 位元的版本，還會安裝 32 位元版本的 Windows PowerShell ( **Windows PowerShell (x86)** )。 執行 Windows PowerShell 時，預設會執行 64 位元版本。

不過，您可能偶爾需要執行 **Windows PowerShell (x86)** 例如，使用需要 32 位元版本的模組時，或遠端連線至 32 位元電腦時。

若要啟動 32 位元版本的 Windows PowerShell，請使用下列任何程序。

#### <a name="in-windows-serverreg-2012-r2"></a>在 Windows Server&reg; 2012 R2 中

- 在 **[開始]** 畫面上，輸入 **Windows PowerShell (x86)** 。 按一下 **[Windows PowerShell x86]** 並排顯示。
- 在 **[伺服器管理員]** 中，從 **[工具]** 功能表中選取 **[Windows PowerShell (x86)]** 。
- 在桌面上，將游標移到右上角、按一下 **[搜尋]** 、輸入 **PowerShell x86** ，然後按一下 **[Windows PowerShell (x86)]** 。
- 透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-serverreg-2012"></a>在 Windows Server&reg; 2012 中

- 在 **[開始]** 畫面上，輸入 **PowerShell** ，然後按一下 **[Windows PowerShell (x86)]** 。
- 在 **[伺服器管理員]** 中，從 **[工具]** 功能表中選取 **[Windows PowerShell (x86)]** 。
- 在桌面上，將游標移到右上角、按一下 **[搜尋]** 、輸入 **PowerShell** ，然後按一下 **[Windows PowerShell (x86)]** 。
- 透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windowsreg-81"></a>在 Windows&reg; 8.1 中

- 在 **[開始]** 畫面上，輸入 **Windows PowerShell (x86)** 。 按一下 **[Windows PowerShell x86]** 並排顯示。
- 如果您正在執行 Windows 8.1 的[遠端伺服器管理工具](https://go.microsoft.com/fwlink/?LinkID=304145)，則也可以從 [伺服器管理員工具] 功能表中開啟 Windows PowerShell x86。 選取 **[Windows PowerShell (x86)]** 。
- 在桌面上，將游標移到右上角、按一下 **[搜尋]** 、輸入 **PowerShell x86** ，然後按一下 **[Windows PowerShell (x86)]** 。
- 透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windowsreg-8"></a>在 Windows&reg; 8 中

- 在 [開始] 畫面上，將游標移到右上角，並依序按一下 [設定] 和 [並排顯示]，然後將 [顯示系統管理工具] 移到 [是]。 然後輸入 **PowerShell** ，並按一下 **[Windows PowerShell (x86)]** 。
- 如果您正在執行 Windows 8 的 [遠端伺服器管理工具](https://www.microsoft.com/download/details.aspx?id=28972)，則也可以從 [伺服器管理員工具] 功能表中開啟 Windows PowerShell x86。 選取 **[Windows PowerShell (x86)]** 。
- 在 **[開始]** 畫面或桌面上，輸入 **PowerShell (x86)** ，然後按一下 **[Windows PowerShell (x86)]** 。
- 透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`
