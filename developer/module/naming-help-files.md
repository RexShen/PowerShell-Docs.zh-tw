---
title: 命名的說明檔 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: 06281a1260dbdc120867fce89e6d5c8dd0754b87
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856664"
---
# <a name="naming-help-files"></a>為說明檔案命名

本主題說明如何以 XML 為基礎的說明檔命名以便[Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help)指令程式可以找到它。 針對每個命令類型，不同的名稱需求。
本主題說明如何以 XML 為基礎的說明檔命名以便[Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help)指令程式可以找到它。 針對每個命令類型，不同的名稱需求。

## <a name="cmdlet-help-files"></a>指令程式說明檔

說明檔，以C#cmdlet 必須命名為 cmdlet 定義所在的組件。 使用下列的檔案名稱格式：

```
<AssemblyName>.dll-help.xml
```

即使在組件為巢狀的模組時，才需要的組件名稱格式。

比方說， [Get-winevent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) Microsoft.PowerShell.Diagnostics.dll 組件中所定義的 cmdlet。 `Get-Help` Cmdlet 會尋找說明主題`Get-WinEvent`只存在於 Microsoft.PowerShell.Diagnostics.dll help.xml 檔案，在模組目錄中的 cmdlet。
比方說， [Get-winevent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) Microsoft.PowerShell.Diagnostics.dll 組件中所定義的 cmdlet。 `Get-Help` Cmdlet 會尋找說明主題`Get-WinEvent`只存在於 Microsoft.PowerShell.Diagnostics.dll help.xml 檔案，在模組目錄中的 cmdlet。

## <a name="provider-help-files"></a>提供者的說明檔

定義提供者所在的組件名稱必須為 Windows PowerShell 提供者的說明檔。 使用下列的檔案名稱格式：

```
<AssemblyName>.dll-help.xml
```

即使在組件為巢狀的模組時，才需要的組件名稱格式。

例如，憑證提供者會定義 Microsoft.PowerShell.Security.dll 組件中。 `Get-Help` Cmdlet 尋找說明主題的憑證提供者只存在於 Microsoft.PowerShell.Security.dll help.xml 檔案，在模組目錄中。

## <a name="function-help-files"></a>函式的說明檔

可以使用記錄函式[註解型說明](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)或 XML 說明檔案中所述。 當函式會記載在 XML 檔案時，此函式必須`.ExternalHelp`註解關聯的 XML 檔案中的函式的關鍵字。 否則， `Get-Help` cmdlet 找不到說明檔。
可以使用記錄函式[註解型說明](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)或 XML 說明檔案中所述。 當函式會記載在 XML 檔案時，此函式必須`.ExternalHelp`註解關聯的 XML 檔案中的函式的關鍵字。 否則， `Get-Help` cmdlet 找不到說明檔。

沒有名稱的函式的說明檔的技術需求。 不過，最佳的作法是在其中定義函式的指令碼模組的說明檔的名稱。 例如，下列函式定義 MyModule.psm1 檔案中。

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>CIM 命令的說明檔

在其中定義 CIM 命令的 CDXML 檔案名稱必須為 CIM 命令的說明檔。 使用下列的檔案名稱格式：

```
<FileName>.cdxml-help.xml
```

CIM 命令可以包含做為巢狀模組的模組中的 CDXML 檔案中定義。 為函式的工作階段匯入 CIM 命令時，Windows PowerShell 會將新增`.ExternalHelp`定義 CIM 命令的 CDXML 檔案命名為關聯的 XML 說明中的函式的函式定義的關鍵字檔案的註解。

## <a name="script-workflow-help-files"></a>指令碼工作流程說明檔

在模組中包含的指令碼工作流程可以記錄以 XML 為基礎的說明檔案中。 沒有名稱的說明檔的技術需求。 不過，最佳的作法是在其中定義指令碼工作流程的指令碼模組的說明檔的名稱。 例如：

```
<ScriptModule>.psm1-help.xml
```

不需要其他指令碼與命令不同，指令碼工作流程`.ExternalHelp`註解將關聯的說明檔的關鍵字。 相反地，Windows PowerShell 搜尋 XML 為基礎的說明檔的模組目錄的 UI 文化特性專屬子目錄，並尋找指令碼中的工作流程的所有檔案的說明。 `.ExternalHelp` 註解的關鍵字會被忽略。

因為`.ExternalHelp`註解的關鍵字會被忽略，`Get-Help`指令程式可以尋找說明指令碼工作流程可以包含在模組時，才。