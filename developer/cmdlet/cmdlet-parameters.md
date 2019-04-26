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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068397"
---
# <a name="cmdlet-parameters"></a>Cmdlet 參數

Cmdlet 參數提供的機制，可讓 cmdlet 接受輸入。 參數可以接受輸入，直接從命令列中，或透過管線中，引數傳遞至 cmdlet 的物件 (也稱為*值*) 這些參數可以指定此 cmdlet 會接受的輸入方式指令程式應該執行其動作和指令程式可傳回至管線的資料。

## <a name="in-this-section"></a>在本節中

[宣告屬性做為參數](./declaring-properties-as-parameters.md)提供宣告之參數的 cmdlet 之前，必須了解的基本資訊。

[Cmdlet 參數的型別](./types-of-cmdlet-parameters.md)說明不同類型的 cmdlet 中，您可以宣告的參數。

[Cmdlet 參數名稱和功能的指導方針](./standard-cmdlet-parameter-names-and-types.md)Discuses 名稱，建議的資料類型和功能的標準參數。

[參數別名](./parameter-aliases.md)討論您可以定義參數的別名。

[常見的參數名稱](./common-parameter-names.md)本主題描述 Windows PowerShell 將新增到 cmdlet 的參數。

[Cmdlet 參數會設定](./cmdlet-parameter-sets.md)討論如何參數集可讓您撰寫單一的 cmdlet，可以針對不同的案例中執行不同的動作。

[Cmdlet 的動態參數](./cmdlet-dynamic-parameters.md)討論在特殊情況下，使用者可以使用的參數。

[在 Cmdlet 參數支援萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)說明如何提供支援的萬用字元，當您設計的 cmdlet，將會針對資源群組中的執行。

[驗證參數輸入](./validating-parameter-input.md)說明 Windows PowerShell 如何驗證傳遞給 cmdlet 參數的引數。

[輸入篩選參數](./input-filter-parameters.md)討論`Filter`， `Include`，和`Exclude`篩選一組指令程式會影響的輸入物件的參數。

## <a name="related-sections"></a>相關的章節

[如何驗證參數的輸入](./how-to-validate-parameter-input.md)

## <a name="see-also"></a>另請參閱

[參數屬性宣告](./parameter-attribute-declaration.md)

[Windows PowerShell Cmdlets](./cmdlet-overview.md)
