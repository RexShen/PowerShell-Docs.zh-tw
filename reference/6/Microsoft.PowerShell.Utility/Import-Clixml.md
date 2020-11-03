---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-clixml?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Clixml
ms.openlocfilehash: 549cb3a33c0020f8033c4a21ccea3f8c2c7ad64c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203776"
---
# <span data-ttu-id="2721c-103">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="2721c-103">Import-Clixml</span></span>

## <span data-ttu-id="2721c-104">概要</span><span class="sxs-lookup"><span data-stu-id="2721c-104">SYNOPSIS</span></span>
<span data-ttu-id="2721c-105">匯入 CLIXML 檔案，並在 PowerShell 中建立對應的物件。</span><span class="sxs-lookup"><span data-stu-id="2721c-105">Imports a CLIXML file and creates corresponding objects in PowerShell.</span></span>

## <span data-ttu-id="2721c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2721c-106">SYNTAX</span></span>

### <span data-ttu-id="2721c-107">ByPath (預設值)</span><span class="sxs-lookup"><span data-stu-id="2721c-107">ByPath (Default)</span></span>

```
Import-Clixml [-Path] <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

### <span data-ttu-id="2721c-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="2721c-108">ByLiteralPath</span></span>

```
Import-Clixml -LiteralPath <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

## <span data-ttu-id="2721c-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2721c-109">DESCRIPTION</span></span>

<span data-ttu-id="2721c-110">指令 `Import-Clixml` 程式會 (CLI) XML 檔案匯入通用語言基礎結構，其中包含代表 Microsoft .NET Framework 物件的資料，並建立 PowerShell 物件。</span><span class="sxs-lookup"><span data-stu-id="2721c-110">The `Import-Clixml` cmdlet imports a Common Language Infrastructure (CLI) XML file with data that represents Microsoft .NET Framework objects and creates the PowerShell objects.</span></span> <span data-ttu-id="2721c-111">如需 CLI 的詳細資訊，請參閱 [語言獨立性](/dotnet/standard/language-independence)。</span><span class="sxs-lookup"><span data-stu-id="2721c-111">For more information about CLI, see [Language independence](/dotnet/standard/language-independence).</span></span>

<span data-ttu-id="2721c-112">`Import-Clixml`在 Windows 電腦上有一個很重要的用途，就是匯入使用來匯出為安全 XML 的認證與安全字串 `Export-Clixml` 。</span><span class="sxs-lookup"><span data-stu-id="2721c-112">A valuable use of `Import-Clixml` on Windows computers is to import credentials and secure strings that were exported as secure XML using `Export-Clixml`.</span></span> <span data-ttu-id="2721c-113">如需範例，請參閱範例2。</span><span class="sxs-lookup"><span data-stu-id="2721c-113">For an example, see Example 2.</span></span>

<span data-ttu-id="2721c-114">`Import-Clixml` 使用位元組順序標記 (BOM) 來偵測檔案的編碼格式。</span><span class="sxs-lookup"><span data-stu-id="2721c-114">`Import-Clixml` uses the byte-order-mark (BOM) to detect the encoding format of the file.</span></span> <span data-ttu-id="2721c-115">如果檔案沒有 BOM，則會假設編碼為 UTF8。</span><span class="sxs-lookup"><span data-stu-id="2721c-115">If the file has no BOM, it assumes the encoding is UTF8.</span></span>

## <span data-ttu-id="2721c-116">範例</span><span class="sxs-lookup"><span data-stu-id="2721c-116">EXAMPLES</span></span>

### <span data-ttu-id="2721c-117">範例 1：匯出序列化的檔案並重新建立物件</span><span class="sxs-lookup"><span data-stu-id="2721c-117">Example 1: Import a serialized file and recreate an object</span></span>

