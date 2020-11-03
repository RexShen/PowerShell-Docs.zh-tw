---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-list?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-List
ms.openlocfilehash: eccee5ad302395116430006ed4dc0395946696b6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203099"
---
# <span data-ttu-id="a6f8f-103">Update-List</span><span class="sxs-lookup"><span data-stu-id="a6f8f-103">Update-List</span></span>

## <span data-ttu-id="a6f8f-104">概要</span><span class="sxs-lookup"><span data-stu-id="a6f8f-104">SYNOPSIS</span></span>
<span data-ttu-id="a6f8f-105">在包含物件集合的屬性值中新增和移除項目。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-105">Adds items to and removes items from a property value that contains a collection of objects.</span></span>

## <span data-ttu-id="a6f8f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a6f8f-106">SYNTAX</span></span>

### <span data-ttu-id="a6f8f-107">AddRemoveSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="a6f8f-107">AddRemoveSet (Default)</span></span>

```
Update-List [-Add <Object[]>] [-Remove <Object[]>] [-InputObject <PSObject>] [[-Property] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="a6f8f-108">ReplaceSet</span><span class="sxs-lookup"><span data-stu-id="a6f8f-108">ReplaceSet</span></span>

```
Update-List -Replace <Object[]> [-InputObject <PSObject>] [[-Property] <String>] [<CommonParameters>]
```

## <span data-ttu-id="a6f8f-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a6f8f-109">DESCRIPTION</span></span>

<span data-ttu-id="a6f8f-110">指令 `Update-List` 程式會新增、移除或取代物件的屬性值中的專案，並傳回更新的物件。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-110">The `Update-List` cmdlet adds, removes, or replaces items in a property value of an object and returns the updated object.</span></span> <span data-ttu-id="a6f8f-111">此 Cmdlet 是專為包含物件集合的屬性所設計。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-111">This cmdlet is designed for properties that contain collections of objects.</span></span>

<span data-ttu-id="a6f8f-112">**Add** 和 **remove** 參數會在集合中加入個別的專案，並將其從集合中移除。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-112">The **Add** and **Remove** parameters add individual items to and remove them from the collection.</span></span>
<span data-ttu-id="a6f8f-113">**Replace** 參數會取代整個集合。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-113">The **Replace** parameter replaces the entire collection.</span></span>

<span data-ttu-id="a6f8f-114">如果您未在命令中指定屬性，則會傳回 `Update-List` 描述更新的物件，而非更新物件。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-114">If you do not specify a property in the command, `Update-List` returns an object that describes the update instead of updating the object.</span></span> <span data-ttu-id="a6f8f-115">您可以將更新物件提交至會變更物件的 Cmdlet，例如 `Set` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-115">You can submit the update object to cmdlets that change objects, such as `Set` cmdlets.</span></span>

<span data-ttu-id="a6f8f-116">只有當正在更新的屬性支援使用的 **IList** 介面時，此 Cmdlet 才會運作 `Update-List` 。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-116">This cmdlet works only when the property that is being updated supports the **IList** interface that `Update-List` uses.</span></span> <span data-ttu-id="a6f8f-117">此外， `Set` 接受更新的任何 Cmdlet 都必須支援 **IList** 介面。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-117">Also, any `Set` cmdlets that accept an update must support the **IList** interface.</span></span>

<span data-ttu-id="a6f8f-118">隨 PowerShell 安裝的核心 Cmdlet 不支援此介面。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-118">The core cmdlets that are installed with PowerShell do not support this interface.</span></span> <span data-ttu-id="a6f8f-119">若要判斷 Cmdlet 是否支援 `Update-List` ，請參閱 Cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-119">To determine whether a cmdlet supports `Update-List`, see the cmdlet Help topic.</span></span>

## <span data-ttu-id="a6f8f-120">範例</span><span class="sxs-lookup"><span data-stu-id="a6f8f-120">EXAMPLES</span></span>

### <span data-ttu-id="a6f8f-121">範例1：將專案加入至屬性值</span><span class="sxs-lookup"><span data-stu-id="a6f8f-121">Example 1: Add items to a property value</span></span>

<span data-ttu-id="a6f8f-122">在此範例中，我們會建立一個類別來代表一組卡片，其中卡片會儲存為 **清單** 集合物件。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-122">In this example we create a class that represents a deck of cards where the cards are stored as a **List** collection object.</span></span> <span data-ttu-id="a6f8f-123">**NewDeck ( # B1** 方法會使用將 `Update-List` 一組完整的卡片值新增至 **卡片** 集合。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-123">The **NewDeck()** method uses `Update-List`to add a complete deck of card values to the **cards** collection.</span></span>

```powershell
class Cards {

