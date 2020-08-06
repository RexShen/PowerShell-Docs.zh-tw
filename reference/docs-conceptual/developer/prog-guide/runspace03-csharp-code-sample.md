---
title: 'RunSpace03 (c # ) 程式碼範例 |Microsoft Docs'
ms.date: 09/13/2016
ms.openlocfilehash: df34652f60ed85b13739a04485cf6622cf924872
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784787"
---
# <a name="runspace03-c-code-sample"></a>RunSpace03 (C#) 程式碼範例

以下是主控台應用程式的 c # 原始程式碼，如「建立執行指定腳本的主控台應用程式」中所述。 這個範例會使用[Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)類別來執行腳本，藉由使用傳入腳本的進程名稱清單來抓取進程資訊。 它會示範如何將輸入物件傳遞至腳本，以及如何抓取錯誤物件以及輸出物件。

> [!NOTE]
> 您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載此範例的 c # 原始程式檔 (runspace03.cs) 。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs" range="11-88":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
