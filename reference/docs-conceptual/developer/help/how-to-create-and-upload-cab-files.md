---
title: 如何建立及上傳 CAB 檔案
ms.date: 09/13/2016
ms.openlocfilehash: 247ed70ba206d70be01155653efbe887bf603f53
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893028"
---
# <a name="how-to-create-and-upload-cab-files"></a>如何建立及上傳 CAB 檔案

本主題說明如何建立可更新的說明 CAB 檔案，並將其上傳至可更新的說明 Cmdlet 可以找到它們的位置。

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>如何建立和上傳可更新的說明 CAB 檔案

您可以使用「可更新的說明」功能，以多種語言和文化特性為模組傳遞新的或更新的說明檔。 模組的可更新說明套件包含一個 HelpInfo XML 檔案和一或多個封包檔（ `.CAB` ）。 每個封包檔都包含一個 UI 文化特性中模組的說明檔。 使用下列程式來建立可更新說明的封包檔。

1. 依 UI 文化特性來組織模組的說明檔。 每個可更新的說明封包檔都包含一個 UI 文化特性中某個模組的說明檔。 您可以為模組傳遞多個說明 CAB 檔案，每個檔案都適用于不同的 UI 文化特性。

1. 確認說明檔只包含 [可更新的說明] 所允許的檔案類型，並根據說明檔案架構來進行驗證。 如果 `Update-Help` Cmdlet 遇到無效或不是允許類型的檔案，則不會安裝不正確檔案，而且會停止從 CAB 安裝檔案。 如需允許的檔案類型清單，請參閱[可更新的說明 CAB 檔案中允許的檔案類型](./file-types-permitted-in-an-updatable-help-cab-file.md)。

1. 以數位方式簽署說明檔。 數位簽章不是必要的，但它們是最佳做法。

1. 以 UI 文化特性包含模組的所有說明檔，而不只是新的或已變更的檔案。 如果 CAB 檔案不完整，則第一次下載說明檔案或未下載每個更新的使用者，將不會有所有模組說明檔案。

1. 使用可建立封包檔的公用程式，例如 `MakeCab.exe` 。 PowerShell 不包含建立 CAB 檔案的 Cmdlet。

1. 為 CAB 檔案命名。 如需詳細資訊，請參閱[如何命名可更新的說明 CAB](./how-to-name-an-updatable-help-cab-file.md)檔案。

1. 將模組的 CAB 檔案上傳到模組的 HelpInfo XML 檔案中**HelpContentUri**元素所指定的位置。 然後，將 HelpInfo XML 檔案上傳至模組資訊清單的**HelpInfoUri**索引鍵所指定的位置。 **HelpContentUri**和**HelpInfoUri**可以指向相同的位置。

> [!CAUTION]
> **HelpInfoUri**索引鍵和**HelpContentUri**元素的值必須以 `http` 或開頭 `https` 。 此值必須指出網際網路位置，而且不能包含檔案名。
