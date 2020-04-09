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
ms.openlocfilehash: 60f0ed4e3d39ee93ab63023161d09a6c7b914798
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978571"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDbProviderSample04 程式碼範例

下列程式碼示範如何執行[建立 Windows Powershell 容器提供者](./creating-a-windows-powershell-container-provider.md)中所述的 windows powershell 提供者。
此提供者適用于多層式資料存放區。 對於這種類型的資料存放區，存放區的最上層包含根專案，而每個後續層級稱為子專案的節點。 藉由允許使用者在這些子節點上工作，使用者可以透過資料存放區以階層方式進行互動。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
