---
ms.date: 07/17/2020
ms.topic: reference
title: DSC for Linux nxSshAuthorizedKeys 資源
description: DSC for Linux nxSshAuthorizedKeys 資源
ms.openlocfilehash: 881e94aa583a745cdac7f01b6e445352ef4ca937
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662754"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="d8809-103">DSC for Linux nxSshAuthorizedKeys 資源</span><span class="sxs-lookup"><span data-stu-id="d8809-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="d8809-104">PowerShell 預期狀態設定 (DSC) 的 **nxAuthorizedKeys** 資源會提供一個機制，管理指定使用者的授權 SSH 金鑰。</span><span class="sxs-lookup"><span data-stu-id="d8809-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8809-105">語法</span><span class="sxs-lookup"><span data-stu-id="d8809-105">Syntax</span></span>

```Syntax
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="d8809-106">屬性</span><span class="sxs-lookup"><span data-stu-id="d8809-106">Properties</span></span>

|<span data-ttu-id="d8809-107">屬性</span><span class="sxs-lookup"><span data-stu-id="d8809-107">Property</span></span> |<span data-ttu-id="d8809-108">描述</span><span class="sxs-lookup"><span data-stu-id="d8809-108">Description</span></span> |
|---|---|
|<span data-ttu-id="d8809-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="d8809-109">KeyComment</span></span> |<span data-ttu-id="d8809-110">金鑰的唯一註解。</span><span class="sxs-lookup"><span data-stu-id="d8809-110">A unique comment for the key.</span></span> <span data-ttu-id="d8809-111">這用來唯一識別金鑰。</span><span class="sxs-lookup"><span data-stu-id="d8809-111">This is used to uniquely identify keys.</span></span> |
|<span data-ttu-id="d8809-112">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="d8809-112">Username</span></span> |<span data-ttu-id="d8809-113">要為其管理 SSH 授權金鑰的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="d8809-113">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="d8809-114">如果未定義，則預設使用者為 **root** 。</span><span class="sxs-lookup"><span data-stu-id="d8809-114">If not defined, the default user is **root** .</span></span> |
|<span data-ttu-id="d8809-115">Key</span><span class="sxs-lookup"><span data-stu-id="d8809-115">Key</span></span> |<span data-ttu-id="d8809-116">金鑰的內容。</span><span class="sxs-lookup"><span data-stu-id="d8809-116">The contents of the key.</span></span> <span data-ttu-id="d8809-117">如果 **Ensure** 設定為 **Present** ，則此項目為必要。</span><span class="sxs-lookup"><span data-stu-id="d8809-117">This is required if **Ensure** is set to **Present** .</span></span>|

## <a name="common-properties"></a><span data-ttu-id="d8809-118">通用屬性</span><span class="sxs-lookup"><span data-stu-id="d8809-118">Common properties</span></span>

|<span data-ttu-id="d8809-119">屬性</span><span class="sxs-lookup"><span data-stu-id="d8809-119">Property</span></span> |<span data-ttu-id="d8809-120">描述</span><span class="sxs-lookup"><span data-stu-id="d8809-120">Description</span></span> |
|---|---|
|<span data-ttu-id="d8809-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d8809-121">DependsOn</span></span> |<span data-ttu-id="d8809-122">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="d8809-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d8809-123">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="d8809-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="d8809-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="d8809-124">Ensure</span></span> |<span data-ttu-id="d8809-125">指定是否已定義金鑰。</span><span class="sxs-lookup"><span data-stu-id="d8809-125">Specifies whether the key is defined.</span></span> <span data-ttu-id="d8809-126">將此屬性設定為 **Absent** 以確保索引鍵不存在於使用者的授權金鑰檔案中。</span><span class="sxs-lookup"><span data-stu-id="d8809-126">Set this property to **Absent** to ensure the key does not exist in the user's authorized keys file.</span></span> <span data-ttu-id="d8809-127">將其設定為 **Present** ，以確保使用者的授權金鑰檔中定義了金鑰。</span><span class="sxs-lookup"><span data-stu-id="d8809-127">Set it to **Present** to ensure the key is defined in the user's authorized key file.</span></span> |

## <a name="example"></a><span data-ttu-id="d8809-128">範例</span><span class="sxs-lookup"><span data-stu-id="d8809-128">Example</span></span>

<span data-ttu-id="d8809-129">下列範例會定義使用者 "monuser" 的公用 SSH 授權金鑰。</span><span class="sxs-lookup"><span data-stu-id="d8809-129">The following example defines a public ssh authorized key for the user "monuser".</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxSshAuthorizedKeys myKey
    {
        KeyComment = "myKey"
        Ensure = "Present"
        Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
        UserName = "monuser"
    }
}
```
