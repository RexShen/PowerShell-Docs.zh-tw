---
title: Windows PowerShell 參考-最新消息
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080521"
---
# <a name="whats-new"></a>新功能

Windows PowerShell 2.0 在撰寫 cmdlet、 提供者，以及裝載應用程式時，會提供使用的下列新功能。

## <a name="modules"></a>模組

您現在可以封裝，並使用模組來散發 Windows PowerShell 解決方案。 模組可讓您將資料分割、 組織和擷取成獨立、 可重複使用單位的 Windows PowerShell 程式碼。 如需有關模組的詳細資訊，請參閱 < 撰寫 Windows PowerShell 模組。

## <a name="the-powershell-class"></a>PowerShell 類別

PowerShell 類別會提供較簡單的解決方案，來建立應用程式，稱為主機應用程式，以程式設計方式執行命令。 這個類別可讓您建立的命令的管線，指定用來執行命令，runspace 並指定同步或非同步方式叫用命令。

## <a name="the-runspacepool-class"></a>RunspacePool 類別

Runspace 集區可讓您使用的單一呼叫中建立多個執行空間。 CreateRunspacePool 方法會提供可用來建立具有相同的功能，例如相同的主機、 初始工作階段狀態和連接資訊的 runspace 的數個多載。

## <a name="the-initialsessionstate-class"></a>InitialSessionState 類別

InitialSessionState 類別可讓您建立 runspace 開啟時，會使用工作階段狀態設定。 您可以建立自訂的組態、 包含 mshshort，所提供的命令的預設組態和設定其命令會限制根據工作階段的功能。

## <a name="remote-runspaces"></a>遠端 runspace

您現在可以建立 runspace 開啟遠端電腦上，可讓您在遠端電腦上執行命令，並收集在本機的結果。 若要建立遠端 runspace，，建立 runspace 時，必須指定遠端連線的相關資訊。 請參閱範例 CreateRunspace 和 CreateRunspacePool 方法。 RunspaceConnectionInfo 類別所定義的連接資訊。

## <a name="private-runspace-elements"></a>私用 runspace 項目

您現在可以建立其項目是公用或私人的 runspace。 這可讓您建立其項目可用來在 runspace，但不適用於使用者的 runspace。 若要了解 runspace 的哪些項目可以設定為私人 ConstrainedSessionStateEntry 類別，請參閱。

## <a name="runspace-threading-modes-and-apartment-state"></a>執行緒模式和 apartment 狀態的 Runspace

您現在可以指定如何建立及使用 runspace 中執行命令時執行緒。 請參閱 System.Management.Automation.Runspaces.Runspace.ThreadOptions 和 System.Management.Automation.Runspaces.RunspacePool.ThreadOptions 屬性。

您現在可以取得用來在 runspace 中執行命令的執行緒的 apartment 狀態。 請參閱 System.Management.Automation.Runspaces.Runspace.ApartmentState 和 System.Management.Automation.Runspaces.RunspacePool.ApartmentState 屬性。

## <a name="transaction-cmdlets"></a>交易 cmdlet

您現在可以建立可在交易內使用的 cmdlet。 在交易中使用 cmdlet 時，它的動作是暫時性的並可以接受或拒絕的 Windows PowerShell 所提供的交易 cmdlet。

如需有關交易的詳細資訊，請參閱如何支援交易。

## <a name="transaction-provider"></a>交易的提供者

您現在可以建立可在交易內使用的提供者。 類似於 cmdlet，在交易中使用的提供者時，它的動作是暫時性的並可以接受或拒絕的 Windows PowerShell 所提供的交易 cmdlet。

如需指定提供者類別中的交易支援的詳細資訊，請參閱 System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities 屬性。

## <a name="job-cmdlets"></a>工作 cmdlet

您現在可以撰寫可執行其動作，以工作的 cmdlet。 這些作業會在背景執行，而不與目前的工作階段互動。 如需有關 Windows PowerShell 如何支援工作的詳細資訊，請參閱背景工作。

## <a name="cmdlet-output-types"></a>Cmdlet 輸出類型

您現在可以指定您的 cmdlet 所傳回宣告 OutputType 屬性，撰寫您的 cmdlet 時.NET Framework 型別。 這可讓其他人決定藉由查看 cmdlet 的 OutputType 屬性由 cmdlet 傳回的物件類型。

## <a name="event-support"></a>事件支援

您現在可以撰寫 cmdlet 新增及耗用事件。 請參閱 PSEvent 類別。

## <a name="proxy-commands"></a>Proxy 命令

您現在可以撰寫 proxy 命令，可用來執行另一個命令。 Proxy 命令可讓您控制哪些功能來源指令程式可供使用者使用。 例如，您可以建立 proxy 命令，移除原始碼命令所提供的參數。 請參閱 ProxyCommand 類別。

## <a name="multiple-choice-prompts"></a>多個選項的提示

您現在可以撰寫應用程式，可允許使用者選取多個選項的提示。 請參閱 IHostUISupportsMultipleChoiceSelection 介面

## <a name="interactive-sessions"></a>互動式工作階段

您現在可以撰寫可以啟動和停止互動式工作階段的遠端電腦上的應用程式。
請參閱 IHostSupportsInteractiveSession 介面。

## <a name="custom-cmdlet-help-for-providers"></a>提供者的自訂 Cmdlet 說明

您現在可以建立自訂提供者 cmdlet 的說明主題。 自訂的 cmdlet 說明主題可闡述 cmdlet 中的提供者路徑和文件特殊功能，包括提供者新增到 cmdlet 的動態參數的運作方式。
