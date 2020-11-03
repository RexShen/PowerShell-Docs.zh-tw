---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/set-logproperties?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LogProperties
ms.openlocfilehash: ff51e4c30c2554ba58aa28862c44bb5fdbfd78d1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203047"
---
# <span data-ttu-id="a092e-102">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="a092e-102">Set-LogProperties</span></span>

## <span data-ttu-id="a092e-103">概要</span><span class="sxs-lookup"><span data-stu-id="a092e-103">SYNOPSIS</span></span>
<span data-ttu-id="a092e-104">變更 Windows 事件記錄檔的屬性。</span><span class="sxs-lookup"><span data-stu-id="a092e-104">Changes the properties of a Windows event log.</span></span>

## <span data-ttu-id="a092e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a092e-105">SYNTAX</span></span>

```
Set-LogProperties [-LogDetails] <LogDetails> [-Force] [<CommonParameters>]
```

## <span data-ttu-id="a092e-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a092e-106">DESCRIPTION</span></span>

<span data-ttu-id="a092e-107">此 Cmdlet 會變更 Windows 事件記錄檔的設定。</span><span class="sxs-lookup"><span data-stu-id="a092e-107">This cmdlet changes the configuration settings of a Windows event log.</span></span> <span data-ttu-id="a092e-108">和 Cmdlet 會使用這個 Cmdlet `Enable-PSTrace` `Disable-PSTrace` 。</span><span class="sxs-lookup"><span data-stu-id="a092e-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

<span data-ttu-id="a092e-109">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a092e-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="a092e-110">範例</span><span class="sxs-lookup"><span data-stu-id="a092e-110">EXAMPLES</span></span>

### <span data-ttu-id="a092e-111">範例1：變更 Windows PowerShell 事件記錄檔的保留設定</span><span class="sxs-lookup"><span data-stu-id="a092e-111">Example 1: Change the retention setting of the Windows PowerShell event log</span></span>

```powershell
$logDetails = Get-LogProperties 'Windows PowerShell'
$logDetails.Retention = $True
Set-LogProperties -LogDetails $logDetails
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : True
AutoBackup : False
MaxLogSize : 15728640
```

## <span data-ttu-id="a092e-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a092e-112">PARAMETERS</span></span>

### <span data-ttu-id="a092e-113">-Force</span><span class="sxs-lookup"><span data-stu-id="a092e-113">-Force</span></span>

<span data-ttu-id="a092e-114">用來在不提示的情況下強制變更。</span><span class="sxs-lookup"><span data-stu-id="a092e-114">Used to force the change without prompting.</span></span>

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

### <span data-ttu-id="a092e-115">-LogDetails</span><span class="sxs-lookup"><span data-stu-id="a092e-115">-LogDetails</span></span>

<span data-ttu-id="a092e-116">要指派給事件記錄檔的更新設定。</span><span class="sxs-lookup"><span data-stu-id="a092e-116">The updated configuration settings to be assigned to the event log.</span></span>

```yaml
Type: Microsoft.PowerShell.Diagnostics.LogDetails
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a092e-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a092e-117">CommonParameters</span></span>

<span data-ttu-id="a092e-118">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a092e-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a092e-119">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a092e-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a092e-120">輸入</span><span class="sxs-lookup"><span data-stu-id="a092e-120">INPUTS</span></span>

### <span data-ttu-id="a092e-121">LogDetails。</span><span class="sxs-lookup"><span data-stu-id="a092e-121">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="a092e-122">您必須將完整設定的 **LogDetails** 物件傳遞給 `Set-LogProperties` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a092e-122">You must pass a fully configured **LogDetails** object to the `Set-LogProperties` cmdlet.</span></span>
<span data-ttu-id="a092e-123">因此，若要變更一項設定，您應該使用 `Get-LogProperties` 來取出目前的設定。</span><span class="sxs-lookup"><span data-stu-id="a092e-123">Therefore, to change one setting, you should use `Get-LogProperties` to retrieve the current configuration.</span></span>

## <span data-ttu-id="a092e-124">輸出</span><span class="sxs-lookup"><span data-stu-id="a092e-124">OUTPUTS</span></span>

### <span data-ttu-id="a092e-125">System.Object</span><span class="sxs-lookup"><span data-stu-id="a092e-125">System.Object</span></span>

## <span data-ttu-id="a092e-126">注意</span><span class="sxs-lookup"><span data-stu-id="a092e-126">NOTES</span></span>

<span data-ttu-id="a092e-127">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a092e-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="a092e-128">相關連結</span><span class="sxs-lookup"><span data-stu-id="a092e-128">RELATED LINKS</span></span>

[<span data-ttu-id="a092e-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="a092e-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="a092e-130">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="a092e-130">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="a092e-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="a092e-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)
