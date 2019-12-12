---
title: 如何將 [另請參閱] 區段新增至提供者說明主題 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367837"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>如何新增＜另請參閱＞小節至提供者說明主題

本節說明如何填入提供者說明主題的 [**另請參閱**] 區段。

[**另請參閱**] 區段是由與提供者相關的主題清單所組成，或可能有助於使用者進一步瞭解並使用該提供者。 主題清單可包含 Windows PowerShell 中的 Cmdlet 說明、提供者說明和概念性（「關於」）說明主題。 它也可以包含書籍、論文和線上主題的參考，包括目前提供者說明主題的線上版本。

當您參考線上主題時，請以純文字提供 URI 或搜尋詞彙。 `Get-Help` Cmdlet 不會連結或重新導向至清單中的任何主題。 此外，`Get-Help` Cmdlet 的 `Online` 參數無法與提供者說明搭配運作。

[另請參閱] 區段是從 `RelatedLinks` 專案及其包含的標記建立而來。 下列 XML 顯示如何新增標記。

### <a name="to-add-see-also-topics"></a>新增「另請參閱」主題

1. 在 dll-help .xml*檔案的 `providerHelp`* 專案中，加入 `RelatedLinks` 元素。 `RelatedLinks` 元素應該是 `providerHelp` 元素中的最後一個元素。 每個提供者說明主題中只允許一個 `RelatedLinks` 元素。

   例如：

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. 針對 [**另請參閱**] 區段中 [`RelatedLinks`] 專案內的每個主題，加入 `navigationLink` 元素。 然後，在每個 `navigationLink` 專案中，加入一個 `linkText` 元素和一個 `uri` 專案。 如果您不是使用 `uri` 專案，您可以將它新增為空的元素（\<uri/>）。

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

3. 在 `linkText` 標記之間輸入主題名稱。 如果您要提供 URI，請在 `uri` 標記之間輸入。 若要指出目前提供者說明主題的線上版本，請在 `linkText` 標記之間輸入「線上版本：」，而不是主題名稱。 一般而言，「線上版本：」連結是 [另請參閱主題] 清單中的第一個主題。

   下列範例包含三個 [另請參閱] 主題。 第一個參考目前主題的線上版本。 第二個則是指 Windows PowerShell Cmdlet 說明主題。 第三個參考另一個線上主題。

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