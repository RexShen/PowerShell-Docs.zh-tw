---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 參考
description: Windows PowerShell 參考
ms.openlocfilehash: 9c1547ac5ec5134c99aa9213e6aaca1af8d5b3e9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "94390230"
---
# <a name="windows-powershell-reference"></a>Windows PowerShell 參考

Windows PowerShell 是 Microsoft .NET Framework 連線的環境，專為系統管理自動化所設計。 Windows PowerShell 提供新的方法來建立命令、撰寫解決方案，以及建立以圖形使用者介面為基礎的管理工具。

Windows PowerShell 可讓系統管理員直接或透過腳本執行命令，自動管理系統資源。

## <a name="developer-audience"></a>開發人員讀者

Windows PowerShell 軟體發展工具組 (SDK) 是針對需要 Windows PowerShell 所提供之 Api 相關參考資訊的命令開發人員所撰寫。 命令開發人員使用 Windows PowerShell 建立命令和提供者，以擴充 Windows PowerShell 可執行檔工作。

## <a name="windows-powershell-resources"></a>Windows PowerShell 資源

除了 Windows PowerShell SDK 之外，下列資源還提供詳細資訊。

[使用 Windows PowerShell 消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell) 提供 Windows PowerShell 的簡介：語言、Cmdlet、提供者及物件的使用。

[撰寫 Windows PowerShell 模組](./module/writing-a-windows-powershell-module.md) 提供系統管理員、腳本開發人員和 Cmdlet 開發人員的資訊和範例，這些開發人員需要使用 Windows PowerShell 模組封裝和散發其 Windows PowerShell 解決方案。

[撰寫 Windows PowerShell Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md) 提供程式管理員的資訊和程式碼範例，以設計 Cmdlet 和執行 Cmdlet 程式碼的開發人員。

[Windows PowerShell Team Blog](https://devblogs.microsoft.com/powershell/) 從其他 Windows PowerShell 使用者學習和共同作業的最佳資源。 閱讀 Windows PowerShell 團隊部落格，然後加入 Windows PowerShell 使用者論壇 (microsoft.public.windows.powershell)。
使用 Windows Live 搜尋來尋找其他 Windows PowerShell 部落格與資源。 然後，當您開發專業知識時，可以自由地貢獻您的想法。

[PowerShell 模組瀏覽器](/powershell/module/) 提供最新版本的命令列說明主題。

## <a name="class-libraries"></a>類別庫

「[系統管理」：](/dotnet/api/System.Management.Automation)此命名空間是 Windows PowerShell 的根命名空間。 它包含執行自訂 Cmdlet 所需的類別、列舉和介面。 尤其是， [system.object](/dotnet/api/System.Management.Automation.Cmdlet) 類別是基類，所有 Cmdlet 類別都必須衍生自此基類。 如需有關 Cmdlet 的詳細資訊，請參閱。

[管理元件](/dotnet/api/System.Management.Automation.Provider) 。此命名空間包含執行 Windows PowerShell 提供者所需的類別、列舉和介面。 尤其是 [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 類別是基類，所有 Windows PowerShell 提供者類別都必須衍生自這個基類。

：此命名空間包含 Windows PowerShell 所執行的 Cmdlet 和提供者的[類別。](/dotnet/api/Microsoft.PowerShell.Commands) 同樣地，建議您建立 *YourName*。您所執行之 Cmdlet 的命令命名空間。

[管理。裝載](/dotnet/api/System.Management.Automation.Host) 此命名空間包含類別、列舉和介面，可供 Cmdlet 用來定義使用者與 Windows PowerShell 之間的互動。

[管理。內部](/dotnet/api/System.Management.Automation.Internal) 這個命名空間包含其他命名空間類別所使用的基類。 例如， [Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute) 類別是 [CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) 類別的基類（base class）（base class）（base class）。

[管理元件](/dotnet/api/System.Management.Automation.Runspaces) 這個命名空間包含用來建立 Windows PowerShell 運行空間的類別、列舉和介面。 在此內容中，Windows PowerShell 的運行空間是一或多個 Windows PowerShell 管線叫用 Cmdlet 的內容。 也就是說，Cmdlet 會在 Windows PowerShell 的運行空間的內容中運作。 如需 aboutWindows PowerShell 空間的詳細資訊，請參閱 [Windows PowerShell 的空間](hosting/creating-runspaces.md)。
