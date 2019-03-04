---
title: 撰寫自訂的 Windows PowerShell 嵌入式管理單元 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], custom PSSnapin example
- cmdlets [PowerShell SDK], specified in snap-ins
ms.assetid: 55c8b5cb-8ee2-4080-afc4-3f09c9f20128
caps.latest.revision: 6
ms.openlocfilehash: 20b7fdce1d31e3dee4598a7595962fca1c99d80a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863344"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>撰寫自訂 Windows PowerShell 嵌入式管理單元

此範例示範如何撰寫 Windows PowerShell 嵌入式管理單元來註冊特定的 cmdlet。

使用此類型的嵌入式管理單元，您可以指定哪些 cmdlet、 提供者、 類型或格式註冊。 如需如何撰寫嵌入式管理單元來註冊組件中的所有 cmdlet 和提供者的詳細資訊，請參閱[撰寫 Windows PowerShell 嵌入式管理單元](./writing-a-windows-powershell-snap-in.md)。

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>若要撰寫 Windows PowerShell 嵌入式管理單元，它會註冊特定的 cmdlet。

1. 新增 RunInstallerAttribute 屬性。

2. 建立公用類別衍生自[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)類別。

   在此範例中，類別名稱會是"CustomPSSnapinTest 」。

3. 新增公用屬性 （必要） 嵌入式管理單元的名稱。 在命名嵌入式管理單元時，請勿使用任何下列字元: #。 , ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ? @ ` *

   在此範例中，嵌入式管理單元的名稱會是"CustomPSSnapInTest 」。

4. 新增嵌入式管理單元 （必要） 廠商的公用屬性。

   在此範例中，廠商會是 「 Microsoft 」。

5. 新增嵌入式管理單元 （選擇性） 廠商資源的公用屬性。

   在此範例中，廠商資源為 「 CustomPSSnapInTest，Microsoft"。

6. 新增公用屬性 （必要） 嵌入式管理單元的描述。

   在此範例中，描述是：「 這是自訂 Windows PowerShell 嵌入式管理單元，其中包含測試 HelloWorld 和測試 CustomSnapinTest 指令程式。 」

7. 新增嵌入式管理單元 （選擇性） 說明資源的公用屬性。

   在此範例中，廠商資源是 「 CustomPSSnapInTest，這是一個自訂 Windows PowerShell 嵌入式管理單元，包含測試 HelloWorld 和測試 CustomSnapinTest cmdlet 」。

8. 指定屬於自訂嵌入式管理單元 （選擇性） 使用的 cmdlet [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry)類別。 在此處加入的資訊包括 cmdlet、 其.NET 型別，以及 （cmdlet 的說明檔名稱的格式應為 name.dll help.xml） 的 cmdlet 說明檔名稱的名稱。

   此範例會將測試 HelloWorld 和 TestCustomSnapinTest cmdlet。

9. 請指定隸屬於自訂 嵌入式管理單元 （選擇性） 提供者。

   此範例中未指定任何提供者。

10. 指定的類型，隸屬於自訂 嵌入式管理單元 （選擇性）。

    此範例中未指定任何類型。

11. 請指定隸屬於自訂 嵌入式管理單元 （選擇性） 的格式。

    此範例中未指定任何格式。

## <a name="example"></a>範例

此範例示範如何撰寫自訂 Windows PowerShell 嵌入式管理單元，可用來註冊測試 HelloWorld 和測試 CustomSnapinTest cmdlet。 請注意，在此範例中，完整的組件可能包含其他的 cmdlet 和提供者不會註冊由這個嵌入式管理單元。

```csharp
[RunInstaller(true)]
public class CustomPSSnapinTest : CustomPSSnapIn
{
  /// <summary>
  /// Creates an instance of CustomPSSnapInTest class.
  /// </summary>
  public CustomPSSnapinTest()
          : base()
  {
  }

  /// <summary>
  /// Specify the name of the custom PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "CustomPSSnapInTest";
    }
  }

  /// <summary>
  /// Specify the vendor for the custom PowerShell snap-in.
  /// </summary>
  public override string Vendor
  {
    get
    {
      return "Microsoft";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the vendor.
  /// Use the format: resourceBaseName,resourceName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
        return "CustomPSSnapInTest,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the custom PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the description.
  /// Use the format: resourceBaseName,Description.
  /// </summary>
  public override string DescriptionResource
  {
    get
    {
        return "CustomPSSnapInTest,This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
    }
  }

  /// <summary>
  /// Specify the cmdlets that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<CmdletConfigurationEntry> _cmdlets;
  public override Collection<CmdletConfigurationEntry> Cmdlets
  {
    get
    {
      if (_cmdlets == null)
      {
        _cmdlets = new Collection<CmdletConfigurationEntry>();
        _cmdlets.Add(new CmdletConfigurationEntry("test-customsnapintest", typeof(TestCustomSnapinTest), "TestCmdletHelp.dll-help.xml"));
        _cmdlets.Add(new CmdletConfigurationEntry("test-helloworld", typeof(TestHelloWorld), "HelloWorldHelp.dll-help.xml"));
      }

      return _cmdlets;
    }
  }

  /// <summary>
  /// Specify the providers that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<ProviderConfigurationEntry> _providers;
  public override Collection<ProviderConfigurationEntry> Providers
  {
    get
    {
      if (_providers == null)
      {
        _providers = new Collection<ProviderConfigurationEntry>();
      }

      return _providers;
    }
  }

  /// <summary>
  /// Specify the types that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<TypeConfigurationEntry> _types;
  public override Collection<TypeConfigurationEntry> Types
  {
    get
    {
      if (_types == null)
      {
        _types = new Collection<TypeConfigurationEntry>();
      }

      return _types;
    }
  }

  /// <summary>
  /// Specify the formats that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<FormatConfigurationEntry> _formats;
  public override Collection<FormatConfigurationEntry> Formats
  {
    get
    {
      if (_formats == null)
      {
        _formats = new Collection<FormatConfigurationEntry>();
      }

      return _formats;
    }
  }
}
```

如需有關如何註冊的嵌入式管理單元的詳細資訊，請參閱[如何註冊 Cmdlet、 提供者，以及裝載應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)中[Windows PowerShell 程式設計人員手冊](../prog-guide/windows-powershell-programmer-s-guide.md)。

## <a name="see-also"></a>另請參閱

[如何註冊 Cmdlet、 提供者，以及裝載應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[如何註冊 Cmdlet、 提供者，以及裝載應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
