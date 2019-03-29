---
title: 如何建立 Windows PowerShell 提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.assetid: 863e48e9-7206-4c6a-a59a-2ab2d30396bc
caps.latest.revision: 5
ms.openlocfilehash: 06910f32752668f13400f9be0767a2179133df04
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623818"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>如何建立 Windows PowerShell 提供者

本節說明如何建置 Windows PowerShell 提供者。 Windows PowerShell 提供者可以視為兩種方式。 給使用者，提供者會代表一組預存的資料。 例如，儲存的資料可以是 Internet Information Services (IIS) Metabase、 Microsoft Windows 登錄、 Windows 檔案系統、 Active Directory 和 Windows PowerShell 所儲存的變數和別名資料。

開發人員，Windows PowerShell 提供者會為使用者和使用者需要存取的資料之間的介面。 從這個觀點來看，這一節所述的提供者的每個類型支援一組特定的基底類別和介面，允許 Windows PowerShell 執行階段公開給使用者的特定 cmdlet 的常見方式。

## <a name="providers-provided-by-windows-powershell"></a>Windows PowerShell 所提供的提供者

Windows PowerShell 提供數個提供者 （例如，FileSystem 提供者、 登錄提供者，以及別名提供者），用來存取已知的資料存放區。 如需有關 Windows PowerShell 所提供的提供者的詳細資訊，請使用下列命令來存取線上說明：

**PS > 取得說明 about_providers**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>存取儲存的資料，使用 Windows PowerShell 路徑

Windows PowerShell 提供者會存取 Windows PowerShell 執行階段，並以程式設計方式透過 Windows PowerShell 路徑使用的命令。 大部分的情況下，這些路徑可直接透過提供者存取資料。 不過，某些路徑是可解析成提供者內部的路徑，讓可使用非 Windows PowerShell 應用程式開發介面 (Api) 來存取資料的 cmdlet。 如需有關 Windows PowerShell 提供者在 Windows PowerShell 的運作方式的詳細資訊，請參閱 < [Windows PowerShell 的運作方式](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)。

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>公開提供者 Cmdlet 使用 Windows PowerShell 磁碟機

Windows PowerShell 提供者會公開其支援使用虛擬 Windows PowerShell 磁碟機的 cmdlet。 Windows PowerShell 適用的 Windows PowerShell 磁碟機的下列規則：

- 磁碟機名稱可以是任何英數字元的序列。

- 在任何有效的時間點上的路徑，稱為 「 根 」，您可以指定磁碟機。

- 磁碟機可以實作的任何預存的資料，不只是檔案系統。

- 每個磁碟機中，會保留自己目前的工作位置，讓使用者能夠保留內容，當磁碟機之間轉移。

## <a name="in-this-section"></a>在本節中

下表列出包含程式碼範例，可建立在彼此的主題。 從開始第二個主題，基本的 Windows PowerShell 提供者可以初始化，並由 Windows PowerShell 執行階段未初始化下, 一個主題中新增功能存取資料下, 一個主題中新增功能操作資料 （中的項目儲存的資料），依此類推。

|主題|定義|
|-----------|----------------|
|[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)|本主題討論實作的 Windows PowerShell 提供者之前，您應該考慮的事項。 它也摘要說明 Windows PowerShell 提供者的基底類別和介面，可用。|
|[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)|本主題說明如何建立 Windows PowerShell 提供者，可讓 Windows PowerShell 執行階段初始化，並取消初始化提供者。|
|[建立 Windows PowerShell 磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)|本主題說明如何建立 Windows PowerShell 提供者，可讓使用者透過 Windows PowerShell 磁碟機存取資料存放區。|
|[建立 Windows PowerShell 項目提供者](./creating-a-windows-powershell-item-provider.md)|本主題說明如何建立 Windows PowerShell 提供者，可讓使用者管理的資料存放區中的項目。|
|[建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)|本主題說明如何建立 Windows PowerShell 提供者，可讓使用者在多層的資料存放區上運作。|
|[建立 Windows PowerShell 巡覽提供者](./creating-a-windows-powershell-navigation-provider.md)|本主題說明如何建立 Windows PowerShell 提供者，可讓使用者瀏覽資料存放區的項目，以階層方式。|
|[建立 Windows PowerShell 內容提供者](./creating-a-windows-powershell-content-provider.md)|本主題說明如何建立 Windows PowerShell 提供者，可讓使用者管理的資料存放區中的項目內容。|
|[建立 Windows PowerShell 屬性提供者](./creating-a-windows-powershell-property-provider.md)|本主題說明如何建立 Windows PowerShell 提供者，可讓使用者管理的資料存放區中的項目屬性。|

## <a name="see-also"></a>另請參閱

[Windows PowerShell 的運作方式](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)
