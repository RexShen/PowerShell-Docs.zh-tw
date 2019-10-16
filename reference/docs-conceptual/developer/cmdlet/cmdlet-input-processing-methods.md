---
title: Cmdlet 輸入處理方法 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369867"
---
# <a name="cmdlet-input-processing-methods"></a>Cmdlet 輸入處理方法

Cmdlet 必須覆寫本主題中所述的一或多個輸入處理方法，才能執行其工作。
這些方法可讓 Cmdlet 執行前置處理、輸入處理和後置處理的作業。
這些方法也可讓您停止 Cmdlet 處理。
如需如何使用這些方法的更詳細範例，請參閱[SelectStr 教學](selectstr-tutorial.md)課程。

## <a name="pre-processing-operations"></a>前置處理作業

Cmdlet 應該覆寫[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法，以新增任何對稍後將由 Cmdlet 處理的所有記錄有效的前置處理作業。
當 PowerShell 處理命令管線時，PowerShell 會針對管線中的每個 Cmdlet 實例呼叫這個方法一次。
如需 PowerShell 如何叫用命令管線的詳細資訊，請參閱[Cmdlet 處理生命週期](/previous-versions/ms714429(v=vs.85))。

下列程式碼顯示 BeginProcessing 方法的執行。

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a>輸入處理作業

Cmdlet 可以覆寫[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，以處理傳送至指令程式的輸入。
當 PowerShell 處理命令管線時，PowerShell 會針對 Cmdlet 所處理的每個輸入記錄呼叫此方法。
如需 PowerShell 如何叫用命令管線的詳細資訊，請參閱[Cmdlet 處理生命週期](/previous-versions/ms714429(v=vs.85))。

下列程式碼顯示 ProcessRecord 方法的執行。

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a>後置處理作業

Cmdlet 應該覆寫[system.servicemodel 方法，](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)以新增對 Cmdlet 所處理之所有記錄有效的任何後置處理作業。
例如，您的 Cmdlet 可能必須在處理完成後清除物件變數。

當 PowerShell 處理命令管線時，PowerShell 會針對管線中的每個 Cmdlet 實例呼叫這個方法一次。
不過，請務必記住，如果 Cmdlet 在其輸入處理過程中取消，或 Cmdlet 的任何部分發生終止錯誤，則 PowerShell 執行時間不會呼叫 EndProcessing 方法。
基於這個理由，需要物件清理的 Cmdlet 應該會執行完整的[IDisposable](/dotnet/api/System.IDisposable)模式，包括完成項，讓執行時間可以在結尾處呼叫 EndProcessing 和 IDisposable 方法[。](/dotnet/api/System.IDisposable.Dispose)流程.
如需 PowerShell 如何叫用命令管線的詳細資訊，請參閱[Cmdlet 處理生命週期](/previous-versions/ms714429(v=vs.85))。

下列程式碼顯示 EndProcessing 方法的執行。

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a>另請參閱

[BeginProcessing 的管理元件](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[ProcessRecord 的管理元件](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.servicemodel. Cmdlet。](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[SelectStr 教學課程](selectstr-tutorial.md)

[IDisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
