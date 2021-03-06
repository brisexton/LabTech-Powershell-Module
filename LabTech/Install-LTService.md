# Install-LTService
## SYNOPSIS
This function will install the LabTech agent on the machine.
## SYNTAX
```powershell
Install-LTService [-Server] <String[]> [[-ServerPassword] <String>] [[-LocationID] <Int32>] [[-TrayPort] <Int32>] [[-Rename] <String>] [-Hide] [-SkipDotNet] [-Force] [-NoWait] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## DESCRIPTION
This function will install the LabTech agent on the machine with the specified server/password/location.
## PARAMETERS
### -Server &lt;String[]&gt;
This is the URL to your LabTech server. 

example: https://lt.domain.com

This is used to download the installation files.

(Get-LTServiceInfo|Select-Object -Expand 'Server Address' -ErrorAction SilentlyContinue)
```
Required                    true
Position                    1
Default value
Accept pipeline input       true (ByPropertyName)
Accept wildcard characters  false
```
### -ServerPassword &lt;String&gt;

```
Required                    false
Position                    2
Default value
Accept pipeline input       true (ByPropertyName)
Accept wildcard characters  false
```
### -LocationID &lt;Int32&gt;
This is the LocationID of the location that the agent will be put into.

(Get-LTServiceInfo).LocationID
```
Required                    false
Position                    3
Default value                0
Accept pipeline input       true (ByPropertyName)
Accept wildcard characters  false
```
### -TrayPort &lt;Int32&gt;
This is the port LTSvc.exe listens on for communication with LTTray processess.
```
Required                    false
Position                    4
Default value                0
Accept pipeline input       true (ByPropertyName)
Accept wildcard characters  false
```
### -Rename &lt;String&gt;
This will call Rename-LTAddRemove after the install.
```
Required                    false
Position                    5
Default value
Accept pipeline input       false
Accept wildcard characters  false
```
### -Hide &lt;SwitchParameter&gt;
This will call Hide-LTAddRemove after the install.
```
Required                    false
Position                    named
Default value                False
Accept pipeline input       false
Accept wildcard characters  false
```
### -SkipDotNet &lt;SwitchParameter&gt;
This will disable the error checking for the .NET 3.5 and .NET 2.0 frameworks during the install process.
```
Required                    false
Position                    named
Default value                False
Accept pipeline input       false
Accept wildcard characters  false
```
### -Force &lt;SwitchParameter&gt;
This will disable some of the error checking on the install process.
```
Required                    false
Position                    named
Default value                False
Accept pipeline input       false
Accept wildcard characters  false
```
### -NoWait &lt;SwitchParameter&gt;
This will skip the ending health check for the install process.

The function will exit once the installer has completed.
```
Required                    false
Position                    named
Default value                False
Accept pipeline input       false
Accept wildcard characters  false
```
### -WhatIf &lt;SwitchParameter&gt;

```
Required                    false
Position                    named
Default value
Accept pipeline input       false
Accept wildcard characters  false
```
### -Confirm &lt;SwitchParameter&gt;

```
Required                    false
Position                    named
Default value
Accept pipeline input       false
Accept wildcard characters  false
```
## EXAMPLES
### EXAMPLE 1
```powershell
PS C:\>Install-LTService -Server https://lt.domain.com -Password sQWZzEDYKFFnTT0yP56vgA== -LocationID 42

This will install the LabTech agent using the provided Server URL, Password, and LocationID.
```

## NOTES
Version:        1.8

Author:         Chris Taylor

Website:        labtechconsulting.com

Creation Date:  3/14/2016

Purpose/Change: Initial script development



Update Date: 6/1/2017

Purpose/Change: Updates for better overall compatibility, including better support for PowerShell V2



Update Date: 6/10/2017

Purpose/Change: Updates for pipeline input, support for multiple servers



Update Date: 6/24/2017

Purpose/Change: Update to detect Server Version and use updated URL format for LabTech 11 Patch 13.



Update Date: 8/24/2017

Purpose/Change: Update to use Clear-Variable. Additional Debugging.



Update Date: 8/29/2017

Purpose/Change: Additional Debugging.



Update Date: 9/7/2017

Purpose/Change: Support for ShouldProcess to enable -Confirm and -WhatIf.



Update Date: 1/26/2018

Purpose/Change: Added support for Proxy Server for Download and Installation steps.



Update Date: 2/13/2018

Purpose/Change: Added -TrayPort parameter.



Update Date: 3/13/2018

Purpose/Change: Added -NoWait parameter.

Added minimum size requirement for agent installer to detect and skip a bad file download.



Update Date: 6/5/2018

Purpose/Change: Added -SkipDotNet parameter.

Allows for skipping of .NET 3.5 and 2.0 framework checks for installing on OS with .NET 4.0+ already installed 
