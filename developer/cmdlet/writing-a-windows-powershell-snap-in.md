---
title: Windows PowerShell 嵌入式管理單元撰寫 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.assetid: 875024f4-e02b-4416-80b9-af5e5b50aad6
caps.latest.revision: 7
ms.openlocfilehash: 0c99f4bcfe5e2d34d31714dc85a53b5e8abe0925
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066952"
---
# <a name="writing-a-windows-powershell-snap-in"></a>撰寫 Windows PowerShell 嵌入式管理單元

此範例示範如何撰寫 Windows PowerShell 嵌入式管理單元，可用來註冊組件中的所有 cmdlet 和 Windows PowerShell 提供者。

使用此類型的嵌入式管理單元，您沒有選取的 cmdlet 與您想要註冊的提供者。 若要撰寫一個嵌入式管理單元，可讓您選取 註冊的項目，請參閱[撰寫自訂 Windows PowerShell 嵌入式管理單元](./writing-a-custom-windows-powershell-snap-in.md)。

### <a name="writing-a-windows-powershell-snap-in"></a>撰寫 Windows PowerShell 嵌入式管理單元

1. 新增 RunInstallerAttribute 屬性。

2. 建立公用類別衍生自[System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)類別。

    在此範例中，類別名稱會是"GetProcPSSnapIn01 」。

3. 新增公用屬性 （必要） 嵌入式管理單元的名稱。 在命名嵌入式管理單元時，請勿使用任何下列字元: #。 , ( ) { } [ ] & - /\ $ ; : " ' \< > ; ? @ ` *

    在此範例中，嵌入式管理單元的名稱會是"GetProcPSSnapIn01 」。

4. 新增嵌入式管理單元 （必要） 廠商的公用屬性。

    在此範例中，廠商會是 「 Microsoft 」。

5. 新增嵌入式管理單元 （選擇性） 廠商資源的公用屬性。

    在此範例中，廠商資源為 「 GetProcPSSnapIn01，Microsoft"。

6. 新增公用屬性 （必要） 嵌入式管理單元的描述。

    在此範例中，描述會是 「 這是一個 Windows PowerShell 嵌入式管理單元，註冊 get-proc cmdlet 」。

7. 新增嵌入式管理單元 （選擇性） 說明資源的公用屬性。

    在此範例中，廠商資源是 「 GetProcPSSnapIn01，這是一個 Windows PowerShell 嵌入式管理單元，註冊 get-proc cmdlet 」。

## <a name="example"></a>範例

此範例示範如何撰寫 Windows PowerShell 嵌入式管理單元，可用來註冊 Get-proc cmdlet 在 Windows PowerShell 介面中。 請注意，在此範例中，完整的組件會包含只有 GetProcPSSnapIn01 嵌入式管理單元類別和 Get-proc cmdlet 類別。

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

[如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
