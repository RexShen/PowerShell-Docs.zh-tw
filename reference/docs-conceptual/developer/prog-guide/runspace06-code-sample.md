---
title: RunSpace06 程式碼範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8767ac8dc3a3d9253c2a53a4754d9bd54304abb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784719"
---
# <a name="runspace06-code-sample"></a>RunSpace06 程式碼範例

以下是[使用 Windows PowerShell 嵌入式管理單元設定運行](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83)時間中所述之 Runspace06 範例的原始程式碼。
這個範例應用程式會根據 Windows PowerShell 嵌入式管理單元建立執行時間，然後使用單一命令來執行管線。 若要這樣做，應用程式會建立運行時設定資訊、建立運行空間、使用單一命令建立管線，然後執行管線。

> [!NOTE]
> 您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Windows 軟體發展工具組， (runspace06.cs) 下載 c # 原始程式檔。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs" range="11-85":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
