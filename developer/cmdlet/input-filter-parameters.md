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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067683"
---
# <a name="input-filter-parameters"></a>輸入篩選參數

Cmdlet 可以定義`Filter`， `Include`，和`Exclude`篩選一組指令程式會影響的輸入物件的參數。

一組輸入物件由通常`InputObject`， `Path`，或`Name`參數。 例如下, 一個 cmdlet 可以有`Path`接受多個路徑使用萬用字元，以及每個路徑會指向輸入物件的參數。 一起使用， `Filter`， `Include`，和`Exclude`參數進一步限定 cmdlet 適用於每次叫用時的路徑。

## <a name="include-and-exclude-parameters"></a>Include 和 Exclude 參數

`Include`和`Exclude`參數識別的物件，包含或排除的一組輸入物件傳遞至 cmdlet。 篩選條件可以表示的標準萬用字元語言時，請使用這些參數。 (如需萬用字元的詳細資訊，請參閱[在 Cmdlet 參數中的 支援使用萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)。)`Include`參數包含其名稱符合包含篩選條件的所有物件。 `Exclude`參數不包括其名稱符合篩選條件的所有物件。

## <a name="filter-parameter"></a>Filter 參數

`Filter`參數可指定篩選，不表示在標準萬用字元語言中。 例如，Active Directory 服務介面 (ADSI) 或 SQL 篩選器可能會傳遞至 cmdlet，透過其`Filter`參數。 在 Windows PowerShell 所提供的 cmdlet，這些篩選器使用 cmdlet 來存取資料存放區的 Windows PowerShell 提供者所指定。 每個提供者通常會定義自己的篩選條件。

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>如果不指定了任何一組輸入物件的篩選

如果不指定了任何一組輸入物件，這通常表示篩選器的所有物件。 如需詳細資訊，請參閱 <<c0> [ Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)