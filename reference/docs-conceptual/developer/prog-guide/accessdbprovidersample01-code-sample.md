---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDbProviderSample01 程式碼範例
description: AccessDbProviderSample01 程式碼範例
ms.openlocfilehash: 5be593b9e86347b2f55de156fe4d9b44cfab5b78
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659406"
---
# <a name="accessdbprovidersample01-code-sample"></a>AccessDbProviderSample01 程式碼範例

下列程式碼顯示 [建立基本 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)中所述之 Windows PowerShell 提供者的執行。
這項實行提供啟動和停止提供者的方法，雖然它不提供存取資料存放區的方法，或是在資料存放區中取得或設定資料，但它確實提供了所有提供者所需的基本功能。

> [!NOTE]
> 您可以使用 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Windows 軟體開發套件，下載此提供者 (AccessDBSampleProvider01.cs) 的 c # 原始程式檔。 如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。 如需其他 Windows PowerShell 提供者實現的詳細資訊，請參閱 [設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
