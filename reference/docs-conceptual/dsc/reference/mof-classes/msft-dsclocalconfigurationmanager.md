---
ms.date: 07/14/2020
ms.topic: reference
title: MSFT_DSCLocalConfigurationManager 類別
description: MSFT_DSCLocalConfigurationManager 類別
ms.openlocfilehash: 31112c7d15884699171ec732ac20b6960b0858a9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644804"
---
# <a name="msft_dsclocalconfigurationmanager-class"></a><span data-ttu-id="088e3-103">MSFT_DSCLocalConfigurationManager 類別</span><span class="sxs-lookup"><span data-stu-id="088e3-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="088e3-104">本機設定管理員 (LCM) 可控制設定檔的狀態，並會使用設定代理程式套用設定。</span><span class="sxs-lookup"><span data-stu-id="088e3-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="088e3-105">下列語法已經過受管理物件格式 (MOF) 程式碼簡化，並包含所有已繼承的屬性。</span><span class="sxs-lookup"><span data-stu-id="088e3-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="088e3-106">語法</span><span class="sxs-lookup"><span data-stu-id="088e3-106">Syntax</span></span>

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="088e3-107">成員</span><span class="sxs-lookup"><span data-stu-id="088e3-107">Members</span></span>

<span data-ttu-id="088e3-108">**MSFT_DSCLocalConfigurationManager** 類別有以下成員：</span><span class="sxs-lookup"><span data-stu-id="088e3-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

- <span data-ttu-id="088e3-109">[方法][]</span><span class="sxs-lookup"><span data-stu-id="088e3-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="088e3-110">方法</span><span class="sxs-lookup"><span data-stu-id="088e3-110">Methods</span></span>

<span data-ttu-id="088e3-111">**MSFT_DSCLocalConfigurationManager** 類別有這些方法。</span><span class="sxs-lookup"><span data-stu-id="088e3-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="088e3-112">方法</span><span class="sxs-lookup"><span data-stu-id="088e3-112">Methods</span></span> |<span data-ttu-id="088e3-113">描述</span><span class="sxs-lookup"><span data-stu-id="088e3-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="088e3-114">ApplyConfiguration(boolean)</span><span class="sxs-lookup"><span data-stu-id="088e3-114">ApplyConfiguration(boolean)</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="088e3-115">使用設定代理程式套用擱置中的設定。</span><span class="sxs-lookup"><span data-stu-id="088e3-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>|
| [<span data-ttu-id="088e3-116">DisableDebugConfiguration()</span><span class="sxs-lookup"><span data-stu-id="088e3-116">DisableDebugConfiguration()</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="088e3-117">停用 DSC 資源偵錯。</span><span class="sxs-lookup"><span data-stu-id="088e3-117">Disables DSC resource debugging.</span></span>|
| [<span data-ttu-id="088e3-118">EnableDebugConfiguration(boolean)</span><span class="sxs-lookup"><span data-stu-id="088e3-118">EnableDebugConfiguration(boolean)</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="088e3-119">啟用 DSC 資源偵錯。</span><span class="sxs-lookup"><span data-stu-id="088e3-119">Enables DSC resource debugging.</span></span>|
| [<span data-ttu-id="088e3-120">GetConfiguration()</span><span class="sxs-lookup"><span data-stu-id="088e3-120">GetConfiguration()</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="088e3-121">將設定文件傳送到受管理的節點，並使用設定代理程式的 **Get** 方法來套用設定。</span><span class="sxs-lookup"><span data-stu-id="088e3-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="088e3-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="088e3-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="088e3-123">取得與特定工作相關的設定代理程式輸出。</span><span class="sxs-lookup"><span data-stu-id="088e3-123">Gets the Configuration Agent output relating to a specific job.</span></span>|
| [<span data-ttu-id="088e3-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="088e3-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="088e3-125">取得設定狀態歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="088e3-125">Get the configuration status history.</span></span>|
| [<span data-ttu-id="088e3-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="088e3-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="088e3-127">取得用於控制設定代理程式的 LCM 設定。</span><span class="sxs-lookup"><span data-stu-id="088e3-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>|
| [<span data-ttu-id="088e3-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="088e3-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="088e3-129">開始一致性檢查。</span><span class="sxs-lookup"><span data-stu-id="088e3-129">Starts the consistency check.</span></span>|
| [<span data-ttu-id="088e3-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="088e3-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="088e3-131">移除設定檔。</span><span class="sxs-lookup"><span data-stu-id="088e3-131">Removes the configuration files.</span></span>|
| [<span data-ttu-id="088e3-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="088e3-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="088e3-133">直接呼叫 DSC 資源的 **Get** 方法。</span><span class="sxs-lookup"><span data-stu-id="088e3-133">Directly calls the **Get** method of a DSC resource.</span></span>|
| [<span data-ttu-id="088e3-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="088e3-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="088e3-135">直接呼叫 DSC 資源的 **Set** 方法。</span><span class="sxs-lookup"><span data-stu-id="088e3-135">Directly calls the **Set** method of a DSC resource.</span></span>|
| [<span data-ttu-id="088e3-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="088e3-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="088e3-137">直接呼叫 DSC 資源的 **Test** 方法。</span><span class="sxs-lookup"><span data-stu-id="088e3-137">Directly calls the **Test** method of a DSC resource.</span></span>|
| [<span data-ttu-id="088e3-138">RollBack</span><span class="sxs-lookup"><span data-stu-id="088e3-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="088e3-139">復原回先前的設定。</span><span class="sxs-lookup"><span data-stu-id="088e3-139">Rolls back to a previous configuration.</span></span>|
| [<span data-ttu-id="088e3-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="088e3-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="088e3-141">將設定文件傳送到受管理的節點，並將其儲存為擱置變更。</span><span class="sxs-lookup"><span data-stu-id="088e3-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>|
| [<span data-ttu-id="088e3-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="088e3-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="088e3-143">將設定文件傳送到受管理的節點，並使用設定代理程式套用設定。</span><span class="sxs-lookup"><span data-stu-id="088e3-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="088e3-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="088e3-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="088e3-145">將設定文件傳送到受管理的節點，並開始使用設定代理程式套用設定。</span><span class="sxs-lookup"><span data-stu-id="088e3-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="088e3-146">使用 GetConfigurationResultOutput 來擷取結果輸出。</span><span class="sxs-lookup"><span data-stu-id="088e3-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>|
| [<span data-ttu-id="088e3-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="088e3-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="088e3-148">設定用於控制設定代理程式的 LCM 設定。</span><span class="sxs-lookup"><span data-stu-id="088e3-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>|
| [<span data-ttu-id="088e3-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="088e3-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="088e3-150">停止進行中的設定。</span><span class="sxs-lookup"><span data-stu-id="088e3-150">Stops the configuration that is in progress.</span></span>|
| [<span data-ttu-id="088e3-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="088e3-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="088e3-152">將設定文件傳送到受管理的節點，並對文件驗證目前的設定。</span><span class="sxs-lookup"><span data-stu-id="088e3-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>|

## <a name="requirements"></a><span data-ttu-id="088e3-153">需求</span><span class="sxs-lookup"><span data-stu-id="088e3-153">Requirements</span></span>

<span data-ttu-id="088e3-154">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="088e3-154">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="088e3-155">**Namespace** ：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="088e3-155">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>
