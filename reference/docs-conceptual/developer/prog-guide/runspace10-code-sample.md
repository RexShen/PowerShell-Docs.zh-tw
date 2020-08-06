---
title: RunSpace10 程式碼範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 976df6c36a5f95d17a76dcd31d287a3f064eff24
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784651"
---
# <a name="runspace10-code-sample"></a>RunSpace10 程式碼範例

以下是 Runspace10 範例的原始程式碼。 這個範例應用程式會將 Cmdlet 新增至[Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) ，然後使用修改過的設定資訊來建立執行時間。

> [!NOTE]
> 您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Windows 軟體發展工具組， (runspace10.cs) 下載 c # 原始程式檔。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs" range="11-118":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
