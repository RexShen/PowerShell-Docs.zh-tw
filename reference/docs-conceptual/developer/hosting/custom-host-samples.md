---
title: 自訂主機範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6a10d3da6d8bf93986a3f5b029fdae3afb23a903
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779517"
---
# <a name="custom-host-samples"></a>自訂主機範例

本節包含用來撰寫自訂主機的範例程式碼。 您可以使用 Microsoft Visual Studio 建立主控台應用程式，然後將此區段中的主題中的程式碼複製到您的主應用程式。

## <a name="in-this-section"></a>本節內容

 [Host01 範例](./host01-sample.md)這個範例示範如何執行使用基本自訂主機的主應用程式。

 [Host02 範例](./host02-sample.md)這個範例示範如何撰寫使用 Windows PowerShell 執行時間以及自訂主機執行的主應用程式。 主應用程式會將主機文化特性設定為德文、執行「[取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process)」 Cmdlet，並顯示您使用 pwrsh.exe 看到的結果，然後以德文印出目前的資料和時間。

 [Host03 範例](./host03-sample.md)這個範例示範如何建立互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後將結果顯示在主控台中。

 [Host04 範例](./host04-sample.md)這個範例示範如何建立互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後將結果顯示在主控台中。 這個主應用程式也支援顯示允許使用者指定多個選項的提示。

 [Host05 範例](./host05-sample.md)這個範例示範如何建立互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後將結果顯示在主控台中。 此主機應用程式也支援使用[輸入-pssession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession)和[Exit-pssession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) Cmdlet 呼叫遠端電腦

 [Host06 範例](./host06-sample.md)這個範例示範如何建立互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後將結果顯示在主控台中。 此外，這個範例會使用權杖化工具 API 指定使用者所輸入的文字色彩。

## <a name="see-also"></a>另請參閱
