---
ms.date: 09/13/2016
ms.topic: reference
title: 輸入篩選參數
description: 輸入篩選參數
ms.openlocfilehash: 419ffea2afb4aa534a3e19ecdfce6d6af1da46a6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648541"
---
# <a name="input-filter-parameters"></a>輸入篩選參數

Cmdlet 可以定義 `Filter` 、 `Include` 和參數， `Exclude` 以篩選 Cmdlet 所影響的輸入物件集合。

通常，輸入物件的集合是由 `InputObject` 、 `Path` 或參數所指定 `Name` 。 例如，Cmdlet 可以有 `Path` 使用萬用字元接受多個路徑的參數，而且每個路徑都指向輸入物件。 搭配使用時， `Filter` 、 `Include` 和 `Exclude` 參數可進一步限定 Cmdlet 在每次叫用時所能運作的路徑。

## <a name="include-and-exclude-parameters"></a>包含和排除參數

`Include`和 `Exclude` 參數會識別傳遞給 Cmdlet 的輸入物件集合中包含或排除的物件。 當篩選可以用標準萬用字元語言表示時，請使用這些參數。  (如需萬用字元的詳細資訊，請參閱 [在 Cmdlet 參數中支援萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)。 ) `Include` 參數包含名稱符合包含篩選準則的所有物件。 `Exclude`參數會排除名稱符合篩選準則的所有物件。

## <a name="filter-parameter"></a>篩選參數

`Filter`參數指定的篩選準則未以標準萬用字元語言表示。 例如， (ADSI) 或 SQL 篩選器 Active Directory 服務介面，可能會透過其參數傳遞至 Cmdlet `Filter` 。 在 Windows PowerShell 所提供的 Cmdlet 中，這些篩選是由使用指令程式來存取資料存放區的 Windows PowerShell 提供者所指定。 每個提供者通常會定義自己的篩選準則。

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>篩選是否未指定輸入物件集合

如果未指定任何輸入物件集，這通常表示要針對所有物件進行篩選。 如需詳細資訊，請參閱[Get 流程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
