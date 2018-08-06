---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: bcf897730881551ec16ce970de6a1330961b67e6
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268260"
---
# <a name="add-pswaauthorizationrule"></a>Add-PswaAuthorizationRule

## <a name="synopsis"></a>概要

在 Windows PowerShell Web 存取授權規則集中新增授權規則。

## <a name="syntax"></a>語法

### <a name="usergroupnamecomputergroupname"></a>UserGroupNameComputerGroupName

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a>UserGroupNameComputerName

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a>UserNameComputerGroupName

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a>UserNameComputerName

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a>描述

**Add-PswaAuthorizationRule** Cmdlet 會在 Windows PowerShell(r) Web 存取授權規則集中新增授權規則。

您必須指定此規則的使用者、電腦和 Windows PowerShell 端點。 您可以依個別使用者帳戶和電腦名稱指定使用者和電腦，或藉由指定群組進行指定。

對於已加入 Active Directory 網域的電腦，此 Cmdlet 會使用電腦的安全性識別碼 (SID) 來建立規則。 這可讓您在登入頁面的 [電腦名稱] 欄位中，使用簡短名稱、完整網域名稱 (FQDN) 或 IP 位址。

對於未加入 Active Directory 網域的電腦，此 Cmdlet 會使用系統管理員所提供的電腦名稱來建立規則。 若要成功連線到這部電腦，終端使用者必須提供與出現在規則中完全相同的電腦名稱。

如果網路上有多部同名的電腦，簡短名稱可能會解析成多部電腦。 這在建立連線時可能會導致模稜兩可的情況。 例如，如果有名為 "*Server1*" 之工作群組電腦的規則，並將名為 *server1.contoso.com* 的新電腦加入網路，則使用授權規則進行的驗證會成功，且 Windows PowerShell Web 存取會嘗試連線到名為 "*Server1*" 的電腦。 不保證會建立與指定工作群組電腦的連線，此嘗試可能是針對名為 "*Server1*" 的工作群組或網域電腦。 為了減少模稜兩可的情況，建議您盡可能針對目的地電腦使用 FQDN 來建立授權規則。

授權規則會評估 Windows PowerShell Web 存取使用者的主要登入認證，而不是替代認證 (在登入頁面的 [選用連線設定] 區段中找到的第二組認證)。 如需相關範例，請參閱範例 6。

## <a name="parameters"></a>參數

### <a name="-computergroupname-string"></a>-ComputerGroupName \<String\>

指定 Active Directory 網域服務 (AD DS) 或本機群組中，此規則授與存取權的電腦群組名稱。

|||
|-|-|
| 別名                     | 無                  |
| 必要？                   | true                  |
| 位置？                   | 具名                 |
| 預設值               | 無                  |
| 接受管線輸入？      | True (ByPropertyName) |
| 接受萬用字元？ | false                 |

### <a name="-computername-string"></a>-ComputerName \<String\>

指定此規則授與存取權的電腦名稱。

|||
|-|-|
| 別名                     | 無                  |
| 必要？                   | true                  |
| 位置？                   | 具名                 |
| 預設值               | 無                  |
| 接受管線輸入？      | True (ByPropertyName) |
| 接受萬用字元？ | false                 |

### <a name="-configurationname-string"></a>-ConfigurationName \<String\>

指定此規則授與存取權的 Windows PowerShell 工作階段設定名稱，也稱為 Runspace。

|||
|-|-|
| 別名                     | 無                  |
| 必要？                   | true                  |
| 位置？                   | 具名                 |
| 預設值               | 無                  |
| 接受管線輸入？      | True (ByPropertyName) |
| 接受萬用字元？ | false                 |

### <a name="-credential--pscredential"></a>-Credential \<PSCredential\>

指定您要用來變更 Windows PowerShell Web 存取授權規則之使用者帳戶的 **PSCredential** 物件。 如果您未新增這個參數，此 Cmdlet 就會使用目前登入的使用者帳戶。 若要取得從遠端新增授權規則所需的 **PSCredential** 物件，請執行 [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) Cmdlet。

|||
|-|-|
| 別名                     | 無  |
| 必要？                   | false |
| 位置？                   | 具名 |
| 預設值               | 無  |
| 接受管線輸入？      | false |
| 接受萬用字元？ | false |

### <a name="-force"></a>-Force

強制執行命令而不要求使用者確認。 此外，當您輸入簡單或簡短電腦名稱時 (例如非網域名稱的名稱或不完整的名稱)，它也會提示確認。 為了安全起見會要求確認，讓您只有在電腦位於工作群組時，才能使用簡單名稱來新增電腦。

