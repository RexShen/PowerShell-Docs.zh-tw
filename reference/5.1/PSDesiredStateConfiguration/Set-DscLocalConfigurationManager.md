---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 04/29/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/set-dsclocalconfigurationmanager?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-DscLocalConfigurationManager
ms.openlocfilehash: 0d35aa56a52f0e6c17abd0e7b2707869e780324c
ms.sourcegitcommit: 0d4d3e47f6979876550591f62061096e7a568f7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2020
ms.locfileid: "93205295"
---
# <span data-ttu-id="e90e8-103">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e90e8-103">Set-DscLocalConfigurationManager</span></span>

## <span data-ttu-id="e90e8-104">概要</span><span class="sxs-lookup"><span data-stu-id="e90e8-104">SYNOPSIS</span></span>

<span data-ttu-id="e90e8-105">將本機 Configuration Manager (LCM) 設定套用至節點。</span><span class="sxs-lookup"><span data-stu-id="e90e8-105">Applies Local Configuration Manager (LCM) settings to nodes.</span></span>

## <span data-ttu-id="e90e8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e90e8-106">SYNTAX</span></span>

### <span data-ttu-id="e90e8-107">ComputerNameSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="e90e8-107">ComputerNameSet (Default)</span></span>

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e90e8-108">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="e90e8-108">CimSessionSet</span></span>

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e90e8-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e90e8-109">DESCRIPTION</span></span>

<span data-ttu-id="e90e8-110">此 `Set-DscLocalConfigurationManager` Cmdlet 會將 LCM 設定或中繼設定套用至節點。</span><span class="sxs-lookup"><span data-stu-id="e90e8-110">The `Set-DscLocalConfigurationManager` cmdlet applies LCM settings, or meta-configuration, to nodes.</span></span> <span data-ttu-id="e90e8-111">透過指定電腦名稱或使用通用訊息模型 (CIM) 工作階段指定電腦。</span><span class="sxs-lookup"><span data-stu-id="e90e8-111">Specify computers by specifying computer names or by using Common Information Model (CIM) sessions.</span></span> <span data-ttu-id="e90e8-112">如果您沒有指定目標電腦，此 Cmdlet 會將設定套用到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="e90e8-112">If you do not specify a target computer, the cmdlet applies settings to the local computer.</span></span>

## <span data-ttu-id="e90e8-113">範例</span><span class="sxs-lookup"><span data-stu-id="e90e8-113">EXAMPLES</span></span>

### <span data-ttu-id="e90e8-114">範例1：套用 LCM 設定</span><span class="sxs-lookup"><span data-stu-id="e90e8-114">Example 1: Apply LCM settings</span></span>

