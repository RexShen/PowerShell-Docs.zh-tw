---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-list?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-List
ms.openlocfilehash: 00ada05f52967c0857cfad63a94cd23c49b69367
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201535"
---
# Update-List

## 概要
在包含物件集合的屬性值中新增和移除項目。

## SYNTAX

### AddRemoveSet (預設值)

```
Update-List [-Add <Object[]>] [-Remove <Object[]>] [-InputObject <PSObject>] [[-Property] <String>]
 [<CommonParameters>]
```

### ReplaceSet

```
Update-List -Replace <Object[]> [-InputObject <PSObject>] [[-Property] <String>] [<CommonParameters>]
```

## DESCRIPTION

指令 `Update-List` 程式會新增、移除或取代物件的屬性值中的專案，並傳回更新的物件。 此 Cmdlet 是專為包含物件集合的屬性所設計。

**Add** 和 **remove** 參數會在集合中加入個別的專案，並將其從集合中移除。
**Replace** 參數會取代整個集合。

如果您未在命令中指定屬性，則會傳回 `Update-List` 描述更新的物件，而非更新物件。 您可以將更新物件提交至會變更物件的 Cmdlet，例如 `Set` Cmdlet。

只有當正在更新的屬性支援使用的 **IList** 介面時，此 Cmdlet 才會運作 `Update-List` 。 此外， `Set` 接受更新的任何 Cmdlet 都必須支援 **IList** 介面。

隨 PowerShell 安裝的核心 Cmdlet 不支援此介面。 若要判斷 Cmdlet 是否支援 `Update-List` ，請參閱 Cmdlet 說明主題。

PowerShell 7 中已重新引入此 Cmdlet。

## 範例

### 範例1：將專案加入至屬性值

在此範例中，我們會建立一個類別來代表一組卡片，其中卡片會儲存為 **清單** 集合物件。 **NewDeck ( # B1** 方法會使用將 `Update-List` 一組完整的卡片值新增至 **卡片** 集合。

```powershell
class Cards {

    [System.Collections.Generic.List[string]]$cards
    [string]$name

    Cards([string]$_name) {
        $this.name = $_name
        $this.cards = [System.Collections.Generic.List[string]]::new()
    }

    NewDeck() {
        $_suits = "`u{2663}","`u{2666}","`u{2665}","`u{2660}"
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
> Cmdlet 會將 `Update-List` 更新的物件輸出到管線。 我們會將輸出輸送至以 `Out-Null` 抑制不必要的顯示。

### 範例2：新增和移除集合屬性的專案

繼續進行範例1中的程式碼，我們將建立 **卡片** 類別的實例，以代表卡片和兩個玩家所持有的卡片。 我們使用 `Update-List` Cmdlet 將卡片新增至玩家手中，並移除牌組中的牌。

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

輸出會在卡片被發給玩家之前，顯示牌組的狀態。 您可以看到每個玩家都收到牌組的五張牌。 最後的輸出會顯示在將卡片處理給玩家之後，該牌組的狀態。 `Update-List` 用來從牌組中選取卡片，然後將它們新增至玩家的集合中。 然後，會使用將玩家的卡片從牌組中移除 `Update-List` 。

### 範例3：在單一命令中加入和移除專案

`Update-List` 可讓您在單一命令中使用 [ **新增** ] 和 [ **移除** ] 參數。 在此範例中，Player 1 想要捨棄 `4♦` 和 `6♦` 取得兩個新的卡片。

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

## PARAMETERS

### -Add

指定要新增至集合的屬性值。 以值應顯示在集合中的順序輸入值。

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

### -InputObject

指定要更新的物件。 您也可以透過管線傳送要更新的物件 `Update-List` 。

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

### -Property

指定包含要更新之集合的屬性。 如果您省略這個參數，則會傳回 `Update-List` 代表變更的物件，而不是變更物件。

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

### -Remove

指定要從集合中移除的屬性值。

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

### -Replace

指定新的集合。 此參數會按其指定的項目來取代原始集合中的所有項目。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以透過管線傳送要更新的物件 `Update-List` 。

## 輸出

### 物件或 System.Management.Automation.PSListModifier

`Update-List` 傳回更新的物件，或傳回代表更新動作的物件。

## 注意

## 相關連結

[Format-List](Format-List.md)

[Select-Object](Select-Object.md)
