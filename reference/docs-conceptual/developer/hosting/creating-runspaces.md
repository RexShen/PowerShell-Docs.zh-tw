---
ms.date: 09/13/2016
ms.topic: reference
title: 建立 Runspace
description: 建立 Runspace
ms.openlocfilehash: c6b2c577e435ec88364b189a0c3d065f54f02525
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649350"
---
# <a name="creating-runspaces"></a>建立 Runspace

運行空間是主機應用程式所叫用之命令的作業環境。 此環境包含目前存在的命令和資料，以及目前適用的任何語言限制。

 主機應用程式可以使用 Windows PowerShell 所提供的預設運行空間（其中包含所有可用的核心命令），或建立只包含可用命令子集的自訂執行空間。 若要建立自訂的運行時，請建立 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 物件，並將它指派給您的運行空間。

## <a name="runspace-tasks"></a>作業空間工作

1. [建立 InitialSessionState](./creating-an-initialsessionstate.md)

2. [建立受限 Runspace](./creating-a-constrained-runspace.md)

3. [建立多個 Runspace](./creating-multiple-runspaces.md)

## <a name="see-also"></a>另請參閱
