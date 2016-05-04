---
title: 使用格式命令變更輸出檢視
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
---
# 使用格式命令變更輸出檢視
Windows PowerShell 的一組 Cmdlet 可讓您控制針對特定物件所顯示的屬性。 所有 Cmdlet 名稱的開頭都是動詞 **Format**。 它們可讓您選取要顯示的一或多個屬性。

**Format** Cmdlet 是 **Format-Wide**、**Format-List**、**Format-Table** 和 **Format-Custom**。 在本使用者手冊中，我們只會描述 **Format-Wide**、**Format-List** 和 **Format-Table** Cmdlet。

每個 Format Cmdlet 都有預設屬性，可在未指定要顯示的特定屬性時使用。 每個 Cmdlet 也都會使用相同的參數名稱 (**Property**) 來指定您想要顯示的屬性。 因為 **Format-Wide** 只會顯示單一屬性，所以其 **Property** 參數只使用單一值，但 **Format-List** 和 **Format-Table** 的屬性參數將接受屬性名稱清單。

如果您搭配使用 **Get-Process -Name powershell** 命令與兩個執行中 Windows PowerShell 執行個體，則會收到與下面類似的輸出︰

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

在本節的其餘部分，我們將探討如何使用 **Format** Cmdlet 來變更這個命令的輸出顯示方式。

### 針對 Single-Item 輸出使用 Format-Wide
**Format-Wide** Cmdlet 預設只會顯示物件的預設屬性。 與每個物件相關聯的資訊會顯示在單一資料行中︰

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

您也可以指定非預設屬性：

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### 使用資料行控制 Format-Wide 顯示
使用 **Format-Wide** Cmdlet，一次只能顯示單一屬性。 這樣適用於顯示一行只顯示一個元素的簡單清單。 若要取得簡單清單，請將 **Column** 屬性的值設為 1，方法是輸入：

```
Get-Command Format-Wide -Property Name -Column 1
```

### 針對清單檢視使用 Format-List
**Format-List** Cmdlet 以清單形式顯示物件，並在個別行上標上和顯示每個屬性：

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

您可以指定您想要的任意數目的屬性︰

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

#### 搭配使用 Format-List 與萬用字元取得詳細資訊
**Format-List** Cmdlet 可讓您使用萬用字元作為其 **Property** 參數的值。 這可讓您顯示詳細資訊。 通常，物件所含的資訊會比您需要的資訊還要多，這是 Windows PowerShell 預設未顯示所有屬性值的原因。 若要顯示物件的所有屬性，請使用 **Format-List -Property \&#42;** 命令。 下列命令會針對單一處理程序產生 60 行以上的輸出︰

```
Get-Process -Name powershell | Format-List -Property *
```

雖然 **Format-List** 命令適用於顯示詳細資料，但是，如果您想要輸出概觀包括許多項目，則較簡單的表格式檢視通常更為有用。

### 針對表格式輸出使用 Format-Table
如果您使用未指定屬性名稱的 **Format-Table** Cmdlet 來格式化 **Get-Process** 命令的輸出，則收到的輸出會與未執行任何格式化所收到的輸出完全相同。 原因是處理程序通常會以表格式格式顯示，這與大部分的 Windows PowerShell 物件一樣。

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### 改善 Format-Table 輸出 (AutoSize)
雖然表格式檢視適用於顯示許多類似資訊，但是可能難以解譯顯示是否太窄無法顯示資料。 例如，如果您嘗試顯示處理程序路徑、識別碼、名稱和公司，則會截斷處理程序路徑和公司資料行的輸出︰

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

如果您在執行 **Format-Table** 命令時指定 **AutoSize** 參數，則 Windows PowerShell 會根據您要顯示的實際資料來計算資料行寬度。 這讓 **Path** 資料行更容易閱讀，但是仍然會截斷公司資料行︰

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

**Format-Table** Cmdlet 可能仍然會截斷資料，但是只會在畫面結尾才這麼做。 如果屬性不是最後一個顯示的屬性，則會提供其所需的大小來正確顯示其最長的資料元素。 如果您在 **Property** 值清單中交換 **Path** 和 **Company** 的位置，則可以看到顯示公司名稱，但截斷路徑：

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

**Format-Table** 命令假設屬性越接近屬性清單開頭，就越重要。 因此，它會嘗試完整顯示最接近開頭的屬性。 如果 **Format-Table** 命令無法顯示所有屬性，則會從顯示中移除一些資料行，並提供警告。 如果您將 **Name** 設為清單中的最後一個屬性，則可以看到這項行為：

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

在上面的輸出中，會截斷識別碼資料行，以將其放入清單中，並堆疊資料行標題。 自動重新調整資料行大小，不一定會執行您要的作業。

#### 在資料行中讓 Format-Table 換行 (Wrap)
您可以使用 **Wrap** 參數，強制冗長的 **Format-Table** 資料在其顯示資料行中換行。 因為未一併指定 **AutoSize** 時會使用預設設定，所以單獨使用 **Wrap** 參數不一定會執行您預期的作業：

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

單獨使用 **Wrap** 參數的優點是不會讓處理變的太慢。 如果您執行大型目錄系統的遞迴檔案清單，則使用 **AutoSize** 時，可能需要很長的時間，並會在顯示第一個輸出項目之前使用大量記憶體。

如果您不在意系統負載，則搭配使用 **AutoSize** 與 **Wrap** 參數的運作效果極佳。 初始資料行一律會獲分配在一行上顯示項目所需的寬度，就像指定沒有 **Wrap** 參數的 **AutoSize** 一樣。 唯一的差異在於，必要時會讓最後一個資料行換行︰

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

如果您先指定最寬的資料行，則可能不會顯示部分資料行，因此最安全的方式是先指定最小的資料元素。 在下列範例中，我們先指定極寬的路徑元素，甚至進行換行，但仍然遺失最後的 **Name** 資料行︰

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### 組織資料表輸出 (-GroupBy)
表格式輸出控制項的另一個有用參數是 **GroupBy**。 較長的表格式清單尤其很難進行比較。 **GroupBy** 參數會根據屬性值將輸出群組在一起。 例如，我們可以依據公司將處理程序群組在一起，並省略屬性清單中的公司值，讓公司更容易進行檢查︰

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```



<!--HONumber=Apr16_HO1-->


