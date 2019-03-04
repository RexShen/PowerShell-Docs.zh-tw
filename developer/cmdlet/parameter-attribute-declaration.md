---
title: 參數屬性的宣告 |Microsoft Docs
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
ms.openlocfilehash: a3488d5fb3f7eb3df28d0242d6c39d07145a3c8d
ms.sourcegitcommit: 10c347a8c3dcbf8962295601834f5ba85342a87b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "56863614"
---
# <a name="parameter-attribute-declaration"></a>參數屬性宣告

參數屬性會識別在 cmdlet 類別的公用屬性當做 cmdlet 參數。

## <a name="syntax"></a>語法

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>參數

`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) 選擇性具名參數。 `True` 表示需要 cmdlet 參數。 如果未提供必要的參數，叫用 cmdlet 時，Windows PowerShell 會提示使用者輸入的參數值。 預設值為 `false`。

`ParameterSetName` ([System.String](/dotnet/api/System.String)) 選擇性具名參數。 指定此 cmdlet 的參數所屬的參數集合。 如果未不指定任何參數集，則參數所屬的所有參數集。

`Position` ([System.Integer](/dotnet/api/System.Integer)) 選擇性具名參數。 指定在 Windows PowerShell 命令中參數的位置。

`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) 選擇性具名參數。 `True` 指出 cmdlet 參數接受從管線物件，其值。 指定此關鍵字，如果 cmdlet 會在存取完整的物件，不只是物件的屬性。 預設值為 `false`。

`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) 選擇性具名參數。 `True` 指出 cmdlet 參數接受從管線物件具有相同名稱或相同的別名作為此參數的屬性及其值。 例如，如果 cmdlet 不會有`Name`參數和管線的物件也有`Name`屬性、 值`Name`屬性會指派給`Name`指令程式參數。 預設值為 `false`。

`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) 選擇性具名參數。 `True` 指出 cmdlet 參數接受所有剩餘的引數傳遞至 cmdlet。 預設值為 `false`。

`HelpMessage` 選擇性具名參數。 指定參數的簡短描述。 指令程式會執行，且未指定必要的參數時，Windows PowerShell 就會顯示此訊息。

`HelpMessageBaseName` 選擇性具名參數。指定資源識別項的所在的位置。 比方說，這個參數可以指定資源組件，其中包含您想要當地語系化的說明訊息。

`HelpMessageResourceId` 選擇性具名參數。指定說明訊息的資源識別項。

## <a name="remarks"></a>備註

- 如需如何宣告這個屬性的詳細資訊，請參閱[如何宣告 Cmdlet 參數](./how-to-declare-cmdlet-parameters.md)。

- Cmdlet 可以有任意數目的參數。 不過，為了更好的使用者體驗，限制參數的數目。

- 參數必須宣告為公用非靜態欄位或屬性。 參數應該宣告為屬性。 此屬性必須具有公用 set 存取子，而如果`ValueFromPipeline`或`ValueFromPipelineByPropertyName`關鍵字指定，則此屬性必須具有公用 get 存取子。

- 當您指定位置參數時，限制參數設定為小於 5 中的位置參數的數目。 而且，不需要是連續的位置參數。 位置 5、 100 到 250 運作相同位置 0、 1 和 2。

- 當`Position`關鍵字未指定，必須依名稱參考的 cmdlet 參數。

- 當您使用參數集時，請注意下列各項：

    - 每個參數集必須至少一個唯一的參數。 良好的 cmdlet 的設計會指出這個唯一參數應該也是必要的話。 如果您的 cmdlet 設計來執行未包含參數，則無法強制唯一的參數。

    - 未設定任何參數應不包含多個位置的參數具有相同的位置。

    - 參數集合中的只有一個參數應該宣告`ValueFromPipeline = true`。 可以定義多個參數`ValueFromPipelineByPropertyName = true`。

    - 可以定義多個參數`ValueFromPipelineByPropertyName = true`。

- 如需參數名稱的指導方針的詳細資訊，請參閱[Cmdlet 的參數名稱](standard-cmdlet-parameter-names-and-types.md)。

- 所定義的參數屬性[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)類別。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Cmdlet 參數名稱](standard-cmdlet-parameter-names-and-types.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