<span data-ttu-id="2721c-118">這個範例會使用 `Export-Clixml` Cmdlet 來儲存所傳回之處理常式資訊的序列化複本 `Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="2721c-118">This example uses the `Export-Clixml` cmdlet to save a serialized copy of the process information returned by `Get-Process`.</span></span> <span data-ttu-id="2721c-119">`Import-Clixml` 抓取序列化檔案的內容，並重新建立儲存在變數中的物件 `$Processes` 。</span><span class="sxs-lookup"><span data-stu-id="2721c-119">`Import-Clixml` retrieves the serialized file's contents and recreates an object that is stored in the `$Processes` variable.</span></span>

```powershell
Get-Process | Export-Clixml -Path .\pi.xml
$Processes = Import-Clixml -Path .\pi.xml
```

### <span data-ttu-id="2721c-120">範例 2：匯入安全認證物件</span><span class="sxs-lookup"><span data-stu-id="2721c-120">Example 2: Import a secure credential object</span></span>

<span data-ttu-id="2721c-121">在此範例中，藉由執行 Cmdlet 來儲存在變數中的認證 `$Credential` `Get-Credential` ，您可以執行 `Export-Clixml` Cmdlet 以將認證儲存至磁片。</span><span class="sxs-lookup"><span data-stu-id="2721c-121">In this example, given a credential that you've stored in the `$Credential` variable by running the `Get-Credential` cmdlet, you can run the `Export-Clixml` cmdlet to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2721c-122">`Export-Clixml` 只會在 Windows 上匯出加密的認證。</span><span class="sxs-lookup"><span data-stu-id="2721c-122">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="2721c-123">在非 Windows 作業系統（例如 macOS 和 Linux）上，認證會以純文字格式匯出。</span><span class="sxs-lookup"><span data-stu-id="2721c-123">On non-Windows operating systems such as macOS and Linux, credentials are exported in plain text.</span></span>

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

<span data-ttu-id="2721c-124">此 `Export-Clixml` Cmdlet 會使用 Windows [資料保護 API](/previous-versions/windows/apps/hh464970(v=win.10))來加密認證物件。</span><span class="sxs-lookup"><span data-stu-id="2721c-124">The `Export-Clixml` cmdlet encrypts credential objects by using the Windows [Data Protection API](/previous-versions/windows/apps/hh464970(v=win.10)).</span></span>
<span data-ttu-id="2721c-125">加密可確保只有您的使用者帳戶可以解密 credential 物件的內容。</span><span class="sxs-lookup"><span data-stu-id="2721c-125">The encryption ensures that only your user account can decrypt the contents of the credential object.</span></span> <span data-ttu-id="2721c-126">匯出的檔案 `CLIXML` 不能用於不同的電腦或不同的使用者。</span><span class="sxs-lookup"><span data-stu-id="2721c-126">The exported `CLIXML` file can't be used on a different computer or by a different user.</span></span>

<span data-ttu-id="2721c-127">在此範例中，用來儲存認證的檔案會以表示 `TestScript.ps1.credential` 。</span><span class="sxs-lookup"><span data-stu-id="2721c-127">In the example, the file in which the credential is stored is represented by `TestScript.ps1.credential`.</span></span> <span data-ttu-id="2721c-128">將 **>testscript** 取代為您要用來載入認證的腳本名稱。</span><span class="sxs-lookup"><span data-stu-id="2721c-128">Replace **TestScript** with the name of the script with which you're loading the credential.</span></span>

<span data-ttu-id="2721c-129">您會將管線下的認證物件傳送至 `Export-Clixml` ，並將它儲存到 `$Credxmlpath` 您在第一個命令中指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="2721c-129">You send the credential object down the pipeline to `Export-Clixml`, and save it to the path, `$Credxmlpath`, that you specified in the first command.</span></span>

<span data-ttu-id="2721c-130">若要將認證自動匯入至您的指令碼，請執行最後兩個命令。</span><span class="sxs-lookup"><span data-stu-id="2721c-130">To import the credential automatically into your script, run the final two commands.</span></span> <span data-ttu-id="2721c-131">執行 `Import-Clixml` 以將安全的認證物件匯入您的腳本中。</span><span class="sxs-lookup"><span data-stu-id="2721c-131">Run `Import-Clixml` to import the secured credential object into your script.</span></span> <span data-ttu-id="2721c-132">這項匯入消除了在腳本中公開純文字密碼的風險。</span><span class="sxs-lookup"><span data-stu-id="2721c-132">This import eliminates the risk of exposing plain-text passwords in your script.</span></span>

## <span data-ttu-id="2721c-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2721c-133">PARAMETERS</span></span>

### <span data-ttu-id="2721c-134">-First</span><span class="sxs-lookup"><span data-stu-id="2721c-134">-First</span></span>

<span data-ttu-id="2721c-135">只取得指定數目的物件。</span><span class="sxs-lookup"><span data-stu-id="2721c-135">Gets only the specified number of objects.</span></span> <span data-ttu-id="2721c-136">輸入要取得的物件數目。</span><span class="sxs-lookup"><span data-stu-id="2721c-136">Enter the number of objects to get.</span></span>

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2721c-137">-IncludeTotalCount</span><span class="sxs-lookup"><span data-stu-id="2721c-137">-IncludeTotalCount</span></span>

<span data-ttu-id="2721c-138">報告資料集中的物件總數，後面接著選取的物件。</span><span class="sxs-lookup"><span data-stu-id="2721c-138">Reports the total number of objects in the data set followed by the selected objects.</span></span> <span data-ttu-id="2721c-139">如果 Cmdlet 無法判斷總數，則會顯示不明的 **總計數** 。</span><span class="sxs-lookup"><span data-stu-id="2721c-139">If the cmdlet can't determine the total count, it displays **Unknown total count** .</span></span> <span data-ttu-id="2721c-140">整數具有 **精確度** 屬性，指出 total count 值的可靠性。</span><span class="sxs-lookup"><span data-stu-id="2721c-140">The integer has an **Accuracy** property that indicates the reliability of the total count value.</span></span> <span data-ttu-id="2721c-141">**精確度** 的值範圍從 `0.0` 到 `1.0` where `0.0` 表示 Cmdlet 無法計算物件數目， `1.0` 表示計數是精確的，而介於之間的值則 `0.0` `1.0` 表示逐漸可靠的估計值。</span><span class="sxs-lookup"><span data-stu-id="2721c-141">The value of **Accuracy** ranges from `0.0` to `1.0` where `0.0` means that the cmdlet couldn't count the objects, `1.0` means that the count is exact, and a value between `0.0` and `1.0` indicates an increasingly reliable estimate.</span></span>

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

### <span data-ttu-id="2721c-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2721c-142">-LiteralPath</span></span>

<span data-ttu-id="2721c-143">指定 XML 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="2721c-143">Specifies the path to the XML files.</span></span> <span data-ttu-id="2721c-144">與 **Path** 不同， **LiteralPath** 參數的值會完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="2721c-144">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="2721c-145">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2721c-145">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="2721c-146">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="2721c-146">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="2721c-147">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="2721c-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2721c-148">-Path</span><span class="sxs-lookup"><span data-stu-id="2721c-148">-Path</span></span>

<span data-ttu-id="2721c-149">指定 XML 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="2721c-149">Specifies the path to the XML files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2721c-150">-Skip</span><span class="sxs-lookup"><span data-stu-id="2721c-150">-Skip</span></span>

<span data-ttu-id="2721c-151">略過指定的物件數目，並取得剩餘的物件。</span><span class="sxs-lookup"><span data-stu-id="2721c-151">Ignores the specified number of objects and then gets the remaining objects.</span></span> <span data-ttu-id="2721c-152">輸入要略過的物件數目。</span><span class="sxs-lookup"><span data-stu-id="2721c-152">Enter the number of objects to skip.</span></span>

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2721c-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2721c-153">CommonParameters</span></span>

<span data-ttu-id="2721c-154">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2721c-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2721c-155">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2721c-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2721c-156">輸入</span><span class="sxs-lookup"><span data-stu-id="2721c-156">INPUTS</span></span>

### <span data-ttu-id="2721c-157">System.String</span><span class="sxs-lookup"><span data-stu-id="2721c-157">System.String</span></span>

<span data-ttu-id="2721c-158">您可以使用管線將包含路徑的字串管線 `Import-Clixml` 。</span><span class="sxs-lookup"><span data-stu-id="2721c-158">You can pipeline a string that contains a path to `Import-Clixml`.</span></span>

## <span data-ttu-id="2721c-159">輸出</span><span class="sxs-lookup"><span data-stu-id="2721c-159">OUTPUTS</span></span>

### <span data-ttu-id="2721c-160">PSObject</span><span class="sxs-lookup"><span data-stu-id="2721c-160">PSObject</span></span>

<span data-ttu-id="2721c-161">`Import-Clixml` 傳回已從儲存的 XML 檔案還原序列化的物件。</span><span class="sxs-lookup"><span data-stu-id="2721c-161">`Import-Clixml` returns objects that were deserialized from the stored XML files.</span></span>

## <span data-ttu-id="2721c-162">注意</span><span class="sxs-lookup"><span data-stu-id="2721c-162">NOTES</span></span>

<span data-ttu-id="2721c-163">當指定參數的多個值時，請使用逗號分隔值。</span><span class="sxs-lookup"><span data-stu-id="2721c-163">When specifying multiple values for a parameter, use commas to separate the values.</span></span> <span data-ttu-id="2721c-164">例如： `<parameter-name> <value1>, <value2>` 。</span><span class="sxs-lookup"><span data-stu-id="2721c-164">For example, `<parameter-name> <value1>, <value2>`.</span></span>

## <span data-ttu-id="2721c-165">相關連結</span><span class="sxs-lookup"><span data-stu-id="2721c-165">RELATED LINKS</span></span>

[<span data-ttu-id="2721c-166">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="2721c-166">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="2721c-167">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="2721c-167">Introducing XML Serialization</span></span>](/dotnet/standard/serialization/introducing-xml-serialization)

[<span data-ttu-id="2721c-168">Join-Path</span><span class="sxs-lookup"><span data-stu-id="2721c-168">Join-Path</span></span>](../Microsoft.PowerShell.Management/Join-Path.md)

[<span data-ttu-id="2721c-169">將認證安全地儲存在磁碟上</span><span class="sxs-lookup"><span data-stu-id="2721c-169">Securely Store Credentials on Disk</span></span>](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[<span data-ttu-id="2721c-170">使用 PowerShell 將認證傳遞給舊版系統</span><span class="sxs-lookup"><span data-stu-id="2721c-170">Use PowerShell to Pass Credentials to Legacy Systems</span></span>](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)
