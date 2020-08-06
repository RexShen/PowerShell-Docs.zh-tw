---
title: RunSpace09 程式碼範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: fc5d8d4d182cca6bfc42d63c68a14a7a5e5f9c97
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784668"
---
# <a name="runspace09-code-sample"></a>RunSpace09 程式碼範例

以下是[建立可非同步叫用管線之主控台應用程式](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47)中所述 Runspace09 範例的原始程式碼。
這個範例應用程式會建立並開啟一個運行時、建立和非同步叫用管線，然後使用管線事件以非同步方式處理腳本。 此應用程式所執行的腳本會在0.5 秒間隔內建立整數1到10， (500 ms) 。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs" range="11-113":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
