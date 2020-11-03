---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/get-logproperties?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LogProperties
ms.openlocfilehash: 0f675c2b0bf2b7e5ebfe3a1677f5bc194e8fe844
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203052"
---
# <span data-ttu-id="6b6b0-102">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="6b6b0-102">Get-LogProperties</span></span>

## <span data-ttu-id="6b6b0-103">概要</span><span class="sxs-lookup"><span data-stu-id="6b6b0-103">SYNOPSIS</span></span>
<span data-ttu-id="6b6b0-104">抓取 Windows 事件記錄檔的屬性。</span><span class="sxs-lookup"><span data-stu-id="6b6b0-104">Retrieves the properties of a Windows event log.</span></span>

## <span data-ttu-id="6b6b0-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6b6b0-105">SYNTAX</span></span>

```
Get-LogProperties [-Name] <string> [<CommonParameters>]
```

## <span data-ttu-id="6b6b0-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6b6b0-106">DESCRIPTION</span></span>

<span data-ttu-id="6b6b0-107">此 Cmdlet 會取得 Windows 事件記錄檔的設定。</span><span class="sxs-lookup"><span data-stu-id="6b6b0-107">This cmdlet gets the configuration settings of a Windows event log.</span></span> <span data-ttu-id="6b6b0-108">和 Cmdlet 會使用這個 Cmdlet `Enable-PSTrace` `Disable-PSTrace` 。</span><span class="sxs-lookup"><span data-stu-id="6b6b0-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

## <span data-ttu-id="6b6b0-109">範例</span><span class="sxs-lookup"><span data-stu-id="6b6b0-109">EXAMPLES</span></span>

### <span data-ttu-id="6b6b0-110">範例1：取得 Windows PowerShell 事件記錄檔的設定</span><span class="sxs-lookup"><span data-stu-id="6b6b0-110">Example 1: Get the configuration settings of the Windows PowerShell event log</span></span>

```powershell
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : False
AutoBackup : False
MaxLogSize : 15728640
```

## <span data-ttu-id="6b6b0-111">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6b6b0-111">PARAMETERS</span></span>

### <span data-ttu-id="6b6b0-112">-Name</span><span class="sxs-lookup"><span data-stu-id="6b6b0-112">-Name</span></span>

<span data-ttu-id="6b6b0-113">事件提供者的名稱。</span><span class="sxs-lookup"><span data-stu-id="6b6b0-113">The name of the event provider.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6b6b0-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6b6b0-114">CommonParameters</span></span>

<span data-ttu-id="6b6b0-115">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6b6b0-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6b6b0-116">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6b6b0-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6b6b0-117">輸入</span><span class="sxs-lookup"><span data-stu-id="6b6b0-117">INPUTS</span></span>

### <span data-ttu-id="6b6b0-118">System.Object</span><span class="sxs-lookup"><span data-stu-id="6b6b0-118">System.Object</span></span>

## <span data-ttu-id="6b6b0-119">輸出</span><span class="sxs-lookup"><span data-stu-id="6b6b0-119">OUTPUTS</span></span>

### <span data-ttu-id="6b6b0-120">LogDetails。</span><span class="sxs-lookup"><span data-stu-id="6b6b0-120">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="6b6b0-121">**PSDiagnostics** 模組會將 **LogDetails** 類別新增至 `Microsoft.PowerShell.Diagnostics` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="6b6b0-121">The **PSDiagnostics** module adds the **LogDetails** class to the `Microsoft.PowerShell.Diagnostics` namespace.</span></span>

## <span data-ttu-id="6b6b0-122">注意</span><span class="sxs-lookup"><span data-stu-id="6b6b0-122">NOTES</span></span>

## <span data-ttu-id="6b6b0-123">相關連結</span><span class="sxs-lookup"><span data-stu-id="6b6b0-123">RELATED LINKS</span></span>

[<span data-ttu-id="6b6b0-124">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="6b6b0-124">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="6b6b0-125">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="6b6b0-125">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="6b6b0-126">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="6b6b0-126">Disable-PSTrace</span></span>](Disable-PSTrace.md)
