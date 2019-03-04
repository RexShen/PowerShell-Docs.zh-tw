---
title: 將資源新增至管理 OData Web 服務 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: b81a32b867795ae51c3f5308c2f82c31ed2747fa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858364"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>新增資源至 Management OData Web 服務

此範例示範如何使用管理 OData 的結構描述設計工具，將資源新增至現有的管理 OData web 服務。 [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)範例會建立 web 服務所公開的程序和伺服器資源。 在此範例中，您將加入至 web 服務的虛擬機器 (VM) 資源。

## <a name="prerequisites"></a>必要條件

本主題假設您已下載並安裝[PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)範例中所述[建立 Windows PowerShell Web 服務](./creating-a-management-odata-web-service.md)，且您已下載並安裝[管理 OData 的結構描述設計工具](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner)。 本主題也假設您已設定管理 Odata 端點的電腦上安裝 HYPER-V Windows PowerShell 模組。

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>新增至 Web 服務做為資源的 VM

第一個步驟是從現有的管理 OData 端點將結構描述匯入至結構描述設計工具。 下列程序描述如何執行該動作。

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>現有的結構描述匯入結構描述設計工具

1. 開啟管理 OData 的結構描述設計工具。

2. 從**檔案**功能表上，選取**檔案**;**新**;**檔案**。 **新的檔案**對話方塊隨即出現。

3. 按一下 **管理 OData 模型**，然後按一下**開啟**。

4. 在主視窗中，以滑鼠右鍵按一下，然後按一下 **結構描述檔案**;**匯入**。 **開啟**對話方塊隨即出現。

5. 瀏覽至 設定管理 OData web 服務的資料夾[PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)範例。 如果您使用該範例使用提供的 Windows PowerShell 指令碼來設定端點，而不需要修改指令碼時，該資料夾就是**C:\inetpub\wwwroot\Modata**。 選取.schema.mof，然後按一下**開啟**。

   到目前為止，在文字編輯器中，開啟的.schema.mof 和 Schema.xml 檔，並請注意，它們會包含對應的程序和服務的資源。 Schema.mof 檔案會使用[分散式管理任務推動小組](https://www.dmtf.org/)(訊號 DTMF) 受管理物件 」 (MOF) 標準。 Schema.xml 檔會使用 XML 結構描述中所述[資源對應的結構描述](./resource-mapping-schema.md)。

   下列程序描述如何匯入結構描述模型中的 HYPER-V cmdlet。

#### <a name="importing-cmdlets-into-the-schema"></a>Cmdlet 匯入結構描述

1. 結構描述設計工具視窗的空白區域上按一下滑鼠右鍵，然後按一下 **匯入 Cmdlet**。 **Cmdlet 匯入精靈**對話方塊隨即出現。

2. 請確定**本機電腦**已選取，然後按一下**下一步**。

3. 請確定選取 已安裝 Windows PowerShell 模組，並從下拉式清單中選取 HYPER-V。 按一下 [**下一步]**。 按 **[下一步]**。

4. 在  **Cmdlet 名詞**清單中，選取**VM**。 按 [下一步]

5. 針對此範例中，我們會繫結只 Get 和 Delete 命令使用 cmdlet。 清除**建立**並**更新**核取方塊，並確定**取得**並**刪除**簽核取方塊。 請確定`Get-VM`cmdlet 會選取**取得**，而`Remove-VM`cmdlet 選取**刪除**。

6. 因為 VM cmdlet 的中繼資料未指定輸出類型，您必須執行 cmdlet，以指定的輸出型別。 選取 **提供輸出型別**然後按一下**執行 cmdlet**。 **執行 Cmdlet**對話方塊隨即出現。 按一下 **執行**。 **CLR 型別**方塊會填入`VirtualMachine`型別。 按一下 [ **[確定]**，然後按一下**下一步]**。

7. 根據預設，會選取所有 VirtualMachine 物件的屬性。 您可以清除您不想為您從 web 服務要求此資源時，傳回資料的一部分的任何屬性。 按 **[下一步]**。

8. 您必須選取至少一個屬性，來做為索引鍵。 選取 [**名稱**在清單中，按一下**下一步]**。

9. 下一步 視窗可讓您將管理 OData 資源的屬性對應到基礎的指令程式的屬性。 精靈預設會對應具有相同名稱的屬性。 例如，`ComputerName`資源的屬性會對應至`ComputerName`指令程式的屬性。  這可讓您指定`ComputerName`web 服務的要求中的屬性，而且有您指定的值傳遞至`Get-VM`cmdlet。 `Id` 和`Name`也會依預設對應。

   10. 按一下 **下一步**，然後按一下**完成**。

       在 VM 資源現在會出現在 [結構描述設計工具] 視窗中。 您可以檢查的屬性和資源相關聯的作業。 接下來，您將更新的結構描述檔案匯出到 web 服務的虛擬目錄中。

#### <a name="exporting-schema-files-from-the-schema-designer"></a>結構描述設計工具匯出結構描述檔案

1. 結構描述設計工具視窗的空白區域上按一下滑鼠右鍵，然後按一下 **結構描述檔案**;**匯出**。 **另存新檔**對話方塊隨即出現。

2. 從您匯入的 MOF 檔案，瀏覽至相同的目錄。 檔案與原始的 MOF 檔案 (預設.schema.mof)，相同的命名，然後按一下**儲存**。 確認您想要覆寫現有的檔案。

   雖然它不中明確陳述**另存新檔** 對話方塊中，這會取代.schema.mof 」 和 「 Schema.xml 檔。

## <a name="next-steps"></a>後續步驟

您可以存取新的 VM 資源從 「 管理 OData web 服務之前，您必須更新 RbacConfiguration.xml 檔案，以允許存取的 HYPER-V Windows PowerShell 模組，如中所述[設定角色為基礎的授權](./configuring-role-based-authorization.md)，而且您也必須重新啟動 web 服務。