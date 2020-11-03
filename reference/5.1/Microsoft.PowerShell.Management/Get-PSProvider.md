---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: 997d86460837946a2cf18fc78f058f21472dd909
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203987"
---
# <span data-ttu-id="338e6-103">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="338e6-103">Get-PSProvider</span></span>

## <span data-ttu-id="338e6-104">概要</span><span class="sxs-lookup"><span data-stu-id="338e6-104">SYNOPSIS</span></span>
<span data-ttu-id="338e6-105">取得指定 Windows PowerShell 提供者的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="338e6-105">Gets information about the specified Windows PowerShell provider.</span></span>

## <span data-ttu-id="338e6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="338e6-106">SYNTAX</span></span>

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="338e6-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="338e6-107">DESCRIPTION</span></span>
<span data-ttu-id="338e6-108">**PSProvider** 指令程式會取得目前會話中的 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="338e6-108">The **Get-PSProvider** cmdlet gets the Windows PowerShell providers in the current session.</span></span>
<span data-ttu-id="338e6-109">您可以取得工作階段中的特定磁碟機或所有磁碟機。</span><span class="sxs-lookup"><span data-stu-id="338e6-109">You can get a particular drive or all drives in the session.</span></span>

<span data-ttu-id="338e6-110">Windows PowerShell 提供者可讓您存取各種資料存放區，就好像它們是檔案系統磁碟機一樣。</span><span class="sxs-lookup"><span data-stu-id="338e6-110">Windows PowerShell providers let you access a variety of data stores as though they were file system drives.</span></span>
<span data-ttu-id="338e6-111">如需 Windows PowerShell 提供者的資訊，請參閱 about_Providers。</span><span class="sxs-lookup"><span data-stu-id="338e6-111">For information about Windows PowerShell providers, see about_Providers.</span></span>

## <span data-ttu-id="338e6-112">範例</span><span class="sxs-lookup"><span data-stu-id="338e6-112">EXAMPLES</span></span>

### <span data-ttu-id="338e6-113">範例 1︰顯示所有可用提供者的清單</span><span class="sxs-lookup"><span data-stu-id="338e6-113">Example 1: Display a list of all available providers</span></span>

```
PS C:\> Get-PSProvider
```

<span data-ttu-id="338e6-114">這個命令會顯示所有可用 Windows PowerShell 提供者的清單。</span><span class="sxs-lookup"><span data-stu-id="338e6-114">This command displays a list of all available Windows PowerShell providers.</span></span>

### <span data-ttu-id="338e6-115">範例 2︰顯示以指定字母開頭的所有 Windows PowerShell 提供者的清單</span><span class="sxs-lookup"><span data-stu-id="338e6-115">Example 2: Display a list of all Windows PowerShell providers that begin with specified letters</span></span>

```
PS C:\> Get-PSProvider f*, r* | Format-List
```

<span data-ttu-id="338e6-116">這個命令會顯示所有名稱以字母 f 或 r 開頭的 Windows PowerShell 提供者清單。</span><span class="sxs-lookup"><span data-stu-id="338e6-116">This command displays a list of all Windows PowerShell providers with names that begin with the letter f or r.</span></span>

### <span data-ttu-id="338e6-117">範例 3︰尋找將提供者新增到您工作階段的嵌入式管理單元或模組</span><span class="sxs-lookup"><span data-stu-id="338e6-117">Example 3: Find snap-ins or module that added providers to your session</span></span>

