---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 參考-新功能
description: Windows PowerShell 參考-新功能
ms.openlocfilehash: b6fa97eacd476f055dd0c69eed2e547c450b85e1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647121"
---
# <a name="whats-new"></a>新功能

Windows PowerShell 2.0 提供下列新功能，可在撰寫 Cmdlet、提供者和主機應用程式時使用。

## <a name="modules"></a>單元

您現在可以使用模組封裝和散發 Windows PowerShell 的解決方案。 模組可讓您分割、組織及抽象化 Windows PowerShell 程式碼，使其成為獨立、可重複使用的單位。 如需模組的詳細資訊，請參閱撰寫 Windows PowerShell 模組。

## <a name="the-powershell-class"></a>PowerShell 類別

PowerShell 類別提供更簡單的解決方案，可讓您以程式設計方式執行命令來建立應用程式，稱為主機應用程式。 這個類別可讓您建立命令的管線、指定用來執行命令的運行時，以及指定以同步或非同步方式叫用命令。

## <a name="the-runspacepool-class"></a>RunspacePool 類別

運行空間集區可讓您使用單一呼叫來建立多個運行空間。 CreateRunspacePool 方法提供數個多載，可用來建立具有相同功能的多載，例如相同的主機、初始會話狀態和連接資訊。

## <a name="the-initialsessionstate-class"></a>>initialsessionstate 類別

>initialsessionstate 類別可讓您建立在開啟配置空間時使用的會話狀態設定。 您可以建立自訂設定，這是預設設定，其中包含 mshshort 所提供的命令，以及根據會話的功能限制其命令的設定。

## <a name="remote-runspaces"></a>遠端空間

您現在可以建立可在遠端電腦上開啟的執行程式，可讓您在遠端電腦上執行命令，並在本機收集結果。 若要建立遠端執行時間，您必須在建立執行時間時指定遠端連線的相關資訊。 如需範例，請參閱 CreateRunspace 和 CreateRunspacePool 方法。 連接資訊是由 RunspaceConnectionInfo 類別定義。

## <a name="private-runspace-elements"></a>私用空間元素

您現在可以建立其元素為公用或私用的空間。 這可讓您建立可供運行空間使用但無法供使用者使用的工作空間。 請參閱 ConstrainedSessionStateEntry 類別，找出可讓運行時的哪些元素成為私用。

## <a name="runspace-threading-modes-and-apartment-state"></a>運行時執行緒模式和單元狀態

您現在可以指定在執行時間中執行命令時，如何建立及使用執行緒。 請參閱 ThreadOptions 和 RunspacePool. ThreadOptions 屬性（此為內容）的內容（）。

您現在可以取得在執行空間中用來執行命令之執行緒的單元狀態。 請參閱 System.threading.thread.apartmentstate 和 RunspacePool. System.threading.thread.apartmentstate 屬性（此為內容）的內容（）。

## <a name="transaction-cmdlets"></a>Transaction Cmdlet

您現在可以建立可在交易內使用的 Cmdlet。 在交易中使用 Cmdlet 時，其動作是暫時性的，而且 Windows PowerShell 所提供的交易 Cmdlet 可以接受或拒絕。

如需交易的詳細資訊，請參閱如何支援交易。

## <a name="transaction-provider"></a>交易提供者

您現在可以建立可在交易內使用的提供者。 類似于 Cmdlet，在交易中使用提供者時，它的動作是暫時性的，而且 Windows PowerShell 提供的交易 Cmdlet 可以接受或拒絕。

如需有關在提供者類別內指定交易支援的詳細資訊，請參閱 CmdletProviderAttribute ProviderCapabilities 屬性。

## <a name="job-cmdlets"></a>作業 Cmdlet

您現在可以撰寫可執行其動作做為作業的 Cmdlet。 這些作業會在背景中執行，而不會與目前的會話互動。 如需 Windows PowerShell 如何支援工作的詳細資訊，請參閱背景工作。

## <a name="cmdlet-output-types"></a>Cmdlet 輸出類型

您現在可以在撰寫 Cmdlet 時宣告 OutputType 屬性，藉以指定 Cmdlet 所傳回的 .NET Framework 類型。 這可讓其他人藉由查看 Cmdlet 的 OutputType 屬性來判斷 Cmdlet 所傳回的物件類型。

## <a name="event-support"></a>事件支援

您現在可以撰寫新增和取用事件的 Cmdlet。 請參閱 PSEvent 類別。

## <a name="proxy-commands"></a>Proxy 命令

您現在可以撰寫可用於執行另一個命令的 proxy 命令。 Proxy 命令可讓您控制使用者可以使用的來源 Cmdlet 功能。 例如，您可以建立 proxy 命令來移除 source 命令所提供的參數。 請參閱 ProxyCommand 類別。

## <a name="multiple-choice-prompts"></a>多個選擇提示

您現在可以撰寫可提供提示的應用程式，讓使用者選取多個選項。 查看 IHostUISupportsMultipleChoiceSelection 介面

## <a name="interactive-sessions"></a>互動式會話

您現在可以撰寫應用程式，在遠端電腦上啟動及停止互動式會話。
請參閱 IHostSupportsInteractiveSession 介面。

## <a name="custom-cmdlet-help-for-providers"></a>提供者的自訂 Cmdlet 說明

您現在可以建立提供者 Cmdlet 的自訂說明主題。 自訂的 Cmdlet 說明主題可解釋 Cmdlet 在提供者路徑中的運作方式，以及檔特殊功能，包括提供者新增至 Cmdlet 的動態參數。