    [System.Collections.Generic.List[string]]$cards
    [string]$name

    Cards([string]$_name) {
        $this.name = $_name
        $this.cards = [System.Collections.Generic.List[string]]::new()
    }

    NewDeck() {
        $_suits = [char]0x2663,[char]0x2666,[char]0x2665,[char]0x2660
        $_values = 'A',2,3,4,5,6,7,8,9,10,'J','Q','K'
        $_deck = foreach ($s in $_suits){ foreach ($v in $_values){ "$v$s"} }
        $this | Update-List -Property cards -Add $_deck | Out-Null
    }

    Show() {
        Write-Host
        Write-Host $this.name ": " $this.cards[0..12]
        if ($this.cards.count -gt 13) {
            Write-Host (' ' * ($this.name.length+3)) $this.cards[13..25]
        }
        if ($this.cards.count -gt 26) {
            Write-Host (' ' * ($this.name.length+3)) $this.cards[26..38]
        }
        if ($this.cards.count -gt 39) {
            Write-Host (' ' * ($this.name.length+3)) $this.cards[39..51]
        }
    }

    Shuffle() { $this.cards = Get-Random -InputObject $this.cards -Count 52 }

    Sort() { $this.cards.Sort() }
}
```

> [!NOTE]
> <span data-ttu-id="a6f8f-124">Cmdlet 會將 `Update-List` 更新的物件輸出到管線。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-124">The `Update-List` cmdlet outputs the updated object to the pipeline.</span></span> <span data-ttu-id="a6f8f-125">我們會將輸出輸送至以 `Out-Null` 抑制不必要的顯示。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-125">We pipe the output to `Out-Null` to suppress the unwanted display.</span></span>

### <span data-ttu-id="a6f8f-126">範例2：新增和移除集合屬性的專案</span><span class="sxs-lookup"><span data-stu-id="a6f8f-126">Example 2: Add and remove items of a collection property</span></span>

<span data-ttu-id="a6f8f-127">繼續進行範例1中的程式碼，我們將建立 **卡片** 類別的實例，以代表卡片和兩個玩家所持有的卡片。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-127">Continuing with the code in Example 1, we will create instances of the **Cards** class to represent a deck of cards and the cards held by two players.</span></span> <span data-ttu-id="a6f8f-128">我們使用 `Update-List` Cmdlet 將卡片新增至玩家手中，並移除牌組中的牌。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-128">We use the `Update-List` cmdlet to add cards to the players' hands and to remove cards from the deck.</span></span>

```powershell
$player1 = [Cards]::new('Player 1')
$player2 = [Cards]::new('Player 2')

$deck = [Cards]::new('Deck')
$deck.NewDeck()
$deck.Shuffle()
$deck.Show()

# Deal two hands
$player1 | Update-List -Property cards -Add $deck.cards[0,2,4,6,8] | Out-Null
$player2 | Update-List -Property cards -Add $deck.cards[1,3,5,7,9] | Out-Null
$deck | Update-List -Property cards -Remove $player1.cards | Out-Null
$deck | Update-List -Property cards -Remove $player2.cards | Out-Null

