---
title: 正在建立空間 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367577"
---
# <a name="creating-runspaces"></a>建立 Runspace

「運行時」是主機應用程式所叫用之命令的作業環境。 此環境包含目前存在的命令和資料，以及目前適用的任何語言限制。

 主應用程式可以使用 Windows PowerShell 所提供的預設執行時間（包括所有可用的核心命令），或建立僅包含可用命令子集的自訂執行時間。 若要建立自訂的運行時，請建立[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件，並將它指派給您的運行空間。

## <a name="runspace-tasks"></a>運行空間工作

1. [建立 InitialSessionState](./creating-an-initialsessionstate.md)

2. [建立受條件約束的運行空間](./creating-a-constrained-runspace.md)

3. [建立多個空間](./creating-multiple-runspaces.md)

## <a name="see-also"></a>另請參閱
