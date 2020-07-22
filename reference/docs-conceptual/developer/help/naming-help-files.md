---
title: 為說明檔案命名
ms.date: 09/12/2016
ms.openlocfilehash: ea95e6d6c87e553ed11fe6e3f058fc9a1b3d03f8
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893266"
---
# <a name="naming-help-files"></a>為說明檔案命名

本主題說明如何命名以 XML 為基礎的說明檔，讓[get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet 可以找到它。 每個命令類型的名稱需求都不同。

## <a name="cmdlet-help-files"></a>Cmdlet 說明檔

C # Cmdlet 的說明檔必須命名為定義 Cmdlet 的元件。 請使用下列檔案名格式：

```
<AssemblyName>.dll-help.xml
```

即使元件是一個嵌套模組，也需要元件名稱格式。

例如， [new-winevent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)指令程式是在 Microsoft.PowerShell.Diagnostics.dll 元件中定義。 此 `Get-Help` Cmdlet `Get-WinEvent` 只會在模組目錄中的檔案尋找 Cmdlet 的說明主題 `Microsoft.PowerShell.Diagnostics.dll-help.xml` 。

## <a name="provider-help-files"></a>提供者說明檔

PowerShell 提供者的說明檔必須針對定義提供者的元件命名。 請使用下列檔案名格式：

`<AssemblyName>.dll-help.xml`

即使元件是一個嵌套模組，也需要元件名稱格式。

例如，憑證提供者是在元件中定義 `Microsoft.PowerShell.Security.dll` 。 此 `Get-Help` Cmdlet 只會在模組目錄中的檔案尋找憑證提供者的說明主題 `Microsoft.PowerShell.Security.dll-help.xml` 。

## <a name="function-help-files"></a>函數說明檔

您可以使用以[批註為基礎的說明](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)來記載函式，或在 XML 說明檔中記載函數。 當函式記載在 XML 檔案中時，函式必須有一個 `.ExternalHelp` comment 關鍵字，以將函式與 xml 檔案產生關聯。 否則，Cmdlet 就找不到說明檔 `Get-Help` 。

函數說明檔的名稱沒有任何技術需求。 不過，最佳作法是為定義函數的腳本模組命名說明檔。 例如，下列函式定義于檔案中 `MyModule.psm1` 。

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>CIM 命令說明檔

CIM 命令的說明檔必須針對定義 CIM 命令的 CDXML 檔案命名。 請使用下列檔案名格式：

`<FileName>.cdxml-help.xml`

CIM 命令定義于 CDXML 檔案中，這些檔案可以包含在模組中當做嵌套模組。 當 CIM 命令以函式的形式匯入會話時，PowerShell 會將 `.ExternalHelp` comment 關鍵字新增至函式定義，以將函式與為定義 CIM 命令的 CDXML 檔案所命名的 XML 說明檔產生關聯。

## <a name="script-workflow-help-files"></a>編寫工作流程說明檔的腳本

模組中所含的腳本工作流程可以記錄在以 XML 為基礎的說明檔中。 說明檔的名稱沒有任何技術需求。 不過，最佳作法是為定義腳本工作流程的腳本模組命名說明檔。 例如：

`<ScriptModule>.psm1-help.xml`

與其他已編寫腳本的命令不同的是，腳本工作流程並不需要 `.ExternalHelp` comment 關鍵字，就可以將它們與說明檔產生關聯。 相反地，PowerShell 會搜尋模組目錄的 UI 文化特性特定子目錄，以尋找 XML 架構的說明檔，並在所有檔案中尋找腳本工作流程的說明。 `.ExternalHelp`已忽略 comment 關鍵字。

由於 `.ExternalHelp` 已忽略 comment 關鍵字，因此， `Get-Help` 只有在模組中包含腳本工作流程時，Cmdlet 才能找到其說明。
