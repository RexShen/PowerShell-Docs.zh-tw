---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-clixml?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Clixml
ms.openlocfilehash: 8e1557bca62ade784bd5b4ed5cb170bbf079b423
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "93206124"
---
# <span data-ttu-id="6245f-103">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="6245f-103">Export-Clixml</span></span>

## <span data-ttu-id="6245f-104">概要</span><span class="sxs-lookup"><span data-stu-id="6245f-104">SYNOPSIS</span></span>
<span data-ttu-id="6245f-105">建立一或多個物件的 XML 表示法，並將它儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="6245f-105">Creates an XML-based representation of an object or objects and stores it in a file.</span></span>

## <span data-ttu-id="6245f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6245f-106">SYNTAX</span></span>

### <span data-ttu-id="6245f-107">ByPath (預設值)</span><span class="sxs-lookup"><span data-stu-id="6245f-107">ByPath (Default)</span></span>

```
Export-Clixml [-Depth <Int32>] [-Path] <String> -InputObject <PSObject> [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6245f-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="6245f-108">ByLiteralPath</span></span>

```
Export-Clixml [-Depth <Int32>] -LiteralPath <String> -InputObject <PSObject> [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6245f-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6245f-109">DESCRIPTION</span></span>

<span data-ttu-id="6245f-110">`Export-Clixml`Cmdlet 會建立通用語言基礎結構 (CLI) 物件或物件的 XML 標記法，並將它儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="6245f-110">The `Export-Clixml` cmdlet creates a Common Language Infrastructure (CLI) XML-based representation of an object or objects and stores it in a file.</span></span> <span data-ttu-id="6245f-111">然後，您可以使用 `Import-Clixml` Cmdlet，根據該檔案的內容重新建立已儲存的物件。</span><span class="sxs-lookup"><span data-stu-id="6245f-111">You can then use the `Import-Clixml` cmdlet to recreate the saved object based on the contents of that file.</span></span>
<span data-ttu-id="6245f-112">如需 CLI 的詳細資訊，請參閱 [語言獨立性](/dotnet/standard/language-independence)。</span><span class="sxs-lookup"><span data-stu-id="6245f-112">For more information about CLI, see [Language independence](/dotnet/standard/language-independence).</span></span>

<span data-ttu-id="6245f-113">這個 Cmdlet 類似于 `ConvertTo-Xml` ，但會將 `Export-Clixml` 產生的 XML 儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="6245f-113">This cmdlet is similar to `ConvertTo-Xml`, except that `Export-Clixml` stores the resulting XML in a file.</span></span> <span data-ttu-id="6245f-114">`ConvertTo-XML` 傳回 XML，讓您可以在 PowerShell 中繼續處理。</span><span class="sxs-lookup"><span data-stu-id="6245f-114">`ConvertTo-XML` returns the XML, so you can continue to process it in PowerShell.</span></span>

<span data-ttu-id="6245f-115">`Export-Clixml`在 Windows 電腦上有一個很重要的用途，就是以 XML 形式安全地匯出認證和安全字串。</span><span class="sxs-lookup"><span data-stu-id="6245f-115">A valuable use of `Export-Clixml` on Windows computers is to export credentials and secure strings securely as XML.</span></span> <span data-ttu-id="6245f-116">如需範例，請參閱範例3。</span><span class="sxs-lookup"><span data-stu-id="6245f-116">For an example, see Example 3.</span></span>

## <span data-ttu-id="6245f-117">範例</span><span class="sxs-lookup"><span data-stu-id="6245f-117">EXAMPLES</span></span>

### <span data-ttu-id="6245f-118">範例1：將字串匯出至 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="6245f-118">Example 1: Export a string to an XML file</span></span>

<span data-ttu-id="6245f-119">這個範例會建立 XML 檔案，該檔案會儲存在目前的目錄中， **此為測試** 的字串表示。</span><span class="sxs-lookup"><span data-stu-id="6245f-119">This example creates an XML file that stores in the current directory, a representation of the string **This is a test** .</span></span>

```powershell
"This is a test" | Export-Clixml -Path .\sample.xml
```

<span data-ttu-id="6245f-120">此字串 `This is a test` 會沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="6245f-120">The string `This is a test` is sent down the pipeline.</span></span> <span data-ttu-id="6245f-121">`Export-Clixml` 使用 **Path** 參數來建立 `sample.xml` 在目前的目錄中名為的 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="6245f-121">`Export-Clixml` uses the **Path** parameter to create an XML file named `sample.xml` in the current directory.</span></span>

### <span data-ttu-id="6245f-122">範例2：將物件匯出至 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="6245f-122">Example 2: Export an object to an XML file</span></span>

<span data-ttu-id="6245f-123">此範例會示範如何將物件匯出至 XML 檔案，然後從檔案匯入 XML 來建立物件。</span><span class="sxs-lookup"><span data-stu-id="6245f-123">This example shows how to export an object to an XML file and then create an object by importing the XML from the file.</span></span>

```powershell
Get-Acl C:\test.txt | Export-Clixml -Path .\FileACL.xml
$fileacl = Import-Clixml -Path .\FileACL.xml
```

<span data-ttu-id="6245f-124">`Get-Acl`Cmdlet 會取得檔案的安全描述項 `Test.txt` 。</span><span class="sxs-lookup"><span data-stu-id="6245f-124">The `Get-Acl` cmdlet gets the security descriptor of the `Test.txt` file.</span></span> <span data-ttu-id="6245f-125">它會將物件沿著管線向下傳送，以將安全描述項傳遞給 `Export-Clixml` 。</span><span class="sxs-lookup"><span data-stu-id="6245f-125">It sends the object down the pipeline to pass the security descriptor to `Export-Clixml`.</span></span> <span data-ttu-id="6245f-126">以 XML 為基礎的物件表示會儲存在名為的檔案中 `FileACL.xml` 。</span><span class="sxs-lookup"><span data-stu-id="6245f-126">The XML-based representation of the object is stored in a file named `FileACL.xml`.</span></span>

<span data-ttu-id="6245f-127">`Import-Clixml`Cmdlet 會從檔案中的 XML 建立物件 `FileACL.xml` 。</span><span class="sxs-lookup"><span data-stu-id="6245f-127">The `Import-Clixml` cmdlet creates an object from the XML in the `FileACL.xml` file.</span></span> <span data-ttu-id="6245f-128">然後，它會將物件儲存在 `$fileacl` 變數中。</span><span class="sxs-lookup"><span data-stu-id="6245f-128">Then, it saves the object in the `$fileacl` variable.</span></span>

### <span data-ttu-id="6245f-129">範例3：在 Windows 上加密匯出的認證物件</span><span class="sxs-lookup"><span data-stu-id="6245f-129">Example 3: Encrypt an exported credential object on Windows</span></span>

<span data-ttu-id="6245f-130">在此範例中，藉由執行 Cmdlet 來儲存在變數中的認證 `$Credential` `Get-Credential` ，您可以執行 `Export-Clixml` Cmdlet 以將認證儲存至磁片。</span><span class="sxs-lookup"><span data-stu-id="6245f-130">In this example, given a credential that you've stored in the `$Credential` variable by running the `Get-Credential` cmdlet, you can run the `Export-Clixml` cmdlet to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6245f-131">`Export-Clixml` 只會在 Windows 上匯出加密的認證。</span><span class="sxs-lookup"><span data-stu-id="6245f-131">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="6245f-132">在非 Windows 作業系統（例如 macOS 和 Linux）上，認證會以純文字格式匯出，並儲存為 Unicode 字元陣列。</span><span class="sxs-lookup"><span data-stu-id="6245f-132">On non-Windows operating systems such as macOS and Linux, credentials are exported as a plain text stored as a Unicode character array.</span></span> <span data-ttu-id="6245f-133">這會提供一些模糊化，但不提供加密。</span><span class="sxs-lookup"><span data-stu-id="6245f-133">This provides some obfuscation but does not provide encryption.</span></span>

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

<span data-ttu-id="6245f-134">此 `Export-Clixml` Cmdlet 會使用 Windows [資料保護 API](/previous-versions/windows/apps/hh464970(v=win.10))來加密認證物件。</span><span class="sxs-lookup"><span data-stu-id="6245f-134">The `Export-Clixml` cmdlet encrypts credential objects by using the Windows [Data Protection API](/previous-versions/windows/apps/hh464970(v=win.10)).</span></span> <span data-ttu-id="6245f-135">加密可確保只有電腦上的使用者帳戶可以解密 credential 物件的內容。</span><span class="sxs-lookup"><span data-stu-id="6245f-135">The encryption ensures that only your user account on only that computer can decrypt the contents of the credential object.</span></span>
<span data-ttu-id="6245f-136">匯出的檔案 `CLIXML` 不能用於不同的電腦或不同的使用者。</span><span class="sxs-lookup"><span data-stu-id="6245f-136">The exported `CLIXML` file can't be used on a different computer or by a different user.</span></span>

<span data-ttu-id="6245f-137">在此範例中，用來儲存認證的檔案會以表示 `TestScript.ps1.credential` 。</span><span class="sxs-lookup"><span data-stu-id="6245f-137">In the example, the file in which the credential is stored is represented by `TestScript.ps1.credential`.</span></span> <span data-ttu-id="6245f-138">將 **>testscript** 取代為您要用來載入認證的腳本名稱。</span><span class="sxs-lookup"><span data-stu-id="6245f-138">Replace **TestScript** with the name of the script with which you're loading the credential.</span></span>

<span data-ttu-id="6245f-139">您會將管線下的認證物件傳送至 `Export-Clixml` ，並將它儲存到 `$Credxmlpath` 您在第一個命令中指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="6245f-139">You send the credential object down the pipeline to `Export-Clixml`, and save it to the path, `$Credxmlpath`, that you specified in the first command.</span></span>

<span data-ttu-id="6245f-140">若要將認證自動匯入至您的指令碼，請執行最後兩個命令。</span><span class="sxs-lookup"><span data-stu-id="6245f-140">To import the credential automatically into your script, run the final two commands.</span></span> <span data-ttu-id="6245f-141">執行 `Import-Clixml` 以將安全的認證物件匯入您的腳本中。</span><span class="sxs-lookup"><span data-stu-id="6245f-141">Run `Import-Clixml` to import the secured credential object into your script.</span></span> <span data-ttu-id="6245f-142">這項匯入消除了在腳本中公開純文字密碼的風險。</span><span class="sxs-lookup"><span data-stu-id="6245f-142">This import eliminates the risk of exposing plain-text passwords in your script.</span></span>

### <span data-ttu-id="6245f-143">範例4：在 Linux 或 macOS 上匯出認證物件</span><span class="sxs-lookup"><span data-stu-id="6245f-143">Example 4: Exporting a credential object on Linux or macOS</span></span>

<span data-ttu-id="6245f-144">在此範例中，我們會使用 Cmdlet 在變數中建立 **PSCredential** `$Credential` `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="6245f-144">In this example, we create a **PSCredential** in the `$Credential` variable using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="6245f-145">然後我們會使用 `Export-Clixml` 將認證儲存至磁片。</span><span class="sxs-lookup"><span data-stu-id="6245f-145">Then we use `Export-Clixml` to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6245f-146">`Export-Clixml` 只會在 Windows 上匯出加密的認證。</span><span class="sxs-lookup"><span data-stu-id="6245f-146">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="6245f-147">在非 Windows 作業系統（例如 macOS 和 Linux）上，認證會以純文字格式匯出，並儲存為 Unicode 字元陣列。</span><span class="sxs-lookup"><span data-stu-id="6245f-147">On non-Windows operating systems such as macOS and Linux, credentials are exported as a plain text stored as a Unicode character array.</span></span> <span data-ttu-id="6245f-148">這會提供一些模糊化，但不提供加密。</span><span class="sxs-lookup"><span data-stu-id="6245f-148">This provides some obfuscation but does not provide encryption.</span></span>

```powershell
PS> $Credential = Get-Credential

PowerShell credential request
Enter your credentials.
User: User1
Password for user User1: ********

PS> $Credential | Export-Clixml ./cred2.xml
PS> Get-Content ./cred2.xml

...
    <Props>
      <S N="UserName">User1</S>
      <SS N="Password">700061007300730077006f0072006400</SS>
    </Props>
...

PS> 'password' | Format-Hex -Encoding unicode

   Label: String (System.String) <52D60C91>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 70 00 61 00 73 00 73 00 77 00 6F 00 72 00 64 00 p a s s w o r d
```

<span data-ttu-id="6245f-149">`Get-Content`此範例中的輸出已截斷，以專注于 XML 檔案中的認證資訊。</span><span class="sxs-lookup"><span data-stu-id="6245f-149">The output of `Get-Content` in this example has been truncate to focus on the credential information in the XML file.</span></span> <span data-ttu-id="6245f-150">請注意，密碼的純文字值會儲存在 XML 檔案中，做為經過驗證的 Unicode 字元陣列 `Format-Hex` 。</span><span class="sxs-lookup"><span data-stu-id="6245f-150">Note that the plain text value of the password is stored in the XML file as a Unicode character array as proven by `Format-Hex`.</span></span> <span data-ttu-id="6245f-151">因此，此值經過編碼，但未加密。</span><span class="sxs-lookup"><span data-stu-id="6245f-151">So the value is encoded but not encrypted.</span></span>

## <span data-ttu-id="6245f-152">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6245f-152">PARAMETERS</span></span>

### <span data-ttu-id="6245f-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6245f-153">-Confirm</span></span>

<span data-ttu-id="6245f-154">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="6245f-154">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6245f-155">-Depth</span><span class="sxs-lookup"><span data-stu-id="6245f-155">-Depth</span></span>

<span data-ttu-id="6245f-156">指定 XML 表示法中包含多少層的內含物件。</span><span class="sxs-lookup"><span data-stu-id="6245f-156">Specifies how many levels of contained objects are included in the XML representation.</span></span> <span data-ttu-id="6245f-157">預設值是 `2`。</span><span class="sxs-lookup"><span data-stu-id="6245f-157">The default value is `2`.</span></span>

<span data-ttu-id="6245f-158">您可以在檔案中覆寫物件類型的預設值 `Types.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="6245f-158">The default value can be overridden for the object type in the `Types.ps1xml` files.</span></span> <span data-ttu-id="6245f-159">如需詳細資訊，請參閱 [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="6245f-159">For more information, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6245f-160">-Encoding</span><span class="sxs-lookup"><span data-stu-id="6245f-160">-Encoding</span></span>

<span data-ttu-id="6245f-161">指定目標檔案的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="6245f-161">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="6245f-162">預設值是 `utf8NoBOM`。</span><span class="sxs-lookup"><span data-stu-id="6245f-162">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="6245f-163">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="6245f-163">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="6245f-164">`ascii`：使用 ASCII (7 位) 字元集的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="6245f-164">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="6245f-165">`bigendianunicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="6245f-165">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="6245f-166">`bigendianutf32`：使用位元組由大到小的順序，以 UTF-32 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="6245f-166">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="6245f-167">`oem`：針對 MS-DOS 和主控台程式使用預設編碼。</span><span class="sxs-lookup"><span data-stu-id="6245f-167">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="6245f-168">`unicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="6245f-168">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="6245f-169">`utf7`：以 UTF-7 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="6245f-169">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="6245f-170">`utf8`：以 UTF-8 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="6245f-170">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="6245f-171">`utf8BOM`：使用 (BOM) 的位元組順序標記來編碼 UTF-8 格式</span><span class="sxs-lookup"><span data-stu-id="6245f-171">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="6245f-172">`utf8NoBOM`：以不含位元組順序標記的 UTF-8 格式來編碼 (BOM) </span><span class="sxs-lookup"><span data-stu-id="6245f-172">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="6245f-173">`utf32`：以 UTF-32 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="6245f-173">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="6245f-174">從 PowerShell 6.2 開始， **編碼** 參數也會允許已註冊字碼頁的數值識別碼 (例如 `-Encoding 1251`) 或已註冊字碼頁的字串名稱 (例如 `-Encoding "windows-1251"`) 。</span><span class="sxs-lookup"><span data-stu-id="6245f-174">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="6245f-175">如需詳細資訊，請參閱 .NET 檔中的 [編碼字碼頁](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)。</span><span class="sxs-lookup"><span data-stu-id="6245f-175">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="6245f-176">您不再建議使用 **utf-7** \*。</span><span class="sxs-lookup"><span data-stu-id="6245f-176">**UTF-7** \* is no longer recommended to use.</span></span> <span data-ttu-id="6245f-177">在 PowerShell 7.1 中，如果您 `utf7` 針對 **編碼** 參數指定，就會寫入警告。</span><span class="sxs-lookup"><span data-stu-id="6245f-177">In PowerShell 7.1, a warning is written if you specify `utf7` for the **Encoding** parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6245f-178">-Force</span><span class="sxs-lookup"><span data-stu-id="6245f-178">-Force</span></span>

<span data-ttu-id="6245f-179">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="6245f-179">Forces the command to run without asking for user confirmation.</span></span>

<span data-ttu-id="6245f-180">會導致 Cmdlet 清除輸出檔案的唯讀屬性 (如有必要)。</span><span class="sxs-lookup"><span data-stu-id="6245f-180">Causes the cmdlet to clear the read-only attribute of the output file if necessary.</span></span> <span data-ttu-id="6245f-181">當命令完成時，Cmdlet 將會嘗試重設唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="6245f-181">The cmdlet will attempt to reset the read-only attribute when the command completes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6245f-182">-InputObject</span><span class="sxs-lookup"><span data-stu-id="6245f-182">-InputObject</span></span>

<span data-ttu-id="6245f-183">指定要轉換的物件。</span><span class="sxs-lookup"><span data-stu-id="6245f-183">Specifies the object to be converted.</span></span> <span data-ttu-id="6245f-184">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="6245f-184">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="6245f-185">您也可以透過管線將物件傳送至 `Export-Clixml` 。</span><span class="sxs-lookup"><span data-stu-id="6245f-185">You can also pipe objects to `Export-Clixml`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6245f-186">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6245f-186">-LiteralPath</span></span>

<span data-ttu-id="6245f-187">指定將儲存物件之 XML 表示法的檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="6245f-187">Specifies the path to the file where the XML representation of the object will be stored.</span></span> <span data-ttu-id="6245f-188">與 **Path** 不同， **LiteralPath** 參數的值會完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="6245f-188">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="6245f-189">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="6245f-189">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="6245f-190">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="6245f-190">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="6245f-191">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="6245f-191">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6245f-192">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="6245f-192">-NoClobber</span></span>

<span data-ttu-id="6245f-193">指出此 Cmdlet 不會覆寫現有檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="6245f-193">Indicates that the cmdlet doesn't overwrite the contents of an existing file.</span></span> <span data-ttu-id="6245f-194">根據預設，如果檔案存在指定的路徑中， `Export-Clixml` 會覆寫檔案而不發出警告。</span><span class="sxs-lookup"><span data-stu-id="6245f-194">By default, if a file exists in the specified path, `Export-Clixml` overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6245f-195">-Path</span><span class="sxs-lookup"><span data-stu-id="6245f-195">-Path</span></span>

<span data-ttu-id="6245f-196">指定將儲存物件之 XML 表示法的檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="6245f-196">Specifies the path to the file where the XML representation of the object will be stored.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6245f-197">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6245f-197">-WhatIf</span></span>

<span data-ttu-id="6245f-198">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="6245f-198">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="6245f-199">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6245f-199">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6245f-200">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6245f-200">CommonParameters</span></span>

<span data-ttu-id="6245f-201">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6245f-201">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6245f-202">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6245f-202">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6245f-203">輸入</span><span class="sxs-lookup"><span data-stu-id="6245f-203">INPUTS</span></span>

### <span data-ttu-id="6245f-204">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="6245f-204">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="6245f-205">您可以將任何物件管線至 `Export-Clixml` 。</span><span class="sxs-lookup"><span data-stu-id="6245f-205">You can pipeline any object to `Export-Clixml`.</span></span>

## <span data-ttu-id="6245f-206">輸出</span><span class="sxs-lookup"><span data-stu-id="6245f-206">OUTPUTS</span></span>

### <span data-ttu-id="6245f-207">System.IO.FileInfo</span><span class="sxs-lookup"><span data-stu-id="6245f-207">System.IO.FileInfo</span></span>

<span data-ttu-id="6245f-208">`Export-Clixml` 建立包含 XML 的檔案。</span><span class="sxs-lookup"><span data-stu-id="6245f-208">`Export-Clixml` creates a file that contains the XML.</span></span>

## <span data-ttu-id="6245f-209">注意</span><span class="sxs-lookup"><span data-stu-id="6245f-209">NOTES</span></span>

## <span data-ttu-id="6245f-210">相關連結</span><span class="sxs-lookup"><span data-stu-id="6245f-210">RELATED LINKS</span></span>

[<span data-ttu-id="6245f-211">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="6245f-211">ConvertTo-Html</span></span>](ConvertTo-Html.md)

[<span data-ttu-id="6245f-212">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="6245f-212">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="6245f-213">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="6245f-213">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="6245f-214">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="6245f-214">Import-Clixml</span></span>](Import-Clixml.md)

[<span data-ttu-id="6245f-215">Join-Path</span><span class="sxs-lookup"><span data-stu-id="6245f-215">Join-Path</span></span>](../Microsoft.PowerShell.Management/Join-Path.md)

[<span data-ttu-id="6245f-216">將認證安全地儲存在磁碟上</span><span class="sxs-lookup"><span data-stu-id="6245f-216">Securely Store Credentials on Disk</span></span>](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[<span data-ttu-id="6245f-217">使用 PowerShell 將認證傳遞給舊版系統</span><span class="sxs-lookup"><span data-stu-id="6245f-217">Use PowerShell to Pass Credentials to Legacy Systems</span></span>](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

[<span data-ttu-id="6245f-218">Windows.Security.Cryptography.DataProtection</span><span class="sxs-lookup"><span data-stu-id="6245f-218">Windows.Security.Cryptography.DataProtection</span></span>](/uwp/api/windows.security.cryptography.dataprotection)
