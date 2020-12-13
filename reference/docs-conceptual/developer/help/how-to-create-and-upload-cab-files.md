---
ms.date: 09/13/2016
ms.topic: reference
title: 如何建立及上傳 CAB 檔案
description: 如何建立及上傳 CAB 檔案
ms.openlocfilehash: bdcf534f48cff27b403d82440ad4ec6a3212b67d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653892"
---
# <a name="how-to-create-and-upload-cab-files"></a>如何建立及上傳 CAB 檔案

本主題說明如何建立可更新的說明 CAB 檔案，並將它們上傳至可更新的說明 Cmdlet 可以找到這些檔案的位置。

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>如何建立及上傳可更新的說明 CAB 檔案

您可以使用「可更新的說明」功能，以多種語言和文化特性為模組提供新的或已更新的說明檔。 模組的可更新說明套件包含一個 HelpInfo XML 檔案，以及一個或多個封包 (`.CAB`) 檔。 每個 CAB 檔案都包含一個 UI 文化特性中模組的說明檔。 使用下列程式建立 CAB 檔案以取得可更新的說明。

1. 依 UI 文化特性組織模組的說明檔。 每個可更新的說明 CAB 檔案都包含一個 UI 文化特性中某個模組的說明檔。 您可以為模組傳遞多個說明 CAB 檔案，每個都有不同的 UI 文化特性。

1. 確認說明檔僅包含可更新的說明所允許的檔案類型，並針對說明檔架構進行驗證。 如果 `Update-Help` Cmdlet 遇到無效或不是允許類型的檔案，則不會安裝不正確檔案，並會停止從 CAB 安裝檔案。 如需允許的檔案類型清單，請參閱 [可更新的說明 CAB 檔案中允許的檔案類型](./file-types-permitted-in-an-updatable-help-cab-file.md)。

1. 以數位方式簽署說明檔。 數位簽章並非必要，但它們是最佳作法。

1. 在 UI 文化特性中包含模組的所有說明檔，而不只是新的或已變更的檔案。 如果 CAB 檔案不完整，則第一次下載說明檔或未下載每個更新的使用者，將不會有所有模組說明檔。

1. 使用可建立封包檔的公用程式，例如 `MakeCab.exe` 。 PowerShell 不包含可建立 CAB 檔案的 Cmdlet。

1. 為 CAB 檔案命名。 如需詳細資訊，請參閱 [如何命名可更新的說明 CAB](./how-to-name-an-updatable-help-cab-file.md)檔。

1. 將模組的 CAB 檔案上傳至模組的 HelpInfo XML 檔案中 **HelpContentUri** 元素所指定的位置。 然後，將 HelpInfo XML 檔案上傳至模組資訊清單的 **HelpInfoUri** 索引鍵所指定的位置。 **HelpContentUri** 和 **HelpInfoUri** 可指向相同的位置。

> [!CAUTION]
> **HelpInfoUri** 索引鍵的值和 **HelpContentUri** 元素的開頭必須是 `http` 或 `https` 。 值必須指出網際網路位置，而且不得包含檔案名。
