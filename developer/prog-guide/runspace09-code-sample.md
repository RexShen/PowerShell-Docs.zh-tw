---
title: RunSpace09 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: e21ef8685598db9a1ae0fcd86051386af526f2a5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854044"
---
# <a name="runspace09-code-sample"></a>RunSpace09 程式碼範例

以下是原始程式碼，Runspace09 範例中所述[建立主控台應用程式，會叫用管線以非同步方式](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47)。 此範例應用程式會建立並開啟 runspace、 建立以及以非同步方式叫用管線，並接著使用管線來以非同步方式處理指令碼的事件。 執行此應用程式指令碼會建立整數 1 到 10，每隔 0.5 秒 （500 毫秒）。

## <a name="code-sample"></a>程式碼範例

[!code-csharp[Runspace09.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)