$player1.Show()
$player2.Show()
$deck.Show()
```

```Output
Deck :  4♦ 7♥ J♦ 5♣ A♣ 8♦ J♣ Q♥ 6♦ 3♦ 9♦ 6♣ 2♣
        K♥ 4♠ 10♥ 8♠ 10♦ 9♠ 6♠ K♦ 7♣ 3♣ Q♣ A♥ Q♠
        3♥ 5♥ 2♦ 5♠ J♥ J♠ 10♣ 4♥ Q♦ 10♠ 4♣ 2♠ 2♥
        6♥ 7♦ A♠ 5♦ 8♣ 9♥ K♠ 7♠ 3♠ 9♣ A♦ K♣ 8♥

Player 1 :  4♦ J♦ A♣ J♣ 6♦

Player 2 :  7♥ 5♣ 8♦ Q♥ 3♦

Deck :  9♦ 6♣ 2♣ K♥ 4♠ 10♥ 8♠ 10♦ 9♠ 6♠ K♦ 7♣ 3♣
        Q♣ A♥ Q♠ 3♥ 5♥ 2♦ 5♠ J♥ J♠ 10♣ 4♥ Q♦ 10♠
        4♣ 2♠ 2♥ 6♥ 7♦ A♠ 5♦ 8♣ 9♥ K♠ 7♠ 3♠ 9♣
        A♦ K♣ 8♥
```

<span data-ttu-id="a6f8f-129">輸出會在卡片被發給玩家之前，顯示牌組的狀態。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-129">The output shows the state of the deck before the cards were dealt to the players.</span></span> <span data-ttu-id="a6f8f-130">您可以看到每個玩家都收到牌組的五張牌。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-130">You can see that each player received five cards from the deck.</span></span> <span data-ttu-id="a6f8f-131">最後的輸出會顯示在將卡片處理給玩家之後，該牌組的狀態。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-131">The final output shows the state of the deck after dealing the cards to the players.</span></span> <span data-ttu-id="a6f8f-132">`Update-List` 用來從牌組中選取卡片，然後將它們新增至玩家的集合中。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-132">`Update-List` was used to select the cards from the deck and add them to the players' collection.</span></span> <span data-ttu-id="a6f8f-133">然後，會使用將玩家的卡片從牌組中移除 `Update-List` 。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-133">Then the players' cards were removed from the deck using `Update-List`.</span></span>

### <span data-ttu-id="a6f8f-134">範例3：在單一命令中加入和移除專案</span><span class="sxs-lookup"><span data-stu-id="a6f8f-134">Example 3: Add and remove items in a single command</span></span>

<span data-ttu-id="a6f8f-135">`Update-List` 可讓您在單一命令中使用 [ **新增** ] 和 [ **移除** ] 參數。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-135">`Update-List` allows you to use the **Add** and **Remove** parameters in a single command.</span></span> <span data-ttu-id="a6f8f-136">在此範例中，Player 1 想要捨棄 `4♦` 和 `6♦` 取得兩個新的卡片。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-136">In this example, Player 1 wants to discard the `4♦` and `6♦` and get two new cards.</span></span>

```powershell
# Player 1 wants two new cards - remove 2 cards & add 2 cards
$player1 | Update-List -Property cards -Remove $player1.cards[0,4] -Add $deck.cards[0..1] | Out-Null
$player1.Show()

# remove dealt cards from deck
$deck | Update-List -Property cards -Remove $deck.cards[0..1] | Out-Null
$deck.Show()
```

```Output
Player 1 :  J♦ A♣ J♣ 9♦ 6♣

Deck :  2♣ K♥ 4♠ 10♥ 8♠ 10♦ 9♠ 6♠ K♦ 7♣ 3♣ Q♣ A♥
        Q♠ 3♥ 5♥ 2♦ 5♠ J♥ J♠ 10♣ 4♥ Q♦ 10♠ 4♣ 2♠
        2♥ 6♥ 7♦ A♠ 5♦ 8♣ 9♥ K♠ 7♠ 3♠ 9♣ A♦ K♣
        8♥
