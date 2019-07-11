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
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733745"
---
# <a name="windows-powershell-reference"></a>Windows PowerShell 參考

Windows PowerShell 是 Microsoft.NET Framework 連線環境專為系統管理自動化。 Windows PowerShell 提供建置命令、 撰寫的解決方案，和建立圖形化使用者介面為基礎的管理工具的新方法。

Windows PowerShell 可讓系統管理員命令執行所進行自動化管理系統資源的直接或透過指令碼。

## <a name="developer-audience"></a>開發人員對象

Windows PowerShell 軟體開發套件 (SDK) 會寫入命令可供開發人員需要 Windows PowerShell 所提供的 Api 的參考資訊。 命令的開發人員會使用 Windows PowerShell 來建立命令和提供者擴充可由 Windows PowerShell 執行的工作。

## <a name="windows-powershell-resources"></a>Windows PowerShell 的資源

Windows PowerShell SDK 中，除了下列資源會提供詳細資訊。

[開始使用 Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)提供 Windows PowerShell 簡介︰ 語言、 cmdlet、 提供者，以及使用的物件。

[撰寫 Windows PowerShell 模組](./module/writing-a-windows-powershell-module.md)提供給系統管理員、 指令碼的開發人員，想要封裝及散發 Windows PowerShell 解決方案使用 Windows PowerShell 模組 cmdlet 開發人員的資訊和範例。

[撰寫 Windows PowerShell Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md)設計 cmdlet 的程式管理員和開發人員會實作指令程式的程式碼，提供資訊和程式碼範例。

[Windows PowerShell 小組部落格](https://blogs.msdn.microsoft.com/PowerShell/)一起學習及其他 Windows PowerShell 使用者一起共同作業的最佳資源。 閱讀 Windows PowerShell 小組部落格，並加入 Windows PowerShell 使用者論壇 (microsoft.public.windows.powershell)。 您可以使用 Windows Live Search 來尋找其他 Windows PowerShell 部落格和資源。 然後，當您開發您的專業知識，自由貢獻您的想法。

[PowerShell 模組瀏覽器](/powershell/module/)提供命令列的 [說明] 主題的最新版本。

## <a name="class-libraries"></a>類別庫

[System.Management.Automation](/dotnet/api/System.Management.Automation)這個命名空間是適用於 Windows PowerShell 的根命名空間。 它包含類別、 列舉和介面需要實作自訂的 cmdlet。 特別是， [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)類別是類別必須衍生自的所有指令程式的基底類別。 如需有關 cmdlet 的詳細資訊，請參閱。

[System.Management.Automation.Provider](/dotnet/api/System.Management.Automation.Provider)這個命名空間包含類別、 列舉和實作的 Windows PowerShell 提供者所需的介面。 特別是， [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)類別是從哪一個所有的 Windows PowerShell 提供者類別必須衍生的基底類別。

[Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands)這個命名空間包含的 cmdlet 與提供者藉由將 Windows PowerShell 的類別。 同樣地，建議您建立*YourName*。針對您所實作的 cmdlet 的命令命名空間。

[System.Management.Automation.Host](/dotnet/api/System.Management.Automation.Host)這個命名空間包含類別、 列舉和介面，此 cmdlet 會使用來定義使用者與 Windows PowerShell 之間的互動。

[System.Management.Automation.Internal](/dotnet/api/System.Management.Automation.Internal)這個命名空間包含命名空間中的其他類別所使用的基底類別。 例如， [System.Management.Automation.Internal.Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute)類別是基底類別[System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)類別。

[System.Management.Automation.Runspaces](/dotnet/api/System.Management.Automation.Runspaces)這個命名空間包含類別、 列舉和介面，可用來建立 Windows PowerShell runspace。 在此情況下，Windows PowerShell runspace 會是一或多個 Windows PowerShell 管線叫用 cmdlet 的內容。 亦即，cmdlet 運作的 Windows PowerShell runspace 的內容中。 如需詳細資訊 aboutWindows PowerShell runspace，請參閱 < [Windows PowerShell Runspace](https://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9)。
