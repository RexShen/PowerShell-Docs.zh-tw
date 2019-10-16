---
title: 自訂主機範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367507"
---
# <a name="custom-host-samples"></a>自訂主機範例

本節包含用來撰寫自訂主機的範例程式碼。 您可以使用 Microsoft Visual Studio 建立主控台應用程式，然後將此區段中的主題中的程式碼複製到您的主應用程式。

## <a name="in-this-section"></a>在本節中

 [Host01 範例](./host01-sample.md)這個範例示範如何執行使用基本自訂主機的主應用程式。

 [Host02 範例](./host02-sample.md)這個範例示範如何撰寫使用 Windows PowerShell 執行時間以及自訂主機執行的主應用程式。 主應用程式會將主機文化特性設定為德文、執行[取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process)Cmdlet 並顯示結果，就像您使用 pwrsh 所看到的一樣，然後以德文印出目前的資料和時間。

 [Host03 範例](./host03-sample.md)這個範例示範如何建立互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後將結果顯示在主控台中。

 [Host04 範例](./host04-sample.md)這個範例示範如何建立互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後將結果顯示在主控台中。 這個主應用程式也支援顯示允許使用者指定多個選項的提示。

 [Host05 範例](./host05-sample.md)這個範例示範如何建立互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後將結果顯示在主控台中。 此主機應用程式也支援使用[輸入-pssession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession)和[Exit-pssession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) Cmdlet 呼叫遠端電腦

 [Host06 範例](./host06-sample.md)這個範例示範如何建立互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後將結果顯示在主控台中。 此外，這個範例會使用權杖化工具 API 指定使用者所輸入的文字色彩。

## <a name="see-also"></a>另請參閱
