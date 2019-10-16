---
title: Cmdlet 參數的類型 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369307"
---
# <a name="types-of-cmdlet-parameters"></a>Cmdlet 參數類型

本主題說明您可以在 Cmdlet 中宣告的不同參數類型。 Cmdlet 參數可以是位置、命名、必要、選擇性或切換參數。

## <a name="positional-and-named-parameters"></a>位置和具名引數

所有 Cmdlet 參數都是命名或位置參數。 呼叫 Cmdlet 時，會要求您輸入參數名稱和引數。 位置參數只需要您以相對順序輸入引數。 然後，系統會將第一個未命名的引數對應到第一個位置參數。 系統會將第二個未命名的引數對應到第二個未命名的參數，依此類推。 根據預設，所有 Cmdlet 參數都會命名為參數。

若要定義名為的參數，請省略**參數**屬性宣告中的 `Position` 關鍵字，如下列參數宣告所示。

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

若要定義位置參數，請在參數屬性宣告中加入 `Position` 關鍵字，然後指定位置。 在下列範例中，`UserName` 參數會宣告為位置參數，其位置為0。 這表示呼叫的第一個引數會自動系結至此參數。

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
> 良好的 Cmdlet 設計建議將最常使用的參數宣告為位置參數，如此一來，當 Cmdlet 執行時，使用者就不需要輸入參數名稱。

位置和具名引數接受單一引數或以逗號分隔的多個引數。 只有當參數接受集合（例如字串陣列）時，才允許使用多個引數。 您可以在相同的 Cmdlet 中混合位置和具名引數。 在此情況下，系統會先抓取具名引數，然後再嘗試將其餘未命名的引數對應到位置參數。

下列命令會顯示您可以為 `Get-Command` Cmdlet 的參數指定單一和多個引數的不同方式。 請注意，在最後兩個範例中，不需要指定 **-name** ，因為 `Name` 參數定義為位置參數。

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>必要和選擇性參數

您也可以將 Cmdlet 參數定義為強制或選擇性參數。 （必須先指定必要參數，Windows PowerShell 執行時間才會叫用 Cmdlet）。 根據預設，參數會定義為選擇性。

若要定義強制參數，請在參數屬性宣告中加入 `Mandatory` 關鍵字，並將它設定為 `true`，如下列參數宣告所示。

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

若要定義選擇性參數，請省略**參數**屬性宣告中的 `Mandatory` 關鍵字，如下列參數宣告所示。

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

Windows PowerShell 提供[SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)類型，可讓您定義參數，如果呼叫 Cmdlet 時未指定參數，其值會自動設定為 `false`。 盡可能使用切換參數來取代布林值參數。

請考慮下列範例。 根據預設，數個 Windows PowerShell Cmdlet 不會將輸出物件沿著管線向下傳遞。 不過，這些 Cmdlet 具有 @no__t 0 切換參數，會覆寫預設行為。 如果在呼叫這些 Cmdlet 時指定了 `PassThru` 參數，Cmdlet 會將輸出物件傳回至管線。

當呼叫中未指定參數時，如果您需要參數的預設值為 `true`，請考慮反轉參數的意義。 如需範例，請將屬性宣告為[SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)類型，然後將參數的預設值設定為 `false`，而不是將參數屬性設定為的布林值 `true`。

若要定義切換參數，請將屬性宣告為[SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)類型，如下列範例所示。

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

若要讓 Cmdlet 在指定時對參數採取動作，請在其中一個輸入處理方法內使用下列結構。

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
