---
title: Credential 屬性宣告 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a6deca52fa6c9e46138ae92401f58ac5dbd15852
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784362"
---
# <a name="credential-attribute-declaration"></a>認證屬性宣告

Credential 屬性是選擇性的屬性，可與 system.servicemodel 類型的 Credential 參數搭配使用[，讓](/dotnet/api/System.Management.Automation.PSCredential)字串也可以當做引數傳遞給參數。 當此屬性加入至參數宣告時，Windows PowerShell 會將字串輸入轉換成[system.web](/dotnet/api/System.Management.Automation.PSCredential)物件。 例如， [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) Cmdlet 會使用這個屬性，讓 Windows PowerShell 產生由 Cmdlet[傳回的 system.servicemodel 物件。](/dotnet/api/System.Management.Automation.PSCredential)

## <a name="syntax"></a>語法

```csharp
[Credential]
```

## <a name="remarks"></a>備註

- 這個屬性通常是由[system.object](/dotnet/api/System.Management.Automation.PSCredential)類型的參數使用，因此字串也可以當做引數傳遞給參數。 當[系統](/dotnet/api/System.Management.Automation.PSCredential)將 system.servicemodel 物件傳遞至參數時，Windows PowerShell 不會執行任何操作。

- 建立[system.web](/dotnet/api/System.Management.Automation.PSCredential)物件時，Windows PowerShell 會使用目前的主機向使用者顯示適當的提示。 例如，當使用此屬性時，預設主機會顯示使用者名稱和密碼的提示。 不過，如果使用自訂主機來定義不同的提示，則會顯示提示。

- 這個屬性會與參數屬性搭配使用。 如需該屬性的詳細資訊，請參閱[參數屬性](./parameter-attribute-declaration.md)宣告。

- Credential 屬性是由[Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute)類別所定義。

## <a name="see-also"></a>另請參閱

[參數別名](./parameter-aliases.md)

[參數屬性宣告](./parameter-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
