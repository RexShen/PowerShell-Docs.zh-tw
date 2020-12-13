---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 範例
description: Cmdlet 範例
ms.openlocfilehash: 6ee149f611e5af5c45a62363e19e66bf200c0c0a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668247"
---
# <a name="cmdlet-samples"></a>Cmdlet 範例

此節描述 Windows PowerShell 2.0 SDK 中提供的範例程式碼。 您可以從此節的主題複製程式碼，或開啟隨 SDK 安裝的原始程式檔。 [Windows PowerShell 2.0 軟體開發工具組 (SDK)](https://www.microsoft.com/download/details.aspx?id=2560) 提供每個範例的讀我檔案、原始程式檔與 Visual Studio 專案檔。 安裝 SDK 之後，您可以在 `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` 資料夾底下找到範例。

## <a name="in-this-section"></a>本節內容

[GetProcessSample01 範例](./getprocesssample01-sample.md) 此範例示範如何撰寫 Cmdlet 來擷取本機電腦上的處理序。

[GetProcessSample02 範例](./getprocesssample02-sample.md) 此範例示範如何撰寫 Cmdlet 來擷取本機電腦上的處理序。 其提供 Name 參數，可用來指定要擷取的處理序。

[GetProcessSample03 範例](./getprocesssample03-sample.md) 此範例示範如何撰寫 Cmdlet 來擷取本機電腦上的處理序。 其提供 Name 參數，此參數接受來自管線的物件，或屬性名稱與參數名稱相同之物件的屬性值。

[GetProcessSample04 範例](./getprocesssample04-sample.md) 此範例示範如何撰寫 Cmdlet 來擷取本機電腦上的處理序。 如果其在擷取處理序時發生錯誤，會產生非終止錯誤。

[GetProcessSample05 範例](./getprocesssample05-sample.md) 此範例會顯示完整版的 Get-Proc Cmdlet。

[StopProcessSample01 範例](./stopprocesssample01-sample.md) 此範例示範如何撰寫 Cmdlet，以在嘗試停止處理序之前要求使用者提供意見反應，並示範如何實作 `PassThru` 參數以指出使用者想要 Cmdlet 傳回物件。

[StopProcessSample02 範例](./stopprocesssample02-sample.md) 此範例示範如何撰寫 Cmdlet，以在停止本機電腦上的處理序時寫入偵錯、詳細與警告訊息。

[StopProcessSample03 範例](./stopprocesssample03-sample.md) 此範例示範如何撰寫其參數具有別名且支援萬用字元的 Cmdlet。

[StopProcessSample04 範例](./stopprocesssample04-sample.md) 此範例示範如何撰寫可宣告參數集、指定預設參數集且可接受輸入物件的 Cmdlet。

[Events01 範例](./events01-sample.md) 此範例示範如何建立 Cmdlet，以讓使用者註冊 [Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher) 所引發的事件。 例如，使用者可以使用此 Cmdlet 來註冊當特定目錄下有檔案建立時要執行的動作。 此範例衍生自 [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) 基底類別。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
