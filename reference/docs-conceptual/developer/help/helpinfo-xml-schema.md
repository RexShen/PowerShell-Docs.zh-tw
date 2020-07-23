---
title: HelpInfo XML 結構描述
ms.date: 09/12/2016
ms.openlocfilehash: f94d053b8fc558d9efc13e6b9fbd597287970e38
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "86953245"
---
# <a name="helpinfo-xml-schema"></a>HelpInfo XML 結構描述

本主題包含可更新的說明資訊檔案的 XML 架構，通常稱為「HelpInfo XML files」。

## <a name="helpinfo-xml-schema"></a>HelpInfo XML 結構描述

HelpInfo XML 檔案是以下列 XML 架構為基礎。

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="http://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
  <element name="HelpInfo">
    <complexType>
      <sequence>
        <element name="HelpContentURI" type="anyURI" minOccurs="1" maxOccurs="1" />
        <element name="SupportedUICultures" minOccurs="1" maxOccurs="1">
          <complexType>
            <sequence>
              <element name="UICulture" minOccurs="1" maxOccurs="unbounded">
                <complexType>
                  <sequence>
                    <element name="UICultureName" type="language" minOccurs="1" maxOccurs="1" />
                    <element name="UICultureVersion" type="string" minOccurs="1" maxOccurs="1" />
                  </sequence>
                </complexType>
              </element>
            </sequence>
          </complexType>
        </element>
      </sequence>
    </complexType>
  </element>
</schema>
```

## <a name="helpinfo-xml-elements"></a>HelpInfo XML 元素

HelpInfo XML 檔案包含下列元素。

- **HelpContentURI** -包含模組之說明 CAB 檔案位置的 URI。 URI 必須以 "HTTP" 或 "HTTPs" 開頭。 URI 應該指定網際網路位置，但不能包含 CAB 檔案名。 **HelpContentURI**值可以是相同或不同于**HelpInfoURI**值。

- **SupportedUICultures** -代表所有 UI 文化特性中的模組說明檔。 包含**UICulture**專案，每個元素都代表指定之 UI 文化特性中模組的一組說明檔。

- **UICulture** -代表指定之 UI 文化特性中模組的一組說明檔。 為寫入說明檔的每個 UI 文化特性新增**UICulture**元素。

- **UICultureName** -包含用來撰寫說明檔案之 UI 文化特性的語言代碼。

- **UICultureVersion** -在 "N1" 中包含4部分版本號碼。N2.N3.N4 "格式，代表 UI 文化特性中的說明 CAB 檔案版本。 每當您在**UICultureName**所指定的 UI 文化特性中上傳新的說明 CAB 檔案時，就會遞增此版本號碼。 如需此值的詳細資訊，請參閱[版本類別](/dotnet/api/system.version)。
