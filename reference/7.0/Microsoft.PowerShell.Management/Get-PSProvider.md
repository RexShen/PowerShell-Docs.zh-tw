---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: cb3b851b9634c052cf9d680fcb7f7e1215f9870d
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201383"
---
# <span data-ttu-id="92ca0-103">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="92ca0-103">Get-PSProvider</span></span>

## <span data-ttu-id="92ca0-104">概要</span><span class="sxs-lookup"><span data-stu-id="92ca0-104">SYNOPSIS</span></span>
<span data-ttu-id="92ca0-105">取得指定 PowerShell 提供者的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="92ca0-105">Gets information about the specified PowerShell provider.</span></span>

## <span data-ttu-id="92ca0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="92ca0-106">SYNTAX</span></span>

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="92ca0-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="92ca0-107">DESCRIPTION</span></span>

<span data-ttu-id="92ca0-108">`Get-PSProvider`Cmdlet 會取得目前會話中的 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="92ca0-108">The `Get-PSProvider` cmdlet gets the PowerShell providers in the current session.</span></span>
<span data-ttu-id="92ca0-109">您可以取得工作階段中的特定磁碟機或所有磁碟機。</span><span class="sxs-lookup"><span data-stu-id="92ca0-109">You can get a particular drive or all drives in the session.</span></span>

<span data-ttu-id="92ca0-110">PowerShell 提供者可讓您存取各種資料存放區，就好像它們是檔案系統磁片磁碟機一樣。</span><span class="sxs-lookup"><span data-stu-id="92ca0-110">PowerShell providers let you access a variety of data stores as though they were file system drives.</span></span>
<span data-ttu-id="92ca0-111">如需 PowerShell 提供者的詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="92ca0-111">For information about PowerShell providers, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="92ca0-112">範例</span><span class="sxs-lookup"><span data-stu-id="92ca0-112">EXAMPLES</span></span>

### <span data-ttu-id="92ca0-113">範例 1︰顯示所有可用提供者的清單</span><span class="sxs-lookup"><span data-stu-id="92ca0-113">Example 1: Display a list of all available providers</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="92ca0-114">此命令會顯示所有可用 PowerShell 提供者的清單。</span><span class="sxs-lookup"><span data-stu-id="92ca0-114">This command displays a list of all available PowerShell providers.</span></span>

### <span data-ttu-id="92ca0-115">範例2：顯示以指定字母開頭之所有 PowerShell 提供者的清單</span><span class="sxs-lookup"><span data-stu-id="92ca0-115">Example 2: Display a list of all PowerShell providers that begin with specified letters</span></span>

```powershell
Get-PSProvider f*, r* | Format-List
```

<span data-ttu-id="92ca0-116">此命令會顯示所有名稱以字母 f 或 r 開頭的 PowerShell 提供者清單。</span><span class="sxs-lookup"><span data-stu-id="92ca0-116">This command displays a list of all PowerShell providers with names that begin with the letter f or r.</span></span>

### <span data-ttu-id="92ca0-117">範例 3︰尋找將提供者新增到您工作階段的嵌入式管理單元或模組</span><span class="sxs-lookup"><span data-stu-id="92ca0-117">Example 3: Find snap-ins or module that added providers to your session</span></span>

```powershell
Get-PSProvider | Format-Table name, module, pssnapin -auto
```

```Output
Name        Module       PSSnapIn
----        ------       --------
Test        TestModule
WSMan                    Microsoft.WSMan.Management
Alias                    Microsoft.PowerShell.Core
Environment              Microsoft.PowerShell.Core
FileSystem               Microsoft.PowerShell.Core
Function                 Microsoft.PowerShell.Core
Registry                 Microsoft.PowerShell.Core
Variable                 Microsoft.PowerShell.Core
Certificate              Microsoft.PowerShell.Security
```

```powershell
Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}
```

