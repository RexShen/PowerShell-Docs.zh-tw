---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/new-dscchecksum?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-DscChecksum
ms.openlocfilehash: cd784c5adac3aeeabc8e4cf9f5f4b0b67e9a000c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203940"
---
# <span data-ttu-id="abe57-103">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="abe57-103">New-DscChecksum</span></span>

## <span data-ttu-id="abe57-104">概要</span><span class="sxs-lookup"><span data-stu-id="abe57-104">SYNOPSIS</span></span>
<span data-ttu-id="abe57-105">建立 DSC 檔和 DSC 資源的總和檢查碼檔案。</span><span class="sxs-lookup"><span data-stu-id="abe57-105">Creates checksum files for DSC documents and DSC resources.</span></span>

## <span data-ttu-id="abe57-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="abe57-106">SYNTAX</span></span>

```
New-DscChecksum [-Path] <String[]> [[-OutPath] <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="abe57-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="abe57-107">DESCRIPTION</span></span>
<span data-ttu-id="abe57-108">**>new-dscchecksum 指令程式** 會針對 Windows PowerShell Desired State Configuration 產生總和檢查碼檔案，以 (DSC) 檔和壓縮的 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="abe57-108">The **New-DSCCheckSum** cmdlet generates checksum files for Windows PowerShell Desired State Configuration (DSC) documents and compressed DSC resources.</span></span>
<span data-ttu-id="abe57-109">這個 Cmdlet 會針對要在提取模式中使用的每個設定和資源，產生總和檢查碼檔案。</span><span class="sxs-lookup"><span data-stu-id="abe57-109">This cmdlet generates a checksum file for each configuration and resource to be used in pull mode.</span></span>
<span data-ttu-id="abe57-110">DSC 服務會使用總和檢查碼來確定目標節點上有正確的設定和資源。</span><span class="sxs-lookup"><span data-stu-id="abe57-110">The DSC service uses the checksums to make sure that the correct configuration and resources exist on the target node.</span></span>
<span data-ttu-id="abe57-111">將總和檢查碼與 dsc 服務存放區中相關聯的 DSC 檔和壓縮的 DSC 資源放在一起。</span><span class="sxs-lookup"><span data-stu-id="abe57-111">Place the checksums together with the associated DSC documents and compressed DSC resources in the DSC service store.</span></span>

## <span data-ttu-id="abe57-112">範例</span><span class="sxs-lookup"><span data-stu-id="abe57-112">EXAMPLES</span></span>

### <span data-ttu-id="abe57-113">範例1：為特定路徑中的所有設定建立總和檢查碼檔案</span><span class="sxs-lookup"><span data-stu-id="abe57-113">Example 1: Create checksum files for all configurations in a specific path</span></span>

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="abe57-114">此命令會在路徑 C:\DSC\Configurations 中建立所有設定的總和檢查碼檔案。</span><span class="sxs-lookup"><span data-stu-id="abe57-114">This command creates checksum files for all configurations in the path C:\DSC\Configurations.</span></span>
<span data-ttu-id="abe57-115">系統會略過已存在的任何總和檢查碼檔案。</span><span class="sxs-lookup"><span data-stu-id="abe57-115">Any checksum files that already exist are skipped.</span></span>

### <span data-ttu-id="abe57-116">範例2：為特定路徑中的所有設定建立總和檢查碼檔案，並覆寫現有的總和檢查碼檔案</span><span class="sxs-lookup"><span data-stu-id="abe57-116">Example 2: Create checksum files for all configurations in a specific path and overwrite the existing checksum files</span></span>

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\" -Force
```

<span data-ttu-id="abe57-117">此命令會在路徑 C:\DSC\Configurations 中建立所有設定的新總和檢查碼檔案。</span><span class="sxs-lookup"><span data-stu-id="abe57-117">This command creates new checksum files for all configurations in the path C:\DSC\Configurations.</span></span>
<span data-ttu-id="abe57-118">指定 *Force* 參數會導致命令覆寫已存在的任何總和檢查碼檔案。</span><span class="sxs-lookup"><span data-stu-id="abe57-118">Specifying the *Force* parameter causes the command to overwrite any checksum files that already exist.</span></span>

## <span data-ttu-id="abe57-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="abe57-119">PARAMETERS</span></span>

### <span data-ttu-id="abe57-120">-Force</span><span class="sxs-lookup"><span data-stu-id="abe57-120">-Force</span></span>
<span data-ttu-id="abe57-121">指出此 Cmdlet 會覆寫指定的輸出檔案 (如果該檔案已存在)。</span><span class="sxs-lookup"><span data-stu-id="abe57-121">Indicates that the cmdlet overwrites the specified output file if it already exists.</span></span>

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

### <span data-ttu-id="abe57-122">-OutPath</span><span class="sxs-lookup"><span data-stu-id="abe57-122">-OutPath</span></span>
<span data-ttu-id="abe57-123">指定輸出總和檢查碼檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="abe57-123">Specifies the path and file name of the output checksum file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="abe57-124">-Path</span><span class="sxs-lookup"><span data-stu-id="abe57-124">-Path</span></span>
<span data-ttu-id="abe57-125">指定輸入檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="abe57-125">Specifies the path of the input file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: ConfigurationPath

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="abe57-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="abe57-126">-Confirm</span></span>
<span data-ttu-id="abe57-127">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="abe57-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="abe57-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="abe57-128">-WhatIf</span></span>
<span data-ttu-id="abe57-129">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="abe57-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="abe57-130">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="abe57-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="abe57-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="abe57-131">CommonParameters</span></span>
<span data-ttu-id="abe57-132">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="abe57-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="abe57-133">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="abe57-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="abe57-134">輸入</span><span class="sxs-lookup"><span data-stu-id="abe57-134">INPUTS</span></span>

## <span data-ttu-id="abe57-135">輸出</span><span class="sxs-lookup"><span data-stu-id="abe57-135">OUTPUTS</span></span>

## <span data-ttu-id="abe57-136">注意</span><span class="sxs-lookup"><span data-stu-id="abe57-136">NOTES</span></span>

## <span data-ttu-id="abe57-137">相關連結</span><span class="sxs-lookup"><span data-stu-id="abe57-137">RELATED LINKS</span></span>

[<span data-ttu-id="abe57-138">Windows PowerShell Desired State Configuration 概觀</span><span class="sxs-lookup"><span data-stu-id="abe57-138">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)
