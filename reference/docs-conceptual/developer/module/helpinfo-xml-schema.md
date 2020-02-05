---
title: HelpInfo XML 架構 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 8142a620f0f71de3d2a6b33fc2e45092b5743a54
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996012"
---
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="af918-102">HelpInfo XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="af918-102">HelpInfo XML Schema</span></span>

<span data-ttu-id="af918-103">本主題包含可更新的說明資訊檔案的 XML 架構，通常稱為「HelpInfo XML files」。</span><span class="sxs-lookup"><span data-stu-id="af918-103">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="af918-104">HelpInfo XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="af918-104">HelpInfo XML Schema</span></span>

<span data-ttu-id="af918-105">HelpInfo XML 檔案是以下列 XML 架構為基礎。</span><span class="sxs-lookup"><span data-stu-id="af918-105">HelpInfo XML files are based on the following XML schema.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="https://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
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

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="af918-106">HelpInfo XML 元素</span><span class="sxs-lookup"><span data-stu-id="af918-106">HelpInfo XML Elements</span></span>

<span data-ttu-id="af918-107">HelpInfo XML 檔案包含下列元素。</span><span class="sxs-lookup"><span data-stu-id="af918-107">The HelpInfo XML file includes the following elements.</span></span>

<span data-ttu-id="af918-108">HelpContentURI 包含模組之說明 CAB 檔案位置的 URI。</span><span class="sxs-lookup"><span data-stu-id="af918-108">HelpContentURI Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="af918-109">URI 必須以 "HTTP" 或 "HTTPs" 開頭。</span><span class="sxs-lookup"><span data-stu-id="af918-109">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="af918-110">URI 應該指定網際網路位置，但不能包含 CAB 檔案名。</span><span class="sxs-lookup"><span data-stu-id="af918-110">The URI should specify an Internet location, but must not include the CAB file name.</span></span> <span data-ttu-id="af918-111">**HelpContentURI**值可以是相同或不同于**HelpInfoURI**值。</span><span class="sxs-lookup"><span data-stu-id="af918-111">The **HelpContentURI** value can be the  same or different from the **HelpInfoURI** value.</span></span>

<span data-ttu-id="af918-112">SupportedUICultures 代表所有 UI 文化特性中的模組說明檔。</span><span class="sxs-lookup"><span data-stu-id="af918-112">SupportedUICultures Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="af918-113">包含**UICulture**專案，每個元素都代表指定之 UI 文化特性中模組的一組說明檔。</span><span class="sxs-lookup"><span data-stu-id="af918-113">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

<span data-ttu-id="af918-114">UICulture 代表指定 UI 文化特性中模組的一組說明檔。</span><span class="sxs-lookup"><span data-stu-id="af918-114">UICulture Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="af918-115">為寫入說明檔的每個 UI 文化特性新增**UICulture**元素。</span><span class="sxs-lookup"><span data-stu-id="af918-115">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

<span data-ttu-id="af918-116">UICultureName 包含用來撰寫說明檔案之 UI 文化特性的語言代碼。</span><span class="sxs-lookup"><span data-stu-id="af918-116">UICultureName Contains the language code for the UI culture in which the help files are written.</span></span>

<span data-ttu-id="af918-117">UICultureVersion 在 "N1 中包含4部分版本號碼。N2.N3.N4 "格式，代表 UI 文化特性中的說明 CAB 檔案版本。</span><span class="sxs-lookup"><span data-stu-id="af918-117">UICultureVersion Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="af918-118">每當您在**UICultureName**所指定的 UI 文化特性中上傳新的說明 CAB 檔案時，就會遞增此版本號碼。</span><span class="sxs-lookup"><span data-stu-id="af918-118">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="af918-119">如需此值的詳細資訊，請參閱 MSDN 中的「版本類別（系統）」。</span><span class="sxs-lookup"><span data-stu-id="af918-119">For more information about this value, see "Version Class (System)" in MSDN.</span></span>