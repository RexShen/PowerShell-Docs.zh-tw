---
ms.date: 07/09/2020
ms.topic: reference
title: 擴充類型系統類別方法
description: 擴充類型系統類別方法
ms.openlocfilehash: b53604a36e0a0c3587f345262e8f274e3a2c4859
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660375"
---
# <a name="ets-class-methods"></a>ETS 類別方法

ETS 方法是可採用引數、可能會傳回結果，且不能出現在運算式左側的成員。 ETS 中可用的方法包括程式碼、Windows PowerShell 和腳本方法。

> [!NOTE]
> 在腳本中，方法是使用與其他成員相同的語法來存取，而在方法名稱的結尾加上括弧。

## <a name="code-methods"></a>程式碼方法

程式碼方法是以 CLR 語言定義的擴充成員。 它會針對基底物件上定義的方法提供類似的功能。不過，程式碼方法可能會動態新增到 **PSObject** 物件。 為了讓程式碼方法可供使用，開發人員必須以某些 CLR 語言撰寫屬性、編譯和傳送結果元件。 此元件必須可在需要程式碼方法的運行空間中使用。 請注意，程式碼方法的執行必須具備執行緒安全。 這些方法的存取是透過提供下列公用方法和屬性的 [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) 物件來完成。

- `PSCodeMethod.Copy` 方法：建立 **PSCodeMethod** 物件的完整複本。
- `PSCodeMethod.Invoke(System.Object[])` 方法：叫用基礎程式碼方法。
- `PSCodeMethod.ToString` 方法：將 **PSCodeMethod** 物件轉換為字串。
- `PSCodeMethod.CodeReference` 屬性：取得程式碼方法所依據的基礎方法。
- **PSMemberInfo. IsInstance** 屬性：取得指出成員來源的 **布林** 值。
- **PSCodeMethod. MemberType** 屬性：取得將此方法識別為程式碼方法的 **psmembertypes. CodeMethod** 列舉常數。
- **PSMemberInfo.Name** 屬性：取得基礎程式碼方法的名稱。
- **PSCodeMethod. OverloadDefinitions** 屬性：取得基礎程式碼方法的所有多載的定義。
- **PSCodeMethod. TypeNameOfValue** 屬性：取得程式碼方法的完整名稱。
- **PSMemberInfo。 Value** 屬性：取得 **PSCodeMethod** 物件。

## <a name="windows-powershell-methods"></a>Windows PowerShell 方法

PowerShell 方法是在基底物件上定義或可透過介面卡存取的 CLR 方法。 這些方法的存取是透過提供下列公用方法和屬性的 **PSMethod** 物件來完成。

- `PSMethod.Copy` 方法：建立 **PSMethod** 物件的完整複本。
- `PSMethod.Invoke(System.Object[])` 方法：叫用基礎方法。
- `PSMethod.ToString` 方法：將 **PSMethod** 物件轉換為字串。
- **PSMemberInfo. IsInstance** 屬性：取得指出成員來源的 **布林** 值。
- **PSMethod. MemberType** 屬性：取得將此方法識別為 PowerShell 方法的 **psmembertypes. 方法** 列舉常數。
- **PSMemberInfo.Name** 屬性：取得基礎方法的名稱。
- **PSMethod. OverloadDefinitions** 屬性：取得基礎方法的所有多載的定義。
- **PSMethod. TypeNameOfValue** 屬性：取得這個方法的 ETS 型別。
- **PSMemberInfo。 Value** 屬性：取得 **PSMethod** 物件。

## <a name="script-methods"></a>腳本方法

腳本方法是以 PowerShell 語言定義的擴充成員。 它會針對基底物件上定義的方法提供類似的功能。不過，您可以將腳本方法動態新增到 **PSObject** 物件。 這些方法的存取是透過提供下列公用方法和屬性的 [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) 物件來完成。

- `PSScriptMethod.Copy` 方法：建立 **PSScriptMethod** 物件的完整複本。
- `PSScriptMethod.Invoke(System.Object[])` 方法：叫用基礎腳本方法。
- `PSScriptMethod.ToString` 方法：將 **PSScriptMethod** 物件轉換為字串。
- **PSMemberInfo. IsInstance** 屬性：取得指出成員來源的 **布林** 值。
- **PSScriptMethod. MemberType** 屬性：取得將這個方法識別為腳本方法的 **psmembertypes. ScriptMethod** 列舉常數。
- **PSMemberInfo.Name** 屬性：取得基礎程式碼方法的名稱。
- **PSScriptMethod. OverloadDefinitions** 屬性：取得基礎腳本方法的所有多載的定義。
- **PSScriptMethod. TypeNameOfValue** 屬性：取得這個方法的 ETS 型別。
- **PSScriptMethod** 屬性：取得用來叫用方法的腳本。
- **PSMemberInfo。 Value** 屬性：取得 **PSScriptMethod** 物件。
