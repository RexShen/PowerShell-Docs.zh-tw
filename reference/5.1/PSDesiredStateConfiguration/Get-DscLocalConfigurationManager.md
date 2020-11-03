---
external help file: Get-DSCLocalConfigurationManager.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dsclocalconfigurationmanager?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscLocalConfigurationManager
ms.openlocfilehash: 162770d8eb3a8953dcfaeb31f30742a46353b33b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203944"
---
# <span data-ttu-id="c822b-103">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c822b-103">Get-DscLocalConfigurationManager</span></span>

## <span data-ttu-id="c822b-104">概要</span><span class="sxs-lookup"><span data-stu-id="c822b-104">SYNOPSIS</span></span>

<span data-ttu-id="c822b-105">取得節點的本機 Configuration Manager (LCM) 設定和狀態。</span><span class="sxs-lookup"><span data-stu-id="c822b-105">Gets Local Configuration Manager (LCM) settings and states for the node.</span></span>

## <span data-ttu-id="c822b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c822b-106">SYNTAX</span></span>

```
Get-DscLocalConfigurationManager [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [<CommonParameters>]
```

## <span data-ttu-id="c822b-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c822b-107">DESCRIPTION</span></span>

<span data-ttu-id="c822b-108">此 `Get-DscLocalConfigurationManager` Cmdlet 會取得節點的 lcm 設定、中繼設定和 lcm 的狀態。</span><span class="sxs-lookup"><span data-stu-id="c822b-108">The `Get-DscLocalConfigurationManager` cmdlet gets LCM settings, or meta-configuration, and the states of LCM for the node.</span></span> <span data-ttu-id="c822b-109">使用通用訊息模型 (CIM) 工作階段指定電腦。</span><span class="sxs-lookup"><span data-stu-id="c822b-109">Specify computers by using Common Information Model (CIM) sessions.</span></span> <span data-ttu-id="c822b-110">如果您沒有指定目標電腦，此 Cmdlet 會從本機電腦取得組態設定。</span><span class="sxs-lookup"><span data-stu-id="c822b-110">If you do not specify a target computer, the cmdlet gets the configuration settings from the local computer.</span></span>

## <span data-ttu-id="c822b-111">範例</span><span class="sxs-lookup"><span data-stu-id="c822b-111">EXAMPLES</span></span>

### <span data-ttu-id="c822b-112">範例1：取得本機電腦的 LCM 設定</span><span class="sxs-lookup"><span data-stu-id="c822b-112">Example 1: Get LCM settings for the local computer</span></span>

```powershell
Get-DscLocalConfigurationManager
```

```Output
ActionAfterReboot              : ContinueConfiguration
AgentId                        : 47edd8c9-2798-4827-839a-b35cc87e69fb
AllowModuleOverWrite           : False
CertificateID                  :
ConfigurationDownloadManagers  : {}
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 15
Credential                     :
DebugMode                      : {NONE}
DownloadManagerCustomData      :
DownloadManagerName            :
LCMCompatibleVersions          : {1.0, 2.0}
LCMState                       : Idle
LCMStateDetail                 :
LCMVersion                     : 2.0
StatusRetentionTimeInDays      : 10
SignatureValidationPolicy      : NONE
SignatureValidations           : {}
MaximumDownloadSizeMB          : 500
PartialConfigurations          :
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 30
RefreshMode                    : PUSH
ReportManagers                 : {}
ResourceModuleManagers         : {}
PSComputerName
```

<span data-ttu-id="c822b-113">此命令會取得本機電腦的 LCM 設定。</span><span class="sxs-lookup"><span data-stu-id="c822b-113">This command gets LCM settings for the local computer.</span></span>

