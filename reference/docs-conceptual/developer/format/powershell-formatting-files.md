---
title: Windows PowerShell 格式化檔案 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 54fae12163f8d439c2acc24df17ed140a556cba0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783495"
---
# <a name="windows-powershell-formatting-files"></a>Windows PowerShell 格式設定檔案

Windows PowerShell 提供數個格式檔案 ( # B0 xml) 位於安裝目錄 (`$pshome`) 。 這些檔案中的每一個都會定義一組特定 .NET 物件的預設顯示。 這些檔案永遠不會變更。 不過，您可以使用它們做為參考，以建立您自己的自訂格式檔案。

`Certificate.Format.ps1xml`定義憑證存放區中的物件顯示，例如 x.509 憑證和憑證存放區。

`DotNetTypes.Format.ps1xml`定義其他 .NET 物件的顯示，例如 CultureInfo、FileVersionInfo 和 EventLogEntry 物件。

`FileSystem.Format.ps1xml`定義檔案系統物件（例如檔案和目錄物件）的顯示方式。

`Help.Format.ps1xml`定義[get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet 使用的不同視圖，例如詳細、完整、參數和範例視圖。

`PowerShellCore.Format.ps1xml`定義 Windows PowerShell 核心 Cmdlet 所產生之物件的顯示方式，例如由[取得成員](/powershell/module/Microsoft.PowerShell.Utility/Get-Member)和[取得歷程記錄](/powershell/module/Microsoft.PowerShell.Core/Get-History)Cmdlet 傳回的物件。

`PowerShellTrace.Format.ps1xml`定義追蹤物件的顯示，如[Trace 命令](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command)Cmdlet 所產生的。

`Registry.Format.ps1xml`定義登錄物件（例如金鑰和專案物件）的顯示。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)
