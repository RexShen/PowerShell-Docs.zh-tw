---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedscript?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledScript
ms.openlocfilehash: 6b99eb73fb126b67b97fc360b2f0474710b4cc52
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204136"
---
# <span data-ttu-id="e818a-103">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="e818a-103">Get-InstalledScript</span></span>

## <span data-ttu-id="e818a-104">概要</span><span class="sxs-lookup"><span data-stu-id="e818a-104">SYNOPSIS</span></span>
<span data-ttu-id="e818a-105">取得已安裝的腳本。</span><span class="sxs-lookup"><span data-stu-id="e818a-105">Gets an installed script.</span></span>

## <span data-ttu-id="e818a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e818a-106">SYNTAX</span></span>

```
Get-InstalledScript [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="e818a-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e818a-107">DESCRIPTION</span></span>

<span data-ttu-id="e818a-108">**>get-installedscript 指令程式** 會針對 CurrentUser 和 AllUsers 範圍取得已安裝的腳本。</span><span class="sxs-lookup"><span data-stu-id="e818a-108">The **Get-InstalledScript** cmdlet gets installed scripts for CurrentUser and AllUsers scopes.</span></span>

## <span data-ttu-id="e818a-109">範例</span><span class="sxs-lookup"><span data-stu-id="e818a-109">EXAMPLES</span></span>

### <span data-ttu-id="e818a-110">範例1：取得所有已安裝的腳本</span><span class="sxs-lookup"><span data-stu-id="e818a-110">Example 1: Get all installed scripts</span></span>

```
PS C:\> Get-InstalledScript
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
2.0        Script-WithDependencies1            Script     local1               Description for the Script-WithDependencies1 script
```

<span data-ttu-id="e818a-111">此命令會取得所有已安裝的腳本。</span><span class="sxs-lookup"><span data-stu-id="e818a-111">This command gets all installed scripts.</span></span>

### <span data-ttu-id="e818a-112">範例2：依名稱取得已安裝的腳本</span><span class="sxs-lookup"><span data-stu-id="e818a-112">Example 2: Get installed scripts by name</span></span>

```
PS C:\> Get-InstalledScript -Name "Required-Scri*"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="e818a-113">此命令會取得名稱開頭為必要-Scri 的腳本。</span><span class="sxs-lookup"><span data-stu-id="e818a-113">This command gets scripts where the name begins with Required-Scri.</span></span>

## <span data-ttu-id="e818a-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e818a-114">PARAMETERS</span></span>

### <span data-ttu-id="e818a-115">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="e818a-115">-AllowPrerelease</span></span>

<span data-ttu-id="e818a-116">包含在標記為發行前版本的結果腳本中。</span><span class="sxs-lookup"><span data-stu-id="e818a-116">Includes in the results scripts marked as a prerelease.</span></span>

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

### <span data-ttu-id="e818a-117">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="e818a-117">-MaximumVersion</span></span>

<span data-ttu-id="e818a-118">指定要取得之腳本的最大或最新版本。</span><span class="sxs-lookup"><span data-stu-id="e818a-118">Specifies the maximum, or latest, version of a script to get.</span></span>
<span data-ttu-id="e818a-119">*MaximumVersion* 和 *RequiredVersion* 參數是互斥的；您無法在相同的命令中使用這兩個參數。</span><span class="sxs-lookup"><span data-stu-id="e818a-119">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e818a-120">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e818a-120">-MinimumVersion</span></span>

<span data-ttu-id="e818a-121">指定要取得之腳本的最小版本。</span><span class="sxs-lookup"><span data-stu-id="e818a-121">Specifies the minimum version of a script to get.</span></span>
<span data-ttu-id="e818a-122">*MinimumVersion* 和 *RequiredVersion* 參數是互斥的；您無法在相同的命令中使用這兩個參數。</span><span class="sxs-lookup"><span data-stu-id="e818a-122">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e818a-123">-Name</span><span class="sxs-lookup"><span data-stu-id="e818a-123">-Name</span></span>

<span data-ttu-id="e818a-124">指定要取得之腳本的名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="e818a-124">Specifies an array of names of scripts to get.</span></span>
<span data-ttu-id="e818a-125">可使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="e818a-125">Wildcards are accepted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="e818a-126">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e818a-126">-RequiredVersion</span></span>

<span data-ttu-id="e818a-127">指定要取得之腳本的確切版本。</span><span class="sxs-lookup"><span data-stu-id="e818a-127">Specifies the exact version of a script to get.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e818a-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e818a-128">CommonParameters</span></span>

<span data-ttu-id="e818a-129">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e818a-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e818a-130">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e818a-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e818a-131">輸入</span><span class="sxs-lookup"><span data-stu-id="e818a-131">INPUTS</span></span>

### <span data-ttu-id="e818a-132">System.String[]</span><span class="sxs-lookup"><span data-stu-id="e818a-132">System.String[]</span></span>

### <span data-ttu-id="e818a-133">System.String</span><span class="sxs-lookup"><span data-stu-id="e818a-133">System.String</span></span>

## <span data-ttu-id="e818a-134">輸出</span><span class="sxs-lookup"><span data-stu-id="e818a-134">OUTPUTS</span></span>

### <span data-ttu-id="e818a-135">System.Object</span><span class="sxs-lookup"><span data-stu-id="e818a-135">System.Object</span></span>

## <span data-ttu-id="e818a-136">注意</span><span class="sxs-lookup"><span data-stu-id="e818a-136">NOTES</span></span>

## <span data-ttu-id="e818a-137">相關連結</span><span class="sxs-lookup"><span data-stu-id="e818a-137">RELATED LINKS</span></span>

[<span data-ttu-id="e818a-138">Install-Script</span><span class="sxs-lookup"><span data-stu-id="e818a-138">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="e818a-139">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="e818a-139">Uninstall-Script</span></span>](Uninstall-Script.md)
