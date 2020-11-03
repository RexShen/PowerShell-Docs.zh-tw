---
external help file: Get-DscConfigurationStatus.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfigurationStatus
ms.openlocfilehash: 0d59ce58a70eab68441ea1fe6097bbdf7792a54f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203968"
---
# <span data-ttu-id="c0c74-103">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="c0c74-103">Get-DscConfigurationStatus</span></span>

## <span data-ttu-id="c0c74-104">概要</span><span class="sxs-lookup"><span data-stu-id="c0c74-104">SYNOPSIS</span></span>
<span data-ttu-id="c0c74-105">抓取已完成設定執行的相關資料。</span><span class="sxs-lookup"><span data-stu-id="c0c74-105">Retrieves data about completed configuration runs.</span></span>

## <span data-ttu-id="c0c74-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c0c74-106">SYNTAX</span></span>

```
Get-DscConfigurationStatus [-All] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [<CommonParameters>]
```

## <span data-ttu-id="c0c74-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c0c74-107">DESCRIPTION</span></span>
<span data-ttu-id="c0c74-108">Get-dscconfigurationstatus 指令 Cmdlet 會 **取得** 系統上已完成設定執行的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c0c74-108">The **Get-DscConfigurationStatus** cmdlet retrieves detailed information about completed configuration runs on the system.</span></span>
<span data-ttu-id="c0c74-109">根據預設，它會傳回上次設定執行的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c0c74-109">By default, it returns the information about the last configuration run.</span></span>
<span data-ttu-id="c0c74-110">此 Cmdlet 適用于尋找設定執行的歷程記錄資訊，例如執行設定的時間、執行的狀態、設定中的資源數目，以及哪些資源成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="c0c74-110">This cmdlet is useful for finding historical information about configuration runs, such as when the configurations were run, the status of the runs, the number of resources in the configurations, and which resources succeeded or failed.</span></span>

## <span data-ttu-id="c0c74-111">範例</span><span class="sxs-lookup"><span data-stu-id="c0c74-111">EXAMPLES</span></span>

### <span data-ttu-id="c0c74-112">範例1：取得上次設定執行的資訊</span><span class="sxs-lookup"><span data-stu-id="c0c74-112">Example 1: Get information on the last configuration run</span></span>

```
PS C:\> Get-DscConfigurationStatus
```

<span data-ttu-id="c0c74-113">此命令會取得最後一次設定執行的資訊。</span><span class="sxs-lookup"><span data-stu-id="c0c74-113">This command gets information on the last configuration run.</span></span>

### <span data-ttu-id="c0c74-114">範例2：取得所有設定的資訊</span><span class="sxs-lookup"><span data-stu-id="c0c74-114">Example 2: Get information on all configurations</span></span>

```
PS C:\> Get-DscConfigurationStatus -All
```

<span data-ttu-id="c0c74-115">此命令會取得系統上執行之所有設定的相關資訊，包括 Windows PowerShell Desired State Configuration (DSC) 一致性檢查。</span><span class="sxs-lookup"><span data-stu-id="c0c74-115">This command gets information about all the configurations that were run on the system, including the Windows PowerShell Desired State Configuration (DSC) consistency check.</span></span>

### <span data-ttu-id="c0c74-116">範例3：取得在遠端電腦上執行設定的資訊</span><span class="sxs-lookup"><span data-stu-id="c0c74-116">Example 3: Get information on the configuration run on a remote computer</span></span>

```
PS C:\> Get-DscConfigurationStatus -CimSession "Server01"
```

<span data-ttu-id="c0c74-117">此命令會取得名為 Server01 之遠端電腦的設定執行詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c0c74-117">This command gets the configuration run details of the remote computer named Server01.</span></span>
<span data-ttu-id="c0c74-118">這會使用 WSMan 傳輸來連接遠端電腦，並要求連接的使用者必須是遠端電腦上的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="c0c74-118">This uses the WSMan transport to connect to the remote computer and requires that the connecting user be an administrator on the remote computer.</span></span>

## <span data-ttu-id="c0c74-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c0c74-119">PARAMETERS</span></span>

### <span data-ttu-id="c0c74-120">-All</span><span class="sxs-lookup"><span data-stu-id="c0c74-120">-All</span></span>
<span data-ttu-id="c0c74-121">指出此 Cmdlet 會抓取電腦上所有設定執行的相關資訊，包括設定應用程式與一致性檢查。</span><span class="sxs-lookup"><span data-stu-id="c0c74-121">Indicates that this cmdlet retrieves information about all the configuration runs on the computer, including the configuration application and the consistency check.</span></span>

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

### <span data-ttu-id="c0c74-122">-AsJob</span><span class="sxs-lookup"><span data-stu-id="c0c74-122">-AsJob</span></span>
<span data-ttu-id="c0c74-123">指出此 Cmdlet 會以背景工作方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="c0c74-123">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="c0c74-124">-CimSession</span><span class="sxs-lookup"><span data-stu-id="c0c74-124">-CimSession</span></span>
<span data-ttu-id="c0c74-125">在遠端工作階段或遠端電腦上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c0c74-125">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="c0c74-126">輸入電腦名稱稱或會話物件，例如 [CimSession](/powershell/module/cimcmdlets/new-cimsession) 或 [CimSession](/powershell/module/cimcmdlets/get-cimsession) Cmdlet 的輸出。</span><span class="sxs-lookup"><span data-stu-id="c0c74-126">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="c0c74-127">預設為本機電腦上的目前工作階段。</span><span class="sxs-lookup"><span data-stu-id="c0c74-127">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c0c74-128">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="c0c74-128">-ThrottleLimit</span></span>
<span data-ttu-id="c0c74-129">指定為執行 Cmdlet 可建立的最大並行作業數。</span><span class="sxs-lookup"><span data-stu-id="c0c74-129">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="c0c74-130">如果省略此參數或輸入的值 `0` ，則 Windows PowerShell 會根據電腦上執行的 CIM Cmdlet 數目，計算 Cmdlet 的最佳節流限制。</span><span class="sxs-lookup"><span data-stu-id="c0c74-130">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="c0c74-131">節流限制僅適用於目前 Cmdlet，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="c0c74-131">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="c0c74-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c0c74-132">CommonParameters</span></span>
<span data-ttu-id="c0c74-133">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c0c74-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c0c74-134">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c0c74-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c0c74-135">輸入</span><span class="sxs-lookup"><span data-stu-id="c0c74-135">INPUTS</span></span>

## <span data-ttu-id="c0c74-136">輸出</span><span class="sxs-lookup"><span data-stu-id="c0c74-136">OUTPUTS</span></span>

## <span data-ttu-id="c0c74-137">注意</span><span class="sxs-lookup"><span data-stu-id="c0c74-137">NOTES</span></span>

## <span data-ttu-id="c0c74-138">相關連結</span><span class="sxs-lookup"><span data-stu-id="c0c74-138">RELATED LINKS</span></span>

[<span data-ttu-id="c0c74-139">Windows PowerShell Desired State Configuration 概觀</span><span class="sxs-lookup"><span data-stu-id="c0c74-139">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="c0c74-140">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c0c74-140">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="c0c74-141">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c0c74-141">Get-DscLocalConfigurationManager</span></span>](Get-DscLocalConfigurationManager.md)

[<span data-ttu-id="c0c74-142">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c0c74-142">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="c0c74-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c0c74-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="c0c74-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="c0c74-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