```
PS C:\> Get-PSProvider | Format-Table name, module, pssnapin -auto

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

PS C:\> Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}

Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

<span data-ttu-id="338e6-118">這些命令會尋找已將提供者新增到您工作階段的 Windows PowerShell 嵌入式管理單元或模組。</span><span class="sxs-lookup"><span data-stu-id="338e6-118">These commands find the Windows PowerShell snap-ins or modules that added providers to your session.</span></span>
<span data-ttu-id="338e6-119">包括提供者在內的所有 Windows PowerShell 元素都源自嵌入式管理單元或模組。</span><span class="sxs-lookup"><span data-stu-id="338e6-119">All Windows PowerShell elements, including providers, originate in a snap-in or in a module.</span></span>

<span data-ttu-id="338e6-120">這些命令會使用 **PSProvider** 傳回之 **ProviderInfo** 物件的 PSSnapin 和 Module 屬性。</span><span class="sxs-lookup"><span data-stu-id="338e6-120">These commands use the PSSnapin and Module properties of the **ProviderInfo** object that **Get-PSProvider** returns.</span></span>
<span data-ttu-id="338e6-121">這些屬性的值包含新增提供者的嵌入式管理單元或模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="338e6-121">The values of these properties contain the name of the snap-in or module that adds the provider.</span></span>

<span data-ttu-id="338e6-122">第一個命令會取得工作階段中的所有提供者，並使用它們的 Name、Module 和 PSSnapin 屬性值，以表格方式設定格式。</span><span class="sxs-lookup"><span data-stu-id="338e6-122">The first command gets all of the providers in the session and formats them in a table with the values of their Name, Module, and PSSnapin properties.</span></span>

<span data-ttu-id="338e6-123">第二個命令會使用 Where-Object Cmdlet 來取得來自 **Microsoft. 安全性** 嵌入式管理單元的提供者。</span><span class="sxs-lookup"><span data-stu-id="338e6-123">The second command uses the Where-Object cmdlet to get the providers that come from the **Microsoft.PowerShell.Security** snap-in.</span></span>

### <span data-ttu-id="338e6-124">範例 4︰解析檔案系統提供者之 Home 屬性的路徑</span><span class="sxs-lookup"><span data-stu-id="338e6-124">Example 4: Resolve the path of the Home property of the file system provider</span></span>

```
PS C:\> Resolve-Path ~

Path
----
C:\Users\User01

PS C:\> (get-psprovider FileSystem).home
C:\Users\User01
```

<span data-ttu-id="338e6-125">這個範例示範以波狀符號 (~) 代表 FileSystem 提供者的 Home 屬性值。</span><span class="sxs-lookup"><span data-stu-id="338e6-125">This example shows that the tilde symbol (~) represents the value of the Home property of the FileSystem provider.</span></span>
<span data-ttu-id="338e6-126">Home 屬性值為選擇性，但針對 FileSystem 提供者定義為 $env:homedrive\$env:homepath 或 $home。</span><span class="sxs-lookup"><span data-stu-id="338e6-126">The Home property value is optional, but for the FileSystem provider, it is defined as $env:homedrive\$env:homepath or $home.</span></span>

## <span data-ttu-id="338e6-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="338e6-127">PARAMETERS</span></span>

### <span data-ttu-id="338e6-128">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="338e6-128">-PSProvider</span></span>
<span data-ttu-id="338e6-129">指定一或多個此 Cmdlet 要取得相關資訊的 Windows PowerShell 提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="338e6-129">Specifies the name or names of the Windows PowerShell providers about which this cmdlet gets information.</span></span>

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

### <span data-ttu-id="338e6-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="338e6-130">CommonParameters</span></span>
<span data-ttu-id="338e6-131">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="338e6-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="338e6-132">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="338e6-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="338e6-133">輸入</span><span class="sxs-lookup"><span data-stu-id="338e6-133">INPUTS</span></span>

### <span data-ttu-id="338e6-134">String[]</span><span class="sxs-lookup"><span data-stu-id="338e6-134">String[]</span></span>

<span data-ttu-id="338e6-135">您可以透過管道將一或多個提供者名稱字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="338e6-135">You can pipe one or more provider name strings to this cmdlet.</span></span>

## <span data-ttu-id="338e6-136">輸出</span><span class="sxs-lookup"><span data-stu-id="338e6-136">OUTPUTS</span></span>

### <span data-ttu-id="338e6-137">System.Management.Automation.ProviderInfo</span><span class="sxs-lookup"><span data-stu-id="338e6-137">System.Management.Automation.ProviderInfo</span></span>
<span data-ttu-id="338e6-138">此 Cmdlet 會傳回代表工作階段中 Windows PowerShell 提供者的物件。</span><span class="sxs-lookup"><span data-stu-id="338e6-138">This cmdlet returns objects that represent the Windows PowerShell providers in the session.</span></span>

## <span data-ttu-id="338e6-139">注意</span><span class="sxs-lookup"><span data-stu-id="338e6-139">NOTES</span></span>

## <span data-ttu-id="338e6-140">相關連結</span><span class="sxs-lookup"><span data-stu-id="338e6-140">RELATED LINKS</span></span>

## <span data-ttu-id="338e6-141">相關連結</span><span class="sxs-lookup"><span data-stu-id="338e6-141">RELATED LINKS</span></span>
