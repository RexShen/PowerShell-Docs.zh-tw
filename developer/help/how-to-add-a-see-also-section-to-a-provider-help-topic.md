---
title: 操作說明，請參閱也將區段新增至提供者說明主題 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858344"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>如何新增＜另請參閱＞小節至提供者說明主題

本節說明如何以填入**另請參閱**區段的提供者說明主題。

**另請參閱**區段包含的主題相關的提供者，或可能有幫助使用者深入了解，並使用提供者清單。 主題清單可以包含 cmdlet 的說明，請提供者說明和概念性 （「 關於 」） 在 Windows PowerShell 中的 [說明] 主題。 它也可以包含書籍、 文件及線上主題，包括目前的提供者說明主題的線上版本的參考。

當您參考線上主題時，提供 URI 或搜尋詞彙，以純文字。 `Get-Help` Cmdlet 不會連結或重新導向至任何清單中的主題。 此外，`Online`參數的`Get-Help`cmdlet 與提供者說明無法運作。

另請參閱 > 一節從建立`RelatedLinks`項目和它所包含的標記。 下列 XML 示範如何新增標記。

### <a name="to-add-see-also-topics"></a>若要新增 「 另請參閱 」 主題

1. 在  *AssemblyName*.dll help.xml 檔案，內`providerHelp`項目，新增`RelatedLinks`項目。 `RelatedLinks`元素應該是中的最後一個項目`providerHelp`項目。 只有一個`RelatedLinks`允許每個提供者說明主題中的項目。

   例如：

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. 每個主題中**另請參閱**區段中，內`RelatedLinks`項目，新增`navigationLink`項目。 然後，在各`navigationLink`項目，新增一個`linkText`項目和一個`uri`項目。 如果您不使用`uri`項目，您可以將它新增為空項目 (\<uri / >)。

   例如：

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. 輸入主題名稱之間`linkText`標記。 如果您要提供的 URI，它之間輸入`uri`標記。 若要指出目前的提供者說明主題的線上版本之間`linkText`標記中，輸入 「 線上版本:"而不是主題名稱。 一般而言，「 線上版本:"連結是在 < 另請參閱主題清單中的第一個主題。

   下列範例包含三個另請參閱主題。 第一個參考目前主題的線上版本。 第二個是指 Windows PowerShell cmdlet 說明主題。 第三個指的是另一個線上主題。

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```