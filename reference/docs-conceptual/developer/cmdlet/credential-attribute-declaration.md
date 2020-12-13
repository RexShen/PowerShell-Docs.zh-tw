---
ms.date: 09/13/2016
ms.topic: reference
title: 認證屬性宣告
description: 認證屬性宣告
ms.openlocfilehash: fb826d9a46cadc021fe0c667091bbc7a9251aaa8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648605"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="9d286-103">認證屬性宣告</span><span class="sxs-lookup"><span data-stu-id="9d286-103">Credential Attribute Declaration</span></span>

<span data-ttu-id="9d286-104">Credential 屬性是選擇性的屬性，可與類型為 system.string 的 Credential 參數一起 [使用，讓](/dotnet/api/System.Management.Automation.PSCredential) 字串也可以當做引數傳遞給參數。</span><span class="sxs-lookup"><span data-stu-id="9d286-104">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="9d286-105">當這個屬性加入至參數宣告時，Windows PowerShell 會將字串輸入轉換為 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 物件。</span><span class="sxs-lookup"><span data-stu-id="9d286-105">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="9d286-106">例如， [取得認證](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) 指令程式會使用這個屬性來讓 Windows PowerShell 產生 Cmdlet 所傳回的 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 物件。</span><span class="sxs-lookup"><span data-stu-id="9d286-106">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="9d286-107">語法</span><span class="sxs-lookup"><span data-stu-id="9d286-107">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="9d286-108">備註</span><span class="sxs-lookup"><span data-stu-id="9d286-108">Remarks</span></span>

- <span data-ttu-id="9d286-109">一般來說，這個屬性是由類型為 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 的參數使用，因此字串也可以當做引數傳遞給參數。</span><span class="sxs-lookup"><span data-stu-id="9d286-109">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="9d286-110">當將 [system.string 物件傳遞](/dotnet/api/System.Management.Automation.PSCredential) 給參數時，Windows PowerShell 不會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="9d286-110">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="9d286-111">建立 [system.string 物件時](/dotnet/api/System.Management.Automation.PSCredential) ，Windows PowerShell 會使用目前的主控制項向使用者顯示適當的提示。</span><span class="sxs-lookup"><span data-stu-id="9d286-111">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="9d286-112">例如，當使用這個屬性時，預設主控制項會顯示提示輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="9d286-112">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="9d286-113">但是，如果使用自訂主機來定義不同的提示，則會顯示該提示。</span><span class="sxs-lookup"><span data-stu-id="9d286-113">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="9d286-114">這個屬性會與參數屬性搭配使用。</span><span class="sxs-lookup"><span data-stu-id="9d286-114">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="9d286-115">如需該屬性的詳細資訊，請參閱 [參數屬性聲明](./parameter-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="9d286-115">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="9d286-116">Credential 屬性是由 [Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) 類別所定義。</span><span class="sxs-lookup"><span data-stu-id="9d286-116">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d286-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d286-117">See Also</span></span>

[<span data-ttu-id="9d286-118">參數別名</span><span class="sxs-lookup"><span data-stu-id="9d286-118">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="9d286-119">參數屬性宣告</span><span class="sxs-lookup"><span data-stu-id="9d286-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="9d286-120">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9d286-120">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
