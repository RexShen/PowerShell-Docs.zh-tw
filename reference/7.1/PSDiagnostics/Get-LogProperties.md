---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
Locale: en-US
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/get-logproperties?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LogProperties
ms.openlocfilehash: 5b95fe3bc643c9e12a3d216523c086d9b0cdf901
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202139"
---
# <span data-ttu-id="a7ca1-102">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="a7ca1-102">Get-LogProperties</span></span>

## <span data-ttu-id="a7ca1-103">概要</span><span class="sxs-lookup"><span data-stu-id="a7ca1-103">SYNOPSIS</span></span>
<span data-ttu-id="a7ca1-104">抓取 Windows 事件記錄檔的屬性。</span><span class="sxs-lookup"><span data-stu-id="a7ca1-104">Retrieves the properties of a Windows event log.</span></span>

## <span data-ttu-id="a7ca1-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a7ca1-105">SYNTAX</span></span>

```
Get-LogProperties [-Name] <Object> [<CommonParameters>]
```

## <span data-ttu-id="a7ca1-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a7ca1-106">DESCRIPTION</span></span>

<span data-ttu-id="a7ca1-107">此 Cmdlet 會取得 Windows 事件記錄檔的設定。</span><span class="sxs-lookup"><span data-stu-id="a7ca1-107">This cmdlet gets the configuration settings of a Windows event log.</span></span> <span data-ttu-id="a7ca1-108">和 Cmdlet 會使用這個 Cmdlet `Enable-PSTrace` `Disable-PSTrace` 。</span><span class="sxs-lookup"><span data-stu-id="a7ca1-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

## <span data-ttu-id="a7ca1-109">範例</span><span class="sxs-lookup"><span data-stu-id="a7ca1-109">EXAMPLES</span></span>

### <span data-ttu-id="a7ca1-110">範例1：取得 Windows PowerShell 事件記錄檔的設定</span><span class="sxs-lookup"><span data-stu-id="a7ca1-110">Example 1: Get the configuration settings of the Windows PowerShell event log</span></span>

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

## <span data-ttu-id="a7ca1-111">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a7ca1-111">PARAMETERS</span></span>

### <span data-ttu-id="a7ca1-112">-Name</span><span class="sxs-lookup"><span data-stu-id="a7ca1-112">-Name</span></span>

<span data-ttu-id="a7ca1-113">事件提供者的名稱。</span><span class="sxs-lookup"><span data-stu-id="a7ca1-113">The name of the event provider.</span></span>

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

### <span data-ttu-id="a7ca1-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a7ca1-114">CommonParameters</span></span>

<span data-ttu-id="a7ca1-115">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a7ca1-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a7ca1-116">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a7ca1-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a7ca1-117">輸入</span><span class="sxs-lookup"><span data-stu-id="a7ca1-117">INPUTS</span></span>

### <span data-ttu-id="a7ca1-118">System.String</span><span class="sxs-lookup"><span data-stu-id="a7ca1-118">System.String</span></span>

## <span data-ttu-id="a7ca1-119">輸出</span><span class="sxs-lookup"><span data-stu-id="a7ca1-119">OUTPUTS</span></span>

### <span data-ttu-id="a7ca1-120">LogDetails。</span><span class="sxs-lookup"><span data-stu-id="a7ca1-120">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="a7ca1-121">**PSDiagnostics** 模組會將 **LogDetails** 類別新增至 `Microsoft.PowerShell.Diagnostics` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="a7ca1-121">The **PSDiagnostics** module adds the **LogDetails** class to the `Microsoft.PowerShell.Diagnostics` namespace.</span></span>

## <span data-ttu-id="a7ca1-122">注意</span><span class="sxs-lookup"><span data-stu-id="a7ca1-122">NOTES</span></span>

## <span data-ttu-id="a7ca1-123">相關連結</span><span class="sxs-lookup"><span data-stu-id="a7ca1-123">RELATED LINKS</span></span>

[<span data-ttu-id="a7ca1-124">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="a7ca1-124">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="a7ca1-125">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="a7ca1-125">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="a7ca1-126">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="a7ca1-126">Disable-PSTrace</span></span>](Disable-PSTrace.md)

