---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 參數集
description: Cmdlet 參數集
ms.openlocfilehash: e84af7faf5b7459d8dbe06847526efe804e2c5e1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668281"
---
# <a name="cmdlet-parameter-sets"></a>Cmdlet 參數集

PowerShell 會使用參數集，讓您撰寫可針對不同案例執行不同動作的單一 Cmdlet。 參數集可讓您向使用者公開不同的參數。 和，根據使用者指定的參數傳回不同的資訊。

## <a name="examples-of-parameter-sets"></a>參數集的範例

例如，PowerShell Cmdlet 會 `Get-EventLog` 根據使用者是否指定 **清單** 或 **LogName** 參數，傳回不同的資訊。 如果指定了 **List** 參數，Cmdlet 會傳回記錄檔本身的相關資訊，但不會傳回它們所包含的事件資訊。 如果指定了 **LogName** 參數，Cmdlet 會傳回特定事件記錄檔中事件的相關資訊。 **List** 和 **LogName** 參數會識別兩個不同的參數集。

## <a name="unique-parameter"></a>唯一參數

每個參數集都必須有一個唯一的參數，PowerShell 執行時間會使用此參數來公開適當的參數集。 可能的話，唯一的參數應該是必要參數。 當參數是必要參數時，使用者必須指定參數，且 PowerShell 執行時間會使用該參數來識別參數集。 如果您的 Cmdlet 是設計為在未指定任何參數的情況下執行，則唯一的參數不可以是必要的。

## <a name="multiple-parameter-sets"></a>多個參數集

在下圖中，左邊的資料行顯示三個有效的參數集。 **參數 A** 對第一個參數集而言是唯一的，第二個參數集的 **參數 B** 是唯一的，而 **參數 C** 對第三個參數集是唯一的。 在右邊的資料行中，參數集沒有唯一的參數。

![參數集的圖例](media/cmdlet-parameter-sets/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>參數集需求

下列需求適用于所有參數集。

- 每個參數集都必須至少有一個唯一的參數。 可能的話，請將此參數設為必要參數。

- 包含多個位置參數的參數集必須定義每個參數的唯一位置。 沒有兩個位置參數可以指定相同的位置。

- 只有一個集合中的參數可以宣告 `ValueFromPipeline` 具有值的關鍵字 `true` 。
  多個參數可以定義 `ValueFromPipelineByPropertyName` 具有值的關鍵字 `true` 。

- 如果未指定參數的參數集，參數將屬於所有參數集。

> [!NOTE]
> 針對 Cmdlet 或函式，有32個參數集的限制。

## <a name="default-parameter-sets"></a>預設參數集

定義多個參數集時，您可以使用 `DefaultParameterSetName` **Cmdlet** 屬性的關鍵字來指定預設參數集。 如果 PowerShell 無法根據命令所提供的資訊來判斷要使用的參數集，則會使用預設參數集。 如需 **Cmdlet** 屬性的詳細資訊，請參閱 [Cmdlet 屬性聲明](./cmdlet-attribute-declaration.md)。

## <a name="declaring-parameter-sets"></a>宣告參數集

若要建立參數集，您必須在 `ParameterSetName` 針對參數集內的每個參數宣告 **參數** 屬性時，指定關鍵字。 對於屬於多個參數集的參數，請為每個參數集加入 **參數** 屬性。 這個屬性可讓您針對每個參數集定義不同的參數。 例如，您可以在一個集合中將參數定義為強制，並在另一個集合中定義選擇性參數。 不過，每個參數集都必須包含一個唯一的參數。 如需詳細資訊，請參閱 [參數屬性聲明](parameter-attribute-declaration.md)。

在下列範例中，使用者 **名稱** 參數是參數集的唯一參數 `Test01` ，而 **ComputerName** 參數是參數集的唯一參數 `Test02` 。 **SharedParam** 參數屬於這兩個集合，而且對參數集而言是必要的， `Test01` 但參數集則是選擇性的 `Test02` 。

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
