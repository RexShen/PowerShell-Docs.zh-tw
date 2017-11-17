---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "適用於 Linux 的內建預期狀態設定資源"
ms.openlocfilehash: b85f32f7559d89bda566d35462cc613d73424c50
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a><span data-ttu-id="18b19-103">適用於 Linux 的內建預期狀態設定資源</span><span class="sxs-lookup"><span data-stu-id="18b19-103">Built-In Desired State Configuration Resources for Linux</span></span>

<span data-ttu-id="18b19-104">資源是可讓您撰寫 PowerShell 預期狀態設定 (DSC) 指令碼的建置組塊。</span><span class="sxs-lookup"><span data-stu-id="18b19-104">Resources are building blocks that you can use to write a PowerShell Desired State Configuration (DSC) script.</span></span> <span data-ttu-id="18b19-105">DSC for Linux 隨附一組內建功能，可用於設定資源，例如檔案和資料夾、套件、環境變數，以及服務和處理序。</span><span class="sxs-lookup"><span data-stu-id="18b19-105">DSC for Linux comes with a set of built-in functionality for configuring resources such as files and folders, packages, environment variables, and services and processes.</span></span>

## <a name="built-in-resources"></a><span data-ttu-id="18b19-106">內建資源</span><span class="sxs-lookup"><span data-stu-id="18b19-106">Built-in resources</span></span> 

<span data-ttu-id="18b19-107">下表提供這些資源和主題詳細資訊的連結清單。</span><span class="sxs-lookup"><span data-stu-id="18b19-107">The following table provides a list of these resources and links to topics that describe them in detail.</span></span>

* <span data-ttu-id="18b19-108">[nxArchive 資源 ](lnxArchiveResource.md) ─ 提供一個機制，將封存 (.tar、.zip) 檔案解壓縮在特定路徑。</span><span class="sxs-lookup"><span data-stu-id="18b19-108">[nxArchive Resource](lnxArchiveResource.md)--Provides a mechanism to unpack archive (.tar, .zip) files at a specific path.</span></span>
* <span data-ttu-id="18b19-109">[nxEnvironment 資源 ](lnxEnvironmentResource.md) ─ 管理目標節點上的環境變數。</span><span class="sxs-lookup"><span data-stu-id="18b19-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--Manages environment variables on target nodes.</span></span> 
* <span data-ttu-id="18b19-110">[nxFile 資源 ](lnxFileResource.md) ─ 管理 Linux 檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="18b19-110">[nxFile Resource](lnxFileResource.md)--Manages Linux files and directories.</span></span> 
* <span data-ttu-id="18b19-111">[nxFileLine 資源 ](lnxFileLineResource.md) ─ 管理 Linux 檔案中的個別程式碼行。</span><span class="sxs-lookup"><span data-stu-id="18b19-111">[nxFileLine Resource](lnxFileLineResource.md)--Manages individual lines in a Linux file.</span></span> 
* <span data-ttu-id="18b19-112">[nxGroup 資源 ](lnxGroupResource.md) ─ 管理本機 Linux 群組。</span><span class="sxs-lookup"><span data-stu-id="18b19-112">[nxGroup Resource](lnxGroupResource.md)--Manages local Linux groups.</span></span> 
* <span data-ttu-id="18b19-113">[nxPackage 資源](lnxPackageResource.md)--管理 Linux 節點上的套件。</span><span class="sxs-lookup"><span data-stu-id="18b19-113">[nxPackage Resource](lnxPackageResource.md)--Manages packages on Linux nodes.</span></span>
* <span data-ttu-id="18b19-114">[nxScript 資源](lnxScriptResource.md)--在目標節點上執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="18b19-114">[nxScript Resource](lnxScriptResource.md)--Runs scripts on target nodes.</span></span>
* <span data-ttu-id="18b19-115">[nxService 資源 ](lnxServiceResource.md) ─ 管理 Linux 服務 (精靈)。</span><span class="sxs-lookup"><span data-stu-id="18b19-115">[nxService Resource](lnxServiceResource.md)--Manages Linux services (daemons).</span></span>
* <span data-ttu-id="18b19-116">[nxSshAuthorizedKeys 資 源](lnxSshAuthorizedKeysResource.md) ─ 管理 Linux 使用者的公用 SSH 金鑰。</span><span class="sxs-lookup"><span data-stu-id="18b19-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Manages public ssh keys for a Linux user.</span></span> 
* <span data-ttu-id="18b19-117">[nxUser 資源 ](lnxUserResource.md) ─ 管理本機 Linux 使用者。</span><span class="sxs-lookup"><span data-stu-id="18b19-117">[nxUser Resource](lnxUserResource.md)--Manages local Linux users.</span></span> 
  
