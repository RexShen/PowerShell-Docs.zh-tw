---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "啟動 32 位元版本的 Windows PowerShell"
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: 927b4028fcab68cb26d92bf292df2f0270837457
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a>啟動 32 位元版本的 Windows PowerShell
當您在 64 位元電腦上安裝 Windows PowerShell 時，除了 64 位元的版本，還會安裝 32 位元版本的 Windows PowerShell (**Windows PowerShell (x86)**)。 執行 Windows PowerShell 時，預設會執行 64 位元版本。

不過，您可能偶而需要執行 **Windows PowerShell (x86)**，例如，使用需要 32 位元版本的模組時，或遠端連線至 32 位元電腦時。

若要啟動 32 位元版本的 Windows PowerShell，請使用下列任何程序。

#### <a name="in-windows-server-2012-r2"></a>在 Windows Server® 2012 R2 中

-   在 **[開始]** 畫面上，輸入 **Windows PowerShell (x86)**。 按一下 **[Windows PowerShell x86]** 並排顯示。

-   在 **[伺服器管理員]** 中，從 **[工具]** 功能表中選取 **[Windows PowerShell (x86)]**。

-   在桌面上，將游標移到右上角、按一下 **[搜尋]**、輸入 **PowerShell x86**，然後按一下 **[Windows PowerShell (x86)]**。

-   透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>在 Windows Server® 2012 中

-   在 **[開始]** 畫面上，輸入 **PowerShell**，然後按一下 **[Windows PowerShell (x86)]**。

-   在 **[伺服器管理員]** 中，從 **[工具]** 功能表中選取 **[Windows PowerShell (x86)]**。

-   在桌面上，將游標移到右上角、按一下 **[搜尋]**、輸入 **PowerShell**，然後按一下 **[Windows PowerShell (x86)]**。

-   透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>在 Windows® 8.1 中

-   在 **[開始]** 畫面上，輸入 **Windows PowerShell (x86)**。 按一下 **[Windows PowerShell x86]** 並排顯示。

-   如果您正在執行 Windows 8.1 的[遠端伺服器管理工具](http://go.microsoft.com/fwlink/?LinkID=304145)，則也可以從 [伺服器管理員工具] 功能表中開啟 Windows PowerShell x86。 選取 **[Windows PowerShell (x86)]**。

-   在桌面上，將游標移到右上角、按一下 **[搜尋]**、輸入 **PowerShell x86**，然後按一下 **[Windows PowerShell (x86)]**。
   
-   透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>在 Windows® 8 中

-   在 **[開始]** 畫面上，將游標移到右上角，並依序按一下 **[設定]** 和 **[並排顯示]**，然後將 **[顯示系統管理工具]** 移到 [是]。 然後輸入 **PowerShell**，並按一下 **[Windows PowerShell (x86)]**。

-   如果您正在執行 Windows 8 的 [遠端伺服器管理工具](http://www.microsoft.com/download/details.aspx?id=28972)，則也可以從 [伺服器管理員工具] 功能表中開啟 Windows PowerShell x86。 選取 **[Windows PowerShell (x86)]**。

-   在 **[開始]** 畫面或桌面上，輸入 **PowerShell (x86)**，然後按一下 **[Windows PowerShell (x86)]**。

-   透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

