---
title: 輸入篩選參數 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ccaf6c4859d2a4f14866ec1252b999e90e1a830f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784039"
---
# <a name="input-filter-parameters"></a>輸入篩選參數

Cmdlet 可以定義 `Filter` 、 `Include` 和參數， `Exclude` 以篩選 Cmdlet 所影響的一組輸入物件。

一般來說，輸入物件的集合是由 `InputObject` 、 `Path` 或 `Name` 參數指定。 例如，Cmdlet 可以具有 `Path` 接受多個路徑的參數，方法是使用萬用字元，而每個路徑都會指向輸入物件。 一起使用時， `Filter` 、 `Include` 和 `Exclude` 參數會進一步限定 Cmdlet 在每次叫用時所能運作的路徑。

## <a name="include-and-exclude-parameters"></a>包含和排除參數

`Include`和 `Exclude` 參數會識別傳遞給 Cmdlet 的一組輸入物件所包含或排除的物件。 當篩選準則可以用標準萬用字元語言表示時，請使用這些參數。  (需萬用字元的詳細資訊，請參閱[在 Cmdlet 參數中支援萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)。 ) `Include` 參數包含名稱符合包含篩選準則的所有物件。 `Exclude`參數會排除其名稱符合篩選準則的所有物件。

## <a name="filter-parameter"></a>篩選參數

`Filter`參數指定的篩選準則不是以標準萬用字元語言表示。 例如，Active Directory 服務介面 (ADSI) 或 SQL 篩選器可能會透過其參數傳遞至 Cmdlet `Filter` 。 在 Windows PowerShell 所提供的 Cmdlet 中，這些篩選器是由使用 Cmdlet 來存取資料存放區的 Windows PowerShell 提供者所指定。 每個提供者通常會定義它自己的篩選準則。

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>篩選是否未指定輸入物件集合

如果未指定任何一組輸入物件，這通常表示要針對所有物件進行篩選。 如需詳細資訊，請參閱[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
