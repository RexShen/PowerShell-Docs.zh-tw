---
title: AccessDbProviderSample04 Code Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081949"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDbProviderSample04 程式碼範例

下列程式碼顯示中所述的 Windows PowerShell 提供者的實作[建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。 此提供者適用於多層資料存放區。 針對此類型的資料存放區中，存放區的最上層包含根項目，以及每個後續的層級指節點的子項目。 藉由讓使用者能夠在這些子節點上運作，使用者可以階層方式透過資料存放區互動。

## <a name="code-sample"></a>程式碼範例

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)