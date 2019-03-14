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
ms.openlocfilehash: 7f8d25e03707052b1d5b62e245caae360da11d0b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794938"
---
# <a name="cmdlet-input-processing-methods"></a>Cmdlet 輸入處理方法

一或多個的輸入處理方法來執行其工作本主題中所述，必須覆寫 Cmdlet。 這些方法可讓 cmdlet 來執行前置處理作業、 輸入處理作業和後置處理作業。 這些方法也可讓您停止指令程式處理。

## <a name="pre-processing-tasks"></a>前置處理工作

指令程式應該覆寫[System.Management.Automation.Cmdlet.Beginprocessing%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)方法來加入有效的指令程式會稍後處理的所有記錄的任何前置處理作業。 當 Windows PowerShell 處理命令管線時，Windows PowerShell 呼叫這個方法一次的管線中的指令程式的每個執行個體。 如需有關 Windows PowerShell 如何叫用命令管道的詳細資訊，請參閱 < [Cmdlet 處理生命週期](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)。

下列程式碼示範如何實作[System.Management.Automation.Cmdlet.Beginprocessing%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)方法。

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

如需更詳細的如何使用範例[System.Management.Automation.Cmdlet.Beginprocessing%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)方法，請參閱 < [SelectStr 教學課程](./selectstr-tutorial.md)。 在本教學課程中，**選取 Str** cmdlet 會使用[System.Management.Automation.Cmdlet.Beginprocessing%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)方法產生的規則運算式，用來搜尋的輸入處理的記錄。

## <a name="input-processing-tasks"></a>輸入處理工作

Cmdlet 可以覆寫[System.Management.Automation.Cmdlet.Processrecord%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法來處理傳送至 cmdlet 的輸入。 當 Windows PowerShell 處理命令管線時，Windows PowerShell 就會呼叫這個方法的 cmdlet 所處理的每個輸入記錄。 如需有關 Windows PowerShell 如何叫用命令管道的詳細資訊，請參閱 < [Cmdlet 處理生命週期](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)。

下列程式碼示範如何實作[System.Management.Automation.Cmdlet.Processrecord%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法。

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

如需更詳細的如何使用範例[System.Management.Automation.Cmdlet.Processrecord%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法，請參閱 < [SelectStr 教學課程](./selectstr-tutorial.md)。

## <a name="post-processing-tasks"></a>後置處理工作

指令程式應該覆寫[System.Management.Automation.Cmdlet.Endprocessing%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)方法來加入有效的 cmdlet 所處理的所有記錄的任何後置處理作業。 例如，您的 cmdlet 可能要清除物件變數，在它完成之後處理。

當 Windows PowerShell 處理命令管線時，Windows PowerShell 呼叫這個方法一次的管線中的指令程式的每個執行個體。 不過，請務必記住，Windows PowerShell 執行階段不會呼叫[System.Management.Automation.Cmdlet.Endprocessing%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)如果 cmdlet 可透過其輸入的處理程序中途取消或終止錯誤發生在 cmdlet 的任何部分的方法。 基於這個理由，需要物件清除 cmdlet 應該實作完整[System.Idisposable](/dotnet/api/System.IDisposable)模式，包括完成項，可讓執行階段呼叫兩者[System.Management.Automation.Cmdlet.Endprocessing%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)並[System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose)結尾的處理方法。 如需有關 Windows PowerShell 如何叫用命令管道的詳細資訊，請參閱 < [Cmdlet 處理生命週期](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)。

下列程式碼示範如何實作[System.Management.Automation.Cmdlet.Processrecord%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法。

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

如需更詳細的如何使用範例[System.Management.Automation.Cmdlet.Processrecord%2A 嗎？Displayproperty = Fullname>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法，請參閱 < [SelectStr 教學課程](./selectstr-tutorial.md)。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[System.Idisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
