---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace08 程式碼範例
description: RunSpace08 程式碼範例
ms.openlocfilehash: f8d08e5b6bbd98d0901abe5b05c8b9ee682b8e04
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654230"
---
# <a name="runspace08-code-sample"></a>RunSpace08 程式碼範例

以下是 [建立將參數新增至命令的主控台應用程式](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba)中所述之 Runspace08 範例的原始程式碼。
這個範例應用程式會建立一個運行空間、建立管線、將兩個命令新增至管線、將兩個參數新增至第二個命令，然後執行管線。 新增至管線的命令為 `Get-Process` 和 `Sort-Object` Cmdlet。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs" range="11-86":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
