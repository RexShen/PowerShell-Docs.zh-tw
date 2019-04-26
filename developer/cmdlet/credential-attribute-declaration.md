---
title: 認證屬性宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068312"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="02c7c-102">認證屬性宣告</span><span class="sxs-lookup"><span data-stu-id="02c7c-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="02c7c-103">認證屬性是選擇性屬性，可與認證參數的型別[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)以便字串也會做為引數傳遞至參數。</span><span class="sxs-lookup"><span data-stu-id="02c7c-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="02c7c-104">當這個屬性會加入至參數宣告中時，Windows PowerShell 會將轉換成字串輸入[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)物件。</span><span class="sxs-lookup"><span data-stu-id="02c7c-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="02c7c-105">例如， [Get-credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential)指令程式會使用此屬性，產生的 Windows powershell [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) cmdlet 所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="02c7c-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="02c7c-106">語法</span><span class="sxs-lookup"><span data-stu-id="02c7c-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="02c7c-107">備註</span><span class="sxs-lookup"><span data-stu-id="02c7c-107">Remarks</span></span>

- <span data-ttu-id="02c7c-108">通常這個屬性會由型別參數[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)以便字串也會做為引數傳遞至參數。</span><span class="sxs-lookup"><span data-stu-id="02c7c-108">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="02c7c-109">當[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)物件傳遞給參數，Windows PowerShell 不會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="02c7c-109">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="02c7c-110">建立時[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)物件時，Windows PowerShell 會使用目前的主機來向使用者顯示適當的提示。</span><span class="sxs-lookup"><span data-stu-id="02c7c-110">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="02c7c-111">比方說，預設主機會顯示使用者名稱和密碼的提示時使用這個屬性時。</span><span class="sxs-lookup"><span data-stu-id="02c7c-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="02c7c-112">不過，如果正在使用自訂主機，定義不同的提示字元，則會顯示該提示。</span><span class="sxs-lookup"><span data-stu-id="02c7c-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="02c7c-113">這個屬性可搭配參數屬性。</span><span class="sxs-lookup"><span data-stu-id="02c7c-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="02c7c-114">如需有關該屬性的詳細資訊，請參閱 <<c0> [ 參數的屬性宣告](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="02c7c-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="02c7c-115">認證屬性所定義[System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute)類別。</span><span class="sxs-lookup"><span data-stu-id="02c7c-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="02c7c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02c7c-116">See Also</span></span>

[<span data-ttu-id="02c7c-117">參數別名</span><span class="sxs-lookup"><span data-stu-id="02c7c-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="02c7c-118">參數屬性宣告</span><span class="sxs-lookup"><span data-stu-id="02c7c-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="02c7c-119">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="02c7c-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
