---
ms.date: 2017-06-05T00:00:00.000Z
keywords: powershell,cmdlet
title: "在舊版 Windows 上啟動 Windows PowerShell"
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: cb56fded1e67a4f4219d210dd95078314e855b1a
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2017
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a>在舊版 Windows 上啟動 Windows PowerShell
本節說明如何在 Windows® 7、Windows Server® 2008 R2 和 Windows Server® 2008 中啟動 Windows PowerShell 和 Windows PowerShell 整合式指令碼環境 (ISE)。 它也會說明如何在 Windows Server® 2008 R2 和 Windows Server® 2008 上的 Windows PowerShell 2.0 中啟用 Windows PowerShell ISE 的選擇性功能。

若要在支援的系統上安裝 Windows PowerShell 4.0，請下載並安裝 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881)。 如需詳細資訊，請參閱[安裝 Windows PowerShell](Installing-Windows-PowerShell.md)。

若要在支援的系統上安裝 Windows PowerShell 3.0，請下載並安裝 [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290)。 如需詳細資訊，請參閱[安裝 Windows PowerShell](Installing-Windows-PowerShell.md)。

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>如何在舊版 Windows 上啟動 Windows PowerShell
使用下列任何方法來啟動已安裝的 Windows PowerShell 3.0 或 Windows PowerShell 4.0 版本 (適用時)。

#### <a name="from-the-start-menu"></a>從 [開始] 功能表

-   按一下 **[開始]**，並輸入 **PowerShell**，然後按一下 **[Windows PowerShell]**。

-   從 **[開始]** 功能表中，依序按一下 **[開始]**、**[所有程式]**、**[附屬應用程式]**、**[Windows PowerShell]** 資料夾和 **[Windows PowerShell]**。

#### <a name="at-the-command-prompt"></a>在命令提示字元中

-   在 Cmd.exe、Windows PowerShell 或 Windows PowerShell ISE 中，若要啟動 Windows PowerShell，請輸入︰

    ```
    PowerShell
    ```

    您也可以使用 PowerShell.exe 程式的參數來自訂工作階段。 如需詳細資訊，請參閱 [PowerShell.exe 命令列說明](../core-powershell/console/PowerShell.exe-Command-Line-Help.md)。

#### <a name="with-administrative-privileges-run-as-administrator"></a>使用系統管理權限 ([以系統管理員身分執行])

1.  按一下 [開始]、輸入 **PowerShell**、以滑鼠右鍵按一下 [Windows PowerShell]，然後按一下 [以系統管理員身分執行]。

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>如何在舊版 Windows 上啟動 Windows PowerShell ISE
使用下列任何方法來啟動 Windows PowerShell ISE。

#### <a name="from-the-start-menu"></a>從 [開始] 功能表

-   按一下 **[開始]**，並輸入 **ISE**，然後按一下 **[Windows PowerShell ISE]**。

-   從 **[開始]** 功能表中，依序按一下 **[開始]**、**[所有程式]**、**[附屬應用程式]**、**[Windows PowerShell]** 資料夾和 **[Windows PowerShell ISE]**。

#### <a name="at-the-command-prompt"></a>在命令提示字元中

-   在 Cmd.exe、Windows PowerShell 或 Windows PowerShell ISE 中，若要啟動 Windows PowerShell，請輸入︰

    ```
    PowerShell_ISE
    ```

    或

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a>使用系統管理權限 ([以系統管理員身分執行])

1.  按一下 [開始]、輸入 **ISE**、以滑鼠右鍵按一下 [Windows PowerShell ISE]，然後按一下 [以系統管理員身分執行]。

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>如何在舊版 Windows 上啟用 Windows PowerShell ISE
在 Windows PowerShell 4.0 和 Windows PowerShell 3.0 中，預設會在所有 Windows 版本上啟用 Windows PowerShell ISE。 如果尚未啟用，則 Windows Management Framework 4.0 或 Windows Management Framework 3.0 會啟用它。

在 Windows PowerShell 2.0 中，預設會在 Windows 7 上啟用 Windows PowerShell ISE。 不過，在 Windows Server 2008 R2 和 Windows Server 2008 中，這是選擇性功能。

若要在 Windows Server 2008 R2 或 Windows Server 2008 上的 Windows PowerShell 2.0 中啟用 Windows PowerShell ISE，請使用下列程序。

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>啟用 Windows PowerShell 整合式指令碼環境 (ISE)

1.  啟動 [伺服器管理員]。

2.  按一下 **[功能]**，然後按一下 **[新增功能]**。

3.  在 [選取功能] 中，按一下 [Windows PowerShell 整合式指令碼環境 (ISE)]。

