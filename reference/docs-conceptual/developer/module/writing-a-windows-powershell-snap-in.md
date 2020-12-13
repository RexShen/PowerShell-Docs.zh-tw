---
ms.date: 09/13/2016
ms.topic: reference
title: 撰寫 Windows PowerShell 嵌入式管理單元
description: 撰寫 Windows PowerShell 嵌入式管理單元
ms.openlocfilehash: f658c2fa1211bfb77d2e8edd3999ce7f92df13bb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659451"
---
# <a name="writing-a-windows-powershell-snap-in"></a>撰寫 Windows PowerShell 嵌入式管理單元

此範例示範如何撰寫 Windows PowerShell 的嵌入式管理單元，可用來註冊元件中的所有 Cmdlet 和 Windows PowerShell 提供者。

使用這種類型的嵌入式管理單元時，不會選取您要註冊的 Cmdlet 和提供者。 若要撰寫可讓您選取已註冊內容的嵌入式管理單元，請參閱 [撰寫自訂 Windows PowerShell 嵌入式管理單元](./writing-a-custom-windows-powershell-snap-in.md)。

### <a name="writing-a-windows-powershell-snap-in"></a>撰寫 Windows PowerShell 嵌入式管理單元

1. 加入 RunInstallerAttribute 屬性。

2. 建立衍生自 [PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) 類別的公用類別。

    在此範例中，類別名稱為 "GetProcPSSnapIn01"。

3. 新增嵌入式管理單元名稱的公用屬性 (所需的) 。 命名嵌入式管理單元時，請勿使用下列任何字元： `#` 、 `.` 、 `,` 、 `(` 、 `)` 、 `{` 、 `}` `[` `]` `&` `-` `/` `\` `$` `;` `:` `"` `'` `<` `>` `|` `?` `@` `` ` `` 、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `*`

    在此範例中，嵌入式管理單元的名稱為 "GetProcPSSnapIn01"。

4. 為嵌入式管理單元的廠商新增公用屬性 (必要的) 。

    在此範例中，廠商為 "Microsoft"。

5. 為嵌入式管理單元的廠商資源新增公用屬性 (選擇性) 。

    在此範例中，廠商資源是「GetProcPSSnapIn01，Microsoft」。

6. 新增嵌入式管理單元描述 (所需) 的公用屬性。

    在此範例中，描述為「這是註冊 proc Cmdlet 的 Windows PowerShell 嵌入式管理單元」。

7. 為嵌入式管理單元的描述資源新增公用屬性 (選擇性) 。

    在此範例中，廠商資源是「GetProcPSSnapIn01，這是註冊 proc Cmdlet 的 Windows PowerShell 嵌入式管理單元」。

## <a name="example"></a>範例

此範例示範如何撰寫 Windows PowerShell 的嵌入式管理單元，可用來在 Windows PowerShell shell 中註冊 Get-Proc Cmdlet。 請注意，在此範例中，完整的元件只會包含 GetProcPSSnapIn01 嵌入式管理單元類別和 `Get-Proc` Cmdlet 類別。

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

[Windows PowerShell 殼層 SDK](../windows-powershell-reference.md)
