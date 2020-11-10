---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-xml?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Xml
ms.openlocfilehash: d3cadbc6ca08741f8e747ad59456e5b6924e1688
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94386905"
---
# <span data-ttu-id="74c35-103">Select-Xml</span><span class="sxs-lookup"><span data-stu-id="74c35-103">Select-Xml</span></span>

## <span data-ttu-id="74c35-104">概要</span><span class="sxs-lookup"><span data-stu-id="74c35-104">SYNOPSIS</span></span>
<span data-ttu-id="74c35-105">尋找 XML 字串或文件中的文字。</span><span class="sxs-lookup"><span data-stu-id="74c35-105">Finds text in an XML string or document.</span></span>

## <span data-ttu-id="74c35-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="74c35-106">SYNTAX</span></span>

### <span data-ttu-id="74c35-107">Xml (預設值)</span><span class="sxs-lookup"><span data-stu-id="74c35-107">Xml (Default)</span></span>

```
Select-Xml [-Xml] <XmlNode[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### <span data-ttu-id="74c35-108">路徑</span><span class="sxs-lookup"><span data-stu-id="74c35-108">Path</span></span>

```
Select-Xml [-Path] <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### <span data-ttu-id="74c35-109">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="74c35-109">LiteralPath</span></span>

```
Select-Xml -LiteralPath <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### <span data-ttu-id="74c35-110">Content</span><span class="sxs-lookup"><span data-stu-id="74c35-110">Content</span></span>

```
Select-Xml -Content <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

## <span data-ttu-id="74c35-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="74c35-111">DESCRIPTION</span></span>

<span data-ttu-id="74c35-112">**Select xml** Cmdlet 可讓您使用 XPath 查詢來搜尋 Xml 字串和檔中的文字。</span><span class="sxs-lookup"><span data-stu-id="74c35-112">The **Select-Xml** cmdlet lets you use XPath queries to search for text in XML strings and documents.</span></span>
<span data-ttu-id="74c35-113">輸入 XPath 查詢，並使用 *Content* 、 *Path* 或 *Xml* 參數指定要搜尋的 Xml。</span><span class="sxs-lookup"><span data-stu-id="74c35-113">Enter an XPath query, and use the *Content* , *Path* , or *Xml* parameter to specify the XML to be searched.</span></span>

## <span data-ttu-id="74c35-114">範例</span><span class="sxs-lookup"><span data-stu-id="74c35-114">EXAMPLES</span></span>

### <span data-ttu-id="74c35-115">範例1：選取 AliasProperty 節點</span><span class="sxs-lookup"><span data-stu-id="74c35-115">Example 1: Select AliasProperty nodes</span></span>

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

<span data-ttu-id="74c35-116">此範例取得 Types.ps1xml 中的別名屬性。</span><span class="sxs-lookup"><span data-stu-id="74c35-116">This example gets the alias properties in the Types.ps1xml.</span></span>
<span data-ttu-id="74c35-117">(如需此檔案的相關資訊，請參閱 about_Types.ps1xml)。</span><span class="sxs-lookup"><span data-stu-id="74c35-117">(For information about this file, see about_Types.ps1xml.)</span></span>

<span data-ttu-id="74c35-118">第一個命令將 Types.ps1xml 檔案的路徑儲存在 $Path 變數中。</span><span class="sxs-lookup"><span data-stu-id="74c35-118">The first command saves the path to the Types.ps1xml file in the $Path variable.</span></span>

<span data-ttu-id="74c35-119">第二個命令將 AliasProperty 節點的 XML 路徑儲存在 $XPath 變數中。</span><span class="sxs-lookup"><span data-stu-id="74c35-119">The second command saves the XML path to the AliasProperty node in the $XPath variable.</span></span>