```Output
Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

<span data-ttu-id="92ca0-118">這些命令會尋找已將提供者新增至您會話的 PowerShell 嵌入式管理單元或模組。</span><span class="sxs-lookup"><span data-stu-id="92ca0-118">These commands find the PowerShell snap-ins or modules that added providers to your session.</span></span>
<span data-ttu-id="92ca0-119">所有的 PowerShell 專案（包括提供者）都源自嵌入式管理單元或模組。</span><span class="sxs-lookup"><span data-stu-id="92ca0-119">All PowerShell elements, including providers, originate in a snap-in or in a module.</span></span>

<span data-ttu-id="92ca0-120">這些命令會使用傳回之 **ProviderInfo** 物件的 PSSnapin 和 Module 屬性 `Get-PSProvider` 。</span><span class="sxs-lookup"><span data-stu-id="92ca0-120">These commands use the PSSnapin and Module properties of the **ProviderInfo** object that `Get-PSProvider` returns.</span></span>
<span data-ttu-id="92ca0-121">這些屬性的值包含新增提供者的嵌入式管理單元或模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="92ca0-121">The values of these properties contain the name of the snap-in or module that adds the provider.</span></span>

<span data-ttu-id="92ca0-122">第一個命令會取得工作階段中的所有提供者，並使用它們的 Name、Module 和 PSSnapin 屬性值，以表格方式設定格式。</span><span class="sxs-lookup"><span data-stu-id="92ca0-122">The first command gets all of the providers in the session and formats them in a table with the values of their Name, Module, and PSSnapin properties.</span></span>

<span data-ttu-id="92ca0-123">第二個命令會使用 `Where-Object` Cmdlet 來取得來自 **Microsoft. 安全性** 嵌入式管理單元的提供者。</span><span class="sxs-lookup"><span data-stu-id="92ca0-123">The second command uses the `Where-Object` cmdlet to get the providers that come from the **Microsoft.PowerShell.Security** snap-in.</span></span>

### <span data-ttu-id="92ca0-124">範例 4︰解析檔案系統提供者之 Home 屬性的路徑</span><span class="sxs-lookup"><span data-stu-id="92ca0-124">Example 4: Resolve the path of the Home property of the file system provider</span></span>

```powershell
C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

```powershell
PS C:\> (get-psprovider FileSystem).home
```

```Output
C:\Users\User01
```

<span data-ttu-id="92ca0-125">此範例顯示波狀符號 (~) 代表 FileSystem 提供者的 **Home** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="92ca0-125">This example shows that the tilde symbol (~) represents the value of the **Home** property of the FileSystem provider.</span></span>
<span data-ttu-id="92ca0-126">**Home** 屬性值為選擇性，但針對 **FileSystem** 提供者，它會定義為 `$env:homedrive\$env:homepath` 或 `$home` 。</span><span class="sxs-lookup"><span data-stu-id="92ca0-126">The **Home** property value is optional, but for the **FileSystem** provider, it is defined as `$env:homedrive\$env:homepath` or `$home`.</span></span>

## <span data-ttu-id="92ca0-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="92ca0-127">PARAMETERS</span></span>

### <span data-ttu-id="92ca0-128">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="92ca0-128">-PSProvider</span></span>

<span data-ttu-id="92ca0-129">指定此 Cmdlet 取得其資訊之 PowerShell 提供者的名稱或名稱。</span><span class="sxs-lookup"><span data-stu-id="92ca0-129">Specifies the name or names of the PowerShell providers about which this cmdlet gets information.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="92ca0-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="92ca0-130">CommonParameters</span></span>

<span data-ttu-id="92ca0-131">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="92ca0-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="92ca0-132">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="92ca0-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="92ca0-133">輸入</span><span class="sxs-lookup"><span data-stu-id="92ca0-133">INPUTS</span></span>

### <span data-ttu-id="92ca0-134">String[]</span><span class="sxs-lookup"><span data-stu-id="92ca0-134">String[]</span></span>

<span data-ttu-id="92ca0-135">您可以透過管道將一或多個提供者名稱字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="92ca0-135">You can pipe one or more provider name strings to this cmdlet.</span></span>

## <span data-ttu-id="92ca0-136">輸出</span><span class="sxs-lookup"><span data-stu-id="92ca0-136">OUTPUTS</span></span>

### <span data-ttu-id="92ca0-137">System.Management.Automation.ProviderInfo</span><span class="sxs-lookup"><span data-stu-id="92ca0-137">System.Management.Automation.ProviderInfo</span></span>

<span data-ttu-id="92ca0-138">此 Cmdlet 會傳回代表會話中 PowerShell 提供者的物件。</span><span class="sxs-lookup"><span data-stu-id="92ca0-138">This cmdlet returns objects that represent the PowerShell providers in the session.</span></span>

## <span data-ttu-id="92ca0-139">注意</span><span class="sxs-lookup"><span data-stu-id="92ca0-139">NOTES</span></span>

## <span data-ttu-id="92ca0-140">相關連結</span><span class="sxs-lookup"><span data-stu-id="92ca0-140">RELATED LINKS</span></span>
