---
title:  取得命令的相關資訊
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
---

# 取得命令的相關資訊
Windows PowerShell **Get-Command** Cmdlet 能取得您目前工作階段中所有可用的命令。 當您在 Windows PowerShell 命令提示字元輸入 **Get-Command** 時，您會看到如下輸出：

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

此輸出與 Cmd.exe 的「說明」輸出 (內部命令的表格式摘要) 十分相似。 如上面 **Get-Command** 命令輸出的摘要所示，每個顯示的命令都有一個屬於 Cmdlet 的 CommandType。 Cmdlet 是 Windows PowerShell 的內建命令類型，大致上是對應到 Cmd.exe 的 **dir** 和 **cd** 命令，以及 UNIX 殼層的內建項 (例如 BASH)。

在 **Get-Command** 命令的輸出中，所有定義的結尾都是省略符號 (...)，表示 PowerShell 無法在可用空間內顯示所有內容。 當 Windows PowerShell 顯示輸出時，它會將輸出格式化為文字，並將其排列以在視窗中整齊地顯示。 我們將稍後在格式化相關的章節中討論此內容。

**Get-Command** Cmdlet 具有一個可取得各 Cmdlet 語法的 **Syntax** 參數。 若要取得 Get-Help Cmdlet 的語法，請使用下列命令：

**Get-Command Get-Help -Syntax**

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### 顯示可用的命令類型
**Get-Command** 命令不會列出 Windows PowerShell 中所有可用的命令。 反之，**Get-Command** 命令只會列出目前工作階段中的 Cmdlet。 Windows PowerShell 實際上支援一些其他類型的命令。 雖然 Windows PowerShell 使用者手冊中沒有詳細討論別名、函式與指令碼，但它們也是 Windows PowerShell 命令。 可執行或具有已登錄檔案類型處理常式的外部檔案，也分類為命令。

若要取得工作階段中的所有命令，請輸入：

```
Get-Command *
```

因為此清單包含您搜尋路徑中的外部檔案，其中可能會有數千個項目。 所以查看一組精簡過的命令會更實用。

若要取得其他類型的原生命令，請使用 **Get-Command** Cmdlet 的 **CommandType** 參數。

> [!NOTE]
> 星號 (*) 在 Windows PowerShell 命令引數中用於萬用字元比對。 * 表示「符合一或多個任意字元」。 您可以輸入 **Get-Command a&#42;** 來尋找開頭為字母 "a" 的所有命令。 與 Cmd.exe 中萬用字元比對不同的是，Windows PowerShell 的萬用字元也會比對句號。

若要取得命令別名 (指派給命令的暱稱)，請輸入：

```
Get-Command -CommandType Alias
```

若要取得目前工作階段中的函式，請輸入：

```
Get-Command -CommandType Function
```

若要顯示 Windows PowerShell 搜尋路徑中的指令碼，請輸入：

```
Get-Command -CommandType Script
```



<!--HONumber=May16_HO2-->


