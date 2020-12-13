---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDbProviderSample04 程式碼範例
description: AccessDbProviderSample04 程式碼範例
ms.openlocfilehash: bb70ce9f1b1c94349c354a8771fedf7fcb1bb320
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647559"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDbProviderSample04 程式碼範例

下列程式碼顯示 [建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)時所述的 Windows PowerShell 提供者的執行。
此提供者適用于多層式資料存放區。 對於這種類型的資料存放區，存放區的最上層包含根專案，而且每個後續層級稱為子專案的節點。 藉由允許使用者在這些子節點上工作，使用者就可以透過資料存放區以階層方式進行互動。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
