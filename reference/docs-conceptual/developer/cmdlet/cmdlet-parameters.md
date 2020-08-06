---
title: Cmdlet 參數 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.openlocfilehash: 98b1d5fd0e7ffbf2d4d161f1bed73fb96a737bd4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774757"
---
# <a name="cmdlet-parameters"></a>Cmdlet 參數

Cmdlet 參數提供允許 Cmdlet 接受輸入的機制。 參數可以直接從命令列或透過管線傳遞給 Cmdlet 的物件接受輸入，引數 (也稱為這些參數的*值*) 可以指定 Cmdlet 接受的輸入、Cmdlet 應如何執行其動作，以及 Cmdlet 傳回給管線的資料。

## <a name="in-this-section"></a>本節內容

將[屬性宣告為參數](./declaring-properties-as-parameters.md)提供在宣告 Cmdlet 的參數之前，您必須瞭解的基本資訊。

[Cmdlet 參數的類型](./types-of-cmdlet-parameters.md)說明您可以在 Cmdlet 中宣告的不同參數類型。

[Cmdlet 參數名稱和功能方針](./standard-cmdlet-parameter-names-and-types.md)討論標準參數的名稱、建議的資料類型和功能。

[參數別名](./parameter-aliases.md)討論您可以為參數定義的別名。

[一般參數名稱](./common-parameter-names.md)本主題說明 Windows PowerShell 新增至 Cmdlet 的參數。

[Cmdlet 參數集](./cmdlet-parameter-sets.md)討論參數集如何讓您撰寫可針對不同案例執行不同動作的單一 Cmdlet。

[Cmdlet 動態參數](./cmdlet-dynamic-parameters.md)討論使用者在特殊條件下可使用的參數。

[支援 Cmdlet 參數中的萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)說明當您設計將針對一組資源執行的 Cmdlet 時，如何提供萬用字元支援。

[驗證參數輸入](./validating-parameter-input.md)說明 Windows PowerShell 如何驗證傳遞給 Cmdlet 參數的引數。

[輸入篩選參數](./input-filter-parameters.md)討論 `Filter` 、 `Include` 和參數，其 `Exclude` 會篩選 Cmdlet 所影響的輸入物件集合。

## <a name="related-sections"></a>相關章節

[如何驗證參數輸入](./how-to-validate-parameter-input.md)

## <a name="see-also"></a>另請參閱

[參數屬性宣告](./parameter-attribute-declaration.md)

[Windows PowerShell Cmdlet](./cmdlet-overview.md)
