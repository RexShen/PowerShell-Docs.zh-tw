---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: 資源庫,powershell,cmdlet,psget
title: psget_moduledependencypopulation
ms.openlocfilehash: c4c9f203e9c526ff532c2388acb6334515d66934
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a>在發行作業期間準備模組相依性的邏輯
1.  列為 RequiredModules 一部分的模組視為相依性。
2.  列為 NestedModules 一部分的模組 (其模組基底不在指定的模組基底下) 視為相依性。

3.  相同目標存放庫上應該會有上述相依性，否則發行作業將會導致錯誤。
    例如：如果存放庫上沒有 'SnippetPx'，則會擲回下列錯誤。
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  有些模組相依性可以在外部進行管理，在該情況下，應該將它們新增至模組資訊清單的 PSData 區段中的 ExternalModuleDependencies 項目。
    上述錯誤訊息中的下方組件
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

模組安裝期間，上方已備妥的相依性清單為安裝相依性之用。

請確定在發行作業期間，系統的 $env:PSModulePath 下具有您模組的相依性。