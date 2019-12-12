---
title: Windows PowerShell 參考 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell SDK
ms.assetid: cbba4879-bcac-484a-9906-4bbe2cd1eb33
caps.latest.revision: 11
ms.openlocfilehash: 48b2b2b9ab2a39cf185ed54bcfa99d46562e13b6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366277"
---
# <a name="windows-powershell-reference"></a>Windows PowerShell 參考

Windows PowerShell 是專為系統管理自動化而設計的 Microsoft .NET Framework 連線環境。 Windows PowerShell 提供新的方法來建立命令、撰寫解決方案，以及建立以圖形化使用者介面為基礎的管理工具。

Windows PowerShell 可讓系統管理員直接或透過腳本執行命令，自動管理系統資源。

## <a name="developer-audience"></a>開發人員讀者

Windows PowerShell 軟體發展工具組（SDK）是針對需要 Windows PowerShell 所提供之 Api 相關參考資訊的命令開發人員所撰寫。 命令開發人員可以使用 Windows PowerShell 來建立命令和提供者，以擴充 Windows PowerShell 可執行檔工作。

## <a name="windows-powershell-resources"></a>Windows PowerShell 資源

除了 Windows PowerShell SDK 以外，下列資源還提供詳細資訊。

[使用 Windows PowerShell 消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell)提供 Windows PowerShell 簡介：語言、Cmdlet、提供者及物件的使用。

[撰寫 Windows PowerShell 模組](./module/writing-a-windows-powershell-module.md)針對需要使用 Windows PowerShell 模組封裝和散佈其 Windows PowerShell 解決方案的系統管理員、腳本開發人員和 Cmdlet 開發人員，提供相關資訊和範例。

[撰寫 Windows PowerShell Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md)針對正在設計 Cmdlet 的程式管理員，以及正在執行 Cmdlet 程式碼的開發人員，提供相關資訊和程式碼範例。

[Windows PowerShell 小組 Blog](https://blogs.msdn.microsoft.com/PowerShell/)與其他 Windows PowerShell 使用者一起學習及協同作業的最佳資源。 閱讀 Windows PowerShell 團隊部落格，然後加入 Windows PowerShell 使用者論壇 (microsoft.public.windows.powershell)。 使用 Windows Live 搜尋來尋找其他 Windows PowerShell 部落格與資源。 然後，當您開發自己的專業知識時，可以自由地提供您的想法。

[PowerShell 模組瀏覽器](/powershell/module/)提供命令列說明主題的最新版本。

## <a name="class-libraries"></a>類別庫

[System.web](/dotnet/api/System.Management.Automation) ：此命名空間是 Windows PowerShell 的根命名空間。 其中包含執行自訂 Cmdlet 所需的類別、列舉和介面。 特別是， [system.object](/dotnet/api/System.Management.Automation.Cmdlet)類別是必須從中衍生所有 Cmdlet 類別的基類（base class）。 如需有關 Cmdlet 的詳細資訊，請參閱。

[提供者](/dotnet/api/System.Management.Automation.Provider)：此命名空間包含執行 Windows PowerShell 提供者所需的類別、列舉和介面。 特別是， [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)類別是所有 Windows PowerShell 提供者類別都必須衍生自的基類。

的[命令](/dotnet/api/Microsoft.PowerShell.Commands)：此命名空間包含 Windows PowerShell 所執行之 Cmdlet 和提供者的類別。 同樣地，建議您建立*YourName*。您所執行之 Cmdlet 的命令命名空間。

[。裝載](/dotnet/api/System.Management.Automation.Host)此命名空間包含類別、列舉和介面，指令程式會使用此 Cmdlet 來定義使用者與 Windows PowerShell 之間的互動。

[。內部](/dotnet/api/System.Management.Automation.Internal)這個命名空間包含其他命名空間類別所使用的基類。 例如， [Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute)類別就是[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)類別的基類（base class），而不是。

[[系統管理](/dotnet/api/System.Management.Automation.Runspaces)]。此命名空間包含用來建立 Windows PowerShell 執行時間的類別、列舉和介面。 在此內容中，Windows PowerShell 執行時間是一或多個 Windows PowerShell 管線叫用 Cmdlet 的內容。 也就是說，Cmdlet 會在 Windows PowerShell 執行時間的內容中工作。 如需 aboutWindows PowerShell 提供程式的詳細資訊，請參閱[Windows powershell 程式空間](https://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9)。
