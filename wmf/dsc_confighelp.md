# DSC 設定的說明支援

您現在可以使用 DSC 設定內以註解為基礎的說明，並取得呼叫具有 `-?` 的設定函式時，該設定使用方式的說明：  

首先，我們定義兩個稱為 HelpSample1 和 HelpSample2 的定義函式，包括它們以註解為基礎的說明︰

```powershell
<#
.SYNOPSIS
The synopsis for the configuration goes here. This can be one line, or many.

.DESCRIPTION
The description for the configuration is usually a longer, more detailed explanation of what the script or function does. Use as many lines as you need.

.PARAMETER computername
Here, the dotted keyword is followed by a single parameter name. Don't precede that with a hyphen. The following lines describe the purpose of the parameter:

.PARAMETER filePath
Provide a PARAMETER section for each parameter that your script or function accepts.

.EXAMPLE
There's no need to number your examples.

.EXAMPLE
Windows PowerShell will number them for you when it displays your help text to a user.
#>

configuration HelpSample1
{
    param([string]$computername,[string]$filePath)
    File f
    {
        Contents="Hello World"
        DestinationPath = "c:\Destination.txt"
    }
}

<#
.SYNOPSIS
The synopsis for the configuration HelpSample2 goes here. This can be one line, or many.

.DESCRIPTION
The description for the configuration bar is usually a longer, more detailed explanation of what the script or function does. Take as many lines as you need.

.PARAMETER computername
Here, the dotted keyword is followed by a single parameter name. Don't precede that with a hyphen. The following lines describe the purpose of the parameter:

.PARAMETER filePath
Provide a PARAMETER section for each parameter that your script or function accepts.

.EXAMPLE
There's no need to number your examples.

.EXAMPLE
Windows PowerShell will number them for you when it displays your help text to a user.

#>

configuration HelpSample2
{
    param([string]$computername,[string]$filePath)

    File f
    {
        Contents="Hello World"
        DestinationPath = "c:\Destination.txt"
    }
}
```

若要取得 HelpSample1 的說明，只要執行下列項目即可︰

```powershell
HelpSample1 -?
```

```
NAME
HelpSample1

SYNOPSIS
The synopsis for the configuration goes here. This can be one line, or many.

SYNTAX
HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-computername] <String>] [[-filePath] <String>] [<CommonParameters>]

DESCRIPTION
The description for the configuration is usually a longer, more detailed explanation of what the script or function does. Take as many lines as you need.

RELATED LINKS

REMARKS

To see the examples, type: "get-help HelpSample1 -examples".
For more information, type: "get-help HelpSample1 -detailed".
For technical information, type: "get-help HelpSample1 -full".
```

您也可以使用 Get-help 取得詳細的說明 ︰

```powershell
get-help HelpSample2 -detailed
```

```
NAME
HelpSample2

SYNOPSIS
The synopsis for the configuration HelpSample2 goes here. This can be one line, or many.

SYNTAX
HelpSample2 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-computername] <String>] [[-filePath] <String>] [<CommonParameters>]

DESCRIPTION
The description for the configuration bar is usually a longer, more detailed explanation of what the script or function does. Take as many lines as you need.

PARAMETERS
-InstanceName <String>
-DependsOn <String[]>
-OutputPath <String>
-ConfigurationData <Hashtable>
-computername <String>

Here, the dotted keyword is followed by a single parameter name. Don't precede that with a hyphen. The following lines describe the purpose of the parameter:

-filePath <String>

Provide a PARAMETER section for each parameter that your script or function accepts.

<CommonParameters>

This cmdlet supports the common parameters: Verbose, Debug,
ErrorAction, ErrorVariable, WarningAction, WarningVariable,
OutBuffer, PipelineVariable, and OutVariable. For more information, see
about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

-------------------------- EXAMPLE 1 --------------------------

PS C:\>There's no need to number your examples.

-------------------------- EXAMPLE 2 --------------------------

PS C:\>Windows PowerShell will number them for you when it displays your help text to a user.

REMARKS
To see the examples, type: "get-help HelpSample2 -examples".
For more information, type: "get-help HelpSample2 -detailed".
For technical information, type: "get-help HelpSample2 -full".
```<!--HONumber=Mar16_HO2-->
