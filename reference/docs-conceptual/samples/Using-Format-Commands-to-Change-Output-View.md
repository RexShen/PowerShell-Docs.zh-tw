---
ms.date: 10/22/2019
keywords: powershell,cmdlet
title: 使用格式命令變更輸出檢視
ms.openlocfilehash: 9d9854362b5150a99bdd0c02518599840c1fd42d
ms.sourcegitcommit: 36e4c79afda2ce11febd93951e143687245f0b50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2019
ms.locfileid: "73444424"
---
# <a name="using-format-commands-to-change-output-view"></a>使用格式命令變更輸出檢視

PowerShell 的一組 Cmdlet 可讓您控制如何針對特定物件顯示屬性。 所有 Cmdlet 名稱的開頭都是動詞 `Format`。 它們可讓您選取要顯示哪些屬性。

```powershell
Get-Command -Verb Format -Module Microsoft.PowerShell.Utility
```

```Output
CommandType     Name               Version    Source
-----------     ----               -------    ------
Cmdlet          Format-Custom      6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Hex         6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-List        6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Table       6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Wide        6.1.0.0    Microsoft.PowerShell.Utility
```

此文章說明 `Format-Wide`、`Format-List` 與 `Format-Table` Cmdlet。

PowerShell 中的每個物件類型都有預設屬性，可在您未指定要顯示哪些屬性時使用。 每個 Cmdlet 也都會使用相同的 **Property** 參數來指定您要顯示的屬性。 因為 `Format-Wide` 只會顯示單一屬性，其 **Property** 參數只會使用單一值，但 `Format-List` 與 `Format-Table` 的 property 參數接受屬性名稱清單。

在此範例中，`Get-Process` Cmdlet 的預設輸出顯示我們有兩個 Internet Explorer 執行個體正在執行。

```powershell
Get-Process -Name iexplore
```

**程序**物件的預設格式會顯示如下所示的屬性：

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     32    25.52      10.25      13.11   12808   1 iexplore
     52    11.46      26.46       3.55   21748   1 iexplore
```

## <a name="using-format-wide-for-single-item-output"></a>針對 Single-Item 輸出使用 Format-Wide

`Format-Wide` Cmdlet 預設只會顯示物件的預設屬性。 與每個物件相關聯的資訊會顯示在單一資料行中︰

```powershell
Get-Command -Verb Format | Format-Wide
```

```Output
Format-Custom          Format-Hex
Format-List            Format-Table
Format-Wide
```

您也可以指定非預設屬性：

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```Output
Custom                 Hex
List                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a>使用資料行控制 Format-Wide 顯示

使用 `Format-Wide` Cmdlet，一次只能顯示單一屬性。 這有助於在多個資料行中顯示大型清單。

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 3
```

```Output
Custom                 Hex                  List
Table                  Wide

```

## <a name="using-format-list-for-a-list-view"></a>針對清單檢視使用 Format-List

`Format-List` Cmdlet 會以清單形式顯示物件，並在個別行上標記和顯示每個屬性：

```powershell
Get-Process -Name iexplore | Format-List
```

```Output
Id      : 12808
Handles : 578
CPU     : 13.140625
SI      : 1
Name    : iexplore

Id      : 21748
Handles : 641
CPU     : 3.59375
SI      : 1
Name    : iexplore
```

您可以指定您想要的任意數目的屬性︰

```powershell
Get-Process -Name iexplore | Format-List -Property ProcessName,FileVersion,StartTime,Id
```

```Output
ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:58 AM
Id          : 12808

ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:57 AM
Id          : 21748
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>搭配使用 Format-List 與萬用字元取得詳細資訊

`Format-List` Cmdlet 可讓您使用萬用字元作為其 **Property** 參數的值。 這可讓您顯示詳細資訊。 通常，物件所含的資訊會比您需要的資訊還要多，這是 PowerShell 預設未顯示所有屬性值的原因。 若要顯示物件的所有屬性，請使用 **Format-List -Property \&#42;** 命令。 下列命令會針對單一處理程序產生 60 行以上的輸出︰

```powershell
Get-Process -Name iexplore | Format-List -Property *
```

雖然 `Format-List` 命令在顯示詳細資料方面非常實用，但若要取得包括許多項目之輸出的概觀，則較簡單的表格式檢視通常更為實用。

## <a name="using-format-table-for-tabular-output"></a>針對表格式輸出使用 Format-Table

