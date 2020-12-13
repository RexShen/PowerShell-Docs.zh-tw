---
ms.date: 09/12/2016
ms.topic: reference
title: 如何新增＜另請參閱＞小節至提供者說明主題
description: 如何新增＜另請參閱＞小節至提供者說明主題
ms.openlocfilehash: df0b14ba84e04baf404081944ef62ef6745d74b2
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667652"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>如何新增＜另請參閱＞小節至提供者說明主題

本節說明如何填入提供者說明主題的 [另 **請參閱** ] 區段。

[另 **請參閱** ] 區段包含與提供者相關的主題清單，或可能有助於使用者更瞭解並使用提供者。 主題清單可以包含 Cmdlet 說明、提供者說明和概念性 ( Windows PowerShell 中的「關於」 ) 說明主題。 它也可以包含書籍、紙張和線上主題的參考，包括目前提供者說明主題的線上版本。

當您參考線上主題時，請以純文字提供 URI 或搜尋字詞。 `Get-Help`Cmdlet 不會連結或重新導向至清單中的任何主題。 此外， `Online` Cmdlet 的參數 `Get-Help` 無法與提供者說明一起使用。

[ **另請參閱** ] 區段是從專案 `RelatedLinks` 和它所包含的標記所建立。
下列 XML 說明如何加入標記。

### <a name="to-add-see-also-topics"></a>若要加入，請參閱主題

1. 在檔案中 `<AssemblyName>.dll-help.xml` 的專案內 `providerHelp` ，加入 `RelatedLinks` 元素。 `RelatedLinks`元素應該是專案中的最後一個元素 `providerHelp` 。 `RelatedLinks`每個提供者說明主題中只允許一個元素。

   例如：

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

1. 針對 [ **另請參閱** ] 區段中的每個主題，在專案中 `RelatedLinks` 加入一個 `navigationLink` 元素。 然後，在每個專案中 `navigationLink` 加入一個專案 `linkText` 和一個 `uri` 元素。 如果您未使用專案 `uri` ，您可以將它新增為空白元素， (\<uri/>) 。

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

1. 輸入標記之間的主題名稱 `linkText` 。 如果您要提供 URI，請在標記之間輸入 `uri` 。 若要指出目前提供者說明主題的線上版本，請在 `linkText` 標記之間輸入 "online version："，而不是主題名稱。 一般而言，[線上版本：] 連結是 [另請參閱主題] 清單中的第一個主題。

   下列範例包含三個另請參閱主題。 第一個參考目前主題的線上版本。 第二個是指 Windows PowerShell 的 Cmdlet 說明主題。 第三個是另一個線上主題。

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
                <uri>https://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```
