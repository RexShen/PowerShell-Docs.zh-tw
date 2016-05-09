---
title: 使用變數儲存物件
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
---
# 使用變數儲存物件
Windows PowerShell 使用物件。 Windows PowerShell 可讓您建立基本上為具名物件的變數，以保留輸出供之後使用。 如果您是用來使用其他殼層中的變數，請記得 Windows PowerShell 變數是物件，而非文字。

變數一律會指定起始字元 $，而且可以在其名稱中包括任何英數字元或底線。

### 建立變數
您可以輸入有效的變數名稱來建立變數︰

```
PS> $loc
PS>
```

這不會傳回任何結果，因為 **$loc** 沒有值。 您可以在相同的步驟中建立變數並指派其值。 Windows PowerShell 只會建立不存在的變數；否則，它會將指定的值指派給現有變數。 若要將您的目前位置儲存在變數 **$loc** 中，請輸入：

```
$loc = Get-Location
```

輸入這個命令時未顯示任何輸出，因為輸出會傳送至 $loc。 在 Windows PowerShell 中，顯示的輸出是下列事實的副作用：未指示的資料一律會傳送至螢幕。 輸入 $loc 將顯示目前的位置：

```
PS> $loc

Path
----
C:\temp
```

您可以使用 **Get-Member** 顯示變數內容的相關資訊。 將 $loc 傳送到 Get-Member 將顯示它是 **PathInfo** 物件，就像 Get-Location 的輸出一樣：

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### 操作變數
Windows PowerShell 提供數個命令來操作變數。 您可以查看可讀取形式的完整清單，方法是輸入︰

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

除了您在目前 Windows PowerShell 工作階段中建立的變數之外，還有數個系統定義的變數。 您可以使用 **Remove-Variable** Cmdlet 來清除所有不受 Windows PowerShell 控制的變數。 輸入下列命令以清除所有變數：

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

這將產生您在下面看到的確認提示。

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

如果您之後執行 **Get-Variable** Cmdlet，則會看到其餘的 Windows PowerShell 變數。 因為也有變數 Windows PowerShell 磁碟機，所以您也可以顯示所有 Windows PowerShell 變數，方法是輸入︰

```
Get-ChildItem variable:
```

### 使用 Cmd.exe 變數
雖然 Windows PowerShell 不是 Cmd.exe，但是會在命令殼層環境中執行，而且可以在 Windows 的任何環境中使用相同的變數。 這些變數是透過名為 **env** 的磁碟機公開： 您可以檢視這些變數，方法是輸入︰

```
Get-ChildItem env:
```

雖然標準變數 Cmdlet 未設計成使用 **env:** 變數，但是您仍然可以指定 **env:** 前置詞來使用它們。 例如，若要查看作業系統根目錄，您可以從 Windows PowerShell 使用命令殼層 **%SystemRoot%** 變數，方法是輸入︰

```
PS> $env:SystemRoot
C:\WINDOWS
```

您也可以從 Windows PowerShell 建立和修改環境變數。 從 Windows PowerShell 存取的環境變數符合 Windows 中其他位置之環境變數的一般規則。



<!--HONumber=Apr16_HO1-->


