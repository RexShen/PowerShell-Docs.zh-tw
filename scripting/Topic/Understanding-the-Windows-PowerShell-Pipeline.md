---
title: 了解 Windows PowerShell 管線
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
---
# 了解 Windows PowerShell 管線
管線幾乎可以在 Windows PowerShell 中的所有位置運作。 雖然您會在畫面上看到文字，但是 Windows PowerShell 並不會在命令之間傳送文字， 而是傳送物件。

用於管線的標記法與其他殼層中所使用的標記法類似，因此第一眼時，Windows PowerShell 引進了新項目可能不大明顯。 例如，如果您使用 **Out-Host** Cmdlet 強制逐頁顯示另一個命令的輸出，則輸出看起來就像畫面上所顯示的一般文字 (分成數頁)：

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

只要有想要慢慢顯示的冗長輸出，Out-Host -Paging 命令就是有用的管線元素。 它特別適用於 CPU 作業十分密集時。 因為有準備好顯示的完整頁面時會將處理傳送給 Out-Host Cmdlet，所以在下一個輸出頁面可用之前，管線中前面的 Cmdlet 會停止作業。 如果您使用 Windows 工作管理員來監視 Windows PowerShell 所使用的 CPU 和記憶體，就可以看到這種狀況。

請執行下列命令︰**Get-ChildItem C:\Windows -Recurse**。 比較與這個命令的 CPU 和記憶體使用量︰**Get-ChildItem C:\Windows -Recurse | Out-Host -Paging**。 您在畫面上看到的是文字，但這是因為在主控台視窗中必須將物件呈現為文字。 這只是 Windows PowerShell 內實際進行之作業的呈現。 例如，請考慮使用 Get-Location Cmdlet。 如果您在目前位置是 C 磁碟機的根目錄時輸入 **Get-Location**，則會看到下列輸出︰

```
PS> Get-Location

Path
----
C:\
```

如果 Windows PowerShell 已傳送文字，則發出 **Get-Location | Out-Host** 這類命令會將一組字元依其在畫面上的顯示順序從 **Get-Location** 傳遞到 **Out-Host**。 換句話說，如果您要忽略標題資訊，則 **Out-Host** 會依序接收到下列字元：'**C'**、'**:'** 和 '**\'**。 **Out-Host** Cmdlet 無法判斷與 **Get-Location** Cmdlet 的字元輸出相關聯的意義。

Windows PowerShell 會使用物件，而不是使用文字讓管線中的命令進行通訊。 從使用者的觀點來看，物件會將相關資訊封裝成容易將資訊當成一個單元操作的表單，以及擷取您需要的特定項目。

**Get-Location** 命令不會傳回包含目前路徑的文字。 它會傳回稱為 **PathInfo** 物件的資訊套件，這個物件包含目前路徑與一些其他資訊。 **Out-Host** Cmdlet 接著會將此 **PathInfo** 物件傳送到畫面，而 Windows PowerShell 會根據格式規則來決定要顯示的資訊和其顯示方式。

事實上，**Get-Location** Cmdlet 的標題資訊輸出只會新增在處理程序結尾，作為格式化畫面顯示資料之處理程序的一部分。 您在畫面上看到的內容是資訊摘要，並不是輸出物件的完整呈現。

如果 Windows PowerShell 命令的資訊輸出多於我們在主控台視窗中看到的顯示內容，則如何擷取看不到的元素？ 如何檢視額外資料？ 如果您要使用不同於 Windows PowerShell 一般使用格式的格式來檢視資料，要怎麼做？

本章的其餘部分將討論如何選取特定項目並對其格式化以更輕鬆地顯示來探索特定 Windows PowerShell 物件的結構，以及如何將此資訊傳送至替代輸出位置 (例如檔案和印表機)。



<!--HONumber=Apr16_HO1-->


