---
title:  了解 Windows PowerShell 名稱
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  b4d0fd22-8298-4ee6-82ae-9b6f2907c986
---

# 了解 Windows PowerShell 名稱
了解大部分命令列介面的命令和命令參數名稱需要投入大量時間。 此問題在於不太有模式可循，因此唯一的了解方式是記住您需要定期使用的每個命令和每個參數。

當您使用新命令或參數時，通常無法運用您既有的知識，而必須尋找及了解新名稱。 如果您看一下介面如何從具有累加新增功能的一小組工具成長為功能性介面，便不難了解此結構無法標準化的原因。 特別是命令名稱，乍聽之下可能很有邏輯 (因為每個命令都是個別工具)，但其實還有更好的方法來處理命令名稱。

大部分命令的建置目的是為了管理作業系統或應用程式的項目，例如服務或處理程序。 命令有各式各樣的名稱，不一定適合放入某個系列。 例如，在 Windows 系統上，您可以使用 **net start** 和 **net stop** 命令來啟動及停止服務。 Windows 有另一個更通用但名稱完全不同的服務控制工具 **sc**，不適合放入 **net** 服務命令的命名模式中。 為了管理處理程序，Windows 提供 **tasklist** 命令來列出處理程序，並提供 **taskkill** 命令來刪除處理程序。

使用參數的命令沒有標準的參數規格。 您無法使用 **net start** 命令啟動遠端電腦上的服務。 **sc** 命令會啟動遠端電腦上的服務，但若要指定遠端電腦，您必須在其名稱前面加上雙反斜線。 例如，若要在名為 DC01 的遠端電腦上啟動多工緩衝處理器服務，您會輸入 **sc \\DC01 start spooler**。 若要列出 DC01 上執行的工作，您必須使用 **/S** (表示「系統」)，並提供名稱 DC01 但不含反斜線，例如：**tasklist /S DC01**。

雖然服務與處理程序之間有重要的技術區別，但是這兩者都是電腦上明確定義生命週期的可管理項目範例。 您可能想要啟動或停止服務或處理程序，或是取得所有目前執行中的服務或處理程序清單。 換句話說，雖然服務和處理程序是不同的項目，但是我們對服務或處理程序執行的動作通常在概念上是相同的。 此外，藉由指定參數來自訂動作的選項在概念上也可能很類似。

Windows PowerShell 利用這些相似之處，減少為了解及使用 Cmdlet 所需知道的不同名稱數量。

### Cmdlet 使用「動詞-名詞」名稱降低記住命令的需求
Windows PowerShell 使用「動詞-名詞」命名系統，其中每個 Cmdlet 名稱是由一個標準動詞後面接著連字號和一個特定名詞所組成。 Windows PowerShell 動詞不一定是英文動詞，但會表示 Windows PowerShell 中的特定動作。 名詞很像是任何語言中的名詞，用於描述系統管理中重要物件的特定類型。 藉由檢視一些動詞和名詞範例，就能輕鬆地示範這些由兩部分組成的名稱如何減少學習工作。

名詞的限制較少，但一律會描述命令的作用。 Windows PowerShell 具有 **Get-Process**、**Stop-Process**、**Get-Service** 和 **Stop-Service** 等命令。

在兩個名詞和兩個動詞的案例中，一致性無法有效簡化學習。 不過，如果您檢視由 10 個動詞和 10 個名詞所組成的標準集合，則只需要了解 20 個字，就能使用這些字組成 100 個不同的命令名稱。

您通常可以藉由讀取命令的名稱來辨識命令的功能，且新命令應該使用哪些名稱通常會很明顯。 例如，電腦關機命令可能是 **Stop-Computer**。 列出網路上所有電腦的命令可能是 **Get-Computer**。 取得系統日期的命令可能是 **Get-Date**。

您可以使用 **Get-Command** 的 **-Verb** 參數列出包含特定動詞的所有命令 (我們將在下一節詳細討論 **Get-Command**)。 例如，若要查看使用 **Get** 動詞的所有 Cmdlet，請輸入︰

```
PS> Get-Command -Verb Get
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

**-Noun** 參數更是實用，因為它可讓您查看影響相同類型物件的一系列命令。 例如，如果您想要查看哪些命令可用於管理服務，請輸入下列命令︰

```
PS> Get-Command -Noun Service
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str... 
...
```

即使命令使用「動詞-名詞」命名配置，也不一定是 Cmdlet。 清除主控台視窗的命令 Clear-Host，即為具有「動詞-名詞」名稱但不是 Cmdlet 的原生 Windows PowerShell 命令範例之一。 Clear-Host 命令實際上為內部函式，如果對它執行 Get-Command 就能看到︰

```
PS> Get-Command -Name Clear-Host

CommandType     Name                            Definition
-----------     ----                            ----------
Function        Clear-Host                      $spaceType = [System.Managem...
```

### Cmdlet 使用標準參數
如前所述，傳統命令列介面中所使用的命令通常不會有一致的參數名稱。 有時候參數完全沒有名稱。 這種情況的參數通常是可快速輸入，但新使用者不容易了解的單字或縮寫字。

不同於其他大部分傳統命令列介面，Windows PowerShell 會直接處理這些參數，並透過直接存取參數及開發人員指引來標準化參數名稱。 雖然這並不保證每個 Cmdlet 一律會符合標準，但會鼓勵其符合標準。

> [!NOTE]
> 當您使用這些參數時，參數名稱前面一律會加上 '-'，以允許 Windows PowerShell 清楚地將它們識別為參數。 在 **Get-Command -Name Clear-Host** 範例中，參數的名稱為 **Name**，但會輸入為 -**Name**。

以下是一些標準參數名稱和使用方式的一般特性。

#### 說明參數 (?)
當您指定 **-?** 參數給任何 Cmdlet 時，不會執行此 Cmdlet。 相反地，Windows PowerShell 會顯示此 Cmdlet 的說明。

#### 一般參數
Windows PowerShell 有幾個稱為*一般參數*的參數。 因為這些參數是由 Windows PowerShell 引擎所控制，所以每當 Cmdlet 實作參數時，這些參數一律會以相同方式運作。 一般參數包括 **WhatIf**、**Confirm**、**Verbose**、**Debug**、**Warn**、**ErrorAction**、**ErrorVariable**、**OutVariable** 和 **OutBuffer**。

#### 建議的參數
Windows PowerShell 核心 Cmdlet 針對類似的參數使用標準名稱。 雖然不會強制使用參數名稱，但針對使用方式有明確的指引，以鼓勵標準化。

例如，該指引建議命名指向電腦的參數時，依照 **ComputerName** 等名稱，而不是依照 Server、Host、System、Node 或其他常見的替代文字。 重要的建議參數名稱包括 **Force**、**Exclude**、**Include**、**PassThru**、**Path**, 和 **CaseSensitive**。



<!--HONumber=May16_HO2-->


