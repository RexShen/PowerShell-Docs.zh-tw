---
title: 正在建立空間 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0c27e2bf54e16a3bdc93c4b91629893bb1cc1e3e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779568"
---
# <a name="creating-runspaces"></a>建立 Runspace

「運行時」是主機應用程式所叫用之命令的作業環境。 此環境包含目前存在的命令和資料，以及目前適用的任何語言限制。

 主應用程式可以使用 Windows PowerShell 所提供的預設執行時間（包括所有可用的核心命令），或建立僅包含可用命令子集的自訂執行時間。 若要建立自訂的運行時，您可以建立[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件，並將它指派給您的運行空間。

## <a name="runspace-tasks"></a>運行空間工作

1. [建立 InitialSessionState](./creating-an-initialsessionstate.md)

2. [建立受限 Runspace](./creating-a-constrained-runspace.md)

3. [建立多個 Runspace](./creating-multiple-runspaces.md)

## <a name="see-also"></a>另請參閱