<span data-ttu-id="74c35-120">第三個命令使用 **Select-Xml** Cmdlet 取得由 Types.ps1xml 檔案的 XPath 陳述式所識別的 AliasProperty 節點。</span><span class="sxs-lookup"><span data-stu-id="74c35-120">The third command uses the **Select-Xml** cmdlet to get the AliasProperty nodes that are identified by the XPath statement from the Types.ps1xml file.</span></span>
<span data-ttu-id="74c35-121">此命令會使用管線運算子將 AliasProperty 節點傳送至 Select-Object Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="74c35-121">The command uses a pipeline operator to send the AliasProperty nodes to the Select-Object cmdlet.</span></span>
<span data-ttu-id="74c35-122">*ExpandProperty* 參數會展開 **Node** 物件，並傳回其 Name 和 ReferencedMemberName 屬性。</span><span class="sxs-lookup"><span data-stu-id="74c35-122">The *ExpandProperty* parameter expands the **Node** object and returns its Name and ReferencedMemberName properties.</span></span>

<span data-ttu-id="74c35-123">結果顯示 Types.ps1xml 檔案中每個別名屬性的 Name 和 ReferencedMemberName。</span><span class="sxs-lookup"><span data-stu-id="74c35-123">The result shows the Name and ReferencedMemberName of each alias property in the Types.ps1xml file.</span></span>
<span data-ttu-id="74c35-124">例如，有一個 **Count** 屬性是 **Length** 屬性的別名。</span><span class="sxs-lookup"><span data-stu-id="74c35-124">For example, there is a **Count** property that is an alias of the **Length** property.</span></span>

### <span data-ttu-id="74c35-125">範例2：輸入 XML 檔</span><span class="sxs-lookup"><span data-stu-id="74c35-125">Example 2: Input an XML document</span></span>

```
PS C:\> [xml]$Types = Get-Content $Pshome\Types.ps1xml
PS C:\> Select-Xml -Xml $Types -XPath "//MethodName"
```

<span data-ttu-id="74c35-126">這個範例示範如何使用 *xml* 參數，將 xml 檔提供給 **Select xml** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="74c35-126">This example shows how to use the *XML* parameter to provide an XML document to the **Select-Xml** cmdlet.</span></span>

<span data-ttu-id="74c35-127">第一個命令會使用 Get-Content Cmdlet 來取得 Types.ps1xml 檔案的內容，並將其儲存在 $Types 變數中。</span><span class="sxs-lookup"><span data-stu-id="74c35-127">The first command uses the Get-Content cmdlet to get the content of the Types.ps1xml file and save it in the $Types variable.</span></span>
<span data-ttu-id="74c35-128">Xml 會將 \[ \] 變數轉換成 xml 物件。</span><span class="sxs-lookup"><span data-stu-id="74c35-128">The \[xml\] casts the variable as an XML object.</span></span>

<span data-ttu-id="74c35-129">第二個命令使用 **Select-Xml** Cmdlet 取得 Types.ps1xml 檔案中的 MethodName 節點。</span><span class="sxs-lookup"><span data-stu-id="74c35-129">The second command uses the **Select-Xml** cmdlet to get the MethodName nodes in the Types.ps1xml file.</span></span>
<span data-ttu-id="74c35-130">此命令使用 *Xml* 參數指定 $Types 變數中的 XML 內容，以及使用 *XPath* 參數指定 MethodName 節點的路徑。</span><span class="sxs-lookup"><span data-stu-id="74c35-130">The command uses the *Xml* parameter to specify the XML content in the $Types variable and the *XPath* parameter to specify the path to the MethodName node.</span></span>

### <span data-ttu-id="74c35-131">範例3：搜尋 PowerShell 說明檔</span><span class="sxs-lookup"><span data-stu-id="74c35-131">Example 3: Search PowerShell Help files</span></span>

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