<span data-ttu-id="c822b-114">如需有關輸出之個別屬性的詳細資訊，請參閱設定 [本機 Configuration Manager](../../docs-conceptual/dsc/managing-nodes/metaconfig.md#basic-settings) 檔。</span><span class="sxs-lookup"><span data-stu-id="c822b-114">For more information on the individual attributes of the output, see the [Configuring the Local Configuration Manager](../../docs-conceptual/dsc/managing-nodes/metaconfig.md#basic-settings) documentation.</span></span>

### <span data-ttu-id="c822b-115">範例2：取得指定電腦的 LCM 設定</span><span class="sxs-lookup"><span data-stu-id="c822b-115">Example 2: Get LCM settings for a specified computer</span></span>

```powershell
$Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
Get-DscLocalConfigurationManager -CimSession $Session
```

```Output
ActionAfterReboot              : ContinueConfiguration
AgentId                        : 169dfa57-a7f9-43be-a7a5-9dd06587e052
AllowModuleOverWrite           : False
CertificateID                  :
ConfigurationDownloadManagers  : {}
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 15
Credential                     :
DebugMode                      : {NONE}
DownloadManagerCustomData      :
DownloadManagerName            :
LCMCompatibleVersions          : {1.0, 2.0}
LCMState                       : Idle
LCMStateDetail                 :
LCMVersion                     : 2.0
StatusRetentionTimeInDays      : 10
SignatureValidationPolicy      : NONE
SignatureValidations           : {}
MaximumDownloadSizeMB          : 500
PartialConfigurations          :
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 30
RefreshMode                    : PUSH
ReportManagers                 : {}
ResourceModuleManagers         : {}
PSComputerName                 : Server01
PSComputerName                 : Server01
```

<span data-ttu-id="c822b-116">此範例會取得 CIM 會話所指定之電腦的 LCM 設定。</span><span class="sxs-lookup"><span data-stu-id="c822b-116">This example gets LCM settings for a computer specified by a CIM session.</span></span>
<span data-ttu-id="c822b-117">這個範例會針對名為 Server01 的電腦，建立一個搭配此 Cmdlet 使用的 CIM 工作階段。</span><span class="sxs-lookup"><span data-stu-id="c822b-117">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="c822b-118">或者，建立一個 CIM 工作階段的陣列，以便將該 Cmdlet 套用到多部指定的電腦。</span><span class="sxs-lookup"><span data-stu-id="c822b-118">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="c822b-119">第一個命令會使用 Cmdlet 建立 CIM 會話 `New-CimSession` ，然後將 **CimSession** 物件儲存在 $Session 變數中。</span><span class="sxs-lookup"><span data-stu-id="c822b-119">The first command creates a CIM session by using the `New-CimSession` cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span> <span data-ttu-id="c822b-120">此命令會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="c822b-120">The command prompts you for a password.</span></span> <span data-ttu-id="c822b-121">如需詳細資訊，請鍵入 `Get-Help New-CimSession`。</span><span class="sxs-lookup"><span data-stu-id="c822b-121">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="c822b-122">第二個命令會取得儲存在 $Session 變數中的 **CimSession** 物件所識別之電腦的本機 Configuration Manager 設定。</span><span class="sxs-lookup"><span data-stu-id="c822b-122">The second command gets Local Configuration Manager settings for the computers identified by the **CimSession** objects stored in the $Session variable.</span></span> <span data-ttu-id="c822b-123">在此案例中，名為 Server01 的電腦。</span><span class="sxs-lookup"><span data-stu-id="c822b-123">In this case, the computer named Server01.</span></span>

## <span data-ttu-id="c822b-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c822b-124">PARAMETERS</span></span>

### <span data-ttu-id="c822b-125">-AsJob</span><span class="sxs-lookup"><span data-stu-id="c822b-125">-AsJob</span></span>

<span data-ttu-id="c822b-126">指出此 Cmdlet 會以背景工作方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="c822b-126">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="c822b-127">-CimSession</span><span class="sxs-lookup"><span data-stu-id="c822b-127">-CimSession</span></span>

<span data-ttu-id="c822b-128">在遠端工作階段或遠端電腦上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c822b-128">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="c822b-129">輸入電腦名稱稱或會話物件，例如 `New-CimSession` 或 Cmdlet 的輸出 `Get-CimSession` 。</span><span class="sxs-lookup"><span data-stu-id="c822b-129">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span>

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

### <span data-ttu-id="c822b-130">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="c822b-130">-ThrottleLimit</span></span>

<span data-ttu-id="c822b-131">指定為執行 Cmdlet 可建立的最大並行作業數。</span><span class="sxs-lookup"><span data-stu-id="c822b-131">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>

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

### <span data-ttu-id="c822b-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c822b-132">CommonParameters</span></span>

<span data-ttu-id="c822b-133">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c822b-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c822b-134">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c822b-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c822b-135">輸入</span><span class="sxs-lookup"><span data-stu-id="c822b-135">INPUTS</span></span>

## <span data-ttu-id="c822b-136">輸出</span><span class="sxs-lookup"><span data-stu-id="c822b-136">OUTPUTS</span></span>

## <span data-ttu-id="c822b-137">注意</span><span class="sxs-lookup"><span data-stu-id="c822b-137">NOTES</span></span>

## <span data-ttu-id="c822b-138">相關連結</span><span class="sxs-lookup"><span data-stu-id="c822b-138">RELATED LINKS</span></span>

[<span data-ttu-id="c822b-139">Windows PowerShell Desired State Configuration 概觀</span><span class="sxs-lookup"><span data-stu-id="c822b-139">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="c822b-140">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c822b-140">Set-DscLocalConfigurationManager</span></span>](Set-DscLocalConfigurationManager.md)
