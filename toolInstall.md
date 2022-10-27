=======

PowerShell
----------
PowerShell is a Windows built-in command line tool. No need to be installed.
However, an execution policy option should be set in order that a server computer could run scripts and so on.
See [Microsoft Official Doc](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.1) for more about execution policies.

Note: Start PowerShell with the **Run as administrator** option, then tap the command:
```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```
![image_installPS][installPS]


Pester
----------
Pester is a test and mock framework for PowerShell. Pester version 3.4.0 ships as part of Windows 10 and Windows server 2016.
Currently, the latest stable version is **5.1.1**.
To install Pester, firstly start PowerShell with the **Run as administrator** option.
Then **enable TLS 1.2** for the current PowerShell instance:
```
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
```
Then **remove the built-in vesion** of Pester with the commands below:
```
$module = "C:\Program Files\WindowsPowerShell\Modules\Pester"
takeown /F $module /A /R
icacls $module /reset
icacls $module /grant "*S-1-5-32-544:F" /inheritance:d /T
Remove-Item -Path $module -Recurse -Force -Confirm:$false
```
For PowerShell Module installation, you may need [NuGet](https://www.nuget.org/) if you did not have one, the package manager for .Net projects.
To install NuGet, use the command:
```
Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force
```
At last, you can properly install the latest stable version of Pester with the command:
```
Install-Module -Name Pester -Force
```

For more information, please see pester [official docs](https://pester.dev/docs/introduction/installation) and [GitHub source](https://github.com/pester/Pester).


Tortoise SVN
----------
Recommended version: [V1.14.0](https://tortoisesvn.net/downloads.html)

Note: Check the `command line client tools` box during installation.

![image_installTortoise][installTortoise]


Visual studio 2005
----------
Please see [this document](Dotnet3_5-Install.pptx).

The procedure below is an old one and doesn't work anymore:

~~The version we use for our SIL / GTNG toolset:~~
```
http://svn.fbrakes.com/svn/RD_Global_Activities/On_Going/RD_4000_Tools_management/RD_4100_Tools_storage/44-VisualStudio2005
```


UNIVW
----------
UNIVW is part of MM6X toolset. MM6X installation exe is located here:
```
http://svn/svn/RD_Global_Activities/On_Going/RD_4000_Tools_management/RD_4100_Tools_storage/21-MM6X
```


[installPS]: http://svn/svn/Benches_Tools/Wiki/images/installPS.png
[installTortoise]: http://svn/svn/Benches_Tools/Wiki/images/installTortoise.png
