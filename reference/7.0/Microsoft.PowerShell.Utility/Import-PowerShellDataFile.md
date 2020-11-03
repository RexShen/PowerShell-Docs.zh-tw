---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: f25191d27013469023b9fcfb03650a8693c6ddb4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201152"
---
# <span data-ttu-id="263e8-103">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="263e8-103">Import-PowerShellDataFile</span></span>

## <span data-ttu-id="263e8-104">概要</span><span class="sxs-lookup"><span data-stu-id="263e8-104">SYNOPSIS</span></span>
<span data-ttu-id="263e8-105">匯入檔案中的值 `.PSD1` ，而不叫用其內容。</span><span class="sxs-lookup"><span data-stu-id="263e8-105">Imports values from a `.PSD1` file without invoking its contents.</span></span>

## <span data-ttu-id="263e8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="263e8-106">SYNTAX</span></span>

### <span data-ttu-id="263e8-107">ByPath (預設值)</span><span class="sxs-lookup"><span data-stu-id="263e8-107">ByPath (Default)</span></span>

```
Import-PowerShellDataFile [-Path] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="263e8-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="263e8-108">ByLiteralPath</span></span>

```
Import-PowerShellDataFile [-LiteralPath] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="263e8-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="263e8-109">DESCRIPTION</span></span>

<span data-ttu-id="263e8-110">此 `Import-PowerShellDataFile` Cmdlet 會從檔案中定義的雜湊表安全地匯入機碼值組 `.PSD1` 。</span><span class="sxs-lookup"><span data-stu-id="263e8-110">The `Import-PowerShellDataFile` cmdlet safely imports key-value pairs from hashtables defined in a `.PSD1` file.</span></span> <span data-ttu-id="263e8-111">您可以使用檔案內容來匯入這些值 `Invoke-Expression` 。</span><span class="sxs-lookup"><span data-stu-id="263e8-111">The values could be imported using `Invoke-Expression` on the contents of the file.</span></span>
<span data-ttu-id="263e8-112">但是，會 `Invoke-Expression` 執行檔案中包含的任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="263e8-112">However, `Invoke-Expression` runs any code contained in the file.</span></span> <span data-ttu-id="263e8-113">這可能會產生不必要的結果，或執行不安全的程式碼。</span><span class="sxs-lookup"><span data-stu-id="263e8-113">This could produce unwanted results or execute unsafe code.</span></span> <span data-ttu-id="263e8-114">`Import-PowerShellDataFile` 匯入資料，而不叫用程式碼。</span><span class="sxs-lookup"><span data-stu-id="263e8-114">`Import-PowerShellDataFile` imports the data without invoking the code.</span></span>

## <span data-ttu-id="263e8-115">範例</span><span class="sxs-lookup"><span data-stu-id="263e8-115">EXAMPLES</span></span>

### <span data-ttu-id="263e8-116">範例1：從 .PSD1 取出值</span><span class="sxs-lookup"><span data-stu-id="263e8-116">Example 1: Retrieve values from PSD1</span></span>

<span data-ttu-id="263e8-117">這個範例會抓取儲存在檔案中的雜湊表中的機碼值組 `Configuration.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="263e8-117">This example retrieves the key-value pairs stored in the hashtable kept inside the `Configuration.psd1` file.</span></span> <span data-ttu-id="263e8-118">`Get-Content` 用來顯示檔案的內容 `Configuration.psd1` 。</span><span class="sxs-lookup"><span data-stu-id="263e8-118">`Get-Content` is used to show the contents of the `Configuration.psd1` file.</span></span>

```powershell
Get-Content .\Configuration.psd1
$config = Import-PowerShellDataFile .\Configuration.psd1
$config.AllNodes
```

```Output
@{
    AllNodes = @(
        @{
            NodeName = 'DSC-01'
        }
        @{
            NodeName = 'DSC-02'
        }
    )
}

Name                           Value
----                           -----
NodeName                       DSC-01
NodeName                       DSC-02
```

## <span data-ttu-id="263e8-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="263e8-119">PARAMETERS</span></span>

### <span data-ttu-id="263e8-120">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="263e8-120">-LiteralPath</span></span>

<span data-ttu-id="263e8-121">要匯入之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="263e8-121">The path to the file being imported.</span></span> <span data-ttu-id="263e8-122">路徑中的所有字元都會被視為常值。</span><span class="sxs-lookup"><span data-stu-id="263e8-122">All characters in the path are treated as literal values.</span></span>
<span data-ttu-id="263e8-123">不會處理萬用字元。</span><span class="sxs-lookup"><span data-stu-id="263e8-123">Wildcard characters are not processed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="263e8-124">-Path</span><span class="sxs-lookup"><span data-stu-id="263e8-124">-Path</span></span>

<span data-ttu-id="263e8-125">要匯入之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="263e8-125">The path to the file being imported.</span></span> <span data-ttu-id="263e8-126">允許使用萬用字元，但只會匯入第一個相符的檔案。</span><span class="sxs-lookup"><span data-stu-id="263e8-126">Wildcards are allowed but only the first matching file is imported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="263e8-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="263e8-127">CommonParameters</span></span>

<span data-ttu-id="263e8-128">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="263e8-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="263e8-129">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="263e8-129">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="263e8-130">輸入</span><span class="sxs-lookup"><span data-stu-id="263e8-130">INPUTS</span></span>

## <span data-ttu-id="263e8-131">輸出</span><span class="sxs-lookup"><span data-stu-id="263e8-131">OUTPUTS</span></span>

### <span data-ttu-id="263e8-132">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="263e8-132">System.Collections.Hashtable</span></span>

## <span data-ttu-id="263e8-133">注意</span><span class="sxs-lookup"><span data-stu-id="263e8-133">NOTES</span></span>

## <span data-ttu-id="263e8-134">相關連結</span><span class="sxs-lookup"><span data-stu-id="263e8-134">RELATED LINKS</span></span>

[<span data-ttu-id="263e8-135">Invoke-Expression</span><span class="sxs-lookup"><span data-stu-id="263e8-135">Invoke-Expression</span></span>](Invoke-Expression.md)

[<span data-ttu-id="263e8-136">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="263e8-136">Import-LocalizedData</span></span>](Import-LocalizedData.md)
