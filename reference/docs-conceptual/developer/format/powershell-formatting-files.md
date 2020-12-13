---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 格式設定檔案
description: Windows PowerShell 格式設定檔案
ms.openlocfilehash: 7fa58a3463dc4b2a23d38d161d83387744334d44
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666360"
---
# <a name="windows-powershell-formatting-files"></a>Windows PowerShell 格式設定檔案

Windows PowerShell 提供數個格式化檔案 ( # B0 xml) ，這些檔案位於安裝目錄 (`$pshome`) 。 每個檔案都會定義一組特定 .NET 物件的預設顯示。 這些檔案永遠不會變更。 不過，您可以使用它們作為建立您專屬自訂格式檔案的參考。

`Certificate.Format.ps1xml` 定義憑證存放區中的物件顯示，例如 x.509 憑證和憑證存放區。

`DotNetTypes.Format.ps1xml` 定義其他 .NET 物件的顯示，例如 CultureInfo、FileVersionInfo 和 EventLogEntry 物件。

`FileSystem.Format.ps1xml` 定義檔案系統物件（例如檔案和目錄物件）的顯示。

`Help.Format.ps1xml` 定義 [get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet 所使用的不同視圖，例如詳細、完整、參數和範例視圖。

`PowerShellCore.Format.ps1xml` 定義 Windows PowerShell 核心 Cmdlet 所產生之物件的顯示，例如 [取得成員](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) 和 [取得歷程記錄](/powershell/module/Microsoft.PowerShell.Core/Get-History) Cmdlet 所傳回的物件。

`PowerShellTrace.Format.ps1xml` 定義追蹤物件的顯示，例如 [追蹤命令](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) Cmdlet 所產生的物件。

`Registry.Format.ps1xml` 定義登錄物件的顯示，例如索引鍵和專案物件。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)