```
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="e90e8-115">此命令會將 LCM 設定套用 `C:\DSC\Configurations\` 至目標節點。</span><span class="sxs-lookup"><span data-stu-id="e90e8-115">This command applies the LCM settings from `C:\DSC\Configurations\` to the targeted nodes.</span></span> <span data-ttu-id="e90e8-116">收到設定之後，LCM 會進行處理。</span><span class="sxs-lookup"><span data-stu-id="e90e8-116">After receiving the settings, LCM processes them.</span></span>

> [!WARNING]
> <span data-ttu-id="e90e8-117">如果相同的電腦上有多個中繼 mof 儲存在指定的資料夾中，則只會套用第一個中繼 mof。</span><span class="sxs-lookup"><span data-stu-id="e90e8-117">If there are multiple meta mofs for the same computer stored in the specified folder, only the first meta mof will be applied.</span></span>

### <span data-ttu-id="e90e8-118">範例2：使用 CIM 會話套用 LCM 設定</span><span class="sxs-lookup"><span data-stu-id="e90e8-118">Example 2: Apply LCM settings by using a CIM session</span></span>

```
$Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\" -CimSession $Session
```

<span data-ttu-id="e90e8-119">此範例會將 LCM 設定套用至電腦，並套用設定。</span><span class="sxs-lookup"><span data-stu-id="e90e8-119">This example applies LCM settings to a computer and applies the settings.</span></span> <span data-ttu-id="e90e8-120">這個範例會針對名為 Server01 的電腦，建立一個搭配此 Cmdlet 使用的 CIM 工作階段。</span><span class="sxs-lookup"><span data-stu-id="e90e8-120">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span> <span data-ttu-id="e90e8-121">或者，建立一個 CIM 工作階段的陣列，以便將該 Cmdlet 套用到多部指定的電腦。</span><span class="sxs-lookup"><span data-stu-id="e90e8-121">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="e90e8-122">第一個命令會使用 Cmdlet 建立 CIM 會話 `New-CimSession` ，然後將 **CimSession** 物件儲存在 `$Session` 變數中。</span><span class="sxs-lookup"><span data-stu-id="e90e8-122">The first command creates a CIM session by using the `New-CimSession` cmdlet, and then stores the **CimSession** object in the `$Session` variable.</span></span> <span data-ttu-id="e90e8-123">此命令會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="e90e8-123">The command prompts you for a password.</span></span> <span data-ttu-id="e90e8-124">如需詳細資訊，請鍵入 `Get-Help New-CimSession`。</span><span class="sxs-lookup"><span data-stu-id="e90e8-124">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="e90e8-125">第二個命令會將目標節點的 LCM 設定套用 `C:\DSC\Configurations\` 至儲存在變數中的 **CimSession** 物件所識別的電腦 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="e90e8-125">The second command applies LCM settings for the targeted node from `C:\DSC\Configurations\` to the computer identified by the **CimSession** objects stored in the `$Session` variable.</span></span> <span data-ttu-id="e90e8-126">在此範例中， `$Session` 變數只會包含名為 Server01 之電腦的 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="e90e8-126">In this example, the `$Session` variable contains a CIM session only for the computer named Server01.</span></span> <span data-ttu-id="e90e8-127">此命令會套用這些設定。</span><span class="sxs-lookup"><span data-stu-id="e90e8-127">The command applies the settings.</span></span> <span data-ttu-id="e90e8-128">收到設定之後，LCM 會進行處理。</span><span class="sxs-lookup"><span data-stu-id="e90e8-128">After receiving the settings, LCM processes them.</span></span>

## <span data-ttu-id="e90e8-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e90e8-129">PARAMETERS</span></span>

### <span data-ttu-id="e90e8-130">-CimSession</span><span class="sxs-lookup"><span data-stu-id="e90e8-130">-CimSession</span></span>

<span data-ttu-id="e90e8-131">在遠端工作階段或遠端電腦上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e90e8-131">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="e90e8-132">輸入電腦名稱稱或會話物件，例如 [CimSession](/powershell/module/CimCmdlets/New-CimSession) 或 [CimSession](/powershell/module/CimCmdlets/Get-CimSession) Cmdlet 的輸出。</span><span class="sxs-lookup"><span data-stu-id="e90e8-132">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) or [Get-CimSession](/powershell/module/CimCmdlets/Get-CimSession) cmdlet.</span></span>
<span data-ttu-id="e90e8-133">預設為本機電腦上的目前工作階段。</span><span class="sxs-lookup"><span data-stu-id="e90e8-133">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e90e8-134">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="e90e8-134">-ComputerName</span></span>

<span data-ttu-id="e90e8-135">指定電腦名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="e90e8-135">Specifies an array of computer names.</span></span> <span data-ttu-id="e90e8-136">此參數會將 **Path** 參數中具有中繼設定檔的電腦限制為數組中指定的電腦。</span><span class="sxs-lookup"><span data-stu-id="e90e8-136">This parameter restricts the computers that have meta-configuration documents in the **Path** parameter to those specified in the array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e90e8-137">-Credential</span><span class="sxs-lookup"><span data-stu-id="e90e8-137">-Credential</span></span>

<span data-ttu-id="e90e8-138">指定目標電腦的使用者名稱和密碼，做為 **PSCredential** 物件。</span><span class="sxs-lookup"><span data-stu-id="e90e8-138">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span> <span data-ttu-id="e90e8-139">若要取得 **PSCredential** 物件，請使用 Get-credential Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e90e8-139">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span> <span data-ttu-id="e90e8-140">如需詳細資訊，請鍵入 `Get-Help Get-Credential`。</span><span class="sxs-lookup"><span data-stu-id="e90e8-140">For more information, type `Get-Help Get-Credential`.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e90e8-141">-Force</span><span class="sxs-lookup"><span data-stu-id="e90e8-141">-Force</span></span>

<span data-ttu-id="e90e8-142">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="e90e8-142">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="e90e8-143">-Path</span><span class="sxs-lookup"><span data-stu-id="e90e8-143">-Path</span></span>

<span data-ttu-id="e90e8-144">指定包含組態設定檔之資料夾的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="e90e8-144">Specifies a file path of a folder that contains configuration settings files.</span></span> <span data-ttu-id="e90e8-145">此 Cmdlet 會發佈這些 LCM 設定，並將這些 LCM 設定套用至在指定路徑中具有設定檔案的電腦。</span><span class="sxs-lookup"><span data-stu-id="e90e8-145">The cmdlet publishes and applies these LCM settings to computers that have settings files in the specified path.</span></span> <span data-ttu-id="e90e8-146">每個目標節點都必須具有下列格式的設定檔： `NetBIOS Name.meta.mof` 。</span><span class="sxs-lookup"><span data-stu-id="e90e8-146">Each target node must have a settings file of the following format: `NetBIOS Name.meta.mof`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e90e8-147">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="e90e8-147">-ThrottleLimit</span></span>

<span data-ttu-id="e90e8-148">指定為執行 Cmdlet 可建立的最大並行作業數。</span><span class="sxs-lookup"><span data-stu-id="e90e8-148">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span> <span data-ttu-id="e90e8-149">如果省略此參數或輸入的值 `0` ，則 Windows PowerShell 會根據電腦上執行的 CIM Cmdlet 數目，計算 Cmdlet 的最佳節流限制。</span><span class="sxs-lookup"><span data-stu-id="e90e8-149">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span> <span data-ttu-id="e90e8-150">節流限制僅適用於目前 Cmdlet，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="e90e8-150">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="e90e8-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e90e8-151">-Confirm</span></span>

<span data-ttu-id="e90e8-152">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="e90e8-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e90e8-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e90e8-153">-WhatIf</span></span>

<span data-ttu-id="e90e8-154">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="e90e8-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e90e8-155">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="e90e8-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e90e8-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e90e8-156">CommonParameters</span></span>

<span data-ttu-id="e90e8-157">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e90e8-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e90e8-158">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e90e8-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e90e8-159">輸入</span><span class="sxs-lookup"><span data-stu-id="e90e8-159">INPUTS</span></span>

## <span data-ttu-id="e90e8-160">輸出</span><span class="sxs-lookup"><span data-stu-id="e90e8-160">OUTPUTS</span></span>

## <span data-ttu-id="e90e8-161">注意</span><span class="sxs-lookup"><span data-stu-id="e90e8-161">NOTES</span></span>

## <span data-ttu-id="e90e8-162">相關連結</span><span class="sxs-lookup"><span data-stu-id="e90e8-162">RELATED LINKS</span></span>

[<span data-ttu-id="e90e8-163">Windows PowerShell Desired State Configuration 概觀</span><span class="sxs-lookup"><span data-stu-id="e90e8-163">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="e90e8-164">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e90e8-164">Get-DscLocalConfigurationManager</span></span>](Get-DscLocalConfigurationManager.md)
