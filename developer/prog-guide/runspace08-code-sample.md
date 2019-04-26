---
title: RunSpace08 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 1a09cfee3bb317de6c1ca4dde86a87d72a498e6e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081269"
---
# <a name="runspace08-code-sample"></a>RunSpace08 程式碼範例

以下是原始程式碼，Runspace08 範例中所述[建立主控台應用程式，將命令參數](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba)。 此範例應用程式建立 runspace，會建立管線，將兩個命令新增至管線，將兩個參數加入至第二個命令中，，然後執行管線。 新增至管線的命令都`Get-Process`和`Sort-Object`cmdlet。

## <a name="code-sample"></a>程式碼範例

[!code-csharp[Runspace08.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)