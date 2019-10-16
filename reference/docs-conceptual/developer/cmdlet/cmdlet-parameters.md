---
title: Cmdlet 參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.assetid: 3f1cca5f-5b95-4bce-94a6-a22db1aefd47
caps.latest.revision: 23
ms.openlocfilehash: 914a10907bcf980eed8d7e2f819c382fe6b341ad
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365927"
---
# <a name="cmdlet-parameters"></a>Cmdlet 參數

Cmdlet 參數提供允許 Cmdlet 接受輸入的機制。 參數可以直接從命令列或透過管線傳遞給 Cmdlet 的物件接受輸入，這些參數的引數（也稱為*值*）可以指定 Cmdlet 接受的輸入，Cmdlet 應如何執行其動作，以及 Cmdlet 傳回給管線的資料。

## <a name="in-this-section"></a>在本節中

將[屬性宣告為參數](./declaring-properties-as-parameters.md)提供在宣告 Cmdlet 的參數之前，您必須瞭解的基本資訊。

[Cmdlet 參數的類型](./types-of-cmdlet-parameters.md)說明您可以在 Cmdlet 中宣告的不同參數類型。

[Cmdlet 參數名稱和功能方針](./standard-cmdlet-parameter-names-and-types.md)Discuses 標準參數的名稱、建議的資料類型和功能。

[參數別名](./parameter-aliases.md)討論您可以為參數定義的別名。

[一般參數名稱](./common-parameter-names.md)本主題說明 Windows PowerShell 新增至 Cmdlet 的參數。

[Cmdlet 參數集](./cmdlet-parameter-sets.md)討論參數集如何讓您撰寫可針對不同案例執行不同動作的單一 Cmdlet。

[Cmdlet 動態參數](./cmdlet-dynamic-parameters.md)討論使用者在特殊條件下可使用的參數。

[支援 Cmdlet 參數中的萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)說明當您設計將針對一組資源執行的 Cmdlet 時，如何提供萬用字元支援。

[驗證參數輸入](./validating-parameter-input.md)說明 Windows PowerShell 如何驗證傳遞給 Cmdlet 參數的引數。

[輸入篩選參數](./input-filter-parameters.md)討論 `Filter`、`Include` 和 `Exclude` 參數，以篩選 Cmdlet 所影響的輸入物件集合。

## <a name="related-sections"></a>相關章節

[如何驗證參數輸入](./how-to-validate-parameter-input.md)

## <a name="see-also"></a>另請參閱

[參數屬性宣告](./parameter-attribute-declaration.md)

[Windows PowerShell Cmdlet](./cmdlet-overview.md)
