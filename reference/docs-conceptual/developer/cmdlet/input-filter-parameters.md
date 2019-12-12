---
title: 輸入篩選參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364387"
---
# <a name="input-filter-parameters"></a>輸入篩選參數

Cmdlet 可以定義 `Filter`、`Include`和 `Exclude` 參數，以篩選 Cmdlet 所影響的輸入物件集合。

一般來說，輸入物件的集合是由 `InputObject`、`Path`或 `Name` 參數所指定。 例如，Cmdlet 可以有使用萬用字元接受多個路徑的 `Path` 參數，而每個路徑都會指向輸入物件。 一起使用時，`Filter`、`Include`和 `Exclude` 參數會進一步限定 Cmdlet 在每次叫用時所能運作的路徑。

## <a name="include-and-exclude-parameters"></a>包含和排除參數

`Include` 和 `Exclude` 參數會識別傳遞給 Cmdlet 的一組輸入物件所包含或排除的物件。 當篩選準則可以用標準萬用字元語言表示時，請使用這些參數。 （如需萬用字元的詳細資訊，請參閱[在 Cmdlet 參數中支援萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)）。`Include` 參數包含其名稱符合包含篩選準則的所有物件。 `Exclude` 參數會排除其名稱符合篩選準則的所有物件。

## <a name="filter-parameter"></a>篩選參數

`Filter` 參數指定的篩選準則不是以標準萬用字元語言表示。 例如，Active Directory 服務介面（ADSI）或 SQL 篩選器可能會透過其 `Filter` 參數傳遞至 Cmdlet。 在 Windows PowerShell 所提供的 Cmdlet 中，這些篩選器是由使用 Cmdlet 來存取資料存放區的 Windows PowerShell 提供者所指定。 每個提供者通常會定義它自己的篩選準則。

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>篩選是否未指定輸入物件集合

如果未指定任何一組輸入物件，這通常表示要針對所有物件進行篩選。 如需詳細資訊，請參閱[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)