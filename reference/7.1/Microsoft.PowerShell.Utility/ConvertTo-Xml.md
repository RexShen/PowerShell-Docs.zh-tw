---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-xml?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Xml
ms.openlocfilehash: 2e7ebe3a528095873dc7ba5ba0deba2905f531ee
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204215"
---
# <span data-ttu-id="f9c33-103">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="f9c33-103">ConvertTo-Xml</span></span>

## <span data-ttu-id="f9c33-104">概要</span><span class="sxs-lookup"><span data-stu-id="f9c33-104">SYNOPSIS</span></span>
<span data-ttu-id="f9c33-105">建立物件的 XML 表示法。</span><span class="sxs-lookup"><span data-stu-id="f9c33-105">Creates an XML-based representation of an object.</span></span>

## <span data-ttu-id="f9c33-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f9c33-106">SYNTAX</span></span>

```
ConvertTo-Xml [-Depth <Int32>] [-InputObject] <PSObject> [-NoTypeInformation] [-As <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="f9c33-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f9c33-107">DESCRIPTION</span></span>

<span data-ttu-id="f9c33-108">`ConvertTo-Xml`Cmdlet 會建立一或多個 .net 物件的[XML](/dotnet/api/system.xml.xmldocument)標記法。</span><span class="sxs-lookup"><span data-stu-id="f9c33-108">The `ConvertTo-Xml` cmdlet creates an [XML-based](/dotnet/api/system.xml.xmldocument) representation of one or more more .NET objects.</span></span> <span data-ttu-id="f9c33-109">若要使用此 Cmdlet，請使用管線將一或多個物件傳送至 Cmdlet，或使用 **InputObject** 參數來指定物件。</span><span class="sxs-lookup"><span data-stu-id="f9c33-109">To use this cmdlet, pipe one or more objects to the cmdlet, or use the **InputObject** parameter to specify the object.</span></span>

<span data-ttu-id="f9c33-110">當您使用管線將多個物件傳送至 `ConvertTo-Xml` 或使用 **InputObject** 參數提交多個物件時，會傳回 `ConvertTo-Xml` 單一的記憶體中 XML 檔，其中包含所有物件的標記法。</span><span class="sxs-lookup"><span data-stu-id="f9c33-110">When you pipe multiple objects to `ConvertTo-Xml` or use the **InputObject** parameter to submit multiple objects, `ConvertTo-Xml` returns a single, in-memory XML document that includes representations of all of the objects.</span></span>

<span data-ttu-id="f9c33-111">[除了將](./Export-Clixml.md) `Export-Clixml` 產生的 XML 儲存在[通用語言基礎結構](https://www.ecma-international.org/publications/standards/Ecma-335.htm)中，此 Cmdlet 也會將產生的 XML 儲存 (CLI) XML 檔案，該檔案可以重新匯入為具有[Clixml](./Import-Clixml.md)的物件。</span><span class="sxs-lookup"><span data-stu-id="f9c33-111">This cmdlet is similar to [Export-Clixml](./Export-Clixml.md) except that `Export-Clixml` stores the resulting XML in a [Common Language Infrastructure(CLI) XML](https://www.ecma-international.org/publications/standards/Ecma-335.htm) file that can be reimported as objects with [Import-Clixml](./Import-Clixml.md).</span></span> <span data-ttu-id="f9c33-112">`ConvertTo-Xml` 傳回 XML 檔的記憶體中表示，讓您可以在 PowerShell 中繼續處理。</span><span class="sxs-lookup"><span data-stu-id="f9c33-112">`ConvertTo-Xml` returns an in-memory representation of an XML document, so you can continue to process it in PowerShell.</span></span> <span data-ttu-id="f9c33-113">`ConvertTo-Xml` 沒有將物件轉換為 CLI XML 的選項。</span><span class="sxs-lookup"><span data-stu-id="f9c33-113">`ConvertTo-Xml` does not have an option to convert objects to CLI XML.</span></span>

## <span data-ttu-id="f9c33-114">範例</span><span class="sxs-lookup"><span data-stu-id="f9c33-114">EXAMPLES</span></span>

### <span data-ttu-id="f9c33-115">範例1：將日期轉換為 XML</span><span class="sxs-lookup"><span data-stu-id="f9c33-115">Example 1: Convert a date to XML</span></span>

```
PS C:\> Get-Date | ConvertTo-Xml
```

<span data-ttu-id="f9c33-116">此命令會將 (日期 **時間** 物件) 的目前日期轉換為 XML。</span><span class="sxs-lookup"><span data-stu-id="f9c33-116">This command converts the current date (a **DateTime** object) to XML.</span></span>

### <span data-ttu-id="f9c33-117">範例2：將處理常式轉換為 XML</span><span class="sxs-lookup"><span data-stu-id="f9c33-117">Example 2: Convert processes to XML</span></span>

```
PS C:\> ConvertTo-Xml -As "Document" -InputObject (Get-Process) -Depth 3
```

<span data-ttu-id="f9c33-118">這個命令會將代表電腦上所有處理程序的處理程序物件轉換為 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="f9c33-118">This command converts the process objects that represent all of the processes on the computer into an XML document.</span></span> <span data-ttu-id="f9c33-119">物件的深度擴充為三個層級。</span><span class="sxs-lookup"><span data-stu-id="f9c33-119">The objects are expanded to a depth of three levels.</span></span>

## <span data-ttu-id="f9c33-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f9c33-120">PARAMETERS</span></span>

### <span data-ttu-id="f9c33-121">-As</span><span class="sxs-lookup"><span data-stu-id="f9c33-121">-As</span></span>

<span data-ttu-id="f9c33-122">決定輸出格式。</span><span class="sxs-lookup"><span data-stu-id="f9c33-122">Determines the output format.</span></span>
<span data-ttu-id="f9c33-123">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="f9c33-123">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f9c33-124">字串。</span><span class="sxs-lookup"><span data-stu-id="f9c33-124">String.</span></span>
<span data-ttu-id="f9c33-125">傳回單一字串。</span><span class="sxs-lookup"><span data-stu-id="f9c33-125">Returns a single string.</span></span>
- <span data-ttu-id="f9c33-126">資料流。</span><span class="sxs-lookup"><span data-stu-id="f9c33-126">Stream.</span></span>
<span data-ttu-id="f9c33-127">傳回字串陣列。</span><span class="sxs-lookup"><span data-stu-id="f9c33-127">Returns an array of strings.</span></span>
- <span data-ttu-id="f9c33-128">文件。</span><span class="sxs-lookup"><span data-stu-id="f9c33-128">Document.</span></span>
<span data-ttu-id="f9c33-129">傳回已 **進行** 的物件。</span><span class="sxs-lookup"><span data-stu-id="f9c33-129">Returns an **XmlDocument** object.</span></span>

<span data-ttu-id="f9c33-130">預設值為 Document。</span><span class="sxs-lookup"><span data-stu-id="f9c33-130">The default value is Document.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Stream, String, Document

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f9c33-131">-Depth</span><span class="sxs-lookup"><span data-stu-id="f9c33-131">-Depth</span></span>

<span data-ttu-id="f9c33-132">指定 XML 表示法中包含多少層的內含物件。</span><span class="sxs-lookup"><span data-stu-id="f9c33-132">Specifies how many levels of contained objects are included in the XML representation.</span></span> <span data-ttu-id="f9c33-133">預設值為 1。</span><span class="sxs-lookup"><span data-stu-id="f9c33-133">The default value is 1.</span></span>

<span data-ttu-id="f9c33-134">例如，如果物件的屬性也包含物件，為了儲存包含物件的屬性的 XML 表示法，您必須將深度指定為 2。</span><span class="sxs-lookup"><span data-stu-id="f9c33-134">For example, if the object's properties also contain objects, to save an XML representation of the properties of the contained objects, you must specify a depth of 2.</span></span>

<span data-ttu-id="f9c33-135">您可以在 Types.ps1xml 檔案中覆寫物件類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="f9c33-135">The default value can be overridden for the object type in the Types.ps1xml files.</span></span> <span data-ttu-id="f9c33-136">如需詳細資訊，請參閱 about_Types.ps1xml。</span><span class="sxs-lookup"><span data-stu-id="f9c33-136">For more information, see about_Types.ps1xml.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f9c33-137">-InputObject</span><span class="sxs-lookup"><span data-stu-id="f9c33-137">-InputObject</span></span>

<span data-ttu-id="f9c33-138">指定要轉換的物件。</span><span class="sxs-lookup"><span data-stu-id="f9c33-138">Specifies the object to be converted.</span></span> <span data-ttu-id="f9c33-139">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="f9c33-139">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="f9c33-140">您也可以透過管線將物件傳送至 **CONVERTTO XML** 。</span><span class="sxs-lookup"><span data-stu-id="f9c33-140">You can also pipe objects to **ConvertTo-XML** .</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f9c33-141">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="f9c33-141">-NoTypeInformation</span></span>

<span data-ttu-id="f9c33-142">省略物件節點的 Type 屬性。</span><span class="sxs-lookup"><span data-stu-id="f9c33-142">Omits the Type attribute from the object nodes.</span></span>

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

### <span data-ttu-id="f9c33-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f9c33-143">CommonParameters</span></span>

<span data-ttu-id="f9c33-144">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f9c33-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f9c33-145">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f9c33-145">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f9c33-146">輸入</span><span class="sxs-lookup"><span data-stu-id="f9c33-146">INPUTS</span></span>

### <span data-ttu-id="f9c33-147">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="f9c33-147">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="f9c33-148">您可以透過管線將任何物件傳送至 **CONVERTTO XML** 。</span><span class="sxs-lookup"><span data-stu-id="f9c33-148">You can pipe any object to **ConvertTo-XML** .</span></span>

## <span data-ttu-id="f9c33-149">輸出</span><span class="sxs-lookup"><span data-stu-id="f9c33-149">OUTPUTS</span></span>

### <span data-ttu-id="f9c33-150">System.string 或 System.Xml.Xml檔</span><span class="sxs-lookup"><span data-stu-id="f9c33-150">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="f9c33-151">*As* 參數的值會決定 **ConvertTo XML** 傳回的物件類型。</span><span class="sxs-lookup"><span data-stu-id="f9c33-151">The value of the *As* parameter determines the type of object that **ConvertTo-XML** returns.</span></span>

## <span data-ttu-id="f9c33-152">注意</span><span class="sxs-lookup"><span data-stu-id="f9c33-152">NOTES</span></span>

## <span data-ttu-id="f9c33-153">相關連結</span><span class="sxs-lookup"><span data-stu-id="f9c33-153">RELATED LINKS</span></span>

[<span data-ttu-id="f9c33-154">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="f9c33-154">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="f9c33-155">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="f9c33-155">ConvertTo-Html</span></span>](ConvertTo-Html.md)

[<span data-ttu-id="f9c33-156">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="f9c33-156">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="f9c33-157">Get-Date</span><span class="sxs-lookup"><span data-stu-id="f9c33-157">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="f9c33-158">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="f9c33-158">Import-Clixml</span></span>](Import-Clixml.md)

