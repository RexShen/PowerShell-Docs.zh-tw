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
ms.openlocfilehash: d919d4ad8554e762230c1448d81b50e27c38ba99
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863364"
---
# <a name="cmdlet-samples"></a>Cmdlet 範例

本節描述 Windows PowerShell 2.0 SDK 中提供的範例程式碼。 您可以在此區段中，主題從程式碼複製，或開啟與 SDK 一起安裝的原始程式檔。 [Windows PowerShell 2.0 軟體開發套件 (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560)提供讀我檔案、 原始程式檔，以及每個範例的 Visual Studio 專案檔。 已安裝 sdk，您可以找到下的範例`<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`資料夾。

## <a name="in-this-section"></a>在本節中

[GetProcessSample01 範例](./getprocesssample01-sample.md)這個範例示範如何撰寫 cmdlet 來擷取本機電腦上的處理程序。

[GetProcessSample02 範例](./getprocesssample02-sample.md)這個範例示範如何撰寫 cmdlet 來擷取本機電腦上的處理程序。 它會提供可用來指定要擷取的處理程序的 Name 參數。

[GetProcessSample03 範例](./getprocesssample03-sample.md)這個範例示範如何撰寫 cmdlet 來擷取本機電腦上的處理程序。 它提供可接受來自管線的物件或從屬性名稱是參數名稱與相同物件的屬性值的 Name 參數。

[GetProcessSample04 範例](./getprocesssample04-sample.md)這個範例示範如何撰寫 cmdlet 來擷取本機電腦上的處理程序。 如果在擷取處理序時發生錯誤，它會產生非終止錯誤。

[GetProcessSample05 範例](./getprocesssample05-sample.md)這個範例會示範 Get-proc cmdlet 的完整版本。

[StopProcessSample01 範例](./stopprocesssample01-sample.md)這個範例示範如何撰寫的 cmdlet，向使用者要求意見反應之前它會嘗試停止處理程序，, 以及如何實作`PassThru`表示使用者想要傳回 cmdlet 的參數物件。

[StopProcessSample02 範例](./stopprocesssample02-sample.md)這個範例示範如何撰寫的 cmdlet，將寫入 verbose、 debug 和警告訊息，同時在本機電腦上停止處理程序。

[StopProcessSample03 範例](./stopprocesssample03-sample.md)這個範例示範如何撰寫的 cmdlet 的參數有別名，支援萬用字元。

[StopProcessSample04 範例](./stopprocesssample04-sample.md)這個範例示範如何撰寫 cmdlet 會宣告參數集，請指定預設參數設定，以及可接受輸入的物件。

[Events01 範例](./events01-sample.md)這個範例示範如何建立所引發的事件可讓使用者註冊的 cmdlet [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher)。 搭配這個指令程式使用者可以比方說，註冊特定的目錄下建立檔案時要執行的動作。 此範例衍生自[Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)基底類別。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