```

## <span data-ttu-id="a6f8f-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a6f8f-137">PARAMETERS</span></span>

### <span data-ttu-id="a6f8f-138">-Add</span><span class="sxs-lookup"><span data-stu-id="a6f8f-138">-Add</span></span>

<span data-ttu-id="a6f8f-139">指定要新增至集合的屬性值。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-139">Specifies the property values to be added to the collection.</span></span> <span data-ttu-id="a6f8f-140">以值應顯示在集合中的順序輸入值。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-140">Enter the values in the order that they should appear in the collection.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: AddRemoveSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a6f8f-141">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a6f8f-141">-InputObject</span></span>

<span data-ttu-id="a6f8f-142">指定要更新的物件。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-142">Specifies the objects to be updated.</span></span> <span data-ttu-id="a6f8f-143">您也可以透過管線傳送要更新的物件 `Update-List` 。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-143">You can also pipe the object to be updated to `Update-List`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a6f8f-144">-Property</span><span class="sxs-lookup"><span data-stu-id="a6f8f-144">-Property</span></span>

<span data-ttu-id="a6f8f-145">指定包含要更新之集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-145">Specifies the property that contains the collection that is being updated.</span></span> <span data-ttu-id="a6f8f-146">如果您省略這個參數，則會傳回 `Update-List` 代表變更的物件，而不是變更物件。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-146">If you omit this parameter, `Update-List` returns an object that represents the change instead of changing the object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a6f8f-147">-Remove</span><span class="sxs-lookup"><span data-stu-id="a6f8f-147">-Remove</span></span>

<span data-ttu-id="a6f8f-148">指定要從集合中移除的屬性值。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-148">Specifies the property values to be removed from the collection.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: AddRemoveSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a6f8f-149">-Replace</span><span class="sxs-lookup"><span data-stu-id="a6f8f-149">-Replace</span></span>

<span data-ttu-id="a6f8f-150">指定新的集合。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-150">Specifies a new collection.</span></span> <span data-ttu-id="a6f8f-151">此參數會按其指定的項目來取代原始集合中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-151">This parameter replaces all items in the original collection with the items specified by this parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: ReplaceSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a6f8f-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a6f8f-152">CommonParameters</span></span>

<span data-ttu-id="a6f8f-153">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a6f8f-154">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a6f8f-155">輸入</span><span class="sxs-lookup"><span data-stu-id="a6f8f-155">INPUTS</span></span>

### <span data-ttu-id="a6f8f-156">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="a6f8f-156">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="a6f8f-157">您可以透過管線傳送要更新的物件 `Update-List` 。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-157">You can pipe the objects to be updated to `Update-List`.</span></span>

## <span data-ttu-id="a6f8f-158">輸出</span><span class="sxs-lookup"><span data-stu-id="a6f8f-158">OUTPUTS</span></span>

### <span data-ttu-id="a6f8f-159">物件或 System.Management.Automation.PSListModifier</span><span class="sxs-lookup"><span data-stu-id="a6f8f-159">Objects or System.Management.Automation.PSListModifier</span></span>

<span data-ttu-id="a6f8f-160">`Update-List` 傳回更新的物件，或傳回代表更新動作的物件。</span><span class="sxs-lookup"><span data-stu-id="a6f8f-160">`Update-List` returns the updated object, or it returns an object that represents the update action.</span></span>

## <span data-ttu-id="a6f8f-161">注意</span><span class="sxs-lookup"><span data-stu-id="a6f8f-161">NOTES</span></span>

## <span data-ttu-id="a6f8f-162">相關連結</span><span class="sxs-lookup"><span data-stu-id="a6f8f-162">RELATED LINKS</span></span>

[<span data-ttu-id="a6f8f-163">Format-List</span><span class="sxs-lookup"><span data-stu-id="a6f8f-163">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="a6f8f-164">Select-Object</span><span class="sxs-lookup"><span data-stu-id="a6f8f-164">Select-Object</span></span>](Select-Object.md)
