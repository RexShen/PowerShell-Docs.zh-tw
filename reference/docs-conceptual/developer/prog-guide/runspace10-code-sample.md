---
title: RunSpace10 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5337dc40-c56e-458b-aedc-5f5d401dfd28
caps.latest.revision: 6
ms.openlocfilehash: da8455a72f6a50b8ab17650541cde8cc9c98a8fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366467"
---
# <a name="runspace10-code-sample"></a>RunSpace10 程式碼範例

以下是 Runspace10 範例的原始程式碼。 這個範例應用程式會將 Cmdlet 新增至[Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) ，然後使用修改過的設定資訊來建立執行時間。

> [!NOTE]
> 您可以使用適用C#于 windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Windows 軟體發展工具組，下載原始程式檔（runspace10.cs）。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 下載的來源檔案可在 **@no__t 1PowerShell 範例 >** 目錄中取得。

## <a name="code-sample"></a>程式碼範例

[!code-csharp[Runspace10.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs#L11-L118 "Runspace10.cs")]

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
