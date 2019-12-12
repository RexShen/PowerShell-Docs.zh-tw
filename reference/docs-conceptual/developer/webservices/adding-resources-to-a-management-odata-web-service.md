---
title: 將資源新增至 Management OData Web 服務 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: b81a32b867795ae51c3f5308c2f82c31ed2747fa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359817"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>新增資源至 Management OData Web 服務

這個範例示範如何使用 Management OData 架構設計工具，將資源新增至現有的管理 OData web 服務。 [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)範例會建立公開進程和伺服器資源的 web 服務。 在此範例中，您會將虛擬機器（VM）資源新增至 web 服務。

## <a name="prerequisites"></a>必要條件

本主題假設您已下載並安裝[PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)範例（如[建立 Windows PowerShell Web 服務](./creating-a-management-odata-web-service.md)中所述），而且您已下載並安裝[Management OData 架構設計](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner)工具。 本主題也假設您已在設定 Management Odata 端點的電腦上安裝 Hyper-v Windows PowerShell 模組。

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>將 VM 作為資源新增至 Web 服務

第一個步驟是將架構從現有的管理 OData 端點匯入到架構設計工具中。 下列程式說明如何執行這項操作。

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>將現有的架構匯入架構設計工具

1. 開啟 [Management OData 架構設計工具]。

2. 從 [**檔案**]**功能表選取 [** 檔案];**New** ;檔案。 [**新增**檔案] 對話方塊隨即出現。

3. 按一下 [**管理 OData 模型**]，然後按一下 [**開啟**]。

4. 在主視窗中按一下滑鼠右鍵，然後按一下 [**架構**檔案]。匯**入**。 [**開啟**] 對話方塊隨即出現。

5. 流覽至您為[PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)範例設定 Management OData web 服務的資料夾。 如果您使用該範例提供的 Windows PowerShell 腳本來設定端點，而不修改腳本，則會**C:\inetpub\wwwroot\Modata**該資料夾。 選取 [Schema. mof]，然後按一下 [**開啟**]。

   此時，請在文字編輯器中開啟架構. mof 和 .xml 檔案，並注意其中包含進程和服務資源的對應。 此架構的 mof 檔案使用[分散式管理工作推動小組](https://www.dmtf.org/)（DTMF）受管理物件（mof）標準。 架構 .xml 檔案會使用[資源對應架構](./resource-mapping-schema.md)中所述的 xml 架構。

   下列程式說明如何將中的 Hyper-v Cmdlet 匯入至架構模型。

#### <a name="importing-cmdlets-into-the-schema"></a>將 Cmdlet 匯入架構

1. 以滑鼠右鍵按一下 [架構設計工具] 視窗的空白區域，然後按一下 [匯**入 Cmdlet**]。 [ **Cmdlet 匯入嚮導**] 對話方塊隨即出現。

2. 請確定已選取 [**本機電腦**]，然後按 **[下一步]** 。

3. 請確定已選取 [已安裝的 Windows PowerShell 模組]，然後從下拉式清單中選取 [Hyper-v]。 按 [下一步]。 按 **[下一步]** 。

4. 在 [ **Cmdlet 名詞**] 清單中，選取 [ **VM**]。 按 [下一步]

5. 在此範例中，我們只會使用 Cmdlet 來系結 Get 和 Delete 命令。 清除 [**建立**和**更新**] 核取方塊，並確定已核**取 [取得**] 和 [**刪除**] 核取方塊。 請確定已選取 [**取得**] `Get-VM` Cmdlet，並已選取 [`Remove-VM`] Cmdlet 進行**刪除**。

6. 因為 VM Cmdlet 的中繼資料不會指定輸出類型，所以您必須執行 Cmdlet 來指定輸出類型。 選取 [**提供輸出類型**]，然後按一下 [**執行 Cmdlet**]。 [**執行 Cmdlet** ] 對話方塊隨即出現。 按一下 [執行]。 [ **CLR 類型**] 方塊會填入 `VirtualMachine` 類型。 按一下 **[確定]** ，然後按 **[下一步]** 。

7. 根據預設，會選取 VirtualMachine 物件的所有屬性。 當您從 web 服務要求此資源時，您可以清除不想要的任何屬性，做為所傳回資料的一部分。 按 **[下一步]** 。

8. 您必須至少選取一個要當做金鑰使用的屬性。 選取清單中的 [**名稱**]，然後按 **[下一步]** 。

9. 下一個視窗可讓您將管理 OData 資源的屬性對應至基礎 Cmdlet 的屬性。 根據預設，嚮導會對應具有相同名稱的屬性。 例如，資源的 `ComputerName` 屬性會對應至 Cmdlet 的 `ComputerName` 屬性。  這可讓您在對 web 服務的要求中指定 `ComputerName` 屬性，並將您指定的值傳遞給 `Get-VM` Cmdlet。 `Id` 和 `Name` 預設也會對應。

   10. 按 **[下一步**]，然後按一下 **[完成]** 。

       VM 資源現在會出現在 [架構設計工具] 視窗中。 您可以檢查與資源相關聯的屬性和作業。 接下來，您會將更新的架構檔案匯出至 web 服務的虛擬目錄。

#### <a name="exporting-schema-files-from-the-schema-designer"></a>從架構設計工具匯出架構檔案

1. 以滑鼠右鍵按一下 [架構設計工具] 視窗的空白區域，然後按一下 [**架構**檔案]。**匯出**。 [**另存**新檔] 對話方塊隨即出現。

2. 流覽至您匯入 MOF 檔案的相同目錄。 將檔案命名為與原始 MOF 檔案相同（預設為 [mof]），然後按一下 [**儲存**]。 確認您想要覆寫現有的檔案。

   雖然它不會在 [**另存**新檔] 對話方塊中明確指出，但這會取代架構. Mof 和 schema .xml 檔案。

## <a name="next-steps"></a>後續步驟

從 Management OData web 服務存取新的 VM 資源之前，您必須更新 RbacConfiguration，以允許存取 Hyper-v Windows PowerShell 模組（如設定以[角色為基礎的授權](./configuring-role-based-authorization.md)中所述），而且您也需要重新開機 web 服務。