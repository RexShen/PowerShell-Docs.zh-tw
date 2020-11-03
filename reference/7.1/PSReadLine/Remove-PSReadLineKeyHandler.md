---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/remove-psreadlinekeyhandler?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSReadLineKeyHandler
ms.openlocfilehash: a13677035581a081df51917bc6b82efec0ff2156
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208799"
---
# <span data-ttu-id="2ac23-103">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="2ac23-103">Remove-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="2ac23-104">概要</span><span class="sxs-lookup"><span data-stu-id="2ac23-104">SYNOPSIS</span></span>
<span data-ttu-id="2ac23-105">移除索引鍵系結。</span><span class="sxs-lookup"><span data-stu-id="2ac23-105">Removes a key binding.</span></span>

## <span data-ttu-id="2ac23-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2ac23-106">SYNTAX</span></span>

```
Remove-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

## <span data-ttu-id="2ac23-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2ac23-107">DESCRIPTION</span></span>

<span data-ttu-id="2ac23-108">`Remove-PSReadLineKeyHandler`Cmdlet 會移除指定的金鑰系結。</span><span class="sxs-lookup"><span data-stu-id="2ac23-108">The `Remove-PSReadLineKeyHandler` cmdlet removes a specified key binding.</span></span>

## <span data-ttu-id="2ac23-109">範例</span><span class="sxs-lookup"><span data-stu-id="2ac23-109">EXAMPLES</span></span>

### <span data-ttu-id="2ac23-110">範例1：移除系結</span><span class="sxs-lookup"><span data-stu-id="2ac23-110">Example 1: Remove a binding</span></span>

```powershell
Remove-PSReadLineKeyHandler -Chord Ctrl+B
```

<span data-ttu-id="2ac23-111">此命令會從按鍵組合（或弦）移除系結 `Ctrl+B` 。</span><span class="sxs-lookup"><span data-stu-id="2ac23-111">This command removes the binding from the key combination, or chord, `Ctrl+B`.</span></span> <span data-ttu-id="2ac23-112">在 `Ctrl+B` 本文中會建立弦 `Set-PSReadLineKeyHandler` 。</span><span class="sxs-lookup"><span data-stu-id="2ac23-112">The `Ctrl+B` chord is created in the `Set-PSReadLineKeyHandler` article.</span></span>

## <span data-ttu-id="2ac23-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2ac23-113">PARAMETERS</span></span>

### <span data-ttu-id="2ac23-114">-弦</span><span class="sxs-lookup"><span data-stu-id="2ac23-114">-Chord</span></span>

<span data-ttu-id="2ac23-115">指定要移除之索引鍵或索引鍵序列的陣列。</span><span class="sxs-lookup"><span data-stu-id="2ac23-115">Specifies an array of keys or sequences of keys to be removed.</span></span> <span data-ttu-id="2ac23-116">單一系結是使用單一字串來指定。</span><span class="sxs-lookup"><span data-stu-id="2ac23-116">A single binding is specified by using a single string.</span></span> <span data-ttu-id="2ac23-117">如果系結是索引鍵的序列，請以逗號分隔索引鍵，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2ac23-117">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+x,Ctrl+l`

<span data-ttu-id="2ac23-118">此參數接受字串陣列。</span><span class="sxs-lookup"><span data-stu-id="2ac23-118">This parameter accepts an array of strings.</span></span> <span data-ttu-id="2ac23-119">每個字串都是個別的系結，而不是單一系結的索引鍵序列。</span><span class="sxs-lookup"><span data-stu-id="2ac23-119">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2ac23-120">-ViMode</span><span class="sxs-lookup"><span data-stu-id="2ac23-120">-ViMode</span></span>

<span data-ttu-id="2ac23-121">指定要套用系結的 vi 模式。</span><span class="sxs-lookup"><span data-stu-id="2ac23-121">Specify which vi mode the binding applies to.</span></span> <span data-ttu-id="2ac23-122">可能的值為： Insert、Command。</span><span class="sxs-lookup"><span data-stu-id="2ac23-122">Possible values are: Insert, Command.</span></span>

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:
Accepted values: Insert, Command

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2ac23-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2ac23-123">CommonParameters</span></span>

<span data-ttu-id="2ac23-124">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2ac23-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2ac23-125">如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2ac23-125">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2ac23-126">輸入</span><span class="sxs-lookup"><span data-stu-id="2ac23-126">INPUTS</span></span>

### <span data-ttu-id="2ac23-127">無</span><span class="sxs-lookup"><span data-stu-id="2ac23-127">None</span></span>

<span data-ttu-id="2ac23-128">您無法使用管線將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2ac23-128">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="2ac23-129">輸出</span><span class="sxs-lookup"><span data-stu-id="2ac23-129">OUTPUTS</span></span>

### <span data-ttu-id="2ac23-130">無</span><span class="sxs-lookup"><span data-stu-id="2ac23-130">None</span></span>

## <span data-ttu-id="2ac23-131">注意</span><span class="sxs-lookup"><span data-stu-id="2ac23-131">NOTES</span></span>

## <span data-ttu-id="2ac23-132">相關連結</span><span class="sxs-lookup"><span data-stu-id="2ac23-132">RELATED LINKS</span></span>

[<span data-ttu-id="2ac23-133">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="2ac23-133">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="2ac23-134">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="2ac23-134">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="2ac23-135">設定-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="2ac23-135">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="2ac23-136">設定-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="2ac23-136">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)

