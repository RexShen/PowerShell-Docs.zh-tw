---
title: 附錄 A - 說明語法
description: 本文說明如何閱讀和了解使用 Get-Help 所呈現的 Cmdlet 語法。
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: e8e28f66c02370b098f63a0396ef8a724cf3a1bd
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84437979"
---
# <a name="appendix-a---help-syntax"></a>附錄 A - 說明語法

下列範例顯示 `Get-EventLog` Cmdlet 說明的 **SYNTAX** 區段。

```powershell
help Get-EventLog
```

```Output
NAME
    Get-EventLog

SYNOPSIS
    Gets the events in an event log, or a list of the event logs, on the local or remote
    computers.


SYNTAX
    Get-EventLog [-LogName] <String> [[-InstanceId] <Int64[]>] [-After <DateTime>]
    [-AsBaseObject] [-Before <DateTime>] [-ComputerName <String[]>] [-EntryType {Error |
    Information | FailureAudit | SuccessAudit | Warning}] [-Index <Int32[]>] [-Message
    <String>] [-Newest <Int32>] [-Source <String[]>] [-UserName <String[]>]
    [<CommonParameters>]

    Get-EventLog [-AsString] [-ComputerName <String[]>] [-List] [<CommonParameters>]
```

此範例中只顯示說明的相關部分。

語法主要由數組左右方括弧 (`[]`) 組成。 根據其使用方式而定，會有兩個不同的意義。 包含在方括弧內的任何項目都是選擇性的，除非它們是一組空的方括弧 `[]`。 只有在 `<string[]>` 之類的資料類型之後，才會出現空的方括弧。 這表示特定參數可以接受一個以上該類型的值。

`Get-EventLog` 的第一個參數集中的第一個參數是 **LogName**。 LogName 是用方括弧括住，這表示它是位置參數。 換句話說，只要已在正確的位置指定，那麼指定參數本身的名稱就會是選擇性。 參數名稱後面角括弧 (`<>`) 中的資訊指出它需要單一**字串**值。 整個參數名稱和資料類型不會以方括弧括住，因此使用此參數集時，需要 **LogName** 參數。

```powershell
Get-EventLog [-LogName] <String>
```

第二個參數是 **InstanceId**。 請注意，參數名稱和資料類型都完全以方括弧括住。 這表示 **InstanceId** 參數是選擇性的，不是強制的。 也請注意，**InstanceId** 是以自己的一組方括弧括住。 如同使用 **LogName** 參數，這表示參數具位置性。 資料類型後面有最後的一組方括弧。 這表示它可以接受陣列或逗號分隔清單格式的一個以上值。

```
[[-InstanceId] <Int64[]>]
```

第二個參數集具有 **List** 參數。 因為參數名稱後面沒有資料類型，所以它是切換參數。 指定 **List** 參數時，此值為 **True**。 若未指定，則值為 **False**。

```
[-List]
```

您也可以使用 **Syntax** 參數，使用 `Get-Command` 來擷取命令的語法資訊。 這是我經常會使用的便利捷徑。 它可讓我快速了解如何使用命令，而不需要篩檢多頁的說明資訊。 如果最後需要更多資訊，我將會還原為使用實際的說明內容。

```powershell
Get-Command -Name Get-EventLog -Syntax
```

```Output
Get-EventLog [-LogName] <string> [[-InstanceId] <long[]>] [-ComputerName <string[]>] [-Newest <int>]
 [-After <datetime>] [-Before <datetime>] [-UserName <string[]>] [-Index <int[]> ]
 [-EntryType <string[]>] [-Source <string[]>] [-Message <string>] [-AsBaseObject]
 [<CommonParameters>]

Get-EventLog [-ComputerName <string[]>] [-List] [-AsString] [<CommonParameters>]
```

您在 PowerShell 中使用說明系統的情況越多，就會更容易記住所有不同的細節。 當您發現時，使用它已變成您的第二個本質了。
