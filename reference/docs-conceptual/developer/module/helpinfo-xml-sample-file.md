---
title: HelpInfo XML 範例檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6544070f-5549-407f-8603-5df60fe9e013
caps.latest.revision: 7
ms.openlocfilehash: 11804db56ec47554e82f04fe6954920ad9577370
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360807"
---
# <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="c88c8-102">HelpInfo XML 範例檔案</span><span class="sxs-lookup"><span data-stu-id="c88c8-102">HelpInfo XML Sample File</span></span>

<span data-ttu-id="c88c8-103">本主題顯示格式正確之可更新的說明資訊檔案的範例，通常稱為「HelpInfo XML file」。</span><span class="sxs-lookup"><span data-stu-id="c88c8-103">This topic displays a sample of a well-formed Updatable Help Information file, commonly known as "HelpInfo XML file."</span></span> <span data-ttu-id="c88c8-104">在此範例檔案中，UI 文化特性元素會依 UI 文化特性名稱以字母順序排列。</span><span class="sxs-lookup"><span data-stu-id="c88c8-104">In this sample file, the UI culture elements are arranged in alphabetical order by UI culture name.</span></span> <span data-ttu-id="c88c8-105">字母順序是最佳做法，但並非必要。</span><span class="sxs-lookup"><span data-stu-id="c88c8-105">Alphabetical ordering is a best practice, but it is not required.</span></span>

## <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="c88c8-106">HelpInfo XML 範例檔案</span><span class="sxs-lookup"><span data-stu-id="c88c8-106">HelpInfo XML Sample File</span></span>

```xml

<?xml version="1.0" encoding="utf-8"?>
<HelpInfo xmlns="http://schemas.microsoft.com/powershell/help/2010/05">
   <HelpContentURI>http://go.microsoft.com/fwlink/?LinkID=141553</HelpContentURI>
   <SupportedUICultures>
    <UICulture>
      <UICultureName>de-DE</UICultureName>
      <UICultureVersion>2.15.0.10</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>en-US</UICultureName>
      <UICultureVersion>3.2.0.7</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>it-IT</UICultureName>
      <UICultureVersion>1.1.0.5</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>ja-JP</UICultureName>
      <UICultureVersion>3.2.0.4</UICultureVersion>
    </UICulture>
   </SupportedUICultures>
</HelpInfo>

```