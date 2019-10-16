---
title: AccessDbProviderSample04 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: ff43286bc90c1a4d2270be0ee03ca5910867cec2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366967"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDbProviderSample04 程式碼範例

下列程式碼示範如何執行[建立 Windows Powershell 容器提供者](./creating-a-windows-powershell-container-provider.md)中所述的 windows powershell 提供者。 此提供者適用于多層式資料存放區。 對於這種類型的資料存放區，存放區的最上層包含根專案，而每個後續層級稱為子專案的節點。 藉由允許使用者在這些子節點上工作，使用者可以透過資料存放區以階層方式進行互動。

## <a name="code-sample"></a>程式碼範例

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
