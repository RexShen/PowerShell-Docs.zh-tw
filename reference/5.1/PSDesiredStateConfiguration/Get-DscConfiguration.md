---
external help file: Get-DSCConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfiguration
ms.openlocfilehash: 42b24e72de4c4bcc9326d52861c08a05853b18e0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203964"
---
# <span data-ttu-id="10be2-103">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="10be2-103">Get-DscConfiguration</span></span>

## <span data-ttu-id="10be2-104">概要</span><span class="sxs-lookup"><span data-stu-id="10be2-104">SYNOPSIS</span></span>
<span data-ttu-id="10be2-105">取得節點的目前設定。</span><span class="sxs-lookup"><span data-stu-id="10be2-105">Gets the current configuration of the nodes.</span></span>

## <span data-ttu-id="10be2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="10be2-106">SYNTAX</span></span>

```
Get-DscConfiguration [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [<CommonParameters>]
```

## <span data-ttu-id="10be2-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="10be2-107">DESCRIPTION</span></span>
<span data-ttu-id="10be2-108">如果設定存在， **update-dscconfiguration 指令程式** 會取得目前的節點設定。</span><span class="sxs-lookup"><span data-stu-id="10be2-108">The **Get-DscConfiguration** cmdlet gets the current configuration of the nodes, if the configuration exists.</span></span>
<span data-ttu-id="10be2-109">使用通用訊息模型 (CIM) 工作階段指定電腦。</span><span class="sxs-lookup"><span data-stu-id="10be2-109">Specify computers by using Common Information Model (CIM) sessions.</span></span>
<span data-ttu-id="10be2-110">如果您沒有指定目標電腦，此 Cmdlet 會從本機電腦取得設定。</span><span class="sxs-lookup"><span data-stu-id="10be2-110">If you do not specify a target computer, the cmdlet gets the configuration from the local computer.</span></span>

## <span data-ttu-id="10be2-111">範例</span><span class="sxs-lookup"><span data-stu-id="10be2-111">EXAMPLES</span></span>

### <span data-ttu-id="10be2-112">範例1：取得本機電腦的設定</span><span class="sxs-lookup"><span data-stu-id="10be2-112">Example 1: Get the configuration for the local computer</span></span>

```
PS C:\> Get-DscConfiguration
```

<span data-ttu-id="10be2-113">此命令會取得本機電腦的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="10be2-113">This command gets the current state for the local computer.</span></span>

### <span data-ttu-id="10be2-114">範例2：取得指定電腦的設定</span><span class="sxs-lookup"><span data-stu-id="10be2-114">Example 2: Get the configuration for a specified computer</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Get-DscConfiguration -CimSession $Session
```

<span data-ttu-id="10be2-115">此範例會從 CIM 會話指定的電腦取得目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="10be2-115">This example gets the current state from a computer specified by a CIM session.</span></span>
<span data-ttu-id="10be2-116">這個範例會針對名為 Server01 的電腦，建立一個搭配此 Cmdlet 使用的 CIM 工作階段。</span><span class="sxs-lookup"><span data-stu-id="10be2-116">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="10be2-117">或者，建立一個 CIM 工作階段的陣列，以便將該 Cmdlet 套用到多部指定的電腦。</span><span class="sxs-lookup"><span data-stu-id="10be2-117">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="10be2-118">第一個命令會使用 **New-CimSession** Cmdlet 建立 CIM 工作階段，然後再以 **$Session** 變數儲存 **CimSession** 物件。</span><span class="sxs-lookup"><span data-stu-id="10be2-118">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the **$Session** variable.</span></span>
<span data-ttu-id="10be2-119">此命令會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="10be2-119">The command prompts you for a password.</span></span>
<span data-ttu-id="10be2-120">如需詳細資訊，請鍵入 `Get-Help New-CimSession`。</span><span class="sxs-lookup"><span data-stu-id="10be2-120">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="10be2-121">第二個命令會取得以 **$Session** 變數儲存的 **CimSession** 物件所識別之電腦的目前設定，在此案例中為名為 Server01 的電腦。</span><span class="sxs-lookup"><span data-stu-id="10be2-121">The second command gets the current configuration for the computers identified by the **CimSession** objects stored in the **$Session** variable, in this case, the computer named Server01.</span></span>

## <span data-ttu-id="10be2-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="10be2-122">PARAMETERS</span></span>

### <span data-ttu-id="10be2-123">-AsJob</span><span class="sxs-lookup"><span data-stu-id="10be2-123">-AsJob</span></span>
<span data-ttu-id="10be2-124">指出此 Cmdlet 會以背景工作方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="10be2-124">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="10be2-125">-CimSession</span><span class="sxs-lookup"><span data-stu-id="10be2-125">-CimSession</span></span>
<span data-ttu-id="10be2-126">在遠端工作階段或遠端電腦上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="10be2-126">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="10be2-127">輸入電腦名稱稱或會話物件，例如 [CimSession](/powershell/module/cimcmdlets/new-cimsession) 或 [CimSession](/powershell/module/cimcmdlets/get-cimsession) Cmdlet 的輸出。</span><span class="sxs-lookup"><span data-stu-id="10be2-127">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="10be2-128">預設為本機電腦上的目前工作階段。</span><span class="sxs-lookup"><span data-stu-id="10be2-128">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="10be2-129">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="10be2-129">-ThrottleLimit</span></span>
<span data-ttu-id="10be2-130">指定為執行 Cmdlet 可建立的最大並行作業數。</span><span class="sxs-lookup"><span data-stu-id="10be2-130">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="10be2-131">如果省略此參數或輸入的值 `0` ，則 Windows PowerShell 會根據電腦上執行的 CIM Cmdlet 數目，計算 Cmdlet 的最佳節流限制。</span><span class="sxs-lookup"><span data-stu-id="10be2-131">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="10be2-132">節流限制僅適用於目前 Cmdlet，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="10be2-132">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="10be2-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="10be2-133">CommonParameters</span></span>
<span data-ttu-id="10be2-134">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="10be2-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="10be2-135">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="10be2-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="10be2-136">輸入</span><span class="sxs-lookup"><span data-stu-id="10be2-136">INPUTS</span></span>

## <span data-ttu-id="10be2-137">輸出</span><span class="sxs-lookup"><span data-stu-id="10be2-137">OUTPUTS</span></span>

## <span data-ttu-id="10be2-138">注意</span><span class="sxs-lookup"><span data-stu-id="10be2-138">NOTES</span></span>

## <span data-ttu-id="10be2-139">相關連結</span><span class="sxs-lookup"><span data-stu-id="10be2-139">RELATED LINKS</span></span>

[<span data-ttu-id="10be2-140">Windows PowerShell Desired State Configuration 概觀</span><span class="sxs-lookup"><span data-stu-id="10be2-140">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="10be2-141">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="10be2-141">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="10be2-142">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="10be2-142">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="10be2-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="10be2-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="10be2-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="10be2-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
