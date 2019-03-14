---
title: 認證屬性宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 1513d340cdadc5cb7622e791cc3c163ff39dfe1d
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795397"
---
# <a name="credential-attribute-declaration"></a>認證屬性宣告

認證屬性是選擇性屬性，可與認證參數的型別[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)以便字串也會做為引數傳遞至參數。 當這個屬性會加入至參數宣告中時，Windows PowerShell 會將轉換成字串輸入[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)物件。 例如， [Get-credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential)指令程式會使用此屬性，產生的 Windows powershell [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) cmdlet 所傳回的物件。

## <a name="syntax"></a>語法

```csharp
[Credential]
```

## <a name="remarks"></a>備註

- 通常這個屬性會由型別參數[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)以便字串也會做為引數傳遞至參數。 當[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)物件傳遞給參數，Windows PowerShell 不會執行任何動作。

- 建立時[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)物件時，Windows PowerShell 會使用目前的主機來向使用者顯示適當的提示。 比方說，預設主機會顯示使用者名稱和密碼的提示時使用這個屬性時。 不過，如果正在使用自訂主機，定義不同的提示字元，則會顯示該提示。

- 這個屬性可搭配參數屬性。 如需有關該屬性的詳細資訊，請參閱 <<c0> [ 參數的屬性宣告](./parameter-attribute-declaration.md)。

- 認證屬性所定義[System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute)類別。

## <a name="see-also"></a>另請參閱

[參數別名](./parameter-aliases.md)

[參數屬性宣告](./parameter-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
