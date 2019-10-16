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
ms.openlocfilehash: 4d50ef4dcd75d5c0ba802fbcfe2d7d1d7c954707
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364247"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>撰寫自訂 Windows PowerShell 嵌入式管理單元

這個範例示範如何撰寫 Windows PowerShell 嵌入式管理單元，以註冊特定 Cmdlet。

使用這種類型的嵌入式管理單元，您可以指定要註冊的 Cmdlet、提供者、類型或格式。 如需有關如何撰寫嵌入式管理單元，以在元件中註冊所有 Cmdlet 和提供者的詳細資訊，請參閱[撰寫 Windows PowerShell 嵌入式管理單元](./writing-a-windows-powershell-snap-in.md)。

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>撰寫可註冊特定 Cmdlet 的 Windows PowerShell 嵌入式管理單元。

1. 加入 RunInstallerAttribute 屬性。

2. 建立衍生自[Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)類別的公用類別。

   在此範例中，類別名稱為 "CustomPSSnapinTest"。

3. 新增嵌入式管理單元名稱的公用屬性（必要）。 命名嵌入式管理單元時，請勿使用下列任何字元： #。 、（） {} [] &-/\ $;： "' \< > &#124; ？ @ ` *

   在此範例中，嵌入式管理單元的名稱是 "CustomPSSnapInTest"。

4. 新增嵌入式管理單元之廠商的公用屬性（必要）。

   在此範例中，廠商是 "Microsoft"。

5. 新增嵌入式管理單元之廠商資源的公用屬性（選擇性）。

   在此範例中，廠商資源為 "CustomPSSnapInTest，Microsoft"。

6. 新增嵌入式管理單元描述的公用屬性（必要）。

   在此範例中，描述為：「這是自訂的 Windows PowerShell 嵌入式管理單元，其中包含 HelloWorld 和 CustomSnapinTest Cmdlet」。

7. 新增嵌入式管理單元的 [描述] 資源的公用屬性（選擇性）。

   在此範例中，廠商資源是 "CustomPSSnapInTest，這是一個自訂的 Windows PowerShell 嵌入式管理單元，其中包含 HelloWorld 和 CustomSnapinTest Cmdlet。

8. 使用[Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry)類別，指定屬於自訂嵌入式管理單元（選擇性）的指令程式。 此處新增的資訊包括 Cmdlet 的名稱、其 .NET 類型和 Cmdlet 說明檔名稱（Cmdlet 說明文件名的格式應為 dll-help .xml）。

   這個範例會新增 HelloWorld 和 TestCustomSnapinTest Cmdlet。

9. 指定屬於自訂嵌入式管理單元的提供者（選擇性）。

   這個範例不會指定任何提供者。

10. 指定屬於自訂嵌入式管理單元的類型（選擇性）。

    這個範例不會指定任何類型。

11. 指定屬於自訂嵌入式管理單元的格式（選擇性）。

    這個範例不會指定任何格式。

## <a name="example"></a>範例

這個範例示範如何撰寫自訂的 Windows PowerShell 嵌入式管理單元，可用來註冊 HelloWorld 和 CustomSnapinTest Cmdlet。 請注意，在此範例中，完整的元件可能包含不會由這個嵌入式管理單元註冊的其他 Cmdlet 和提供者。

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

如需註冊嵌入式管理單元的詳細資訊，請參閱《 [Windows PowerShell 程式設計人員指南》](../prog-guide/windows-powershell-programmer-s-guide.md)中的[如何註冊 Cmdlet、提供者和主機應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="see-also"></a>另請參閱

[如何註冊 Cmdlet、提供者和主機應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
