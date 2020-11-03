---
description: 說明如何解讀遠端命令的輸出並設定其格式。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_output?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Output
ms.openlocfilehash: c5636a301017111adf97b6332237e737b4bf0716
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207924"
---
# <a name="about-remote-output"></a>關於遠端輸出

## <a name="short-description"></a>簡短描述

說明如何解讀遠端命令的輸出並設定其格式。

## <a name="long-description"></a>詳細描述

在遠端電腦上執行之命令的輸出看起來可能像是在本機電腦上執行相同命令的輸出，但是有一些重大差異。

本主題說明如何解讀、格式化和顯示在遠端電腦上執行之命令的輸出。

## <a name="displaying-the-computer-name"></a>顯示電腦名稱稱

當您使用 Invoke-Command Cmdlet 在遠端電腦上執行命令時，此命令會傳回物件，其中包含產生資料的電腦名稱稱。 遠端電腦名稱稱會儲存在 PSComputerName 屬性中。

針對許多命令，預設會顯示 PSComputerName。 例如，下列命令會在兩部遠端電腦（Server01 和 Server02）上執行 Get-Culture 命令。 輸出（如下所示）包含命令執行所在的遠端電腦名稱稱。

```powershell
C:\PS> invoke-command -script {get-culture} -comp Server01, Server02

LCID  Name    DisplayName                PSComputerName
----  ----    -----------                --------------
1033  en-US   English (United States)    Server01
1033  es-AR   Spanish (Argentina)        Server02
```

您可以使用 Invoke-Command 的 HideComputerName 參數來隱藏 PSComputerName 屬性。 此參數是針對只從一部遠端電腦收集資料的命令所設計。

下列命令會在 Server01 遠端電腦上執行 Get-Culture 命令。 它會使用 HideComputerName 參數來隱藏 PSComputerName 屬性和相關屬性。

```powershell
C:\PS> invoke-command -scr {get-culture} -comp Server01 -HideComputerName

LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

您也可以顯示 [PSComputerName] 屬性（如果預設未顯示）。

例如，下列命令會使用 Format-Table Cmdlet，將 PSComputerName 屬性新增至遠端 Get-Date 命令的輸出。

```powershell
$dates = invoke-command -script {get-date} -computername Server01, Server02
$dates | format-table DateTime, PSComputerName -auto

DateTime                            PSComputerName
--------                            --------------
Monday, July 21, 2008 7:16:58 PM    Server01
Monday, July 21, 2008 7:16:58 PM    Server02
```

## <a name="displaying-the-machinename-property"></a>顯示 MACHINENAME 屬性

數個指令程式（包括 Get 進程、Get-help 和 Get-help）都有 ComputerName 參數，可取得遠端電腦上的物件。
這些 Cmdlet 不會使用 Windows PowerShell 遠端功能，因此您甚至可以在未設定為在 Windows PowerShell 中進行遠端處理的電腦上使用它們。

這些 Cmdlet 傳回的物件會將遠端電腦的名稱儲存在 MachineName 屬性中。  (這些物件沒有 PSComputerName 屬性。 ) 

例如，此命令會取得 Server01 和 Server02 遠端電腦上的 PowerShell 處理常式。 預設顯示不包含 MachineName 屬性。

```powershell
C:\PS> get-process PowerShell -computername server01, server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
920      38    97524     114504   575     9.66   2648 PowerShell
194       6    24256      32384   142            3020 PowerShell
352      27    63472      63520   577     3.84   4796 PowerShell
```

您可以使用 Format-Table Cmdlet 顯示處理常式物件的 MachineName 屬性。

例如，下列命令會將處理常式儲存在 $p 變數中，然後使用管線運算子 (|) 將 $p 中的處理常式傳送至 Format-Table 命令。 命令使用 Format-Table 的 Property 參數將 MachineName 屬性包含在顯示中。

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02
C:\PS> $P | format-table -property ID, ProcessName, MachineName -auto

Id ProcessName MachineName
-- ----------- -----------
2648 PowerShell  Server02
3020 PowerShell  Server01
4796 PowerShell  Server02
```

