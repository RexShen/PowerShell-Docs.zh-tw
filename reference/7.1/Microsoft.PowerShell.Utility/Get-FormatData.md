---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-formatdata?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FormatData
ms.openlocfilehash: 0024bb83b983d0b13e2fbfafb24505849acf15f6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202827"
---
# <span data-ttu-id="285d8-103">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="285d8-103">Get-FormatData</span></span>

## <span data-ttu-id="285d8-104">概要</span><span class="sxs-lookup"><span data-stu-id="285d8-104">SYNOPSIS</span></span>
<span data-ttu-id="285d8-105">取得目前工作階段中的格式化資料。</span><span class="sxs-lookup"><span data-stu-id="285d8-105">Gets the formatting data in the current session.</span></span>

## <span data-ttu-id="285d8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="285d8-106">SYNTAX</span></span>

```
Get-FormatData [[-TypeName] <String[]>] [-PowerShellVersion <Version>] [<CommonParameters>]
```

## <span data-ttu-id="285d8-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="285d8-107">DESCRIPTION</span></span>

<span data-ttu-id="285d8-108">`Get-FormatData`Cmdlet 會取得目前會話中的格式化資料。</span><span class="sxs-lookup"><span data-stu-id="285d8-108">The `Get-FormatData` cmdlet gets the formatting data in the current session.</span></span>

<span data-ttu-id="285d8-109">會話中的格式化資料包括格式化檔案的格式設定 `Format.ps1xml` ，例如目錄中的檔案 `$PSHOME` 、格式化您匯入會話中之模組的資料，以及使用指令程式將您匯入到會話的命令格式化資料 `Import-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="285d8-109">The formatting data in the session includes formatting data from `Format.ps1xml` formatting files, such as those in the `$PSHOME` directory, formatting data for modules that you import into the session, and formatting data for commands that you import into your session by using the `Import-PSSession` cmdlet.</span></span>

<span data-ttu-id="285d8-110">您可以使用這個 Cmdlet 來檢查格式化資料。</span><span class="sxs-lookup"><span data-stu-id="285d8-110">You can use this cmdlet to examine the formatting data.</span></span> <span data-ttu-id="285d8-111">然後，您可以使用 `Export-FormatData` Cmdlet 序列化物件、將它們轉換成 XML，然後將它們儲存在檔案中 `Format.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="285d8-111">Then, you can use the `Export-FormatData` cmdlet to serialize the objects, convert them to XML, and save them in `Format.ps1xml` files.</span></span>

<span data-ttu-id="285d8-112">如需有關在 PowerShell 中格式化檔案的詳細資訊，請參閱 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="285d8-112">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="285d8-113">範例</span><span class="sxs-lookup"><span data-stu-id="285d8-113">EXAMPLES</span></span>

### <span data-ttu-id="285d8-114">範例1：取得所有格式化資料</span><span class="sxs-lookup"><span data-stu-id="285d8-114">Example 1: Get all formatting data</span></span>

<span data-ttu-id="285d8-115">此範例會取得會話中的所有格式化資料。</span><span class="sxs-lookup"><span data-stu-id="285d8-115">This example gets all the formatting data in the session.</span></span>

```powershell
Get-FormatData
```

### <span data-ttu-id="285d8-116">範例2：依類型名稱取得格式化資料</span><span class="sxs-lookup"><span data-stu-id="285d8-116">Example 2: Get formatting data by type name</span></span>

<span data-ttu-id="285d8-117">這個範例會取得名稱開頭為的格式化資料項目 `System.Management.Automation.Cmd` 。</span><span class="sxs-lookup"><span data-stu-id="285d8-117">This example gets the formatting data items whose names begin with `System.Management.Automation.Cmd`.</span></span>

```powershell
Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
```

### <span data-ttu-id="285d8-118">範例3：檢查格式化資料物件</span><span class="sxs-lookup"><span data-stu-id="285d8-118">Example 3: Examine a formatting data object</span></span>

<span data-ttu-id="285d8-119">這個範例示範如何取得格式化資料物件，並檢查其屬性。</span><span class="sxs-lookup"><span data-stu-id="285d8-119">This example shows how to get a formatting data object and examine its properties.</span></span>

```powershell
$F = Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
$F
```

```Output
TypeName        FormatViewDefinition
--------        --------------------
HelpInfoShort   {help , TableControl}
```

```powershell
$F.FormatViewDefinition[0].control
```

```Output
Headers          : {System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader}
Rows             : {System.Management.Automation.TableControlRow}
AutoSize         : False
HideTableHeaders : False
GroupBy          :
OutOfBand        : False
```

```powershell
$F.FormatViewDefinition[0].control.Headers
```

```Output
Label       Alignment Width
-----       --------- -----
CommandType Undefined    15
Name        Undefined    50
Version     Undefined    10
Source      Undefined     0
```

### <span data-ttu-id="285d8-120">範例4：取得格式化資料並匯出</span><span class="sxs-lookup"><span data-stu-id="285d8-120">Example 4: Get formatting data and export it</span></span>

<span data-ttu-id="285d8-121">這個範例示範如何使用 `Get-FormatData` 和 `Export-FormatData` 來匯出模組所新增的格式化資料。</span><span class="sxs-lookup"><span data-stu-id="285d8-121">This example shows how to use `Get-FormatData` and `Export-FormatData` to export the formatting data that is added by a module.</span></span>

```powershell
$A = Get-FormatData
Import-Module bitstransfer
$B = Get-FormatData
Compare-Object $A $B
```

```Output
InputObject                                                SideIndicator
-----------                                                -------------
Microsoft.BackgroundIntelligentTransfer.Management.BitsJob =>
```

