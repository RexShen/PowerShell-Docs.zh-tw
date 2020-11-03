---
description: 描述適用于 .NET framework 類別的型別加速器
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/01/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_type_accelerators?view=powershell-6.0&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Type_Accelerators
ms.openlocfilehash: 05b602a118cf5dfed3672d89dfce86e283d24266
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206832"
---
# <a name="about-type-accelerators"></a>關於類型加速器

## <a name="short-desription"></a>簡短說明
描述適用于 .NET framework 類別的型別加速器

## <a name="long-description"></a>詳細描述

型別加速器是 .NET framework 類別的別名。 它們可讓您存取特定的 .NET framework 類別，而不需要明確地輸入整個類別名稱。 例如，您可以將的 **AliasAttribute** 類別縮短 `[System.Management.Automation.AliasAttribute]` 為 `[Alias]` 。

> [!NOTE]
> 所有類型加速器仍需要以方括弧括住 (`[]`) 。

## <a name="available-type-accelerators"></a>可用的型別加速器

|        加速器          |                           完整類別名稱                           |
|---------------------------- | ------------------------------------------------------------------- |
|編輯器                         | DirectoryServices                             |
|adsisearcher                 | DirectoryServices. DirectorySearcher                          |
|Alias                        | AliasAttribute。                         |
|AllowEmptyCollection         | AllowEmptyCollectionAttribute。          |
|AllowEmptyString             | AllowEmptyStringAttribute。              |
|AllowNull                    | AllowNullAttribute。                     |
|ArgumentCompleter            | ArgumentCompleterAttribute。             |
|ArgumentCompletions          | ArgumentCompletionsAttribute。           |
|array                        | System.Array                                                        |
|bigint                       | BigInteger                                          |
|bool                         | System.Boolean                                                      |
|byte                         | System.Byte                                                         |
|char                         | System.Char                                                         |
|cimclass                     | CimClass。                        |
|cimconverter                 | CimConverter。                    |
|ciminstance                  | Microsoft.Management.Infrastructure.CimInstance                     |
|CimSession                   | Microsoft.Management.Infrastructure.CimSession                      |
|cimtype                      | CimType。                         |
|CmdletBinding                | CmdletBindingAttribute。                 |
|cultureinfo                  | System.Globalization.CultureInfo                                    |
|Datetime                     | System.DateTime                                                     |
|decimal                      | System.Decimal                                                      |
|double                       | System.Double                                                       |
|DscLocalConfigurationManager | DscLocalConfigurationManagerAttribute。  |
|DscProperty                  | DscPropertyAttribute。                   |
|DscResource                  | DscResourceAttribute。                   |
|ExperimentAction             | ExperimentAction。                       |
|實驗                 | Core.experimentalattribute。                  |
|ExperimentalFeature          | ExperimentalFeature。                    |
|float                        | System.Single                                                       |
|guid                         | System.Guid                                                         |
|雜湊表                    | System.Collections.Hashtable                                        |
|>initialsessionstate          | System.Management.Automation.Runspaces.InitialSessionState          |
|int                          | System.Int32                                                        |
|int16                        | System.Int16                                                        |
|int32                        | System.Int32                                                        |
|int64                        | System.Int64                                                        |
|址                    | 系統 .Net IPAddress                                                |
|IPEndpoint                   | System .Net. IPEndPoint                                               |
|long                         | System.Int64                                                        |
|mailaddress                  | 系統 .Net MailAddress                                         |
|NullString                   | NullString （英文）                    |
|ObjectSecurity               | AccessControl. ObjectSecurity                        |
|OutputType                   | OutputTypeAttribute。                    |
|參數                    | ParameterAttribute。                     |
|PhysicalAddress              | System.net.networkinformation.networkinformationexception. PhysicalAddress                       |
|powershell                   | 系統管理。 PowerShell                             |
|psaliasproperty              | PSAliasProperty。                        |
|pscredential                 | System.Management.Automation.PSCredential                           |
|pscustomobject               | System.Management.Automation.PSObject                               |
|PSDefaultValue               | System.Management.Automation.PSDefaultValueAttribute                |
|pslistmodifier               | PSListModifier。                         |
|psmoduleinfo                 | System.Management.Automation.PSModuleInfo                           |
|psnoteproperty               | PSNoteProperty。                         |
|psobject                     | System.Management.Automation.PSObject                               |
|psprimitivedictionary        | PSPrimitiveDictionary。                  |
|pspropertyexpression         | PSPropertyExpression。                  |
|psscriptmethod               | PSScriptMethod。                         |
|psscriptproperty             | PSScriptProperty。                       |
|PSTypeNameAttribute          | PSTypeNameAttribute。                    |
|system.management.automation.psvariable                   | System.Management.Automation.PSVariable                             |
|psvariableproperty           | PSVariableProperty。                     |
|ref                          | PSReference。                            |
|RegEx                        | System.Text.RegularExpressions.Regex                                |
|Runspace                     | 系統管理。運行空間                     |
|runspacefactory              | RunspaceFactory 的管理。              |
|sbyte                        | System.SByte                                                        |
|scriptblock                  | 系統管理. ScriptBlock                            |
|securestring                 | System.Security.SecureString                                        |
|semver                       | SemanticVersion。                        |
|short                        | System.Int16                                                        |
|single                       | System.Single                                                       |
|字串                       | System.String                                                       |
|SupportsWildcards            | SupportsWildcardsAttribute。             |
|switch                       | System.Management.Automation.SwitchParameter                        |
|時間範圍                     | System.TimeSpan                                                     |
|類型                         | System.Type                                                         |
|uint                         | System.UInt32                                                       |
|uint16                       | System.UInt16                                                       |
|uint32                       | System.UInt32                                                       |
|uint64                       | System.UInt64                                                       |
|ulong                        | System.UInt64                                                       |
|uri                          | System.Uri                                                          |
|ushort                       | System.UInt16                                                       |
|ValidateCount                | ValidateCountAttribute。                 |
|ValidateDrive                | ValidateDriveAttribute。                 |
|ValidateLength               | ValidateLengthAttribute。                |
|ValidateNotNull              | ValidateNotNullAttribute。               |
|ValidateNotNullOrEmpty       | ValidateNotNullOrEmptyAttribute。        |
|ValidatePattern              | ValidatePatternAttribute。               |
|ValidateRange                | ValidateRangeAttribute。                 |
|ValidateScript               | ValidateScriptAttribute。                |
|ValidateSet                  | ValidateSetAttribute。                   |
|ValidateTrustedData          | ValidateTrustedDataAttribute。           |
|ValidateUserDrive            | ValidateUserDriveAttribute。             |
|version                      | System.Version                                                      |
|void                         | System.Void                                                         |
|WildcardPattern              | WildcardPattern。                        |
|Wmi                          | System.Management.ManagementObject                                  |
|wmiclass                     | ManagementClass                                   |
|wmisearcher                  | ManagementObjectSearcher                          |
|System.security.cryptography.x509certificates.x500distinguishedname        | System.security.cryptography.x509certificates.x509certificate2. System.security.cryptography.x509certificates.x500distinguishedname。 |
|X509Certificate              | System.security.cryptography.x509certificates.x509certificate2. X509Certificate。       |
|xml                          | System.Xml.XmlDocument                                              |
