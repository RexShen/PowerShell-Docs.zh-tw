---
title: 建立 Runspace |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082935"
---
# <a name="creating-runspaces"></a>建立 Runspace

Runspace 都由主應用程式叫用命令的作業環境。 此環境包含命令和資料目前存在於，以及目前適用於任何語言限制。

 裝載應用程式可以使用預設 runspace 所提供的 Windows PowerShell 中，其中包含所有可用的核心命令，或建立自訂的 runspace，其中包含可用命令的子集。 若要建立自訂的 runspace，建立[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件，並將它指派給您的 runspace。

## <a name="runspace-tasks"></a>Runspace 工作

1. [建立 InitialSessionState](./creating-an-initialsessionstate.md)

2. [建立受限的 runspace](./creating-a-constrained-runspace.md)

3. [建立多個執行空間](./creating-multiple-runspaces.md)

## <a name="see-also"></a>另請參閱
