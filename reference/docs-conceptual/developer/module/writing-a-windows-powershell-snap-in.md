---
title: 撰寫 Windows PowerShell 嵌入式管理單元 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.openlocfilehash: 02603c54fb9852a8b78ecf68e3ee387d1fd418fc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779098"
---
# <a name="writing-a-windows-powershell-snap-in"></a>撰寫 Windows PowerShell 嵌入式管理單元

這個範例示範如何撰寫 Windows PowerShell 嵌入式管理單元，可用來在元件中註冊所有的 Cmdlet 和 Windows PowerShell 提供者。

使用這種類型的嵌入式管理單元時，您不會選取要註冊的 Cmdlet 和提供者。 若要撰寫可讓您選取已註冊內容的嵌入式管理單元，請參閱[撰寫自訂的 Windows PowerShell 嵌入式管理單元](./writing-a-custom-windows-powershell-snap-in.md)。

### <a name="writing-a-windows-powershell-snap-in"></a>撰寫 Windows PowerShell 嵌入式管理單元

1. 加入 RunInstallerAttribute 屬性。

2. 建立衍生自[PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)類別的公用類別。

    在此範例中，類別名稱為 "GetProcPSSnapIn01"。

3. 新增 (所需的嵌入式管理單元名稱) 的公用屬性。 命名嵌入式管理單元時，請勿使用下列任何字元： `#` 、 `.` 、 `,` 、、 `(` `)` `{` `}` `[` `]` `&` `-` `/` `\` `$` `;` `:` `"` `'` `<` `>` `|` `?` `@` 、、、、 `` ` `` 、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、`*`

    在此範例中，嵌入式管理單元的名稱是 "GetProcPSSnapIn01"。

4. 新增嵌入式管理單元廠商的公用屬性， (所需的) 。

    在此範例中，廠商是 "Microsoft"。

5. 新增嵌入式管理單元之廠商資源的公用屬性 (選擇性) 。

    在此範例中，廠商資源為 "GetProcPSSnapIn01，Microsoft"。

6. 針對所需的嵌入式管理單元 (，新增 [公用] 屬性) 。

    在此範例中，描述是「這是註冊了 get proc Cmdlet 的 Windows PowerShell 嵌入式管理單元」。

7. 新增嵌入式管理單元之 [描述] 資源的 [公用] 屬性 (選擇性) 。

    在此範例中，廠商資源是 "GetProcPSSnapIn01，這是一個 Windows PowerShell 嵌入式管理單元，它會註冊「get-proc」 Cmdlet」。

## <a name="example"></a>範例

這個範例示範如何撰寫 Windows PowerShell 嵌入式管理單元，以在 Windows PowerShell shell 中用來註冊該程式。 請注意，在此範例中，完整的元件只會包含 GetProcPSSnapIn01 嵌入式管理單元類別和 `Get-Proc` Cmdlet 類別。

```csharp
[RunInstaller(true)]
public class GetProcPSSnapIn01 : PSSnapIn
{
  /// <summary>
  /// Create an instance of the GetProcPSSnapIn01 class.
  /// </summary>
  public GetProcPSSnapIn01()
         : base()
  {
  }

  /// <summary>
  /// Specify the name of the PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "GetProcPSSnapIn01";
    }
  }

  /// <summary>
  /// Specify the vendor for the PowerShell snap-in.
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
  /// Use the format: resourceBaseName,VendorName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
      return "GetProcPSSnapIn01,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
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
      return "GetProcPSSnapIn01,This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }
}
```

## <a name="see-also"></a>另請參閱

[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
