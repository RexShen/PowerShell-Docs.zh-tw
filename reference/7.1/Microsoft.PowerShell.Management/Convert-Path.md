---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/convert-path?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-Path
ms.openlocfilehash: 498620ee79285f0c0fe2a001b99fe5dc179ea0ac
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205084"
---
# <span data-ttu-id="12f44-103">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="12f44-103">Convert-Path</span></span>

## <span data-ttu-id="12f44-104">概要</span><span class="sxs-lookup"><span data-stu-id="12f44-104">SYNOPSIS</span></span>
<span data-ttu-id="12f44-105">將路徑從 PowerShell 路徑轉換為 PowerShell 提供者路徑。</span><span class="sxs-lookup"><span data-stu-id="12f44-105">Converts a path from a PowerShell path to a PowerShell provider path.</span></span>

## <span data-ttu-id="12f44-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="12f44-106">SYNTAX</span></span>

### <span data-ttu-id="12f44-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="12f44-107">Path (Default)</span></span>

```
Convert-Path [-Path] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="12f44-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="12f44-108">LiteralPath</span></span>

```
Convert-Path -LiteralPath <String[]> [<CommonParameters>]
```

## <span data-ttu-id="12f44-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="12f44-109">DESCRIPTION</span></span>

<span data-ttu-id="12f44-110">`Convert-Path`Cmdlet 會將路徑從 powershell 路徑轉換成 powershell 提供者路徑。</span><span class="sxs-lookup"><span data-stu-id="12f44-110">The `Convert-Path` cmdlet converts a path from a PowerShell path to a PowerShell provider path.</span></span>

## <span data-ttu-id="12f44-111">範例</span><span class="sxs-lookup"><span data-stu-id="12f44-111">EXAMPLES</span></span>

### <span data-ttu-id="12f44-112">範例 1︰將工作目錄轉換成標準檔案系統路徑</span><span class="sxs-lookup"><span data-stu-id="12f44-112">Example 1: Convert the working directory to a standard file system path</span></span>

<span data-ttu-id="12f44-113">這個範例會將目前的工作目錄（以點 (`.`) 表示）轉換成標準檔案系統路徑。</span><span class="sxs-lookup"><span data-stu-id="12f44-113">This example converts the current working directory, which is represented by a dot (`.`), to a standard FileSystem path.</span></span>

```
PS C:\> Convert-Path .
C:\
```

### <span data-ttu-id="12f44-114">範例 2︰將提供者路徑轉換成標準登錄路徑</span><span class="sxs-lookup"><span data-stu-id="12f44-114">Example 2: Convert a provider path to a standard registry path</span></span>

<span data-ttu-id="12f44-115">此範例會將 PowerShell 提供者路徑轉換成標準登錄路徑。</span><span class="sxs-lookup"><span data-stu-id="12f44-115">This example converts the PowerShell provider path to a standard registry path.</span></span>

```powershell
PS C:\> Convert-Path HKLM:\Software\Microsoft
HKEY_LOCAL_MACHINE\Software\Microsoft
```

### <span data-ttu-id="12f44-116">範例 3︰將路徑轉換成字串</span><span class="sxs-lookup"><span data-stu-id="12f44-116">Example 3: Convert a path to a string</span></span>

<span data-ttu-id="12f44-117">這個範例會將目前提供者（FileSystem 提供者）的主目錄路徑轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="12f44-117">This example converts the path to the home directory of the current provider, which is the FileSystem provider, to a string.</span></span>

```powershell
PS C:\> Convert-Path ~
C:\Users\User01
```

## <span data-ttu-id="12f44-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="12f44-118">PARAMETERS</span></span>

### <span data-ttu-id="12f44-119">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="12f44-119">-LiteralPath</span></span>

<span data-ttu-id="12f44-120">以字串陣列指定要轉換的路徑。</span><span class="sxs-lookup"><span data-stu-id="12f44-120">Specifies, as a string array, the path to be converted.</span></span> <span data-ttu-id="12f44-121">**LiteralPath** 參數的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="12f44-121">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="12f44-122">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="12f44-122">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="12f44-123">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="12f44-123">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="12f44-124">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="12f44-124">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="12f44-125">-Path</span><span class="sxs-lookup"><span data-stu-id="12f44-125">-Path</span></span>

<span data-ttu-id="12f44-126">指定要轉換的 PowerShell 路徑。</span><span class="sxs-lookup"><span data-stu-id="12f44-126">Specifies the PowerShell path to be converted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="12f44-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="12f44-127">CommonParameters</span></span>

<span data-ttu-id="12f44-128">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="12f44-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="12f44-129">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="12f44-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="12f44-130">輸入</span><span class="sxs-lookup"><span data-stu-id="12f44-130">INPUTS</span></span>

### <span data-ttu-id="12f44-131">System.String</span><span class="sxs-lookup"><span data-stu-id="12f44-131">System.String</span></span>

<span data-ttu-id="12f44-132">您可以使用管線將路徑 (而非常值路徑) 傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="12f44-132">You can pipe a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="12f44-133">輸出</span><span class="sxs-lookup"><span data-stu-id="12f44-133">OUTPUTS</span></span>

### <span data-ttu-id="12f44-134">System.String</span><span class="sxs-lookup"><span data-stu-id="12f44-134">System.String</span></span>

<span data-ttu-id="12f44-135">此 Cmdlet 會傳回包含已轉換路徑的字串。</span><span class="sxs-lookup"><span data-stu-id="12f44-135">This cmdlet returns a string that contains the converted path.</span></span>

## <span data-ttu-id="12f44-136">注意</span><span class="sxs-lookup"><span data-stu-id="12f44-136">NOTES</span></span>

<span data-ttu-id="12f44-137">包含路徑名詞的 Cmdlet 會操作路徑名稱，並傳回所有 PowerShell 提供者都可解讀的精簡格式名稱。</span><span class="sxs-lookup"><span data-stu-id="12f44-137">The cmdlets that contain the Path noun manipulate path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="12f44-138">它們是設計用於程式與指令碼，您可以在其中以特定格式顯示所有或部分路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="12f44-138">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="12f44-139">使用它們，就像您使用 **Dirname** 、 **Normpath** 、 **Realpath** 、 **Join** 或其他路徑操作工具一樣。</span><span class="sxs-lookup"><span data-stu-id="12f44-139">Use them like you would use **Dirname** , **Normpath** , **Realpath** , **Join** , or other path manipulators.</span></span>

<span data-ttu-id="12f44-140">您可以使用 Path Cmdlet 於數種提供者，包括 FileSystem、Registry 與 Certificate 提供者。</span><span class="sxs-lookup"><span data-stu-id="12f44-140">You can use the path cmdlets with several providers, including the FileSystem, Registry, and Certificate providers.</span></span>

<span data-ttu-id="12f44-141">此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="12f44-141">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="12f44-142">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="12f44-142">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="12f44-143">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="12f44-143">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="12f44-144">`Convert-Path` 只會轉換現有的路徑。</span><span class="sxs-lookup"><span data-stu-id="12f44-144">`Convert-Path` only converts existing paths.</span></span> <span data-ttu-id="12f44-145">它無法用來轉換尚未存在的位置。</span><span class="sxs-lookup"><span data-stu-id="12f44-145">It cannot be used to convert a location that does not exist yet.</span></span>

## <span data-ttu-id="12f44-146">相關連結</span><span class="sxs-lookup"><span data-stu-id="12f44-146">RELATED LINKS</span></span>

[<span data-ttu-id="12f44-147">Join-Path</span><span class="sxs-lookup"><span data-stu-id="12f44-147">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="12f44-148">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="12f44-148">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="12f44-149">Split-Path</span><span class="sxs-lookup"><span data-stu-id="12f44-149">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="12f44-150">Test-Path</span><span class="sxs-lookup"><span data-stu-id="12f44-150">Test-Path</span></span>](Test-Path.md)

[<span data-ttu-id="12f44-151">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="12f44-151">Get-PSProvider</span></span>](Get-PSProvider.md)

