---
ms.date: 09/13/2016
ms.topic: reference
title: 認證屬性宣告
description: 認證屬性宣告
ms.openlocfilehash: fb826d9a46cadc021fe0c667091bbc7a9251aaa8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648605"
---
# <a name="credential-attribute-declaration"></a>認證屬性宣告

Credential 屬性是選擇性的屬性，可與類型為 system.string 的 Credential 參數一起 [使用，讓](/dotnet/api/System.Management.Automation.PSCredential) 字串也可以當做引數傳遞給參數。 當這個屬性加入至參數宣告時，Windows PowerShell 會將字串輸入轉換為 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 物件。 例如， [取得認證](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) 指令程式會使用這個屬性來讓 Windows PowerShell 產生 Cmdlet 所傳回的 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 物件。

## <a name="syntax"></a>語法

```csharp
[Credential]
```

## <a name="remarks"></a>備註

- 一般來說，這個屬性是由類型為 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 的參數使用，因此字串也可以當做引數傳遞給參數。 當將 [system.string 物件傳遞](/dotnet/api/System.Management.Automation.PSCredential) 給參數時，Windows PowerShell 不會執行任何動作。

- 建立 [system.string 物件時](/dotnet/api/System.Management.Automation.PSCredential) ，Windows PowerShell 會使用目前的主控制項向使用者顯示適當的提示。 例如，當使用這個屬性時，預設主控制項會顯示提示輸入使用者名稱和密碼。 但是，如果使用自訂主機來定義不同的提示，則會顯示該提示。

- 這個屬性會與參數屬性搭配使用。 如需該屬性的詳細資訊，請參閱 [參數屬性聲明](./parameter-attribute-declaration.md)。

- Credential 屬性是由 [Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) 類別所定義。

## <a name="see-also"></a>另請參閱

[參數別名](./parameter-aliases.md)

[參數屬性宣告](./parameter-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
