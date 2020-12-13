---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace09 程式碼範例
description: RunSpace09 程式碼範例
ms.openlocfilehash: 52ebfa5dcfd6c12d2ded78a41a6090caa5087149
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654200"
---
# <a name="runspace09-code-sample"></a>RunSpace09 程式碼範例

以下是 [建立以非同步方式叫用管線的主控台應用程式](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47)中所述之 Runspace09 範例的原始程式碼。
這個範例應用程式會建立並開啟運行空間、建立和非同步叫用管線，然後使用管線事件以非同步方式處理腳本。 此應用程式所執行的腳本會在0.5 秒的間隔內建立整數1到10， (500 ms) 。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs" range="11-113":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
