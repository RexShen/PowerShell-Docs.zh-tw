---
title: 如何撰寫一個簡單的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067734"
---
# <a name="how-to-write-a-cmdlet"></a>如何撰寫 cmdlet

這篇文章會示範如何撰寫的 cmdlet。 `Send-Greeting` Cmdlet 會取得單一使用者名稱作為輸入，並接著將祝賀詞寫入該使用者。 此 cmdlet 不會執行的工作，雖然此範例會示範指令程式的主要區段。

## <a name="steps-to-write-a-cmdlet"></a>若要撰寫的 cmdlet 的步驟

1. 若要將類別宣告為 cmdlet，使用**Cmdlet**屬性。 **Cmdlet**屬性會指定動詞與名詞的 cmdlet 名稱。

   如需詳細資訊**Cmdlet**屬性，請參閱[CmdletAttribute 宣告](cmdlet-attribute-declaration.md)。

2. 指定類別的名稱。

3. 指定此 cmdlet 會衍生自下列類別之一：

   * [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)
   * [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

4. 若要定義此 cmdlet 的參數，請使用**參數**屬性。 在此情況下，只有一個必須指定參數。

   如需詳細資訊**參數**屬性，請參閱[ParameterAttribute 宣告](parameter-attribute-declaration.md)。

5. 覆寫的輸入處理方法，以處理輸入。 在此情況下， [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)會覆寫方法。

6. 撰寫問候，使用的方法[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)。
   問候語會顯示以下列格式：

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a>範例

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify the
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory=true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)

[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[CmdletAttribute Declaration](cmdlet-attribute-declaration.md)

[ParameterAttribute 宣告](parameter-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](writing-a-windows-powershell-cmdlet.md)