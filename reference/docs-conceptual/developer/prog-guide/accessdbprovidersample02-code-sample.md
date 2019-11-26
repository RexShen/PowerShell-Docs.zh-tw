---
title: AccessDbProviderSample02 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 33cdebd7f2f5ae21ec7aff559382362025d12e47
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416256"
---
# <a name="accessdbprovidersample02-code-sample"></a>AccessDbProviderSample02 程式碼範例

下列程式碼示範如何執行[建立 Windows Powershell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)中所述的 windows powershell 提供者。 此執行會建立路徑、連接到 Access 資料庫，然後移除磁片磁碟機。

> [!NOTE]
> 您可以使用適用C#于 Windows Vista 和 microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載此提供者的原始程式檔（AccessDBSampleProvider02.cs）。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
>
> 下載的來源檔案可在 **\<PowerShell 範例 >** 目錄中取得。
>
> 如需其他 Windows PowerShell 提供者執行的詳細資訊，請參閱[設計您的 Windows Powershell 提供者](./designing-your-windows-powershell-provider.md)。

## <a name="code-sample"></a>程式碼範例

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