```powershell
Get-FormatData *bits* | Export-FormatData -FilePath c:\test\bits.format.ps1xml
Get-Content c:\test\bits.format.ps1xml
```

```Output
<?xml version="1.0" encoding="utf-8"?><Configuration><ViewDefinitions>
<View><Name>Microsoft.BackgroundIntelligentTransfer.Management.BitsJob</Name>
...
```

<span data-ttu-id="285d8-122">前四個命令會使用 `Get-FormatData` 、 `Import-Module` 和 `Compare-Object` Cmdlet 來識別 **BitsTransfer** 模組新增至會話的格式類型。</span><span class="sxs-lookup"><span data-stu-id="285d8-122">The first four commands use the `Get-FormatData`, `Import-Module`, and `Compare-Object` cmdlets to identify the format type that the **BitsTransfer** module adds to the session.</span></span>

<span data-ttu-id="285d8-123">第五個命令會使用 `Get-FormatData` Cmdlet 來取得 **BitsTransfer** 模組所新增的格式類型。</span><span class="sxs-lookup"><span data-stu-id="285d8-123">The fifth command uses the `Get-FormatData` cmdlet to get the format type that the **BitsTransfer** module adds.</span></span> <span data-ttu-id="285d8-124">它使用管線運算子 (`|`) 將格式類型物件傳送至 `Export-FormatData` Cmdlet，以將它轉換回 XML，並將它儲存在指定的檔案中 `format.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="285d8-124">It uses a pipeline operator (`|`) to send the format type object to the `Export-FormatData` cmdlet, which converts it back to XML and saves it in the specified `format.ps1xml` file.</span></span>

<span data-ttu-id="285d8-125">最後一個命令會顯示檔案內容的摘要 `format.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="285d8-125">The final command shows an excerpt of the `format.ps1xml` file content.</span></span>

### <span data-ttu-id="285d8-126">範例5：根據指定的 PowerShell 版本取得格式化資料</span><span class="sxs-lookup"><span data-stu-id="285d8-126">Example 5: Get formatting data based on the specified version of PowerShell</span></span>

<span data-ttu-id="285d8-127">此範例示範如何使用 `Get-FormatData` 來取得指定之 **TypeName** 和 PowerShell 版本的格式資料。</span><span class="sxs-lookup"><span data-stu-id="285d8-127">This example shows how to use `Get-FormatData` to get format data for a specified **TypeName** and PowerShell version.</span></span>

```powershell
Get-FormatData -TypeName 'Microsoft.Powershell.Utility.FileHash' -PowerShellVersion $PSVersionTable.PSVersion

TypeNames                               FormatViewDefinition
---------                               --------------------
{Microsoft.Powershell.Utility.FileHash} {Microsoft.Powershell.Utility.FileHash}
```

## <span data-ttu-id="285d8-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="285d8-128">PARAMETERS</span></span>

### <span data-ttu-id="285d8-129">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="285d8-129">-PowerShellVersion</span></span>

<span data-ttu-id="285d8-130">指定此 Cmdlet 取得格式化資料的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="285d8-130">Specify the version of PowerShell this cmdlet gets for the formatting data.</span></span> <span data-ttu-id="285d8-131">輸入以句號分隔的兩位數數位。</span><span class="sxs-lookup"><span data-stu-id="285d8-131">Enter a two digit number separated by a period.</span></span>

<span data-ttu-id="285d8-132">此參數是在 PowerShell 5.1 中新增的，可改善執行舊版 PowerShell 的遠端電腦的相容性。</span><span class="sxs-lookup"><span data-stu-id="285d8-132">This parameter was added in PowerShell 5.1 to improve compatibility when remoting computers running older versions of PowerShell.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="285d8-133">-TypeName</span><span class="sxs-lookup"><span data-stu-id="285d8-133">-TypeName</span></span>

<span data-ttu-id="285d8-134">指定此 Cmdlet 為格式化資料取得的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="285d8-134">Specifies the type names that this cmdlet gets for the formatting data.</span></span>
<span data-ttu-id="285d8-135">輸入類型名稱。</span><span class="sxs-lookup"><span data-stu-id="285d8-135">Enter the type names.</span></span>
<span data-ttu-id="285d8-136">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="285d8-136">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="285d8-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="285d8-137">CommonParameters</span></span>

<span data-ttu-id="285d8-138">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="285d8-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="285d8-139">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="285d8-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="285d8-140">輸入</span><span class="sxs-lookup"><span data-stu-id="285d8-140">INPUTS</span></span>

### <span data-ttu-id="285d8-141">無</span><span class="sxs-lookup"><span data-stu-id="285d8-141">None</span></span>

<span data-ttu-id="285d8-142">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="285d8-142">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="285d8-143">輸出</span><span class="sxs-lookup"><span data-stu-id="285d8-143">OUTPUTS</span></span>

### <span data-ttu-id="285d8-144">System.Management.Automation.ExtendedTypeDefinition</span><span class="sxs-lookup"><span data-stu-id="285d8-144">System.Management.Automation.ExtendedTypeDefinition</span></span>

## <span data-ttu-id="285d8-145">注意</span><span class="sxs-lookup"><span data-stu-id="285d8-145">NOTES</span></span>

## <span data-ttu-id="285d8-146">相關連結</span><span class="sxs-lookup"><span data-stu-id="285d8-146">RELATED LINKS</span></span>

[<span data-ttu-id="285d8-147">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="285d8-147">Export-FormatData</span></span>](Export-FormatData.md)

[<span data-ttu-id="285d8-148">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="285d8-148">Update-FormatData</span></span>](Update-FormatData.md)
