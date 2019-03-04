---
title: Cmdlet 參數集 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857264"
---
# <a name="cmdlet-parameter-sets"></a>Cmdlet 參數集

Windows PowerShell 會使用參數集，讓您撰寫單一的 cmdlet，可以針對不同的案例中執行不同的動作。 參數集可讓您公開給使用者的不同參數，並傳回不同的資訊，根據使用者所指定的參數。

## <a name="examples-of-parameter-sets"></a>參數集範例

例如， `Get-EventLog` （Windows PowerShell 所提供） 的 cmdlet 會傳回不同的資訊，根據使用者指定了是否`List`或`LogName`參數。 如果`List`參數指定，則此 cmdlet 會傳回資訊的記錄檔本身，但不是包含事件的資訊。 如果`LogName`參數指定，則指令程式可傳回特定的事件記錄檔事件的相關資訊。 `List`和`LogName`參數會識別兩個不同的參數集。

## <a name="unique-parameter"></a>唯一的參數

每個參數集必須具有唯一的參數，Windows PowerShell 執行階段可供公開適當的參數組。 可能的話，唯一的參數應該是必要的參數。 時為必要參數，來指定參數，會強制使用者和 Windows PowerShell 執行階段可以使用該參數，來識別設定為使用的參數。 唯一的參數不得為必要項目，如果您的指令程式可執行，而不指定任何參數。

## <a name="multiple-parameter-sets"></a>多個參數集

下圖中，在左方的欄會顯示三個有效的參數集。 參數的而言是唯一的第一個參數集、 參數 B 是唯一的第二個參數集，而且參數 C 是專用的第三個參數集。 不過，在右欄中，參數集不需要唯一的參數。

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>參數集需求

下列需求適用於所有參數集。

- 每個參數集必須至少一個唯一的參數。 如果可能，請此參數為必要參數。

- 參數集，其中包含多個位置的參數必須定義每個參數的唯一位置。 沒有兩個位置參數可以指定相同的位置。

- 集合中的只有一個參數可以宣告`ValueFromPipeline`關鍵字的值與`true`。 可以定義多個參數`ValueFromPipelineByPropertyName`關鍵字的值與`true`。

- 如果未設定任何參數不指定為參數，參數是屬於所有參數集。

## <a name="default-parameter-sets"></a>預設參數集

定義了多個參數集，您可以使用`DefaultParameterSetName`Cmdlet 屬性，以指定預設參數集的關鍵字。 Windows PowerShell 會使用的預設參數集，如果它無法判斷將參數設定為使用根據命令所提供的資訊。 如需有關 Cmdlet 屬性的詳細資訊，請參閱[Cmdlet 屬性宣告](./cmdlet-attribute-declaration.md)。

## <a name="declaring-parameter-sets"></a>宣告參數集

若要建立參數集，您必須指定`ParameterSetName`關鍵字宣告的參數集的每個參數的參數屬性。 對於屬於多個參數集的參數，新增每個參數集的參數屬性。 這可讓您定義每個參數集不同的參數。 比方說，您可以將參數定義為在一組必要和選用在另一個。 不過，每個參數集必須包含一個唯一的參數。

在下列範例中，`UserName`參數是 Test01 參數集的唯一的參數和`ComputerName`參數是 Test02 參數集的唯一參數。 `SharedParam`參數屬於這兩個集合，且為 Test01 參數，但 Test02 參數集的選擇性設定的必要項目。

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```