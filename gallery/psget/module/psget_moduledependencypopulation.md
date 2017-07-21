---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "資源庫,powershell,cmdlet,psget"
title: psget_moduledependencypopulation
ms.openlocfilehash: 126cd65ac35a31f4118474bc36dac1836ec0f22e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a><span data-ttu-id="55321-103">在發行作業期間準備模組相依性的邏輯</span><span class="sxs-lookup"><span data-stu-id="55321-103">Logic for preparing the module dependencies during Publish operation</span></span>
1.  <span data-ttu-id="55321-104">列為 RequiredModules 一部分的模組視為相依性。</span><span class="sxs-lookup"><span data-stu-id="55321-104">Modules listed as part of RequiredModules are considered as dependencies.</span></span>
2.  <span data-ttu-id="55321-105">列為 NestedModules 一部分的模組 (其模組基底不在指定的模組基底下) 視為相依性。</span><span class="sxs-lookup"><span data-stu-id="55321-105">Modules listed as part of NestedModules, whose module base is not under the specified module base, are considered as dependencies.</span></span>

3.  <span data-ttu-id="55321-106">相同目標存放庫上應該會有上述相依性，否則發行作業將會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="55321-106">Above dependencies should be available on the same target repository, otherwise publish operation will result in an error.</span></span>
    <span data-ttu-id="55321-107">例如：如果存放庫上沒有 'SnippetPx'，則會擲回下列錯誤。</span><span class="sxs-lookup"><span data-stu-id="55321-107">For example: If 'SnippetPx' is not available on the repository, below error will be thrown.</span></span>
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  <span data-ttu-id="55321-108">有些模組相依性可以在外部進行管理，在該情況下，應該將它們新增至模組資訊清單的 PSData 區段中的 ExternalModuleDependencies 項目。</span><span class="sxs-lookup"><span data-stu-id="55321-108">Some module dependencies can be managed externally, in that case they should be added to the ExternalModuleDependencies entry in the PSData section of the module manifest.</span></span>
    <span data-ttu-id="55321-109">上述錯誤訊息中的下方組件</span><span class="sxs-lookup"><span data-stu-id="55321-109">Below part in the above error message</span></span>
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

<span data-ttu-id="55321-110">模組安裝期間，上方已備妥的相依性清單為安裝相依性之用。</span><span class="sxs-lookup"><span data-stu-id="55321-110">*During the module installation, above prepared dependencies list is used for installing the dependencies.*</span></span>

<span data-ttu-id="55321-111">請確定在發行作業期間，系統的 $env:PSModulePath 下具有您模組的相依性。</span><span class="sxs-lookup"><span data-stu-id="55321-111">*Please ensure that your module’s dependencies are available under $env:PSModulePath on your system during publish operation.*</span></span>

