---
title: Credential 屬性宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369887"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="f2e56-102">認證屬性宣告</span><span class="sxs-lookup"><span data-stu-id="f2e56-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="f2e56-103">Credential 屬性是選擇性的屬性，可與 system.servicemodel 類型的 Credential 參數搭配使用[，讓](/dotnet/api/System.Management.Automation.PSCredential)字串也可以當做引數傳遞給參數。</span><span class="sxs-lookup"><span data-stu-id="f2e56-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="f2e56-104">當此屬性加入至參數宣告時，Windows PowerShell 會將字串輸入轉換成[system.web](/dotnet/api/System.Management.Automation.PSCredential)物件。</span><span class="sxs-lookup"><span data-stu-id="f2e56-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="f2e56-105">例如， [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) Cmdlet 會使用這個屬性，讓 Windows PowerShell 產生由 Cmdlet[傳回的 system.servicemodel 物件。](/dotnet/api/System.Management.Automation.PSCredential)</span><span class="sxs-lookup"><span data-stu-id="f2e56-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="f2e56-106">語法</span><span class="sxs-lookup"><span data-stu-id="f2e56-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="f2e56-107">備註</span><span class="sxs-lookup"><span data-stu-id="f2e56-107">Remarks</span></span>

- <span data-ttu-id="f2e56-108">這個屬性通常是由[system.object](/dotnet/api/System.Management.Automation.PSCredential)類型的參數使用，因此字串也可以當做引數傳遞給參數。</span><span class="sxs-lookup"><span data-stu-id="f2e56-108">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="f2e56-109">當[系統](/dotnet/api/System.Management.Automation.PSCredential)將 system.servicemodel 物件傳遞至參數時，Windows PowerShell 不會執行任何操作。</span><span class="sxs-lookup"><span data-stu-id="f2e56-109">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="f2e56-110">建立[system.web](/dotnet/api/System.Management.Automation.PSCredential)物件時，Windows PowerShell 會使用目前的主機向使用者顯示適當的提示。</span><span class="sxs-lookup"><span data-stu-id="f2e56-110">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="f2e56-111">例如，當使用此屬性時，預設主機會顯示使用者名稱和密碼的提示。</span><span class="sxs-lookup"><span data-stu-id="f2e56-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="f2e56-112">不過，如果使用自訂主機來定義不同的提示，則會顯示提示。</span><span class="sxs-lookup"><span data-stu-id="f2e56-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="f2e56-113">這個屬性會與參數屬性搭配使用。</span><span class="sxs-lookup"><span data-stu-id="f2e56-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="f2e56-114">如需該屬性的詳細資訊，請參閱[參數屬性](./parameter-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="f2e56-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="f2e56-115">Credential 屬性是由[Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute)類別所定義。</span><span class="sxs-lookup"><span data-stu-id="f2e56-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2e56-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2e56-116">See Also</span></span>

[<span data-ttu-id="f2e56-117">參數別名</span><span class="sxs-lookup"><span data-stu-id="f2e56-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="f2e56-118">參數屬性宣告</span><span class="sxs-lookup"><span data-stu-id="f2e56-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="f2e56-119">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f2e56-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
