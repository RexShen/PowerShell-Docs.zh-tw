---
title: GetProc03 （C#）範例程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 10c41ffd03e9adae82813bfe79d3e15030087953
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360337"
---
# <a name="getproc03-c-sample-code"></a>GetProc03 (C#) 範例程式碼

下列程式碼顯示可接受管線輸入的 @no__t 0 Cmdlet 的執行。 此實作為定義 `Name` 參數，可接受管線輸入、根據提供的名稱從本機電腦上抓取進程資訊，然後使用[WriteObject （system.object，system.string）](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)方法做為輸出將物件傳送至管線的機制。

> [!NOTE]
> 您可以使用適用C#于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載這個 getprov03.cs 的原始程式檔（）。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 下載的來源檔案可在 **@no__t 1PowerShell 範例 >** 目錄中取得。

## <a name="code-sample"></a>程式碼範例

[!code-csharp[GetProcessSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