<span data-ttu-id="74c35-132">此範例示範如何使用 **Select xml** Cmdlet 來搜尋以 PowerShell Xml 為基礎的 Cmdlet 說明檔。</span><span class="sxs-lookup"><span data-stu-id="74c35-132">This example shows how to use the **Select-Xml** cmdlet to search the PowerShell XML-based cmdlet help files.</span></span>
<span data-ttu-id="74c35-133">在此範例中，我們會搜尋作為每個說明檔標題和說明檔路徑的 Cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="74c35-133">In this example, we'll search for the cmdlet name that serves as a title for each help file and the path to the help file.</span></span>

<span data-ttu-id="74c35-134">第一個命令建立代表針對說明檔使用的 XML 命名空間的雜湊表，並將它儲存在 $Namespace 變數中。</span><span class="sxs-lookup"><span data-stu-id="74c35-134">The first command creates a hash table that represents the XML namespace that is used for the help files and saves it in the $Namespace variable.</span></span>

### <span data-ttu-id="74c35-135">範例4：輸入 XML 的不同方式</span><span class="sxs-lookup"><span data-stu-id="74c35-135">Example 4: Different ways to input XML</span></span>

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

<span data-ttu-id="74c35-136">此範例顯示兩種不同的方式，可將 XML 傳送至 **Select xml** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="74c35-136">This example shows two different ways to send XML to the **Select-Xml** cmdlet.</span></span>

<span data-ttu-id="74c35-137">第一個命令會將包含 XML 的字串儲存在 $Xml 變數中。</span><span class="sxs-lookup"><span data-stu-id="74c35-137">The first command saves a here-string that contains XML in the $Xml variable.</span></span>
<span data-ttu-id="74c35-138">(如需有關 here-string 的詳細資訊，請參閱 about_Quoting_Rules)。</span><span class="sxs-lookup"><span data-stu-id="74c35-138">(For more information about here-strings, see about_Quoting_Rules.)</span></span>

### <span data-ttu-id="74c35-139">範例5：使用預設的 xmlns 命名空間</span><span class="sxs-lookup"><span data-stu-id="74c35-139">Example 5: Use the default xmlns namespace</span></span>

```
PS C:\> $SnippetNamespace = @{snip = "http://schemas.microsoft.com/PowerShell/Snippets"}

The second command uses the **Select-Xml** cmdlet to get the content of the Title element of each snippet. It uses the *Path* parameter to specify the Snippets directory and the *Namespace* parameter to specify the namespace in the $SnippetNamespace variable. The value of the *XPath* parameter is the "snip" namespace key, a colon (:), and the name of the Title element.The command uses a pipeline operator (|) to send each **Node** property that **Select-Xml** returns to the ForEach-Object cmdlet, which gets the title in the value of the **InnerXml** property of the node.
PS C:\> Select-Xml -Path $Home\Documents\WindowsPowerShell\Snippets -Namespace $SnippetNamespace -XPath "//snip:Title" | foreach {$_.Node.Innerxml}
```

<span data-ttu-id="74c35-140">此範例示範如何搭配使用 default xmlns 命名空間的 XML 檔來使用 **Select xml** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="74c35-140">This example shows how to use the **Select-Xml** cmdlet with XML documents that use the default xmlns namespace.</span></span>
<span data-ttu-id="74c35-141">此範例取得 Windows PowerShell ISE 使用者建立的程式碼片段檔案的標題。</span><span class="sxs-lookup"><span data-stu-id="74c35-141">The example gets the titles of Windows PowerShell ISE user-created snippet files.</span></span>
<span data-ttu-id="74c35-142">如需程式碼片段的相關資訊，請參閱 New-IseSnippet。</span><span class="sxs-lookup"><span data-stu-id="74c35-142">For information about snippets, see New-IseSnippet.</span></span>

