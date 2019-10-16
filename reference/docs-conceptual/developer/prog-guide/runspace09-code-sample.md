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
ms.openlocfilehash: 122a40dea93d874a7c131774e3d1abb148bcd4fc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360127"
---
# <a name="runspace09-code-sample"></a>RunSpace09 程式碼範例

以下是[建立可非同步叫用管線之主控台應用程式](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47)中所述 Runspace09 範例的原始程式碼。 這個範例應用程式會建立並開啟一個運行時、建立和非同步叫用管線，然後使用管線事件以非同步方式處理腳本。 此應用程式所執行的腳本會在0.5 秒的間隔（500毫秒）內建立整數1到10。

## <a name="code-sample"></a>程式碼範例

[!code-csharp[Runspace09.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
