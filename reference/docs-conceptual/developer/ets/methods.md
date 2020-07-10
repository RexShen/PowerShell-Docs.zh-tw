---
title: 擴充類型系統類別方法
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: 97c11093d2faeb2a73b349c479d6de34ae2ea788
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217919"
---
# <a name="ets-class-methods"></a>ETS 類別方法

ETS 方法是可以接受引數、可能會傳回結果，而且不能出現在運算式左側的成員。 ETS 內可用的方法包括程式碼、Windows PowerShell 和腳本方法。

> [!NOTE]
> 在腳本中，方法是使用與其他成員相同的語法來存取，並在方法名稱的結尾加上括弧。

## <a name="code-methods"></a>程式碼方法

程式碼方法是以 CLR 語言定義的擴充成員。 它會針對基底物件上定義的方法提供類似的功能;不過，程式碼方法可能會動態新增至**PSObject**物件。 為了讓程式碼方法可供使用，開發人員必須以某種 CLR 語言撰寫屬性、編譯和傳送結果元件。 這個元件必須可在需要程式碼方法的運行時使用。 請注意，程式碼方法的執行必須是安全線程。 這些方法的存取是透過提供下列公用方法和屬性的[PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod)物件來完成。

- `PSCodeMethod.Copy`method：建立**PSCodeMethod**物件的完全相同複本。
- `PSCodeMethod.Invoke(System.Object[])`method：叫用基礎程式碼方法。
- `PSCodeMethod.ToString`method：將**PSCodeMethod**物件轉換為字串。
- `PSCodeMethod.CodeReference`property：取得程式碼方法所依據的基礎方法。
- **PSMemberInfo. IsInstance**屬性：取得指出成員來源的**布林**值。
- **PSCodeMethod. MemberType**屬性：取得將此方法識別為程式碼方法的** psmembertypes. CodeMethod**列舉常數。
- **PSMemberInfo.Name**屬性：取得基礎程式碼方法的名稱。
- **PSCodeMethod. OverloadDefinitions**屬性：取得基礎程式碼方法的所有多載的定義。
- **PSCodeMethod. TypeNameOfValue**屬性：取得程式碼方法的完整名稱。
- **PSMemberInfo**屬性：取得**PSCodeMethod**物件。

## <a name="windows-powershell-methods"></a>Windows PowerShell 方法

PowerShell 方法是在基底物件上定義的 CLR 方法，或透過介面卡來存取。 這些方法的存取是透過提供下列公用方法和屬性的**PSMethod**物件來完成。

- `PSMethod.Copy`method：建立**PSMethod**物件的完全相同複本。
- `PSMethod.Invoke(System.Object[])`method：叫用基礎方法。
- `PSMethod.ToString`method：將**PSMethod**物件轉換為字串。
- **PSMemberInfo. IsInstance**屬性：取得指出成員來源的**布林**值。
- **PSMethod. MemberType**屬性：取得將此方法識別為 PowerShell 方法的** psmembertypes**方法列舉常數。
- **PSMemberInfo.Name**屬性：取得基礎方法的名稱。
- **PSMethod. OverloadDefinitions**屬性：取得基礎方法之所有多載的定義。
- **PSMethod. TypeNameOfValue**屬性：取得這個方法的 ETS 類型。
- **PSMemberInfo**屬性：取得**PSMethod**物件。

## <a name="script-methods"></a>腳本方法

腳本方法是以 PowerShell 語言定義的擴充成員。 它會針對基底物件上定義的方法提供類似的功能;不過，腳本方法可能會動態新增至**PSObject**物件。 這些方法的存取是透過提供下列公用方法和屬性的[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod)物件來完成。

- `PSScriptMethod.Copy`method：建立**PSScriptMethod**物件的完全相同複本。
- `PSScriptMethod.Invoke(System.Object[])`method：叫用基礎腳本方法。
- `PSScriptMethod.ToString`method：將**PSScriptMethod**物件轉換為字串。
- **PSMemberInfo. IsInstance**屬性：取得指出成員來源的**布林**值。
- **PSScriptMethod. MemberType**屬性：取得將此方法識別為腳本方法的** psmembertypes. ScriptMethod**列舉常數。
- **PSMemberInfo.Name**屬性：取得基礎程式碼方法的名稱。
- **PSScriptMethod. OverloadDefinitions**屬性：取得基礎腳本方法之所有多載的定義。
- **PSScriptMethod. TypeNameOfValue**屬性：取得這個方法的 ETS 類型。
- **PSScriptMethod**屬性：取得用來叫用方法的腳本。
- **PSMemberInfo**屬性：取得**PSScriptMethod**物件。
