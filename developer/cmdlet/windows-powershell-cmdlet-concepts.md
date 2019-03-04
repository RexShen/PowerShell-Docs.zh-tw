---
title: Windows PowerShell Cmdlet 概念 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855784"
---
# <a name="windows-powershell-cmdlet-concepts"></a>Windows PowerShell Cmdlet 概念

本章節描述 cmdlet 的運作方式。

## <a name="in-this-section"></a>在本節中

本節包含下列主題。

[Cmdlet 開發指導方針](./cmdlet-development-guidelines.md)本主題提供可用來產生格式正確的指令程式的開發指導方針。

[Cmdlet 類別宣告](./cmdlet-class-declaration.md)本主題說明 cmdlet 類別宣告。

[核准 Windows PowerShell 命令的指令動詞](./approved-verbs-for-windows-powershell-commands.md)本主題列出當您宣告 cmdlet 類別時，您可以使用的預先定義的 cmdlet 動詞命令。

[Cmdlet 的輸入處理方法](./cmdlet-input-processing-methods.md)本主題說明的方法，可讓 cmdlet 來執行前置處理的作業、 輸入處理作業，以及張貼處理作業。

[Cmdlet 參數](./cmdlet-parameters.md)本章節描述您可以將它新增至 cmdlet 的參數不同型別。

[Cmdlet 屬性](./cmdlet-attributes.md)本章節描述用來將.NET Framework 類別宣告為 cmdlet，宣告為 cmdlet 參數的欄位，並宣告參數的輸入的驗證規則的屬性。

[Cmdlet 別名](./cmdlet-aliases.md)本主題描述 cmdlet 的別名。

[Cmdlet 輸出](./cmdlet-output.md)本章節描述的指令程式可傳回的輸出，以及如何定義，並顯示由 cmdlet 所傳回的物件類型。

[註冊 Cmdlet](./modules-and-snap-ins.md)本章節描述如何使用模組和嵌入式管理單元來註冊 cmdlet。

[要求確認](./requesting-confirmation-from-cmdlets.md)本章節描述如何 cmdlet 確認向使用者要求它們對系統進行變更之前。

[Windows PowerShell 錯誤報告](./error-reporting-concepts.md)本章節描述如何 cmdlet 會將報告的終止錯誤和非終止錯誤，並說明如何解譯錯誤記錄。

[背景工作](./background-jobs.md)本主題描述如何 cmdlet 可以執行其工作內不會干擾目前的工作階段中執行的命令的背景工作。

[叫用 Cmdlet 與 Cmdlet 中的指令碼](./invoking-cmdlets-and-scripts-within-a-cmdlet.md)本主題描述如何 cmdlet 可以叫用其他 cmdlet 和指令碼，從其輸入處理方法。

[Cmdlet 會設定](./cmdlet-sets.md)本主題描述如何使用基底類別來建立 cmdlet 的集合。

[Windows PowerShell 工作階段狀態](./windows-powershell-session-state.md)本主題描述 Windows PowerShell 工作階段狀態。
