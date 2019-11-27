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
ms.openlocfilehash: dfe747893b4aef6376ea3b12dd79b7c144455ed0
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74415681"
---
# <a name="cmdlet-parameter-sets"></a>Cmdlet 參數集

PowerShell 會使用參數集，讓您撰寫可針對不同案例執行不同動作的單一 Cmdlet。 參數集可讓您向使用者公開不同的參數。 和，根據使用者指定的參數傳回不同的資訊。

## <a name="examples-of-parameter-sets"></a>參數集的範例

例如，PowerShell `Get-EventLog` Cmdlet 會根據使用者是否指定**List**或**LogName**參數，傳回不同的資訊。 如果指定了**List**參數，Cmdlet 會傳回記錄檔本身的相關資訊，但不會傳回其包含的事件資訊。 如果指定**LogName**參數，此 Cmdlet 會傳回特定事件記錄檔中事件的相關資訊。 **List**和**LogName**參數會識別兩個不同的參數集。

## <a name="unique-parameter"></a>唯一參數

每個參數集都必須有一個唯一的參數，讓 PowerShell 執行時間用來公開適當的參數集。 可能的話，unique 參數應該是必要參數。 當參數為強制性時，使用者必須指定參數，而且 PowerShell 執行時間會使用該參數來識別參數集。 如果您的 Cmdlet 設計成在不指定任何參數的情況下執行，則唯一的參數不能是強制的。

## <a name="multiple-parameter-sets"></a>多個參數集

在下圖中，左邊的資料行顯示三個有效的參數集。 **參數 A**對第一個參數集而言是唯一的，**參數 B**對第二個參數集而言是唯一的，而**參數 C**則是第三個參數集獨有的。 在右邊的資料行中，參數集沒有唯一的參數。

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>參數集需求

下列需求適用于所有參數集。

- 每個參數集必須至少有一個唯一的參數。 可能的話，請將此參數設為必要參數。

- 包含多個位置參數的參數集必須為每個參數定義唯一的位置。 沒有兩個位置參數可以指定相同的位置。

- 在集合中，只有一個參數可以宣告具有 `true`值的 `ValueFromPipeline` 關鍵字。
  多個參數可以定義具有 `true`值的 `ValueFromPipelineByPropertyName` 關鍵字。

- 如果沒有為參數指定參數集，參數就會屬於所有參數集。

> [!NOTE]
> Cmdlet 或函式的限制為32個參數集。

## <a name="default-parameter-sets"></a>預設參數集

定義多個參數集時，您可以使用**Cmdlet**屬性的 `DefaultParameterSetName` 關鍵字來指定預設參數集。 如果 PowerShell 無法根據命令所提供的資訊來判斷要使用的參數，則會使用預設參數集。 如需**Cmdlet**屬性的詳細資訊，請參閱[Cmdlet 屬性](./cmdlet-attribute-declaration.md)宣告。

## <a name="declaring-parameter-sets"></a>宣告參數集

若要建立參數集，您必須在宣告參數集內每個參數的**參數**屬性時，指定 `ParameterSetName` 關鍵字。 針對屬於多個參數集的參數，請為每個參數集新增**參數**屬性。 這個屬性可讓您針對每個參數集定義不同的參數。 例如，您可以將參數定義為一個集合中的必要項，並在另一個集合中將其設為選擇性。 不過，每個參數集都必須包含一個唯一的參數。 如需詳細資訊，請參閱[參數屬性](parameter-attribute-declaration.md)宣告。

在下列範例中， **UserName**參數是 `Test01` 參數集的唯一參數，而**ComputerName**參數是 `Test02` 參數集的唯一參數。 **SharedParam**參數同時屬於這兩個集合，而且對 `Test01` 參數集而言是必要的，但 `Test02` 參數集則是選擇性的。

```csharp
[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test02")]
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
private string sharedParam;
```
