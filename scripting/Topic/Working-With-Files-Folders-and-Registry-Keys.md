---
title: 使用檔案、資料夾與登錄機碼
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
---
# 使用檔案、資料夾與登錄機碼
Windows PowerShell 使用名詞 **Item** 參照在 Windows PowerShell 磁碟機上找到的項目。 使用 Windows PowerShell FileSystem 提供者時，**Item** 可能是檔案、資料夾或 Windows PowerShell 磁碟機。 在大部分的系統管理設定中，列出及使用這些項目是很重要的基本工作，因此，我們要詳細討論這些工作。

### 列舉檔案、資料夾與登錄機碼 (Get-ChildItem)
從特定位置取得項目集合是很常見的工作，因此，**Get-ChildItem** Cmdlet 專門設計為傳回容器 (例如資料夾) 內的所有項目。

若要傳回直接包含於資料夾 C:\\Windows 內的所有檔案和資料夾，請輸入：

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

清單看起來會與您在 **Cmd.exe** 中輸入 **dir** 命令 (或在 UNIX 命令殼層中輸入 **ls** 命令) 時看到的類似。

您可以使用 **Get-ChildItem** Cmdlet 的參數執行極為複雜的清單。 我們接下來會介紹幾個案例。 您可以輸入以下命令以查看 **Get-ChildItem** Cmdlet 的語法：

```
PS> Get-Command -Name Get-ChildItem -Syntax
```

這些參數可混合使用以得到高度自訂的輸出。

#### 列出所有包含的項目 (\-Recurse)
若要查看 Windows 資料夾內的項目和子資料夾中包含的任一項目，請使用 **Get-ChildItem** 的 **Recurse** 參數。 清單會顯示 Windows 資料夾中的所有項目和子資料夾中的項目。 例如：

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

#### 依名稱篩選項目 (\-Name)
若只要顯示項目的名稱，請使用 **Get-Childitem** 的 **Name** 參數：

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

#### 強制列出隱藏的項目 (\-Force)
通常在 [檔案總管] 或 Cmd.exe 中不可見的項目，則不會顯示在 **Get-ChildItem** 命令的輸出中。 若要顯示隱藏的項目，請使用 **Get-ChildItem** 的 **Force** 參數。 例如：

```
Get-ChildItem -Path C:\Windows -Force
```

此參數之所以名為 Force，是因為您可以強制覆寫 **Get-ChildItem** 命令的正常行為。 Force 是廣泛使用的參數，會強制執行 Cmdlet 一般不會執行的動作，但並不會執行危害系統安全性的任何動作。

#### 使用萬用字元比對項目名稱
**Get-ChildItem** 命令可接受在要列出的項目清單路徑中使用萬用字元。

因為萬用字元比對是由 Windows PowerShell 引擎處理，接受萬用字元的所有 Cmdlet 都會使用相同的標記法，並有相同的比對行為。 Windows PowerShell 萬用字元標記法包括：

-   星號 (\*) 會比對任一字元零次或更多次。

-   問號 (?) 會精確比對一個字元。

-   左中括弧 (\[) 字元與右中括弧 (]) 字元是用來夾住要比對的一組字元。

以下是萬用字元規格如何運作的一些範例。

若要在 Windows 目錄中尋找具有副檔名 **.log** 且基底名稱為剛好 5 個字元的所有檔案，請輸入下列命令：

```
PS> Get-ChildItem -Path C:\Windows\?????.log
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

若要在 Windows 目錄中尋找開頭是字母 **x** 的所有檔案，請輸入：

```
Get-ChildItem -Path C:\Windows\x*
```

若要尋找名稱開頭是 **x** 或 **z** 的所有檔案，請輸入：

```
Get-ChildItem -Path C:\Windows\[xz]*
```

#### 排除項目 (\-Exclude)
您可以使用 Get-ChildItem 的 **Exclude** 參數排除特定項目。 這可讓您在單一陳述式中執行複雜的篩選。

例如，假設您嘗試在 [System32] 資料夾中尋找 Windows 時間服務 DLL，而您只記得 DLL 名稱的開頭是 "W" 且其中含有 "32"。

類似 **w\&#42;32\&#42;.dll** 的運算式會尋找滿足上述條件的所有 DLL，但也會傳回名稱中包含 "95" 或 "16" 的 Windows 95 及 16 位元的 Windows 相容 DLL。 您可以使用 **Exclude** 參數搭配模式 **\&#42;\[9516]\&#42;**，以省略名稱中含有這些數字中之任一數字的檔案：

<pre>PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*
目錄︰Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll</pre>

#### 混合使用 Get-ChildItem 參數
您可以在同一個命令中使用 **Get-ChildItem** Cmdlet 的數個參數。 在混合使用參數之前，請確定您了解萬用字元比對的原則。 例如，下列命令不會傳回任何結果：

```
PS> Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

即使 Windows 資料夾中有兩個開頭是字母 "z" 的 DLL 也不會有任何結果。

因為我們將萬用字元指定為路徑的一部分，因此不會傳回任何結果。 即使命令是遞迴命令，**Get-ChildItem** Cmdlet 也會將項目限制為 Windows 資料夾中名稱結尾是 ".dll" 的項目。

若要為名稱符合特殊模式的檔案指定遞迴搜尋，請使用 **\-Include** 參數。

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```



<!--HONumber=Apr16_HO1-->


