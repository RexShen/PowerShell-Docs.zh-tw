---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
Locale: en-US
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/get-logproperties?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LogProperties
ms.openlocfilehash: 08638749b7a5bb57bee804fccf9de17f50fd6736
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201639"
---
# <span data-ttu-id="3605e-102">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="3605e-102">Get-LogProperties</span></span>

## <span data-ttu-id="3605e-103">概要</span><span class="sxs-lookup"><span data-stu-id="3605e-103">SYNOPSIS</span></span>
<span data-ttu-id="3605e-104">抓取 Windows 事件記錄檔的屬性。</span><span class="sxs-lookup"><span data-stu-id="3605e-104">Retrieves the properties of a Windows event log.</span></span>

## <span data-ttu-id="3605e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3605e-105">SYNTAX</span></span>

```
Get-LogProperties [-Name] <Object> [<CommonParameters>]
```

## <span data-ttu-id="3605e-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3605e-106">DESCRIPTION</span></span>

<span data-ttu-id="3605e-107">此 Cmdlet 會取得 Windows 事件記錄檔的設定。</span><span class="sxs-lookup"><span data-stu-id="3605e-107">This cmdlet gets the configuration settings of a Windows event log.</span></span> <span data-ttu-id="3605e-108">和 Cmdlet 會使用這個 Cmdlet `Enable-PSTrace` `Disable-PSTrace` 。</span><span class="sxs-lookup"><span data-stu-id="3605e-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

## <span data-ttu-id="3605e-109">範例</span><span class="sxs-lookup"><span data-stu-id="3605e-109">EXAMPLES</span></span>

### <span data-ttu-id="3605e-110">範例1：取得 Windows PowerShell 事件記錄檔的設定</span><span class="sxs-lookup"><span data-stu-id="3605e-110">Example 1: Get the configuration settings of the Windows PowerShell event log</span></span>

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

## <span data-ttu-id="3605e-111">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3605e-111">PARAMETERS</span></span>

### <span data-ttu-id="3605e-112">-Name</span><span class="sxs-lookup"><span data-stu-id="3605e-112">-Name</span></span>

<span data-ttu-id="3605e-113">事件提供者的名稱。</span><span class="sxs-lookup"><span data-stu-id="3605e-113">The name of the event provider.</span></span>

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

### <span data-ttu-id="3605e-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3605e-114">CommonParameters</span></span>

<span data-ttu-id="3605e-115">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3605e-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3605e-116">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3605e-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3605e-117">輸入</span><span class="sxs-lookup"><span data-stu-id="3605e-117">INPUTS</span></span>

### <span data-ttu-id="3605e-118">System.String</span><span class="sxs-lookup"><span data-stu-id="3605e-118">System.String</span></span>

## <span data-ttu-id="3605e-119">輸出</span><span class="sxs-lookup"><span data-stu-id="3605e-119">OUTPUTS</span></span>

### <span data-ttu-id="3605e-120">LogDetails。</span><span class="sxs-lookup"><span data-stu-id="3605e-120">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="3605e-121">**PSDiagnostics** 模組會將 **LogDetails** 類別新增至 `Microsoft.PowerShell.Diagnostics` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="3605e-121">The **PSDiagnostics** module adds the **LogDetails** class to the `Microsoft.PowerShell.Diagnostics` namespace.</span></span>

## <span data-ttu-id="3605e-122">注意</span><span class="sxs-lookup"><span data-stu-id="3605e-122">NOTES</span></span>

## <span data-ttu-id="3605e-123">相關連結</span><span class="sxs-lookup"><span data-stu-id="3605e-123">RELATED LINKS</span></span>

[<span data-ttu-id="3605e-124">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="3605e-124">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="3605e-125">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="3605e-125">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="3605e-126">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="3605e-126">Disable-PSTrace</span></span>](Disable-PSTrace.md)