|||
|-|-|
| 別名                              | 無                                 |
| 必要？                            | false                                |
| 位置？                            | 具名                                |
| 預設值                        | 無                                 |
| 接受管線輸入？               | false                                |
| 接受萬用字元？          | false                                |

### <a name="-rulename-string"></a>-RuleName \<String\>

指定此規則的易記名稱。

|||
|-|-|
| 別名                              | 無                                 |
| 必要？                            | false                                |
| 位置？                            | 具名                                |
| 預設值                        | 無                                 |
| 接受管線輸入？               | True (ByPropertyName)                |
| 接受萬用字元？          | false                                |

### <a name="-usergroupname-string"></a>-UserGroupName \<String\[\]\>

指定 AD DS 或本機群組中，此規則授與存取權的一或多個使用者群組名稱。

|||
|-|-|
| 別名                              | 無                                 |
| 必要？                            | true                                 |
| 位置？                            | 具名                                |
| 預設值                        | 無                                 |
| 接受管線輸入？               | True (ByPropertyName)                |
| 接受萬用字元？          | false                                |

### <a name="-username-string"></a>-UserName \<String\[\]\>

指定此規則授與存取權的一或多個使用者。 使用者名稱可以是閘道電腦上的本機使用者帳戶，或是 AD DS 中的使用者。 格式是 `domain\user` 或 `computer\user`。

|||
|-|-|
| 別名                              | 無                                 |
| 必要？                            | true                                 |
| 位置？                            | 1                                    |
| 預設值                        | 無                                 |
| 接受管線輸入？               | True (ByValue, ByPropertyName)       |
| 接受萬用字元？          | false                                |

###  <a name="commonparameters"></a>\<CommonParameters\>

這個指令程式支援一般參數：

-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。
如需詳細資訊，請參閱 [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters)。

## <a name="inputs"></a>輸入

### <a name="string"></a>String

此 Cmdlet 會接受字串或字串陣列作為輸入。

### <a name="string"></a>String\[\]

此 Cmdlet 會接受字串或字串陣列作為輸入。

## <a name="outputs"></a>輸出

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule

此 Cmdlet 會傳回授權規則物件。

## <a name="examples"></a>範例

### <a name="example-1"></a>範例 1

這個範例會授權 _SMAdmins_ 群組中的使用者存取 _srv2_ 上的工作階段設定 _PSWAEndpoint_，這是有限制的 Runspace。

> [!NOTE]
> 電腦名稱必須是完整網域名稱 (FQDN)。 系統管理員會定義受限制的工作階段設定或 Runspace，也就是終端使用者可以執行之一組有限的 Cmdlet 和工作。 定義受限制的 Runspace 可防止使用者存取不在允許的 Windows PowerShell(r) Runspace 中的其他電腦，因此可提供更安全的連線。 如需工作階段設定的詳細資訊，請參閱 [about_Session_Configurations](/powershell/module/microsoft.powershell.core/about/about_session_configurations) 或[安裝和使用 Windows PowerShell Web 存取](../install-and-use-windows-powershell-web-access.md)。

```powershell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a>範例 2

此範例會授權名為 `contoso\user1`、`contoso\user2` 和 `contoso\user3` 之使用者群組中的使用者，存取 *srv2* 上的預設 Windows PowerShell 工作階段設定 `Microsoft.PowerShell`。 此 Cmdlet 會建立三個規則 (一人一個)。

```powershell
Add-PswaAuthorizationRule -UserName contoso\user1, contoso\user2, contoso\user3 -ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a>範例 3

此範例示範如何透過管線輸入使用者名稱值。

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule -ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a>範例 4

此範例示範所有參數如何依屬性名稱採用來自管線的值。

````powershell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" -PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a>範例 5

此範例會新增規則，允許名為 `PswaServer\ChrisLocal` 的本機使用者存取名為 **srv1.contoso.com** 的伺服器。

此範例描述閘道位於工作群組且目的地電腦位於網域的案例。 授權規則適用於閘道上的本機使用者。 在 Windows PowerShell Web 存取登入頁面上，若要成功驗證，使用者必須提供 [選用連線設定] 區域中的第二組認證。 閘道伺服器會使用這組額外的認證，在目的地電腦 (名為 *srv1.contoso.com* 的伺服器) 上驗證使用者。

````powershell
Add-PswaAuthorizationRule -UserName PswaServer\ChrisLocal -ComputerName srv1.contoso.com -ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a>範例 6

此範例允許所有使用者存取所有電腦上的所有端點。 這基本上就是關閉授權規則。

> [!NOTE]
> 不建議在有安全性顧慮的部署中使用萬用字元 `*`，只有在測試環境或不需要嚴格安全性的部署中才應考慮使用。

````powershell
Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a>另請參閱

[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)

[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)

[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)

[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)

[Add-Member](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936)