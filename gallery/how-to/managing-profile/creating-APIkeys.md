---
ms.date: 09/10/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 管理 API 金鑰
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084323"
---
# <a name="managing-api-keys"></a>管理 API 金鑰

PowerShell 資源庫支援建立多個 API 金鑰，以支援各種不同的發佈需求。 API 金鑰可以套用至一或多個套件、會授與特定權限，而且具有到期日。

> [!IMPORTANT]
> 使用者若未採用限域 API 金鑰就發佈至 PowerShell 資源庫，將會有「完整存取 API 金鑰」。 完整存取金鑰沒有限域 API 金鑰內建的安全性改善。 完整存取金鑰永遠有效，而且會套用至使用者擁有的所有項目。 如果您刪除此金鑰，則無法加以重新建立。

下圖顯示建立限域 API 金鑰時可以使用的選項。

![建立 API 金鑰](../../Images/PSGallery_KeyScoped.png)

在此範例中，我們建立了名為 **AzureRMDataFactory** 的 API 金鑰。 此金鑰值可用來推送名稱開頭為 'AzureRM.DataFactory' 的套件，有效期限為 365 天。 這是同一個組織中不同小組處理不同套件時的典型案例。 小組成員所擁有的金鑰會授與他們權限來存取其所處理的特定套件。
到期值可防止使用過時的金鑰或忘記金鑰。

## <a name="using-glob-patterns"></a>使用 Glob 模式

如果您處理多個套件，您可以使用 Glob 模式將多個套件當作一個群組來比對。 API 金鑰權限會套用至符合 Glob 模式的所有新套件。 例如，上一個範例使用 **Glob 模式** 值 'AzureRM.DataFactory*'。 由於套件符合 Glob 模式，因此您可以推送名為 'AzureRm.DataFactoryV2.Netcore' 的套件。

## <a name="create-api-keys-securely"></a>安全地建立 API 金鑰

基於安全考量，新建立的金鑰值永遠不會顯示在畫面上，而且只能透過 [複製] 按鈕使用，如下所示。

![取得新的 API 金鑰值](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> 您只能在建立或重新整理之後立即複製 API 金鑰值。 該值不會顯示，而且在重新整理頁面之後將無法再次存取。 如果您遺失金鑰值，您必須使用 [重新產生]，並在重新產生金鑰之後加以複製。

## <a name="key-permissions-and-expiration"></a>金鑰權限和到期日

限域 API 金鑰可以指派下列任何權限：

- 推送新的套件
- 推送新的套件或更新套件
- 取消列出套件

每個新金鑰都有到期日。 到期值是以天為測量單位。 可能的到期值包括：

- 1 天
- 90 天
- 180 天
- 270 天
- 365 天 (預設值)

一旦建立金鑰，就無法變更這些設定。 您無法建立永遠有效的新金鑰。

## <a name="editing-and-deleting-existing-api-keys"></a>編輯和刪除現有的 API 金鑰

您可以變更現有金鑰的某些設定。 如前所述，您無法修改現有 API 金鑰的安全性範圍，或變更到期日。 下列螢幕擷取畫面顯示可變更的選項：

![取得新的 API 金鑰值](../../Images/PSGallery_EditAPIKey.png)

若要變更受金鑰控制的套件，您可以從清單中選擇個別套件，或變更 Glob 模式。

按一下 [重新產生] 會建立新的金鑰值。 如同初始建立金鑰，您必須在更新金鑰之後**複製**其值。 一旦離開此頁面，就無法使用 [複製] 選項。

按一下 [刪除] 會顯示確認訊息。 金鑰一旦刪除，就無法使用。

## <a name="key-expiration"></a>金鑰到期日

在到期十天前，PowerShell 資源庫會傳送警告電子郵件給 API 金鑰的帳戶持有人。 到期後，金鑰將無法使用。 API 金鑰管理頁面頂端會出現一則警告訊息，顯示哪些金鑰不再有效。 您可以產生新的金鑰值。
