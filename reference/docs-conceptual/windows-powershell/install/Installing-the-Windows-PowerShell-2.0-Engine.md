---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 安裝 Windows PowerShell 2.0 引擎
description: Windows PowerShell 2.0 引擎是 Windows 的選用功能。 此文章說明如何安裝此功能及必要的需求。
ms.openlocfilehash: c82725c34f5c5864eba0c88eb33ecac9e43f86d3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663969"
---
# <a name="installing-the-windows-powershell-20-engine"></a>安裝 Windows PowerShell 2.0 引擎

本主題說明如何安裝 Windows PowerShell 2.0 引擎。

Windows PowerShell 3.0 已設計為可回溯相容至 Windows PowerShell 2.0。 針對 Windows PowerShell 2.0 撰寫的 Cmdlet、提供者、嵌入式管理單元、模組及指令碼，在 Windows PowerShell 3.0 和 Windows PowerShell 4.0 中仍以同樣方式執行。 不過，因為 Microsoft .NET Framework 4 中執行階段啟用原則的變更，所以在較新版的 Windows PowerShell (使用 CLR 4.0 編譯) 中，必須修改才能執行針對 Windows PowerShell 2.0 所撰寫並使用通用語言執行平台 (CLR) 2.0 編譯的 Windows PowerShell 主機程式。

為了維持與受到這些變更影響之主機程式的回溯相容性，已將 Windows PowerShell 2.0、Windows PowerShell 3.0 及 Windows PowerShell 4.0 引擎設計為並存執行。 此外，Windows PowerShell 2.0 引擎隨附於 Windows Server 2012 R2、Windows 8.1、Windows 8、Windows Server 2012 及 Windows Management Framework 3.0 中。 只有在現有指令碼或主機程式無法執行時才會使用 Windows PowerShell 2.0 引擎，因為它與 Windows PowerShell 3.0、Windows PowerShell 4.0 或 Microsoft .NET Framework 4 不相容。 這種情況應該很少見。

Windows PowerShell 2.0 引擎是 Windows Server 2012 R2、Windows 8.1、Windows&reg; 8 與 Windows Server&reg; 2012 的選用功能。 在舊版 Windows 中，當您安裝 Windows Management Framework 3.0 時，Windows PowerShell 3.0 安裝會完全取代 Windows PowerShell 安裝目錄中的 Windows PowerShell 2.0 安裝。 不過，會保留 Windows PowerShell 2.0 引擎。

如需啟動 Windows PowerShell 2.0 引擎的相關資訊，請參閱[啟動 Windows PowerShell 2.0 引擎](../Starting-the-Windows-PowerShell-2.0-Engine.md)。

## <a name="on-windows-81-and-windows-8"></a>在 Windows 8.1 和 Windows 8 上

在 Windows 8.1 和 Windows 8 上，預設會開啟 Windows PowerShell 2.0 引擎功能。
不過若要使用，則必須開啟所需的 Microsoft .NET Framework 3.5 選項。 本節也會說明如何開啟及關閉 Windows PowerShell 2.0 引擎功能。

#### <a name="to-turn-on-net-framework-35"></a>開啟 .NET Framework 3.5

1. 在 **[開始]** 畫面上，輸入 **Windows 功能** 。
2. 在 **[應用程式]** 列中按一下 **[設定]** ，然後按一下 **[開啟或關閉 Windows 功能]** 。
3. 在 **[Windows 功能]** 方塊中，按一下 **[.NET Framework 3.5 (包括 .NET 2.0 和 3.0)]** 加以選取。

   當您選取 **[.NET Framework 3.5 (包括 .NET 2.0 和 3.0)]** 時，會填入方塊中以指出僅選取部分功能。 不過，這樣已足以應付 Windows PowerShell 2.0 引擎。

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a>啟動和關閉 Windows PowerShell 2.0 引擎

1. 在 **[開始]** 畫面上，輸入 **Windows 功能** 。

2. 在 **[應用程式]** 列中按一下 **[設定]** ，然後按一下 **[開啟或關閉 Windows 功能]** 。

3. 在 [Windows 功能] 方塊中，展開 [Windows PowerShell 2.0] 節點，然後按一下 [Windows PowerShell 2.0 引擎] 方塊加以選取或清除。

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a>在 Windows Server 2012 R2 和 Windows Server 2012 上

使用下列程序來新增 Windows PowerShell 2.0 引擎和 Microsoft .NET Framework 3.5 功能。 Windows PowerShell 2.0 引擎至少需要 Microsoft .NET Framework 2.0.50727。 Microsoft .NET Framework 3.5 可完成這項需求。

#### <a name="to-add-the-net-framework-35-feature"></a>新增 .NET Framework 3.5 功能

1. 在 **[伺服器管理員]** 中，從 **[管理]** 功能表選取 **[新增角色及功能]** 。

    或者，在 [伺服器管理員] 中，按一下 [所有伺服器]，以滑鼠右鍵按一下伺服器名稱，然後選取 [新增角色及功能]。

2. 在 [安裝類型] 頁面上，選取 [角色型或功能型安裝]。

3. 在 **[功能]** 頁面上，展開 **[.NET 3.5 Framework 功能]** 節點，然後選取 **[.NET Framework 3.5 (包括 .NET 2.0 和 3.0)]** 。

   Windows PowerShell 2.0 引擎不需要該節點下方的其他選項。

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a>新增 Windows PowerShell 2.0 引擎功能

- 在 **[伺服器管理員]** 中，從 **[管理]** 功能表選取 **[新增角色及功能]** 。

  或者，在 [伺服器管理員] 中，按一下 [所有伺服器]，以滑鼠右鍵按一下伺服器名稱，然後選取 [新增角色及功能]。

- 在 [安裝類型] 頁面上，選取 [角色型或功能型安裝]。

- 在 **[功能]** 頁面上，展開 **[Windows PowerShell (Installed) (Windows PowerShell (已安裝))]** 節點，然後選取 **[Windows PowerShell 2.0 引擎]** 。

如需啟動 Windows PowerShell 2.0 引擎的相關資訊，請參閱[啟動 Windows PowerShell 2.0 引擎](../Starting-the-Windows-PowerShell-2.0-Engine.md)。

## <a name="on-earlier-systems"></a>在舊版系統上

在 Windows 7、Windows Server 2008 R2 和 Windows Server 2012 上安裝 Windows PowerShell 4.0 的 [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) 套件會包含 Windows PowerShell 2.0 引擎。 Windows PowerShell 2.0 引擎可視需要啟用並開始使用，而不需要額外的安裝、設定或組態。

在 Windows 7、Windows Server 2008 R2 和 Windows Server 2008 上安裝 Windows PowerShell 3.0 的 Windows Management Framework 3.0 套件會包含 Windows PowerShell 2.0 引擎。 Windows PowerShell 2.0 引擎可視需要啟用並開始使用，而不需要額外的安裝、設定或組態。

## <a name="see-also"></a>另請參閱

- [Windows PowerShell 系統需求](Windows-PowerShell-System-Requirements.md)
- [安裝 Windows PowerShell](Installing-Windows-PowerShell.md)
- [啟動 Windows PowerShell](/previous-versions/ms714415(v=vs.85))
- [啟動 Windows PowerShell 2.0 引擎](../Starting-the-Windows-PowerShell-2.0-Engine.md)
