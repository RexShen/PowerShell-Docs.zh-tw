---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 參數類型
description: Cmdlet 參數類型
ms.openlocfilehash: 8daaa3c778396e06a826de3b93e0610c51160fb4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660485"
---
# <a name="types-of-cmdlet-parameters"></a>Cmdlet 參數類型

本主題說明您可以在 Cmdlet 中宣告的不同參數類型。 Cmdlet 參數可以是位置、命名、必要、選擇性或切換參數。

## <a name="positional-and-named-parameters"></a>位置和具名引數

所有 Cmdlet 參數都是命名或位置參數。 具名引數需要您在呼叫 Cmdlet 時輸入參數名稱和引數。 位置參數只需要您以相對順序輸入引數。 然後系統會將第一個未命名的引數對應到第一個位置參數。 系統會將第二個未命名的引數對應至第二個未命名的參數，依此類推。 根據預設，所有 Cmdlet 參數都是具名引數。

若要定義具名引數，請省略 `Position` **參數** 屬性宣告中的關鍵字，如下列參數宣告所示。

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

若要定義位置參數，請 `Position` 在參數屬性宣告中加入關鍵字，然後指定位置。 在下列範例中， `UserName` 會將參數宣告為位置0的位置參數。 這表示呼叫的第一個引數會自動系結至此參數。

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
> 良好的 Cmdlet 設計建議，最常使用的參數會宣告為位置參數，如此一來，當 Cmdlet 執行時，使用者就不需要輸入參數名稱。

位置和具名引數接受單一引數，或以逗號分隔的多個引數。 只有在參數接受集合（例如字串陣列）時，才允許使用多個引數。 您可以在相同的 Cmdlet 中混合位置和具名引數。 在此情況下，系統會先抓取指名的引數，然後嘗試將其餘未命名的引數對應到位置參數。

下列命令示範您可以針對 Cmdlet 的參數指定單一和多個引數的不同方式 `Get-Command` 。 請注意，在最後兩個範例中，不需要指定 **-name** ，因為 `Name` 參數定義為位置參數。

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>必要參數和選擇性參數

您也可以將 Cmdlet 參數定義為強制或選擇性參數。  (必須在 Windows PowerShell 執行時間叫用 Cmdlet 之前指定必要參數。 ) 預設會將參數定義為選擇性。

若要定義強制參數，請 `Mandatory` 在參數屬性宣告中加入關鍵字，並將其設定為 `true` ，如下列參數宣告所示。

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

若要定義選擇性參數，請省略 `Mandatory` **參數** 屬性宣告中的關鍵字，如下列參數宣告所示。

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

Windows PowerShell 會提供 [SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) 類型，可讓您定義參數，其值會在 `false` 呼叫 Cmdlet 時未指定參數時，自動設定為。 可能的話，請使用 switch 參數取代布林值參數。

請考慮下列範例。 根據預設，數個 Windows PowerShell Cmdlet 不會將輸出物件沿著管線向下傳遞。 不過，這些 Cmdlet 有一個 `PassThru` 切換參數，可覆寫預設行為。 如果在 `PassThru` 呼叫這些 Cmdlet 時指定參數，Cmdlet 會將輸出物件傳回至管線。

如果您在 `true` 呼叫中未指定參數時需要參數的預設值，請考慮反轉參數的意義。 如需範例，請將屬性宣告為 `true` [SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) 類型，然後將參數的預設值設定為，而不是將參數屬性設定為的布林 `false` 值。

若要定義切換參數，請將屬性宣告為 [SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) 類型，如下列範例所示。

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

若要讓 Cmdlet 在指定參數時採取動作，請在其中一個輸入處理方法內使用下列結構。

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
