---
title: RunSpace03 （C#）程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 06b5a06ae20a4bbb2c58eaa1776700aa8f80555c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416058"
---
# <a name="runspace03-c-code-sample"></a>RunSpace03 (C#) 程式碼範例

以下是主控台C#應用程式的原始程式碼，如「建立執行指定腳本的主控台應用程式」中所述。 這個範例會使用[Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)類別來執行腳本，藉由使用傳入腳本的進程名稱清單來抓取進程資訊。 它會示範如何將輸入物件傳遞至腳本，以及如何抓取錯誤物件以及輸出物件。

> [!NOTE]
> 您可以使用適用C#于 Windows Vista 和 microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載此範例的原始程式檔（runspace03.cs）。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下載的來源檔案可在 **\<PowerShell 範例 >** 目錄中取得。

## <a name="code-sample"></a>範例程式碼

[!code-csharp[Runspace03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
