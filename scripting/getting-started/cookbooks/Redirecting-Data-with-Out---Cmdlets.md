---
title: 使用 Out-* Cmdlet 重新導向資料
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
---
# 使用 Out-* Cmdlet 重新導向資料
Windows PowerShell 提供幾個可讓您直接控制資料輸出的 Cmdlet。 這些 Cmdlet 有兩個重要特性：

首先，它們通常會將資料轉換成某種文字格式。 這樣做是因為它們會將資料輸出至需要文字輸入的系統元件， 所以必須以文字表示物件。 因此，文字會格式化為您在 Windows PowerShell 主控台視窗中看到的樣子。

其次，這些 Cmdlet 使用 Windows PowerShell 動詞 **Out**，因為它們會將資訊從 Windows PowerShell 送出至其他位置。 **Out-Host** Cmdlet 也不例外︰主機視窗顯示會在 Windows PowerShell 之外。 這點很重要，因為當資料從 Windows PowerShell 送出時，實際上會遭到移除。 如果您嘗試建立管線將資料分頁至主機視窗，然後嘗試將其格式化為清單，就會看到這種情況，如下所示︰

```
PS> Get-Process | Out-Host -Paging | Format-List
```

您可能預期命令會以清單格式分頁顯示處理程序資訊。 相反地，它會顯示預設的表格式清單︰

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

**Out-Host** Cmdlet 會將資料直接傳送至主控台，因此 **Format-List** 命令永遠不會收到需要格式化的項目。

建構此命令的正確方式是將 **Out-Host** Cmdlet 置於管線結尾，如下所示。 這會格式化清單中的處理程序資料，再將其分頁顯示。

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

這適用於所有 **Out** Cmdlet。 **Out** Cmdlet 一律會出現在管線結尾處。

> [!NOTE]
> 所有 **Out** Cmdlet 都會使用對主控台視窗有效的格式 (包括行的長度限制)，將輸出轉譯成文字。

#### 分頁主控台輸出 (Out-Host)
根據預設，Windows PowerShell 會將資料傳送至主機視窗，這與 Out-Host Cmdlet 的功能完全相同。 如前所述，Out-Host Cmdlet 主要用於將資料分頁。 例如，下列命令會使用 Out-Host 將 Get-Command Cmdlet 的輸出分頁︰

```
PS> Get-Command | Out-Host -Paging
```

您也可以使用 **more** 函式將資料分頁。 在 Windows PowerShell 中，**more** 是呼叫 **Out-Host -Paging** 的函式。 下列命令示範如何使用 **more** 函式將 Get-Command 的輸出分頁︰

```
PS> Get-Command | more
```

如果您包含一或多個檔案名稱作為 more 函式的引數，該函式會讀取指定的檔案並將其內容分頁至主機︰

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### 捨棄輸出 (Out-Null)
**Out-Null** Cmdlet 設計成可立即捨棄任何收到的輸入。 這在捨棄因執行命令的副作用所得到的不必要資料時會很有用。 輸入下列命令時，命令不會傳回任何項目︰

```
PS> Get-Command | Out-Null
```

**Out-Null** Cmdlet 不會捨棄錯誤輸出。 例如，如果您輸入下列命令，會顯示訊息通知您 Windows PowerShell 無法辨識 'Is-NotACommand'：

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### 列印資料 (Out-Printer)
您可以使用 **Out-Printer** Cmdlet 列印資料。 如果您未提供印表機名稱，**Out-Printer** Cmdlet 會使用預設印表機。 您可以使用任何 Windows 印表機，方法是指定其顯示名稱。 您不需要任何印表機連接埠對應，或甚至是真正的實體印表機。 例如，如果您已安裝 Microsoft Office Document Imaging 工具，您可以輸入下列命令將資料傳送至影像檔︰

```
PS> Get-Command Get-Command | Out-Printer -Name "Microsoft Office Document Image Writer"
```

#### 儲存資料 (Out-File)
您可以使用 **Out-File** Cmdlet 將輸出傳送至檔案，而不是主控台視窗。 下列命令列會將處理程序清單傳送至檔案 **C:\temp\processlist.txt**：

```
PS> Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

如果您習慣於傳統輸出重新導向，使用 **Out-File** Cmdlet 的結果可能不如您的預期。 若要了解其行為，您必須知道 **Out-File** Cmdlet 操作所在的內容。

**Out-File** Cmdlet 預設會建立 Unicode 檔案。 從長遠看來，這是最佳的預設值，但這表示預期 ASCII 檔案的工具將無法以預設輸出格式正常運作。 您可以使用 **Encoding** 參數，將預設輸出格式變更為 ASCII︰

```
PS> Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

**Out-file** 會格式化檔案內容，使其看起來像是主控台輸出。 這會導致輸出和在大部分情況下的主控台視窗中一樣被截斷。 例如，如果您執行下列命令：

```
PS> Get-Command | Out-File -FilePath c:\temp\output.txt
```

輸出看起來像這樣：

```
CommandType     Name                            Definition                     
-----------     ----                            ----------                     
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

若要取得不會強制行換行以符合螢幕寬度的輸出，您可以使用**Width** 參數指定行的寬度。 因為 **Width** 是 32 位元整數參數，所有可以有最大值 2147483647。 請輸入下列命令將行的寬度設定為此最大值︰

```
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

當您想要以輸出主控台上的顯示格式來儲存輸出時，**Out-File** Cmdlet 會很有用。 如需更細微地控制輸出格式，您需要更進階的工具。 我們將在下一章探討這些工具，以及有關物件操作的一些詳細資訊。



<!--HONumber=Apr16_HO1-->


