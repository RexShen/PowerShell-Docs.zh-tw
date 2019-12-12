---
title: 參數別名 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369587"
---
# <a name="parameter-aliases"></a>參數別名

Cmdlet 參數也可以有別名。 當您在命令中輸入或指定參數時，可以使用別名而非參數名稱。

## <a name="benefits-of-using-aliases"></a>使用別名的優點

將別名新增至參數可提供下列優點。

- 您可以提供快捷方式，讓使用者在呼叫 Cmdlet 時不需要使用完整的參數名稱。 例如，您可以使用 "CN" 別名，而不是參數名稱 "ComputerName"。

- 如果您想要為相同的參數提供不同的名稱，可以定義多個別名。 如果您必須使用以不同方式參考相同資料的多個使用者群組，您可能會想要定義多個別名。

- 如果參數的名稱變更，您可以為現有的腳本提供回溯相容性。

- 藉由使用 Alias 屬性和 ValueFromPipelineByName 屬性，您可以定義參數，讓您的 Cmdlet 系結至不同的物件類型。 例如，假設您有兩個不同類型的物件，而第一個物件具有寫入器屬性，而第二個物件具有 editor 屬性。 如果您的 Cmdlet 具有具有寫入器和編輯器別名的參數，且 Cmdlet 接受以屬性名稱為基礎的管線輸入，則您的 Cmdlet 可以使用兩個參數別名系結至這兩個物件。

如需可搭配特定參數使用之別名的詳細資訊，請參閱[一般參數名稱](./common-parameter-names.md)。

## <a name="defining-parameter-aliases"></a>定義參數別名

若要定義參數的別名，請宣告 Alias 屬性，如下列參數宣告所示。 在此範例中，會為相同的參數定義多個別名。 （如需詳細資訊，請參閱 how[To Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md)）。

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a>另請參閱

[一般參數名稱](./common-parameter-names.md)

[如何宣告 Cmdlet 參數](./how-to-declare-cmdlet-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
