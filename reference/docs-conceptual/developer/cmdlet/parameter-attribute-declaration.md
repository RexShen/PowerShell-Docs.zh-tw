---
ms.date: 09/13/2016
ms.topic: reference
title: 參數屬性宣告
description: 參數屬性宣告
ms.openlocfilehash: bab48a94cb4b1e8501fb79c2f3ef71393fa2ee68
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650354"
---
# <a name="parameter-attribute-declaration"></a>參數屬性宣告

Parameter 屬性會將 Cmdlet 類別的公用屬性識別為 Cmdlet 參數。

## <a name="syntax"></a>語法

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>參數

`Mandatory` ([system.string) 選擇性的命名](/dotnet/api/System.Boolean) 參數。 `True` 指出需要 Cmdlet 參數。 如果叫用 Cmdlet 時未提供必要的參數，Windows PowerShell 會提示使用者提供參數值。 預設值為 `false`。

`ParameterSetName` ([system.string](/dotnet/api/System.String)) 選擇性的具名引數。 指定此 Cmdlet 參數所屬的參數集。 如果未指定任何參數集，則參數屬於所有參數集。

`Position` ([的 system.object](/dotnet/api/System.Int32)) 選擇性的具名引數。 指定參數在 Windows PowerShell 命令中的位置。

`ValueFromPipeline` ([system.string) 選擇性的命名](/dotnet/api/System.Boolean) 參數。 `True` 指出 Cmdlet 參數接受來自管線物件的值。 如果 Cmdlet 存取完整的物件，而不只是物件的屬性，請指定此關鍵字。 預設值為 `false`。

`ValueFromPipelineByPropertyName` ([system.string) 選擇性的命名](/dotnet/api/System.Boolean) 參數。 `True` 指出 Cmdlet 參數會從具有相同名稱或與此參數相同別名的管線物件的屬性取得其值。 例如，如果 Cmdlet 有 `Name` 參數，且管線物件也有 `Name` 屬性，則會將屬性的值指派給 `Name` Cmdlet 的 `Name` 參數。 預設值為 `false`。

`ValueFromRemainingArguments` ([system.string) 選擇性的命名](/dotnet/api/System.Boolean) 參數。 `True` 指出 Cmdlet 參數接受所有傳遞給 Cmdlet 的其餘引數。 預設值為 `false`。

`HelpMessage` 選擇性的具名引數。 指定參數的簡短描述。 Windows PowerShell 在執行 Cmdlet 且未指定必要參數時，會顯示此訊息。

`HelpMessageBaseName` 選擇性的具名引數。指定資源識別碼所在的位置。 例如，這個參數可以指定資源元件，其中包含您要當地語系化的說明訊息。

`HelpMessageResourceId` 選擇性的具名引數。指定說明訊息的資源識別碼。

## <a name="remarks"></a>備註

- 如需如何宣告此屬性的詳細資訊，請參閱 [如何宣告 Cmdlet 參數](./how-to-declare-cmdlet-parameters.md)。

- Cmdlet 可以有任意數目的參數。 不過，若要獲得更好的使用者體驗，請限制參數的數目。

- 您必須在公用非靜態欄位或屬性上宣告參數。 必須在屬性上宣告參數。 屬性必須具有公用 set 存取子，而且如果指定了 `ValueFromPipeline` 或 `ValueFromPipelineByPropertyName` 關鍵字，屬性必須具有公用 get 存取子。

- 當您指定位置參數時，請將參數中的位置參數數目限制為小於5。 而且，位置參數不一定要是連續的。 位置5、100和250的運作方式與位置0、1和2相同。

- 如果 `Position` 未指定關鍵字，則 Cmdlet 參數必須由其名稱參考。

- 當您使用參數集時，請注意下列事項：

  - 每個參數集都必須至少有一個唯一的參數。 良好的 Cmdlet 設計指出，如果可能的話，這個唯一的參數也應該是必要的。 如果您的 Cmdlet 是設計為在沒有參數的情況下執行，則唯一的參數不能是強制性的。

  - 沒有任何參數集應包含一個以上具有相同位置的位置參數。

  - 參數集中只能有一個參數 `ValueFromPipeline = true` 。 可以定義多個參數 `ValueFromPipelineByPropertyName = true` 。

  - 可以定義多個參數 `ValueFromPipelineByPropertyName = true` 。

- 如需參數名稱指導方針的詳細資訊，請參閱 [Cmdlet 參數名稱](standard-cmdlet-parameter-names-and-types.md)。

- Parameter 屬性是由 [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 類別所定義。

## <a name="see-also"></a>另請參閱

[Parameterattribute。](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Cmdlet 參數名稱](standard-cmdlet-parameter-names-and-types.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
