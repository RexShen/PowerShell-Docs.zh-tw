---
title: HelpInfo XML 結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 0f965f4ee1ef92a6a538b52b4348c04366cabf66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082459"
---
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="a08e6-102">HelpInfo XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="a08e6-102">HelpInfo XML Schema</span></span>

<span data-ttu-id="a08e6-103">本主題包含 XML 結構描述，可更新的說明資訊檔案，通常稱為 「 HelpInfo XML 檔案 」。</span><span class="sxs-lookup"><span data-stu-id="a08e6-103">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="a08e6-104">HelpInfo XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="a08e6-104">HelpInfo XML Schema</span></span>

<span data-ttu-id="a08e6-105">HelpInfo XML 檔案根據下列的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="a08e6-105">HelpInfo XML files are based on the following XML schema.</span></span>

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

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="a08e6-106">HelpInfo XML 項目</span><span class="sxs-lookup"><span data-stu-id="a08e6-106">HelpInfo XML Elements</span></span>

<span data-ttu-id="a08e6-107">HelpInfo XML 檔案包含下列項目。</span><span class="sxs-lookup"><span data-stu-id="a08e6-107">The HelpInfo XML file includes the following elements.</span></span>

<span data-ttu-id="a08e6-108">HelpContentURI 包含說明模組的 CAB 檔案的位置的 URI。</span><span class="sxs-lookup"><span data-stu-id="a08e6-108">HelpContentURI Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="a08e6-109">URI 必須以"http"或"https"開頭。</span><span class="sxs-lookup"><span data-stu-id="a08e6-109">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="a08e6-110">URI 應指定網際網路位置，但不是能包含 CAB 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="a08e6-110">The URI should specify an Internet location, but must not include the CAB file name.</span></span> <span data-ttu-id="a08e6-111">**HelpContentURI**值可以是相同或不同**HelpInfoURI**值。</span><span class="sxs-lookup"><span data-stu-id="a08e6-111">The **HelpContentURI** value can be the  same or different from the **HelpInfoURI** value.</span></span>

<span data-ttu-id="a08e6-112">SupportedUICultures 代表模組的說明檔案，在所有 UI 文化特性。</span><span class="sxs-lookup"><span data-stu-id="a08e6-112">SupportedUICultures Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="a08e6-113">包含**UICulture**項目，每一個都代表一組指定的 UI 文化特性中的模組的說明檔案。</span><span class="sxs-lookup"><span data-stu-id="a08e6-113">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

<span data-ttu-id="a08e6-114">UICulture 代表一組指定的 UI 文化特性中的模組的說明檔案。</span><span class="sxs-lookup"><span data-stu-id="a08e6-114">UICulture Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="a08e6-115">新增**UICulture**每個 UI 文化特性的說明檔案寫入的項目。</span><span class="sxs-lookup"><span data-stu-id="a08e6-115">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

<span data-ttu-id="a08e6-116">UICultureName 包含說明檔寫入的 UI 文化特性的語言代碼。</span><span class="sxs-lookup"><span data-stu-id="a08e6-116">UICultureName Contains the language code for the UI culture in which the help files are written.</span></span>

<span data-ttu-id="a08e6-117">UICultureVersion 含有 4 部分版本號碼中"N1。N2。N3。N4"格式表示的 UI 文化特性說明封包檔的版本。</span><span class="sxs-lookup"><span data-stu-id="a08e6-117">UICultureVersion Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="a08e6-118">每當您上傳新的說明中所指定的 UI 文化特性的封包檔遞增此版本號碼**UICultureName**。</span><span class="sxs-lookup"><span data-stu-id="a08e6-118">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="a08e6-119">如需此值的詳細資訊，請參閱"版本中的類別 （系統） > MSDN。</span><span class="sxs-lookup"><span data-stu-id="a08e6-119">For more information about this value, see "Version Class (System)" in MSDN.</span></span>