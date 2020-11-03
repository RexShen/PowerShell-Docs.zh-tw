---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: 2885b2624f8334e8699e0baea5fc41b3f025fe2a
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "93206303"
---
# <span data-ttu-id="7b90e-103">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="7b90e-103">Get-Clipboard</span></span>

## <span data-ttu-id="7b90e-104">概要</span><span class="sxs-lookup"><span data-stu-id="7b90e-104">SYNOPSIS</span></span>
<span data-ttu-id="7b90e-105">取得目前的 Windows 剪貼簿專案。</span><span class="sxs-lookup"><span data-stu-id="7b90e-105">Gets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="7b90e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7b90e-106">SYNTAX</span></span>

```
Get-Clipboard [-Format <ClipboardFormat>] [-TextFormatType <TextDataFormat>] [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="7b90e-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7b90e-107">DESCRIPTION</span></span>

<span data-ttu-id="7b90e-108">`Get-Clipboard`Cmdlet 會取得目前的 Windows 剪貼簿專案。</span><span class="sxs-lookup"><span data-stu-id="7b90e-108">The `Get-Clipboard` cmdlet gets the current Windows clipboard entry.</span></span> <span data-ttu-id="7b90e-109">多行文字會以類似于的字串陣列形式傳回 `Get-Content` 。</span><span class="sxs-lookup"><span data-stu-id="7b90e-109">Multiple lines of text are returned as an array of strings similar to `Get-Content`.</span></span>

## <span data-ttu-id="7b90e-110">範例</span><span class="sxs-lookup"><span data-stu-id="7b90e-110">EXAMPLES</span></span>

### <span data-ttu-id="7b90e-111">範例1：取得剪貼簿的內容，並將它顯示在命令列中</span><span class="sxs-lookup"><span data-stu-id="7b90e-111">Example 1: Get the content of the clipboard and display it to the command-line</span></span>

<span data-ttu-id="7b90e-112">在此範例中，我們在瀏覽器中以滑鼠右鍵按一下影像，然後選擇 [ **複製** ] 動作。</span><span class="sxs-lookup"><span data-stu-id="7b90e-112">In this example we have right-clicked on an image in a browser and chose the **Copy** action.</span></span> <span data-ttu-id="7b90e-113">下列命令會顯示儲存在剪貼簿中之影像的 URL 連結。</span><span class="sxs-lookup"><span data-stu-id="7b90e-113">The following command displays the link, as a URL, of the image that is stored in the clipboard.</span></span>

```powershell
Get-Clipboard
```

```Output
https://en.wikipedia.org/wiki/PowerShell
```

### <span data-ttu-id="7b90e-114">範例2：取得特定格式之剪貼簿的內容</span><span class="sxs-lookup"><span data-stu-id="7b90e-114">Example 2: Get the content of the clipboard in a specific format</span></span>

<span data-ttu-id="7b90e-115">在此範例中，我們會在 Windows Explorerby 中將檔案複製到剪貼簿，並在其中選取並按下 <kbd>ctrl-c</kbd>。</span><span class="sxs-lookup"><span data-stu-id="7b90e-115">In this example we copied files to the clipboard in Windows Explorerby selecting them and pressing <kbd>Ctrl-C</kbd>.</span></span> <span data-ttu-id="7b90e-116">您可以使用下列命令，以檔案清單的形式存取剪貼簿的內容：</span><span class="sxs-lookup"><span data-stu-id="7b90e-116">Using the following command, you can access the contents of the clipboard as a list of files:</span></span>

```powershell
Get-Clipboard -Format FileDropList
```

```Output
    Directory: C:\Git\PS-Docs\PowerShell-Docs\wmf

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/7/2019   1:11 PM          10010 TOC.yml
-a----       11/18/2016  10:10 AM             53 md.style
-a----         5/6/2019   9:32 AM           4177 overview.md
-a----        6/28/2018   2:28 PM            345 README.md
```

## <span data-ttu-id="7b90e-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7b90e-117">PARAMETERS</span></span>

### <span data-ttu-id="7b90e-118">-Format</span><span class="sxs-lookup"><span data-stu-id="7b90e-118">-Format</span></span>

<span data-ttu-id="7b90e-119">指定剪貼簿的類型或格式。</span><span class="sxs-lookup"><span data-stu-id="7b90e-119">Specifies the type, or format, of the clipboard.</span></span> <span data-ttu-id="7b90e-120">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="7b90e-120">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7b90e-121">Text</span><span class="sxs-lookup"><span data-stu-id="7b90e-121">Text</span></span>
- <span data-ttu-id="7b90e-122">FileDropList</span><span class="sxs-lookup"><span data-stu-id="7b90e-122">FileDropList</span></span>
- <span data-ttu-id="7b90e-123">映像</span><span class="sxs-lookup"><span data-stu-id="7b90e-123">Image</span></span>
- <span data-ttu-id="7b90e-124">音訊</span><span class="sxs-lookup"><span data-stu-id="7b90e-124">Audio</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ClipboardFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, FileDropList, Image, Audio

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7b90e-125">-Raw</span><span class="sxs-lookup"><span data-stu-id="7b90e-125">-Raw</span></span>

<span data-ttu-id="7b90e-126">取得剪貼簿的整個內容。</span><span class="sxs-lookup"><span data-stu-id="7b90e-126">Gets the entire contents of the clipboard.</span></span> <span data-ttu-id="7b90e-127">多行文字會以單一多行字串的形式傳回，而不是字串陣列。</span><span class="sxs-lookup"><span data-stu-id="7b90e-127">Multiline text is returned as a single multiline string rather than an array of strings.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7b90e-128">-TextFormatType</span><span class="sxs-lookup"><span data-stu-id="7b90e-128">-TextFormatType</span></span>

<span data-ttu-id="7b90e-129">指定剪貼簿的文字資料格式類型。</span><span class="sxs-lookup"><span data-stu-id="7b90e-129">Specifies the text data format type of the clipboard.</span></span> <span data-ttu-id="7b90e-130">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="7b90e-130">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7b90e-131">Text</span><span class="sxs-lookup"><span data-stu-id="7b90e-131">Text</span></span>
- <span data-ttu-id="7b90e-132">UnicodeText</span><span class="sxs-lookup"><span data-stu-id="7b90e-132">UnicodeText</span></span>
- <span data-ttu-id="7b90e-133">Rtf</span><span class="sxs-lookup"><span data-stu-id="7b90e-133">Rtf</span></span>
- <span data-ttu-id="7b90e-134">HTML</span><span class="sxs-lookup"><span data-stu-id="7b90e-134">Html</span></span>
- <span data-ttu-id="7b90e-135">CommaSeparatedValue</span><span class="sxs-lookup"><span data-stu-id="7b90e-135">CommaSeparatedValue</span></span>

```yaml
Type: System.Windows.Forms.TextDataFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, UnicodeText, Rtf, Html, CommaSeparatedValue

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7b90e-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7b90e-136">CommonParameters</span></span>

<span data-ttu-id="7b90e-137">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="7b90e-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7b90e-138">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="7b90e-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7b90e-139">輸入</span><span class="sxs-lookup"><span data-stu-id="7b90e-139">INPUTS</span></span>

## <span data-ttu-id="7b90e-140">輸出</span><span class="sxs-lookup"><span data-stu-id="7b90e-140">OUTPUTS</span></span>

### <span data-ttu-id="7b90e-141">System.string、FileInfo、system.object、Image、Image、Image、Image</span><span class="sxs-lookup"><span data-stu-id="7b90e-141">System.String, System.IO.FileInfo, System.IO.Stream, System.Drawing.Image</span></span>

## <span data-ttu-id="7b90e-142">注意</span><span class="sxs-lookup"><span data-stu-id="7b90e-142">NOTES</span></span>

## <span data-ttu-id="7b90e-143">相關連結</span><span class="sxs-lookup"><span data-stu-id="7b90e-143">RELATED LINKS</span></span>

[<span data-ttu-id="7b90e-144">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="7b90e-144">Set-Clipboard</span></span>](Set-Clipboard.md)
