---
title: 如何建立及上傳 CAB 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082374"
---
# <a name="how-to-create-and-upload-cab-files"></a>如何建立及上傳 CAB 檔案

本主題說明如何建立可更新說明的 CAB 檔案，然後將它們上傳至其中的可更新說明的 cmdlet 可以在其中找到它們的位置。

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>如何建立及上傳可更新的說明封包檔

您可以使用 「 可更新的說明 」 功能，提供多種語言和文化特性中的模組的新的或更新的說明檔案。 模組的可更新的說明套件包含一個 HelpInfo XML 檔案和一或多個封包 (。CAB) 檔案。 每個封包檔包含一個 UI 文化特性中的模組的說明檔案。 使用下列程序來建立封包檔的可更新的說明。

1. 組織的 UI 文化特性之模組的說明檔案。 每個可更新說明的 CAB 檔案包含一個 UI 文化特性中的一個模組的說明檔案。 您可以提供多個說明對於模組，每個不同的 UI 文化特性的封包檔。

2. 確認的說明檔包含只允許可更新說明的檔案類型和驗證的說明檔案結構描述。 如果`Update-Help`cmdlet 發生檔案無效或不允許的型別，它不會安裝無效的檔案，並停止封包從安裝檔案。 如需允許的檔案類型的清單，請參閱 <<c0> [ 可更新的說明封包檔中的檔案類型允許](./file-types-permitted-in-an-updatable-help-cab-file.md)。

3. 數位簽章說明檔。 數位簽章是不必要的但最佳作法。

4. 包含所有文化特性，不只是新的檔案或變更的 UI 中的模組檔案的說明。 如果封包檔不完整，第一次下載說明檔案，或不要下載每個更新中，使用者不會所有模組的說明檔案。

5. 使用會建立封包檔，例如 MakeCab.exe 公用程式。 Windows PowerShell 不包含建立 CAB 檔案的 cmdlet。

6. 命名封包檔。 如需詳細資訊，請參閱 <<c0> [ 如何命名可更新的說明封包檔](./how-to-name-an-updatable-help-cab-file.md)。

7. 將模組的 CAB 檔案上傳到所指定的位置**HelpContentUri**模組 HelpInfo XML 檔案中的項目。 然後將 HelpInfo XML 檔案上傳至所指定的位置**HelpInfoUri**模組資訊清單索引鍵。 **HelpContentUri**並**HelpInfoUri**可以指向相同的位置。

> [!CAUTION]
> 值**HelpInfoUri**機碼並**HelpContentUri**項目必須以"http"或"https"開頭。 值必須表示網際網路位置，它不能包含檔案名稱。