下列更複雜的命令會將 MachineName 屬性新增至預設進程顯示。 它會使用雜湊表來指定計算屬性。 幸運的是，您不需要瞭解它的使用方式。

 (請注意，倒引號 ['] 是接續字元。 ) 

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02

C:\PS> $p | format-table -property Handles, `
@{Label="NPM(K)";Expression={int}}, `
@{Label="PM(K)";Expression={int}}, `
@{Label="WS(K)";Expression={int}}, `
@{Label="VM(M)";Expression={int}}, `
@{Label="CPU(s)";Expression={if ($.CPU -ne $()){ $.CPU.ToString("N")}}}, `
Id, ProcessName, MachineName -auto

Handles NPM(K) PM(K)  WS(K) VM(M) CPU(s)   Id ProcessName MachineName
------- ------ -----  ----- ----- ------   -- ----------- -----------
920     38 97560 114532   576        2648 PowerShell  Server02
192      6 24132  32028   140        3020 PowerShell  Server01
438     26 48436  59132   565        4796 PowerShell  Server02

```

## <a name="deserialized-objects"></a>還原序列化的物件

當您執行會產生輸出的遠端命令時，命令輸出會在網路上傳輸回本機電腦。

因為大部分的即時 Microsoft .NET Framework 物件 (例如 Windows PowerShell Cmdlet 傳回的物件) 無法透過網路傳輸，所以即時物件會「序列化」。 換句話說，即時物件會轉換成物件和其屬性的 XML 標記法。 然後，會在網路上傳輸以 XML 為基礎的序列化物件。

在本機電腦上，Windows PowerShell 會接收以 xml 為基礎的序列化物件，並將 XML 型物件轉換成標準的 .NET Framework 物件，以將它「還原序列化」。

不過，已還原序列化的物件不是即時物件。 它是物件在序列化時的快照集，而且包含屬性，但不包含任何方法。 您可以在 Windows PowerShell 中使用和管理這些物件，包括在管線中傳遞這些物件、顯示選取的屬性，以及將它們格式化。

大部分還原序列化的物件都會自動格式化，以依 Types.ps1xml 或 Format.ps1xml 檔案中的專案顯示。 不過，本機電腦可能沒有在遠端電腦上產生的所有已還原序列化物件的格式檔案。 當物件未格式化時，每個物件的所有屬性都會出現在主控台的串流清單中。

當物件未自動格式化時，您可以使用格式化 Cmdlet （例如 Format-Table 或格式清單）來格式化和顯示選取的屬性。 或者，您可以使用 Out-GridView Cmdlet，在資料表中顯示物件。

此外，如果您在使用本機電腦上沒有指令程式的遠端電腦上執行命令，命令傳回的物件可能無法正確格式化，因為您的電腦上沒有這些物件的格式化檔案。 若要從另一部電腦取得格式設定資料，請使用 Get-FormatData 和 Export-FormatData Cmdlet。

某些物件類型（例如 DirectoryInfo 物件和 Guid）會在收到時轉換回即時物件。 這些物件不需要任何特殊處理或格式化。

## <a name="ordering-the-results"></a>排序結果

指令程式的 ComputerName 參數中電腦名稱稱的順序會決定 Windows PowerShell 連接到遠端電腦的順序。 不過，結果會以本機電腦接收的順序顯示，可能是不同的順序。

若要變更結果的順序，請使用 Sort-Object Cmdlet。 您可以針對 PSComputerName 或 MachineName 屬性進行排序。 您也可以在物件的其他屬性上進行排序，以便讓不同電腦的結果分開。

## <a name="see-also"></a>另請參閱

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table)

[Get-EventLog](xref:Microsoft.PowerShell.Management.Get-EventLog)

[Get-Process](xref:Microsoft.PowerShell.Management.Get-Process)

[Get-Service](xref:Microsoft.PowerShell.Management.Get-Service)

[Get-WmiObject](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Out-GridView](xref:Microsoft.PowerShell.Utility.Out-GridView)

[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object)
