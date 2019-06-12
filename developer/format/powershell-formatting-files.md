---
title: Windows PowerShell 格式化檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 3ec127d5ff60754de5d7f1ac73f2965524228b9c
ms.sourcegitcommit: 4ec9e10647b752cc62b1eabb897ada3dc03c93eb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830252"
---
# <a name="windows-powershell-formatting-files"></a>Windows PowerShell 格式設定檔案

Windows PowerShell 提供數個格式化檔案 (。 format.ps1xml)，位於安裝目錄 (`$pshome`)。 每個檔案會定義一組特定的.NET 物件的預設顯示。 這些檔案應該永遠不會變更。 不過，您可以使用它們做為參考來建立您自己自訂的格式檔案。

`Certificate.Format.ps1xml` 定義物件的顯示，例如 x.509 憑證的憑證存放區和憑證存放區中。

`DotNetTypes.Format.ps1xml` 定義其他的.NET 物件，例如 CultureInfo、 FileVersionInfo 和 EventLogEntry 物件的顯示。

`FileSystem.Format.ps1xml` 定義檔案系統物件，例如檔案和目錄物件的顯示。

`Help.Format.ps1xml` 定義所使用的不同檢視[Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet，例如全文、 參數和範例的詳細的檢視。

`PowerShellCore.Format.ps1xml` 定義的 Windows PowerShell 核心 cmdlet，例如所傳回的物件所產生的物件顯示[Get-member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member)並[Get-history](/powershell/module/Microsoft.PowerShell.Core/Get-History) cmdlet。

`PowerShellTrace.Format.ps1xml` 定義的追蹤物件，例如所產生的物件顯示[Trace-command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) cmdlet。

`Registry.Format.ps1xml` 定義登錄物件，例如索引鍵和項目物件的顯示。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)
