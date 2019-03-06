---
title: GetProc03 (C#) 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 328f4eeea27243102679ab5d139181a878165ad6
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429749"
---
# <a name="getproc03-c-sample-code"></a>GetProc03 (C#) 範例程式碼

下列程式碼顯示實作`Get-Process`cmdlet 可接受管線輸入。 此實作會定義`Name`接受管線輸入參數會從本機電腦，根據提供的名稱，擷取程序資訊，然後使用[System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29)方法，將物件傳送至管線的輸出機制。

> [!NOTE]
> 您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件這個 Get-proc cmdlet 的原始程式檔 (getprov03.cs)。 如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。

## <a name="code-sample"></a>程式碼範例

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)