<span data-ttu-id="74c35-143">第一個命令會針對程式碼片段為 XML 檔案使用的預設命名空間建立一個雜湊表，並將它指派給 $SnippetNamespace 變數。</span><span class="sxs-lookup"><span data-stu-id="74c35-143">The first command creates a hash table for the default namespace that snippet XML files use and assigns it to the $SnippetNamespace variable.</span></span>
<span data-ttu-id="74c35-144">雜湊表值是在程式碼片段 XML 中的 XMLNS 結構描述 URI。</span><span class="sxs-lookup"><span data-stu-id="74c35-144">The hash table value is the XMLNS schema URI in the snippet XML.</span></span>
<span data-ttu-id="74c35-145">雜湊表索引鍵名稱（剪取）是任意的。</span><span class="sxs-lookup"><span data-stu-id="74c35-145">The hash table key name, snip, is arbitrary.</span></span>
<span data-ttu-id="74c35-146">您可以使用任何未保留的名稱，但不能使用 xmlns。</span><span class="sxs-lookup"><span data-stu-id="74c35-146">You can use any name that is not reserved, but you cannot use xmlns.</span></span>

## <span data-ttu-id="74c35-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="74c35-147">PARAMETERS</span></span>

### <span data-ttu-id="74c35-148">-Content</span><span class="sxs-lookup"><span data-stu-id="74c35-148">-Content</span></span>

<span data-ttu-id="74c35-149">指定包含要搜尋的 XML 字串。</span><span class="sxs-lookup"><span data-stu-id="74c35-149">Specifies a string that contains the XML to search.</span></span>
<span data-ttu-id="74c35-150">您也可以透過管線將字串傳送至 **Select-Xml** 。</span><span class="sxs-lookup"><span data-stu-id="74c35-150">You can also pipe strings to **Select-Xml**.</span></span>

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

### <span data-ttu-id="74c35-151">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="74c35-151">-LiteralPath</span></span>

<span data-ttu-id="74c35-152">指定要搜尋的 XML 檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="74c35-152">Specifies the paths and file names of the XML files to search.</span></span>
<span data-ttu-id="74c35-153">與 *Path* 不同， *LiteralPath* 參數值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="74c35-153">Unlike *Path* , the value of the *LiteralPath* parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="74c35-154">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="74c35-154">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="74c35-155">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="74c35-155">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="74c35-156">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="74c35-156">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="74c35-157">-Namespace</span><span class="sxs-lookup"><span data-stu-id="74c35-157">-Namespace</span></span>

<span data-ttu-id="74c35-158">指定用於 XML 的命名空間雜湊表。</span><span class="sxs-lookup"><span data-stu-id="74c35-158">Specifies a hash table of the namespaces used in the XML.</span></span>
<span data-ttu-id="74c35-159">使用格式 @ { \<namespaceName\>  =  \<namespaceValue\> }。</span><span class="sxs-lookup"><span data-stu-id="74c35-159">Use the format @{\<namespaceName\> = \<namespaceValue\>}.</span></span>

<span data-ttu-id="74c35-160">當 XML 使用預設命名空間（以 xmlns 開頭）時，請為命名空間名稱使用任意索引鍵。</span><span class="sxs-lookup"><span data-stu-id="74c35-160">When the XML uses the default namespace, which begins with xmlns, use an arbitrary key for the namespace name.</span></span>
<span data-ttu-id="74c35-161">您無法使用 xmlns。</span><span class="sxs-lookup"><span data-stu-id="74c35-161">You cannot use xmlns.</span></span>
<span data-ttu-id="74c35-162">在 XPath 語句中，在每個節點名稱前面加上命名空間名稱和冒號，例如//namespaceName： Node。</span><span class="sxs-lookup"><span data-stu-id="74c35-162">In the XPath statement, prefix each node name with the namespace name and a colon, such as //namespaceName:Node.</span></span>

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

### <span data-ttu-id="74c35-163">-Path</span><span class="sxs-lookup"><span data-stu-id="74c35-163">-Path</span></span>

