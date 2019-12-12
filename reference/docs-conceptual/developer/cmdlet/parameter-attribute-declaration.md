---
title: 參數屬性宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: 81b1ed95669f51ba554f6f99031d098e239f02e0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365357"
---
# <a name="parameter-attribute-declaration"></a>參數屬性宣告

Parameter 屬性會將 Cmdlet 類別的公用屬性識別為 Cmdlet 參數。

## <a name="syntax"></a>語法

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>參數

`Mandatory` （[布林值](/dotnet/api/System.Boolean)）選擇性的具名引數。 `True` 表示 Cmdlet 參數是必要的。 如果叫用 Cmdlet 時未提供必要的參數，Windows PowerShell 會提示使用者輸入參數值。 預設值為 `false`。

`ParameterSetName` （[system.string](/dotnet/api/System.String)）選擇性的具名引數。 指定此 Cmdlet 參數所屬的參數集。 如果未指定參數集，參數會屬於所有參數集。

`Position` （[system.object](/dotnet/api/System.Int32)）選擇性的具名引數。 指定參數在 Windows PowerShell 命令中的位置。

`ValueFromPipeline` （[布林值](/dotnet/api/System.Boolean)）選擇性的具名引數。 `True` 表示 Cmdlet 參數接受管線物件的值。 如果 Cmdlet 存取完整的物件，而不只是物件的屬性，請指定此關鍵字。 預設值為 `false`。

`ValueFromPipelineByPropertyName` （[布林值](/dotnet/api/System.Boolean)）選擇性的具名引數。 `True` 表示 Cmdlet 參數從管線物件的屬性取得其值，其名稱或別名與此參數相同。 例如，如果 Cmdlet 具有 `Name` 參數，而且管線物件也具有 `Name` 屬性，則 `Name` 屬性的值會指派給 Cmdlet 的 `Name` 參數。 預設值為 `false`。

`ValueFromRemainingArguments` （[布林值](/dotnet/api/System.Boolean)）選擇性的具名引數。 `True` 表示 Cmdlet 參數接受傳遞給 Cmdlet 的所有其餘引數。 預設值為 `false`。

`HelpMessage` 選擇性的具名引數。 指定參數的簡短描述。 當 Cmdlet 執行時，Windows PowerShell 會顯示此訊息，且未指定強制參數。

`HelpMessageBaseName` 選擇性的具名引數。指定資源識別碼所在的位置。 例如，此參數可以指定資源元件，其中包含您想要當地語系化的說明訊息。

`HelpMessageResourceId` 選擇性的具名引數。指定說明訊息的資源識別碼。

## <a name="remarks"></a>備註

- 如需如何宣告此屬性的詳細資訊，請參閱 how [To Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md)。

- Cmdlet 可以有任意數目的參數。 不過，若要獲得更佳的使用者體驗，請限制參數的數目。

- 參數必須在公用非靜態欄位或屬性上宣告。 參數應該在屬性上宣告。 屬性必須具有公用 set 存取子，如果已指定 `ValueFromPipeline` 或 `ValueFromPipelineByPropertyName` 關鍵字，則屬性必須具有公用 get 存取子。

- 當您指定位置參數時，請將參數集中的位置參數數目限制為小於五個。 和，位置參數不一定要是連續的。 位置5、100和250的工作方式與位置0、1和2相同。

- 未指定 `Position` 關鍵字時，Cmdlet 參數必須由其名稱參考。

- 當您使用參數集時，請注意下列事項：

    - 每個參數集必須至少有一個唯一的參數。 良好的 Cmdlet 設計表示如果可能，此唯一參數也應該是強制的。 如果您的 Cmdlet 設計為不搭配參數執行，則 unique 參數不可以是強制的。

    - 沒有參數集應包含一個以上具有相同位置的位置參數。

    - 參數集中只有一個參數應該宣告 `ValueFromPipeline = true`。 多個參數可以定義 `ValueFromPipelineByPropertyName = true`。

    - 多個參數可以定義 `ValueFromPipelineByPropertyName = true`。

- 如需參數名稱指導方針的詳細資訊，請參閱[Cmdlet 參數名稱](standard-cmdlet-parameter-names-and-types.md)。

- Parameter 屬性是由[Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)類別所定義。

## <a name="see-also"></a>另請參閱

[Parameterattribute。](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Cmdlet 參數名稱](standard-cmdlet-parameter-names-and-types.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
