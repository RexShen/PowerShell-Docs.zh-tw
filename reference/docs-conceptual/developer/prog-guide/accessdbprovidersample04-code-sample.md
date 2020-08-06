---
title: AccessDbProviderSample04 程式碼範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 05509c5b36475bcd3f91c9ab7413974994d668d6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787269"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDbProviderSample04 程式碼範例

下列程式碼示範如何執行[建立 Windows Powershell 容器提供者](./creating-a-windows-powershell-container-provider.md)中所述的 windows powershell 提供者。
此提供者適用于多層式資料存放區。 對於這種類型的資料存放區，存放區的最上層包含根專案，而每個後續層級稱為子專案的節點。 藉由允許使用者在這些子節點上工作，使用者可以透過資料存放區以階層方式進行互動。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
