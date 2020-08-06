---
title: AccessDbProviderSample01 程式碼範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2e9f81b3011ea1b27bafd9e02ea7e0faf7903a62
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784821"
---
# <a name="accessdbprovidersample01-code-sample"></a>AccessDbProviderSample01 程式碼範例

下列程式碼示範如何執行[建立基本 Windows Powershell 提供者](./creating-a-basic-windows-powershell-provider.md)中所述的 Windows powershell 提供者。
此實作為提供啟動和停止提供者的方法，雖然它並未提供存取資料存放區或取得或設定資料存放區中資料的方式，但它確實提供了所有提供者所需的基本功能。

> [!NOTE]
> 您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Windows 軟體發展工具組，為此提供者下載 c # 原始程式檔 (AccessDBSampleProvider01.cs) 。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。 如需其他 Windows PowerShell 提供者執行的詳細資訊，請參閱[設計您的 Windows Powershell 提供者](./designing-your-windows-powershell-provider.md)。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
