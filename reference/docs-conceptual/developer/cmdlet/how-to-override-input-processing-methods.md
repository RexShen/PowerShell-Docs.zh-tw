---
title: 如何覆寫輸入處理方法 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364467"
---
# <a name="how-to-override-input-processing-methods"></a>如何覆寫輸入處理方法

這些範例示範如何覆寫 Cmdlet 內的輸入處理方法。 這些方法是用來執行下列作業：

- [BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法是用來執行一次性啟動作業，這是對 Cmdlet 所處理的所有物件有效的。 Windows PowerShell 執行時間只會呼叫這個方法一次。

- [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法是用來處理傳遞至指令程式的物件。 Windows PowerShell 執行時間會針對傳遞給 Cmdlet 的每個物件，呼叫這個方法。

- System.servicemodel[方法是](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)用來執行一次性的後置處理作業。 Windows PowerShell 執行時間只會呼叫這個方法一次。

## <a name="to-override-the-beginprocessing-method"></a>覆寫 BeginProcessing 方法

- 宣告[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法的受保護覆寫。

下列類別會列印範例訊息。 若要使用此類別，請變更 Cmdlet 屬性中的動詞和名詞、變更類別的名稱以反映新的動詞和名詞，然後將您需要的功能新增至[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)的覆寫。方法.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a>覆寫 ProcessRecord 方法

- 宣告[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的受保護覆寫。

下列類別會列印範例訊息。 若要使用這個類別，請變更 Cmdlet 屬性中的動詞和名詞、變更類別的名稱以反映新的動詞和名詞，然後將您需要的功能新增至[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的覆寫。

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a>若要覆寫 EndProcessing 方法

- 宣告[system.web](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法的受保護覆寫。

下列類別會列印範例。 若要使用這個類別，請變更 Cmdlet 屬性中的動詞和名詞、變更類別的名稱以反映新的動詞和名詞，然後將您需要的功能加入至[system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)的覆寫方法。

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a>另請參閱

[BeginProcessing 的管理元件](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.servicemodel. Cmdlet。](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[ProcessRecord 的管理元件](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
