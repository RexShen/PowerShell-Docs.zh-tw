---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-xml?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Xml
ms.openlocfilehash: 85d5869650a95a011f705612927b55acf4901ed3
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205484"
---
# Select-Xml

## 概要
尋找 XML 字串或文件中的文字。

## SYNTAX

### Xml (預設值)

```
Select-Xml [-Xml] <XmlNode[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### 路徑

```
Select-Xml [-Path] <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### LiteralPath

```
Select-Xml -LiteralPath <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### Content

```
Select-Xml -Content <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

## DESCRIPTION

**Select xml** Cmdlet 可讓您使用 XPath 查詢來搜尋 Xml 字串和檔中的文字。
輸入 XPath 查詢，並使用 *Content* 、 *Path* 或 *Xml* 參數指定要搜尋的 Xml。

## 範例

### 範例1：選取 AliasProperty 節點

```
PS C:\> $Path = "$Pshome\Types.ps1xml"
PS C:\> $XPath = "/Types/Type/Members/AliasProperty"
PS C:\> Select-Xml -Path $Path -XPath $Xpath | Select-Object -ExpandProperty Node
Name                 ReferencedMemberName
----                 --------------------
Count                Length
Name                 Key
Name                 ServiceName
RequiredServices     ServicesDependedOn
ProcessName          Name
Handles              Handlecount
VM                   VirtualSize
WS                   WorkingSetSize
Name                 ProcessName
Handles              Handlecount
VM                   VirtualMemorySize
WS                   WorkingSet
PM                   PagedMemorySize
NPM                  NonpagedSystemMemorySize
Name                 __Class
Namespace            ModuleName
```

此範例取得 Types.ps1xml 中的別名屬性。
(如需此檔案的相關資訊，請參閱 about_Types.ps1xml)。

第一個命令將 Types.ps1xml 檔案的路徑儲存在 $Path 變數中。

第二個命令將 AliasProperty 節點的 XML 路徑儲存在 $XPath 變數中。

第三個命令使用 **Select-Xml** Cmdlet 取得由 Types.ps1xml 檔案的 XPath 陳述式所識別的 AliasProperty 節點。
此命令會使用管線運算子將 AliasProperty 節點傳送至 Select-Object Cmdlet。
*ExpandProperty* 參數會展開 **Node** 物件，並傳回其 Name 和 ReferencedMemberName 屬性。

結果顯示 Types.ps1xml 檔案中每個別名屬性的 Name 和 ReferencedMemberName。
例如，有一個 **Count** 屬性是 **Length** 屬性的別名。

### 範例2：輸入 XML 檔

```
PS C:\> [xml]$Types = Get-Content $Pshome\Types.ps1xml
PS C:\> Select-Xml -Xml $Types -XPath "//MethodName"
```

這個範例示範如何使用 *xml* 參數，將 xml 檔提供給 **Select xml** Cmdlet。

第一個命令會使用 Get-Content Cmdlet 來取得 Types.ps1xml 檔案的內容，並將其儲存在 $Types 變數中。
Xml 會將 \[ \] 變數轉換成 xml 物件。

第二個命令使用 **Select-Xml** Cmdlet 取得 Types.ps1xml 檔案中的 MethodName 節點。
此命令使用 *Xml* 參數指定 $Types 變數中的 XML 內容，以及使用 *XPath* 參數指定 MethodName 節點的路徑。

### 範例3：搜尋 PowerShell 說明檔

```
PS C:\> $Namespace = @{command = "http://schemas.microsoft.com/maml/dev/command/2004/10"; maml = "http://schemas.microsoft.com/maml/2004/10"; dev = "http://schemas.microsoft.com/maml/dev/2004/10"}

The second command saves the path to the help files in the $Path variable.If there are no help files in this path on your computer, use the Update-Help cmdlet to download the help files. For more information about Updatable Help, see about_Updatable_Help (https://go.microsoft.com/fwlink/?LinkId=235801).
PS C:\> $Path = "$Pshome\en-us\*dll-Help.xml"

The third command uses the **Select-Xml** cmdlet to search the XML for cmdlet names by finding Command:Name element anywhere in the files. It saves the results in the $Xml variable.**Select-Xml** returns a **SelectXmlInfo** object that has a Node property, which is a **System.Xml.XmlElement** object. The Node property has an InnerXML property, which contains the actual XML that is retrieved.
PS C:\> $Xml = Select-Xml -Path $Path -Namespace $Namespace -XPath "//command:name"

The fourth command sends the XML in the $Xml variable to the Format-Table cmdlet. The **Format-Table** command uses a calculated property to get the Node.InnerXML property of each object in the $Xml variable, trim the white space before and after the text, and display it in the table, along with the path to the source file.
PS C:\> $Xml | Format-Table @{Label="Name"; Expression= {($_.node.innerxml).trim()}}, Path -AutoSize

Name                    Path
----                    ----
Export-Counter          C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Get-Counter             C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Get-WinEvent            C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Import-Counter          C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Add-Computer            C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
Add-Content             C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
Checkpoint-Computer     C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
...
```

此範例示範如何使用 **Select xml** Cmdlet 來搜尋以 PowerShell Xml 為基礎的 Cmdlet 說明檔。
在此範例中，我們會搜尋作為每個說明檔標題和說明檔路徑的 Cmdlet 名稱。

