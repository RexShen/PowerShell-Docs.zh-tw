---
title: Cmdlet 參數的型別 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: 59921a92661482b8d518b82f490c9879643543bb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859864"
---
# <a name="types-of-cmdlet-parameters"></a>Cmdlet 參數類型

本主題說明不同類型的 cmdlet 中，您可以宣告的參數。 Cmdlet 參數可以是位置、 具名、 必要、 選擇性的或切換參數。

## <a name="positional-and-named-parameters"></a>位置和具名參數

所有的 cmdlet 參數是具名或位置參數。 具名的參數需要呼叫 cmdlet 時，您輸入的參數名稱和引數。 位置參數只要求您輸入的引數，以相對順序。 系統則會對應至第一個位置參數的第一個未命名的引數。 系統會將第二個未命名的引數對應到第二個未命名的參數，並依此類推。 根據預設，所有的 cmdlet 參數為具名參數。

若要定義具名的參數，請省略`Position`中的關鍵字**參數**屬性宣告，如下列的參數宣告中所示。

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

若要定義位置的參數，新增`Position`參數中的關鍵字屬性宣告，然後再指定 位置。 在下列範例中，`UserName`參數宣告為位置參數與位置 0。 這表示，呼叫的第一個引數會自動繫結至這個參數。

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> 良好的 cmdlet 的設計建議，最常用的參數可以宣告為位置參數，讓使用者沒有執行此 cmdlet 時輸入參數名稱。

位置和具名參數接受單一引數或以逗號分隔的多個引數。 只有當參數接受字串陣列，例如集合時，才允許多個引數。 您可能會混合在相同的 cmdlet 中的位置和具名參數。 在此情況下，系統第一，擷取具名引數，然後將對應的剩餘的嘗試未命名的位置參數的引數。

下列命令會顯示不同的方式，可以指定單一和多個引數的參數`Get-Command`cmdlet。 請注意，在最後兩個範例中， **-名稱**不需要指定因為`Name`參數會定義為位置參數。

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>必要和選擇性參數

您也可以定義為強制或選擇性參數的 cmdlet 參數。 （必要的參數必須指定之前，Windows PowerShell 執行階段會叫用此指令程式。）根據預設，參數會定義為選擇性。

若要定義必要的參數，請新增`Mandatory`參數中的關鍵字屬性宣告，並將它設定為`true`，如下列的參數宣告中所示。

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

若要定義的選擇性參數，請省略`Mandatory`中的關鍵字**參數**屬性宣告，如下列的參數宣告中所示。

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a>切換參數

Windows PowerShell 提供[System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)可讓您定義的參數值的型別會自動設為`false`如果 cmdlet 時未指定參數呼叫。 可能的話，使用切換參數來取代布林參數。

請考慮下列的範例。 根據預設，數個 Windows PowerShell cmdlet 不要傳遞到管線的輸出物件。 不過，這些 cmdlet 有`PassThru`切換參數會覆寫預設行為。 如果`PassThru`呼叫這些 cmdlet 時指定參數，此 cmdlet 會輸出物件傳回至管線。

如果您需要的參數具有預設值是`true`時呼叫中未指定參數，請考慮將反轉參數的意義。 如需範例，而不是設定參數屬性的布林值`true`，宣告為屬性[System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)輸入，並將參數的預設值`false`.

若要定義的切換參數，宣告將屬性視為[System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)類型，如下列範例所示。

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

若要讓參數在處理時有指定此 cmdlet，使用下列結構的輸入處理方法的其中一個內。

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
