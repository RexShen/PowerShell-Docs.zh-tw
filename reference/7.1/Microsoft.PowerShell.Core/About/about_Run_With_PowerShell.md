---
description: 說明如何使用「使用 PowerShell 執行」功能，從檔案系統磁片磁碟機執行腳本。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_run_with_powershell?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Run_With_PowerShell
ms.openlocfilehash: 83931fcfcc89340b1d4958e41cb182642a554737
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208144"
---
# <a name="about-run-with-powershell"></a>關於使用 PowerShell 執行

## <a name="short-description"></a>簡短描述
說明如何使用「使用 PowerShell 執行」功能，從檔案系統磁片磁碟機執行腳本。

## <a name="long-description"></a>詳細描述

從 Windows PowerShell 3.0 開始，您可以使用「使用 PowerShell 執行」功能，從 Windows 8 和 Windows Server 2012 中的檔案總管，以及舊版 Windows 中的 Windows 檔案總管執行腳本。

「使用 PowerShell 執行」功能的設計目的是要執行沒有必要參數的腳本，而不會將輸出傳回命令提示字元。

當您使用「使用 PowerShell 執行」功能時，PowerShell 主控台視窗只會短暫顯示（如果有的話）。 您無法與其互動。

若要使用「使用 PowerShell 執行」功能：

在檔案總管 (或 Windows 檔案總管) 的指令檔名上按一下滑鼠右鍵，然後選取 [使用 PowerShell 執行]。

[以 PowerShell 執行] 功能會啟動具有 [略過] 執行原則的 PowerShell 會話，然後執行腳本並關閉會話。

它會執行具有下列格式的命令：

```
PowerShell.exe -File <FileName> -ExecutionPolicy Bypass
```

「使用 PowerShell 執行」會針對會話 (設定腳本執行) 的目前 PowerShell 進程實例的略過執行原則。
這項功能不會變更電腦或使用者的執行原則。

只有 AllSigned 執行原則會影響「使用 PowerShell 執行」功能。 如果電腦或使用者的 AllSigned 執行原則是有效的，「使用 PowerShell 執行」就只會執行已簽署的腳本。 「使用 PowerShell 執行」不會受到任何其他執行原則的影響。 如需詳細資訊，請參閱 [about_Execution_Policies](about_Execution_Policies.md)。

疑難排解注意事項：以 PowerShell 執行命令可能會提示您確認執行原則變更。

## <a name="see-also"></a>另請參閱

[about_Execution_Policies](about_Execution_Policies.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Scripts](about_Scripts.md)