第一個命令建立代表針對說明檔使用的 XML 命名空間的雜湊表，並將它儲存在 $Namespace 變數中。

### 範例4：輸入 XML 的不同方式

```
PS C:\> $Xml = @"
<?xml version="1.0" encoding="utf-8"?>
<Book>
  <projects>
    <project name="Book1" date="2009-01-20">
      <editions>
        <edition language="English">En.Book1.com</edition>
        <edition language="German">Ge.Book1.Com</edition>
        <edition language="French">Fr.Book1.com</edition>
        <edition language="Polish">Pl.Book1.com</edition>
      </editions>
    </project>
  </projects>
</Book>
"@

The second command uses the *Content* parameter of **Select-Xml** to specify the XML in the $Xml variable.
PS C:\> Select-Xml -Content $Xml -XPath "//edition" | foreach {$_.node.InnerXML}

En.Book1.com
Ge.Book1.Com
Fr.Book1.com
Pl.Book1.com

The third command is equivalent to the second. It uses a pipeline operator (|) to send the XML in the $Xml variable to the **Select-Xml** cmdlet.
PS C:\> $Xml | Select-Xml -XPath "//edition" | foreach {$_.node.InnerXML}

En.Book1.com
Ge.Book1.Com
Fr.Book1.com
Pl.Book1.com
```

此範例顯示兩種不同的方式，可將 XML 傳送至 **Select xml** Cmdlet。

第一個命令會將包含 XML 的字串儲存在 $Xml 變數中。
(如需有關 here-string 的詳細資訊，請參閱 about_Quoting_Rules)。

### 範例5：使用預設的 xmlns 命名空間

```
PS C:\> $SnippetNamespace = @{snip = "http://schemas.microsoft.com/PowerShell/Snippets"}

The second command uses the **Select-Xml** cmdlet to get the content of the Title element of each snippet. It uses the *Path* parameter to specify the Snippets directory and the *Namespace* parameter to specify the namespace in the $SnippetNamespace variable. The value of the *XPath* parameter is the "snip" namespace key, a colon (:), and the name of the Title element.The command uses a pipeline operator (|) to send each **Node** property that **Select-Xml** returns to the ForEach-Object cmdlet, which gets the title in the value of the **InnerXml** property of the node.
PS C:\> Select-Xml -Path $Home\Documents\WindowsPowerShell\Snippets -Namespace $SnippetNamespace -XPath "//snip:Title" | foreach {$_.Node.Innerxml}
```

此範例示範如何搭配使用 default xmlns 命名空間的 XML 檔來使用 **Select xml** Cmdlet。
此範例取得 Windows PowerShell ISE 使用者建立的程式碼片段檔案的標題。
如需程式碼片段的相關資訊，請參閱 New-IseSnippet。

第一個命令會針對程式碼片段為 XML 檔案使用的預設命名空間建立一個雜湊表，並將它指派給 $SnippetNamespace 變數。
雜湊表值是在程式碼片段 XML 中的 XMLNS 結構描述 URI。
雜湊表索引鍵名稱（剪取）是任意的。
您可以使用任何未保留的名稱，但不能使用 xmlns。

## PARAMETERS

### -Content

指定包含要搜尋的 XML 字串。
您也可以透過管線將字串傳送至 **Select-Xml** 。

```yaml
Type: System.String[]
Parameter Sets: Content
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定要搜尋的 XML 檔案的路徑和檔案名稱。
與 *Path* 不同， *LiteralPath* 參數值將完全依照其輸入值來使用。
沒有字元會被視為萬用字元。
如果路徑包含逸出字元，請將它括在單引號中。
單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Namespace

指定用於 XML 的命名空間雜湊表。
使用格式 @ { \<namespaceName\>  =  \<namespaceValue\> }。

當 XML 使用預設命名空間（以 xmlns 開頭）時，請為命名空間名稱使用任意索引鍵。
您無法使用 xmlns。
在 XPath 語句中，在每個節點名稱前面加上命名空間名稱和冒號，例如//namespaceName： Node。

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定要搜尋的 XML 檔案的路徑和檔案名稱。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Xml

指定一或多個 XML 節點。

XML 文件將會視為 XML 節點的集合處理。
如果您使用管線將 XML 檔傳送至 **Select-xml** ，則每個檔節點都會在通過管線時分開搜尋。

```yaml
Type: System.Xml.XmlNode[]
Parameter Sets: Xml
Aliases: Node

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -XPath

指定 XPath 搜尋查詢。
查詢語言會區分大小寫。
這是必要參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String 或 System.Xml.XmlNode

您可以使用管線將路徑或 XML 節點傳送至此 Cmdlet。

## 輸出

### Microsoft.PowerShell.Commands.SelectXmlInfo

## 注意

* XPath 是一種設計來識別 XML 文件組件的標準語言。 如需有關 XPath 語言的詳細資訊，請參閱 MSDN library 中[事件選取專案](https://msdn.microsoft.com/library/aa385231)的 [ [xpath 參考](https://msdn.microsoft.com/library/ms256115)] 和 [選取篩選] 區段。

## 相關連結

[ConvertTo-Xml](ConvertTo-Xml.md)