如果您使用未指定屬性名稱的 `Format-Table` Cmdlet 來設定 `Get-Process` 命令輸出格式，則收到的輸出會與未使用 `Format` Cmdlet 的情況相同。 根據預設，PowerShell 會以表格格式格式顯示**程序**物件。

```powershell
Get-Service -Name win* | Format-Table
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  WinHttpAutoProx... WinHTTP Web Proxy Auto-Discovery Se...
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Manag...
```

### <a name="improving-format-table-output-autosize"></a>改善 Format-Table 輸出 (AutoSize)

雖然表格式檢視適用於顯示許多資訊，但是若顯示器太窄而無法容納資料，則可能難以解譯。 在上述範例中，輸出會被截斷。 如果您在執行 `Format-Table` 命令時指定 **AutoSize** 參數，PowerShell 會根據顯示的實際資料計算欄寬。 這可讓欄變成可讀取。

```powershell
Get-Service -Name win* | Format-Table -AutoSize
```

```Output
Status  Name                DisplayName
------  ----                -----------
Running WinDefend           Windows Defender Antivirus Service
Running WinHttpAutoProxySvc WinHTTP Web Proxy Auto-Discovery Service
Running Winmgmt             Windows Management Instrumentation
Running WinRM               Windows Remote Management (WS-Management)
```

`Format-Table` Cmdlet 可能仍然會截斷資料，但是只會在畫面結尾截斷。 如果屬性不是最後一個顯示的屬性，則會提供其所需的大小來正確顯示其最長的資料元素。

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -AutoSize
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc, iphl…
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms, TPHKLO…
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

`Format-Table` 命令會假設屬性是依重要性順序列出的。 因此，它會嘗試完整顯示最接近開頭的屬性。 如果 `Format-Table` 命令無法顯示所有屬性，它會從顯示中移除一些欄。 您可以在 **DependentServices** 屬性先前的範例中看到此行為。

### <a name="wrapping-format-table-output-in-columns-wrap"></a>在資料行中讓 Format-Table 換行 (Wrap)

您可以使用 **Wrap** 參數，強制冗長的 `Format-Table` 資料在其顯示欄中換行。 因為未一併指定 **AutoSize** 時會使用預設設定，所以單獨使用 **Wrap** 參數可能不會執行您預期的作業：

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -Wrap
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc,
                                                                                iphlpsvc}
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms,
                                                                                TPHKLOAD,
                                                                                SUService,
                                                                                smstsmgr…}
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

單獨使用 **Wrap** 參數不會讓處理速度變得太慢。 但是，使用 **AutoSize** 設定大型目錄結構的遞迴檔案清單格式時，可能需要很長的時間，並在顯示第一個輸出項目之前使用大量記憶體。

如果您不在意系統負載，搭配 **Wrap** 參數使用 **AutoSize** 並沒有問題。
初始欄仍會使用所需的寬度在一行上顯示項目，但如有必要，就會在最後一欄換行。

> [!NOTE]
> 當您先指定最寬的欄時，某些欄就可能不會顯示。 為求最佳結果，請先指定最小的資料元素。

在下列範例中，我們會先指定最寬的屬性。

```powershell
Get-Process -Name iexplore | Format-Table -Wrap -AutoSize -Property FileVersion,Path,Name,Id
```

即使換行，也會省略最後的 **Id** 資料行：

```Output
FileVersion                          Path                                                  Nam
                                                                                           e
-----------                          ----                                                  ---
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files (x86)\Internet Explorer\IEXPLORE.EXE iex
                                                                                           plo
                                                                                           re
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files\Internet Explorer\iexplore.exe       iex
                                                                                           plo
                                                                                           re
```

### <a name="organizing-table-output--groupby"></a>組織資料表輸出 (-GroupBy)

表格式輸出控制項的另一個有用參數是 **GroupBy**。 較長的表格式清單尤其很難進行比較。 **GroupBy** 參數會根據屬性值將輸出群組在一起。 例如，我們可以依 **StartType** 將服務分組，並省略屬性清單中的 **StartType** 值，以方便檢查︰

```powershell
Get-Service -Name win* | Sort-Object StartType | Format-Table -GroupBy StartType
```

```Output
   StartType: Automatic
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Managem…

   StartType: Manual
Status   Name               DisplayName
------   ----               -----------
Running  WinHttpAutoProxyS… WinHTTP Web Proxy Auto-Discovery Serv…
```
