---
ms.date: 09/13/2016
ms.topic: reference
title: 撰寫自訂 Windows PowerShell 嵌入式管理單元
description: 撰寫自訂 Windows PowerShell 嵌入式管理單元
ms.openlocfilehash: e79c0c3db583fa0add9287745e97958a71360592
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659531"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>撰寫自訂 Windows PowerShell 嵌入式管理單元

此範例示範如何撰寫可註冊特定 Cmdlet 的 Windows PowerShell 嵌入式管理單元。

使用這種類型的嵌入式管理單元，您可以指定要註冊的 Cmdlet、提供者、類型或格式。 如需如何撰寫嵌入式管理單元以註冊元件中所有 Cmdlet 和提供者的詳細資訊，請參閱 [撰寫 Windows PowerShell 嵌入式管理](./writing-a-windows-powershell-snap-in.md)單元。

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>撰寫註冊特定 Cmdlet 的 Windows PowerShell 嵌入式管理單元。

1. 加入 RunInstallerAttribute 屬性。
2. 建立衍生自 [Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) 類別的公用類別。

   在此範例中，類別名稱為 "CustomPSSnapinTest"。

3. 新增嵌入式管理單元名稱的公用屬性 (所需的) 。 命名嵌入式管理單元時，請勿使用下列任何字元： `#` 、 `.` 、 `,` 、 `(` 、 `)` 、 `{` 、 `}` `[` `]` `&` `-` `/` `\` `$` `;` `:` `"` `'` `<` `>` `|` `?` `@` `` ` `` 、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `*`

   在此範例中，嵌入式管理單元的名稱為 "CustomPSSnapInTest"。

4. 為嵌入式管理單元的廠商新增公用屬性 (必要的) 。

   在此範例中，廠商為 "Microsoft"。

5. 為嵌入式管理單元的廠商資源新增公用屬性 (選擇性) 。

   在此範例中，廠商資源是「CustomPSSnapInTest，Microsoft」。

6. 新增嵌入式管理單元描述 (所需) 的公用屬性。

   在此範例中，描述為：「這是包含和 Cmdlet 的自訂 Windows PowerShell 嵌入式管理單元」 `Test-HelloWorld` `Test-CustomSnapinTest` 。

7. 為嵌入式管理單元的描述資源新增公用屬性 (選擇性) 。

   在此範例中，廠商資源是：

   > CustomPSSnapInTest，這是自訂的 Windows PowerShell 嵌入式管理單元，其中包含 Test-HelloWorld 和 Test-CustomSnapinTest Cmdlet」。

8. 使用 [Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) 類別，指定屬於自訂嵌入式管理單元的 Cmdlet (選用) ）。 此處新增的資訊包括 Cmdlet 的名稱、.NET 類型和 Cmdlet 說明文件名 (應) Cmdlet 說明檔名稱的格式 `name.dll-help.xml` 。

   此範例會新增 Test-HelloWorld 和 TestCustomSnapinTest Cmdlet。

9. 指定屬於自訂嵌入式管理單元的提供者 (選擇性) 。

   此範例不會指定任何提供者。

10. 指定屬於自訂嵌入式管理單元的類型 (選擇性) 。

    此範例不會指定任何類型。

11. 指定屬於自訂嵌入式管理單元的格式 (選擇性) 。

    此範例不會指定任何格式。

## <a name="example"></a>範例

此範例示範如何撰寫自訂 Windows PowerShell 嵌入式管理單元，可用來註冊 `Test-HelloWorld` 和 `Test-CustomSnapinTest` Cmdlet。 請注意，在此範例中，完整的元件可能包含其他不會由此嵌入式管理單元註冊的 Cmdlet 和提供者。

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

如需註冊嵌入式管理單元的詳細資訊，請參閱《 Windows PowerShell 程式設計[人員指南》](../prog-guide/windows-powershell-programmer-s-guide.md)中的[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))。

## <a name="see-also"></a>另請參閱

[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell 殼層 SDK](../windows-powershell-reference.md)