<span data-ttu-id="74c35-164">指定要搜尋的 XML 檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="74c35-164">Specifies the path and file names of the XML files to search.</span></span>
<span data-ttu-id="74c35-165">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="74c35-165">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="74c35-166">-Xml</span><span class="sxs-lookup"><span data-stu-id="74c35-166">-Xml</span></span>

<span data-ttu-id="74c35-167">指定一或多個 XML 節點。</span><span class="sxs-lookup"><span data-stu-id="74c35-167">Specifies one or more XML nodes.</span></span>

<span data-ttu-id="74c35-168">XML 文件將會視為 XML 節點的集合處理。</span><span class="sxs-lookup"><span data-stu-id="74c35-168">An XML document will be processed as a collection of XML nodes.</span></span>
<span data-ttu-id="74c35-169">如果您使用管線將 XML 檔傳送至 **Select-xml** ，則每個檔節點都會在通過管線時分開搜尋。</span><span class="sxs-lookup"><span data-stu-id="74c35-169">If you pipe an XML document to **Select-Xml** , each document node will be searched separately as it comes through the pipeline.</span></span>

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

### <span data-ttu-id="74c35-170">-XPath</span><span class="sxs-lookup"><span data-stu-id="74c35-170">-XPath</span></span>

<span data-ttu-id="74c35-171">指定 XPath 搜尋查詢。</span><span class="sxs-lookup"><span data-stu-id="74c35-171">Specifies an XPath search query.</span></span>
<span data-ttu-id="74c35-172">查詢語言會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="74c35-172">The query language is case-sensitive.</span></span>
<span data-ttu-id="74c35-173">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="74c35-173">This parameter is required.</span></span>

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

### <span data-ttu-id="74c35-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="74c35-174">CommonParameters</span></span>

<span data-ttu-id="74c35-175">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="74c35-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="74c35-176">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="74c35-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="74c35-177">輸入</span><span class="sxs-lookup"><span data-stu-id="74c35-177">INPUTS</span></span>

### <span data-ttu-id="74c35-178">System.String 或 System.Xml.XmlNode</span><span class="sxs-lookup"><span data-stu-id="74c35-178">System.String or System.Xml.XmlNode</span></span>

<span data-ttu-id="74c35-179">您可以使用管線將路徑或 XML 節點傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="74c35-179">You can pipe a path or XML node to this cmdlet.</span></span>

## <span data-ttu-id="74c35-180">輸出</span><span class="sxs-lookup"><span data-stu-id="74c35-180">OUTPUTS</span></span>

### <span data-ttu-id="74c35-181">Microsoft.PowerShell.Commands.SelectXmlInfo</span><span class="sxs-lookup"><span data-stu-id="74c35-181">Microsoft.PowerShell.Commands.SelectXmlInfo</span></span>

## <span data-ttu-id="74c35-182">注意</span><span class="sxs-lookup"><span data-stu-id="74c35-182">NOTES</span></span>

<span data-ttu-id="74c35-183">XPath 是一種設計來識別 XML 文件組件的標準語言。</span><span class="sxs-lookup"><span data-stu-id="74c35-183">XPath is a standard language that is designed to identify parts of an XML document.</span></span> <span data-ttu-id="74c35-184">如需有關 XPath 語言的詳細資訊，請參閱[事件選取專案](/previous-versions//aa385231(v=vs.85))的 [ [xpath 參考](/dotnet/standard/data/xml/select-nodes-using-xpath-navigation)] 和 [選取篩選] 區段。</span><span class="sxs-lookup"><span data-stu-id="74c35-184">For more information about the XPath language, see [XPath Reference](/dotnet/standard/data/xml/select-nodes-using-xpath-navigation) and the Selection Filters section of [Event Selection](/previous-versions//aa385231(v=vs.85)).</span></span>

## <span data-ttu-id="74c35-185">相關連結</span><span class="sxs-lookup"><span data-stu-id="74c35-185">RELATED LINKS</span></span>

[<span data-ttu-id="74c35-186">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="74c35-186">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)
