---
description: 說明 PowerShell 中輸出資料流程的可用性和用途。
keywords: PowerShell，Cmdlet
Locale: en-US
ms.date: 10/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_output_streams?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Output_Streams
ms.openlocfilehash: 03b908406d9d2555479e511245ea1838d7774443
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208528"
---
# <a name="about-output-streams"></a>關於輸出資料流程

## <a name="short-description"></a>簡短描述
說明 PowerShell 中輸出資料流程的可用性和用途。

## <a name="long-description"></a>完整描述

PowerShell 提供多個輸出資料流程。 資料流程會針對不同類型的訊息提供通道。 您可以使用相關聯的 Cmdlet 或重新導向來寫入這些資料流程。 如需詳細資訊，請參閱 [about_Redirection](about_Redirection.md)。

PowerShell 支援下列輸出資料流程。

| 流# |      Description       | 引進于  |    Write Cmdlet     |
| -------- | ---------------------- | -------------- | ------------------- |
| 1        | **成功** 串流     | PowerShell 2.0 | `Write-Output`      |
| 2        | **錯誤** 資料流程       | PowerShell 2.0 | `Write-Error`       |
| 3        | **警告** 資料流程     | PowerShell 3.0 | `Write-Warning`     |
| 4        | **詳細** 資訊串流     | PowerShell 3.0 | `Write-Verbose`     |
| 5        | **Debug** 資料流程       | PowerShell 3.0 | `Write-Debug`       |
| 6        | **資訊** 資料流程 | PowerShell 5.0 | `Write-Information` |
| n/a      | **進度** 資料流程    | PowerShell 3.0 | `Write-Progress`    |

> [!NOTE]
> **進度** 資料流程不支援重新導向。

## <a name="success-stream"></a>成功串流

**成功** 資料流程是正常成功結果的預設資料流程。
使用 `Write-Output` Cmdlet 明確地將物件寫入此資料流程。 此資料流程用於透過 PowerShell 管線傳遞物件。 **成功** 資料流程會連接到原生應用程式的 **stdout** 資料流程。

## <a name="error-stream"></a>錯誤資料流程

**錯誤** 資料流程是錯誤結果的預設資料流程。 使用 `Write-Error` Cmdlet 明確寫入此資料流程。 **錯誤** 資料流程會連接到原生應用程式的 **stderr** 資料流程。 在大部分的情況下，這些錯誤可能會終止執行管線。 寫入此資料流程的錯誤也會新增至 `$Error` 自動變數。 如需詳細資訊，請參閱 [about_Automatic_Variables](about_Automatic_Variables.md)。

## <a name="warning-stream"></a>警告資料流程

**警告** 資料流程適用于比寫入 **錯誤** 資料流程的錯誤更不嚴重的錯誤狀況。 在正常情況下，這些警告不會終止執行。 警告不會寫入 `$Error` 自動變數中。 使用 `Write-Warning` Cmdlet 明確寫入此資料流程。

## <a name="verbose-stream"></a>詳細資訊資料流

**詳細** 資訊資料流程適用于協助使用者以互動方式執行命令或從腳本執行命令的訊息。 使用 `Write-Verbose` Cmdlet 明確地將訊息寫入此資料流程。 許多 Cmdlet 都提供詳細資訊輸出，有助於瞭解 Cmdlet 的內部運作方式。 只有當您使用一般參數時，才會輸出詳細資訊訊息 `-Verbose` 。 如需詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。

## <a name="debug-stream"></a>偵錯資料流

**調試** 程式資料流程用於協助腳本設計師瞭解其程式碼失敗原因的訊息。 使用 `Write-Debug` Cmdlet 明確寫入此資料流程。 只有當您使用一般參數時，才會輸出 debug 訊息 `-Debug` 。 如需詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。

Debug 訊息適用于比一般使用者更多的腳本和 Cmdlet 開發人員。 這些偵錯工具訊息可能包含深度疑難排解所需的內部詳細資料。

## <a name="information-stream"></a>資訊資料流程

**資訊** 資料流程旨在提供訊息，協助使用者瞭解腳本的作用。 開發人員也可以使用它當做額外的資料流程，用來透過 PowerShell 傳遞資訊。 開發人員可以標記串流資料，並具有該資料流程的特定處理。 使用 `Write-Information` Cmdlet 明確寫入此資料流程。

## <a name="progress-stream"></a>進度資料流程

**進度** 資料流程是用於傳達長時間執行命令和腳本之進度的訊息。 使用 `Write-Progress` Cmdlet 明確地將訊息寫入此資料流程。 **進度** 資料流程不支援重新導向。

## <a name="see-also"></a>另請參閱

- [Write-Debug](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [Write-Error](xref:Microsoft.PowerShell.Utility.Write-Error)
- [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host)
- [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)
- [Write-Output](xref:Microsoft.PowerShell.Utility.Write-Output)
- [Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [about_CommonParameters](about_CommonParameters.md)
- [about_Redirection](about_Redirection.md)
