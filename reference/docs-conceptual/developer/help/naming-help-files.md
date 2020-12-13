---
ms.date: 09/12/2016
ms.topic: reference
title: 為說明檔案命名
description: 為說明檔案命名
ms.openlocfilehash: b77af8f9b9510785a4198fed9da1263184a27b99
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667584"
---
# <a name="naming-help-files"></a>為說明檔案命名

本主題說明如何命名以 XML 為基礎的說明檔，讓 [get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet 可以找到它。 每個命令類型的名稱需求各不相同。

## <a name="cmdlet-help-files"></a>Cmdlet 說明檔

C # Cmdlet 的說明檔必須針對已定義 Cmdlet 的元件命名。 使用下列檔案名格式：

```
<AssemblyName>.dll-help.xml
```

即使元件是嵌套模組，也需要元件名稱格式。

例如， [new-winevent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) 指令程式是在 Microsoft.PowerShell.Diagnostics.dll 元件中定義。 此 `Get-Help` Cmdlet `Get-WinEvent` 只會在模組目錄的檔案中尋找 Cmdlet 的說明主題 `Microsoft.PowerShell.Diagnostics.dll-help.xml` 。

## <a name="provider-help-files"></a>提供者說明檔

PowerShell 提供者的說明檔必須針對定義提供者的元件進行命名。 使用下列檔案名格式：

`<AssemblyName>.dll-help.xml`

即使元件是嵌套模組，也需要元件名稱格式。

例如，憑證提供者是在元件中定義 `Microsoft.PowerShell.Security.dll` 。 此 `Get-Help` Cmdlet 只會在模組目錄的檔案中尋找憑證提供者的說明主題 `Microsoft.PowerShell.Security.dll-help.xml` 。

## <a name="function-help-files"></a>函數說明檔

您可以使用以 [批註為基礎的說明](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) 或 XML 說明檔中記載的功能來記錄函式。 當函式記載于 XML 檔案時，函式必須有 `.ExternalHelp` 批註關鍵字，才能將函式與 xml 檔案產生關聯。 否則，此 Cmdlet 找不到說明檔 `Get-Help` 。

函數說明檔的名稱沒有任何技術需求。 不過，最佳作法是為定義函數的腳本模組命名說明檔。 例如，在檔案中定義了下列函數 `MyModule.psm1` 。

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>CIM 命令說明檔

CIM 命令的說明檔必須針對已定義 CIM 命令的 CDXML 檔案命名。 使用下列檔案名格式：

`<FileName>.cdxml-help.xml`

CIM 命令會定義在可包含在模組中做為嵌套模組的 CDXML 檔案中。 當 CIM 命令以函式的形式匯入會話時，PowerShell 會將 `.ExternalHelp` comment 關鍵字加入至函式定義，此定義會將函式與 XML 說明檔建立關聯，該檔案是針對定義 CIM 命令的 CDXML 檔案命名。

## <a name="script-workflow-help-files"></a>編寫工作流程說明檔的腳本

模組中所包含的腳本工作流程可以記錄在以 XML 為基礎的說明檔中。 說明檔的名稱沒有技術需求。 不過，最佳作法是為腳本模組命名定義腳本工作流程的說明檔。 例如：

`<ScriptModule>.psm1-help.xml`

不同于其他已編寫腳本的命令，腳本工作流程不需要 `.ExternalHelp` comment 關鍵字，就可以將它們與說明檔產生關聯。 相反地，PowerShell 會在模組目錄的 UI 文化特性特定子目錄中搜尋 XML 的說明檔，並在所有檔案中尋找腳本工作流程的說明。 `.ExternalHelp` 忽略批註關鍵字。

因為 `.ExternalHelp` 會忽略 comment 關鍵字，所以 `Get-Help` 只有當腳本包含在模組中時，Cmdlet 才可以找到腳本工作流程的說明。
