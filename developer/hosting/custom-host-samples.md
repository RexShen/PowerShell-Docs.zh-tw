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
ms.openlocfilehash: 2d88847e17371c4c04b783569fbd983218b6791b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858614"
---
# <a name="custom-host-samples"></a>自訂主機範例

本節包含範例程式碼撰寫自訂主機。 您可以使用 Microsoft Visual Studio 來建立主控台應用程式，然後將從這一節的主題的程式碼複製到主應用程式。

## <a name="in-this-section"></a>在本節中

 [Host01 範例](./host01-sample.md)這個範例示範如何實作使用基本的自訂主機的主機應用程式。

 [Host02 範例](./host02-sample.md)這個範例示範如何撰寫使用 Windows PowerShell 執行階段，以及自訂主機實作的主應用程式。 主應用程式設定為德文、 執行的主控件的文化特性[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet，並顯示結果，您會看到它們以德文使用 pwrsh.exe，然後列印目前的日期和時間。
此範例示範如何撰寫使用 Windows PowerShell 執行階段，以及自訂主機實作的主應用程式。 主應用程式設定為德文、 執行的主控件的文化特性[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet，並顯示結果，您會看到它們以德文使用 pwrsh.exe，然後列印目前的日期和時間。

 [Host03 範例](./host03-sample.md)這個範例示範如何建置互動式主控台主機應用程式，從命令列讀取命令、 執行命令，然後在主控台中顯示結果。

 [Host04 範例](./host04-sample.md)這個範例示範如何建置互動式主控台主機應用程式，從命令列讀取命令、 執行命令，然後在主控台中顯示結果。 這個主應用程式也支援顯示允許使用者指定多個選項的提示。

 [Host05 範例](./host05-sample.md)這個範例示範如何建置互動式主控台主機應用程式，從命令列讀取命令、 執行命令，然後在主控台中顯示結果。 這個主應用程式也支援呼叫遠端電腦使用[Enter-pssession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession)並[Exit-pssession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlet，此範例示範如何建置互動式主控台主機應用程式從命令列讀取命令、 執行命令，，然後在主控台中顯示結果。 這個主應用程式也支援呼叫遠端電腦使用[Enter-pssession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession)並[Exit-pssession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlet

 [Host06 範例](./host06-sample.md)這個範例示範如何建置互動式主控台主機應用程式，從命令列讀取命令、 執行命令，然後在主控台中顯示結果。 此外，這個範例會使用權杖化工具 API 指定使用者所輸入的文字色彩。

## <a name="see-also"></a>另請參閱
