---
title: Cmdlet 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365877"
---
# <a name="cmdlet-samples"></a>Cmdlet 範例

本節說明 Windows PowerShell 2.0 SDK 中提供的範例程式碼。 您可以從本節的主題複製程式碼，或開啟隨 SDK 安裝的原始程式檔。 [Windows PowerShell 2.0 軟體發展工具組（SDK）](https://www.microsoft.com/en-us/download/details.aspx?id=2560)會提供每個範例的讀我檔案、原始程式檔和 Visual Studio 專案檔案。 安裝 SDK 之後，您可以在 [`<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`] 資料夾底下找到範例。

## <a name="in-this-section"></a>在本節中

[GetProcessSample01 範例](./getprocesssample01-sample.md)這個範例會示範如何撰寫 Cmdlet 來抓取本機電腦上的處理常式。

[GetProcessSample02 範例](./getprocesssample02-sample.md)這個範例會示範如何撰寫 Cmdlet 來抓取本機電腦上的處理常式。 它會提供名稱參數，可用來指定要抓取的進程。

[GetProcessSample03 範例](./getprocesssample03-sample.md)這個範例會示範如何撰寫 Cmdlet 來抓取本機電腦上的處理常式。 它所提供的 Name 參數可以接受來自管線的物件，或是從屬性名稱與參數名稱相同的物件屬性值。

[GetProcessSample04 範例](./getprocesssample04-sample.md)這個範例會示範如何撰寫 Cmdlet 來抓取本機電腦上的處理常式。 如果在抓取進程時發生錯誤，就會產生非終止錯誤。

[GetProcessSample05 範例](./getprocesssample05-sample.md)這個範例會顯示完整版的 Get Proc Cmdlet。

[StopProcessSample01 範例](./stopprocesssample01-sample.md)這個範例會示範如何撰寫 Cmdlet，以在嘗試停止進程之前要求使用者提供意見反應，以及如何執行 `PassThru` 參數，表示使用者想要 Cmdlet 傳回物件。

[StopProcessSample02 範例](./stopprocesssample02-sample.md)這個範例示範如何撰寫 Cmdlet，以在停止本機電腦上的處理常式時寫入 debug、verbose 和警告訊息。

[StopProcessSample03 範例](./stopprocesssample03-sample.md)這個範例示範如何撰寫 Cmdlet，其參數具有可支援萬用字元的別名和。

[StopProcessSample04 範例](./stopprocesssample04-sample.md)這個範例會示範如何撰寫宣告參數集的 Cmdlet、指定預設參數集，以及接受輸入物件。

[Events01 範例](./events01-sample.md)這個範例示範如何建立 Cmdlet，讓使用者註冊[Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher)所引發的事件。 例如，使用此 Cmdlet 時，使用者可以在特定目錄下建立檔案時，註冊要執行的動作。 這個範例是衍生自[自 objecteventregistrationbase Cmdlet](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)基類。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
