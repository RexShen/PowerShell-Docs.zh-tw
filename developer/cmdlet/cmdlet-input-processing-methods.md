---
title: Cmdlet 的輸入處理方法 |Microsoft Docs
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
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670315"
---
# <a name="cmdlet-input-processing-methods"></a>Cmdlet 輸入處理方法

一或多個的輸入處理方法來執行其工作本主題中所述，必須覆寫 Cmdlet。
這些方法可讓 cmdlet 來執行前置處理、 輸入的處理和後處理作業。
這些方法也可讓您停止指令程式處理。
如何使用這些方法的詳細範例，請參閱[SelectStr 教學課程](selectstr-tutorial.md)。

## <a name="pre-processing-operations"></a>前置處理的作業

指令程式應該覆寫[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法來加入有效的指令程式會稍後處理的所有記錄的任何前置處理作業。
當 PowerShell 處理命令管線時，PowerShell 呼叫這個方法一次的管線中的指令程式的每個執行個體。
如需有關如何 PowerShell 叫用命令管道的詳細資訊，請參閱[Cmdlet 處理生命週期](/previous-versions/ms714429(v=vs.85))。

下列程式碼顯示 BeginProcessing 方法的實作。

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a>處理作業的輸入

Cmdlet 可以覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法來處理傳送至 cmdlet 的輸入。
當 PowerShell 處理命令管線時，PowerShell 會呼叫這個方法的 cmdlet 所處理的每個輸入記錄。
如需有關如何 PowerShell 叫用命令管道的詳細資訊，請參閱[Cmdlet 處理生命週期](/previous-versions/ms714429(v=vs.85))。

下列程式碼顯示 ProcessRecord 方法的實作。

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a>後置處理作業

指令程式應該覆寫[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法來加入有效的 cmdlet 所處理的所有記錄的任何後置處理作業。
例如，您的 cmdlet 可能要清除物件變數，在它完成之後處理。

當 PowerShell 處理命令管線時，PowerShell 呼叫這個方法一次的管線中的指令程式的每個執行個體。
不過，務必記得 PowerShell 執行階段將無法呼叫 EndProcessing 方法如果 cmdlet 可透過其輸入的處理程序中途取消或終止錯誤，就會發生此指令程式的任何部分。
基於這個理由，需要物件清除 cmdlet 應該實作完整[System.IDisposable](/dotnet/api/System.IDisposable)模式，包括完成項，可讓執行階段呼叫這兩個 EndProcessing 和[System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose)結尾的處理方法。
如需有關如何 PowerShell 叫用命令管道的詳細資訊，請參閱[Cmdlet 處理生命週期](/previous-versions/ms714429(v=vs.85))。

下列程式碼顯示 EndProcessing 方法的實作。

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[SelectStr 教學課程](selectstr-tutorial.md)

[System.IDisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
