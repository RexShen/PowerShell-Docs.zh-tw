---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 了解 DSC 在 CI/CD 管線中的角色
ms.openlocfilehash: 7aec414b3d8e61d1daa1ce796184ac34dbbb43ce
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803373"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a>了解 DSC 在 CI/CD 管線中的角色

本文描述可用於結合設定和資源的方法類型。
每個案例的目標都相同，那就是在想要使用多項設定來達到伺服器部署結束狀態時降低其複雜度。
其中一個例子是多個小組參與伺服器部署的結果；例如，應用程式擁有者維護應用程式狀態，而核心小組將變更發行至安全性基準。
以下詳細說明每種方法的細微差異，包括優點和風險。

![管線](../images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a>共同撰寫技術類型

本機設定管理員內建兩個解決方案，可實現此概念：

| 概念 | 詳細資訊
|-|-
| 部分設定 | [文件](../pull-server/partialConfigs.md)
| 複合資源 | [文件](../resources/authoringResourceComposite.md)

## <a name="understanding-the-impact-of-each-approach"></a>了解每種方法的影響

任一解決方案都可用來管理伺服器部署的結果。
不過，使用每種方法的影響會有明顯差異。

## <a name="partial-configurations"></a>部分設定

使用部分設定時，本機設定管理員會設定為獨立管理多項設定。
這些設定會獨立編譯，再指派給節點。
這需要使用每項設定的名稱事先設定 LCM。

![PartialConfiguration](../images/PartialConfiguration.jpg)

部分設定提供兩個 (含) 以上的小組對伺服器設定的完整控制權，通常沒有通訊或共同作業優點。

客戶反應這可能會導致資源衝突、意外覆寫，最終失去資產的真正設定控制權。

此外，客戶也反應使用此模型時，每個控制小組設定變更不太可能透過發行管線完全測試，而導致在生產環境中有非預期的結果。

**請務必使用單一管線來評估發行至伺服器的所有變更。**

在下圖中，小組 B 將其部分設定發行至小組 A。小組 A 接著對已同時套用兩項設定的伺服器執行其測試。
在此模型中，只有一個授權單位有權在生產環境中進行變更。

![PartialSinglePipeline](../images/PartialSinglePipeline.jpg)

當小組 B 需要變更時，他們應該對小組 A 的原始檔控制環境提交提取要求。
小組 A 會接著使用測試自動化檢閱變更，並在確認變更不會在伺服器所裝載的應用程式或服務中造成錯誤時將它發行至生產環境。

## <a name="composite-resources"></a>複合資源

複合資源只是封裝成資源的 DSC 設定。
設定 LCM 接受複合資源沒有特殊需求。
這些資源會在新設定中使用，而且每次編譯都會產生一個 MOF 檔案。

![CompositeResource](../images/CompositeResource.jpg)

複合資源有兩個常見的案例。
第一個是降低複雜度及提取獨特概念。
第二個是允許封裝基準，讓應用程式小組在所有測試皆成功之後，透過其發行管線安全地部署到生產環境。

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

複合資源使用管線來促進撰寫和共同作業，並同時讓營運更臻成熟

您可能已在使用複合資源而不自知。
**ServiceSet** 即為一例。
此資源可管理多個 Windows 服務的狀態，而不需要個別列出。
Name 屬性接受字串陣列提供每項服務的名稱。
編譯設定之後，針對傳遞至 ServiceSet 的每個名稱，MOF 會包含其唯一的 [服務] 區段。

組織可能會有應安裝在每一部伺服器上的「代理程式」或「中介軟體」。
複合資源是管理任何這類工具和公用程式相依性、安裝程式和設定的最佳選擇。

跨多部伺服器解決方案的負責人和小組可撰寫含有其需求的設定。
接下來，使用複合資源文件中提供的指示，將設定封裝成複合資源。
最後，新的複合資源應發佈至檔案共用或 NuGet 摘要等位置，以供應用程式小組在其設定中取用。

每次小組發行新版本，都會將其複合資源模組資訊清單中的版本號碼遞增。
應用程式小組會將為管理應用程式相依性所撰寫的複合資源包含在設定中。
當營運/安全性小組發行其資源的新版本時，他們會通知應用程式小組有這項新變更。

如果只變更基準，應用程式小組可能會觸發發行至生產環境。
不過，這讓他們有機會在發生服務中斷風險之前評估這對應用程式的影響。

注意 - 關於使用複合資源的意見反應包括了對於進行變更需要編譯和發行新 MOF 的批評。
這是原本設計的做法。
每個新設定版本都應該包含每個資源特定版本的靜態參考，而且應該經過測試驗證，再到達生產伺服器節點。
測試和發行原始檔控制中變更的程序會建立安全的環境，以少量但頻繁的批次來發行變更。

如需使用發行管線管理核心基礎結構的詳細資訊，請參閱技術白皮書：[發行管線模型](../further-reading/whitepapers.md)。
