# SANS SEC 504
Incident Response and Cyber Investigations

## Powershell Commands 
a Powerful tool for data access, analysis, and automation

<ul>
<li>Examining Processes</li>
<li>Identifying Suspicious Processes</li>
<li>Examining Network Usage</li>
<li>Identifying Suspicious Network Activity</li>
<li></li>
<li></li>
<li></li>
<li></li>
<li>Unusual Log Entries</li>
</ul>


| Functionality | Powershell | Legacy Command|
| --- | --- | --- |
|List processes|Get-Process|wmic.exe process|




## Examining Processes

Get brief information about running processes

``` powershell

    Get-Process

```
Get brief information about a named process with wildcard

``` powershell

    Get-Process 'powersh*'
```

Detailed information

``` powershell

    Get-Process 'powershell' | Select-Object *

```



Remote systems

``` powershell

    Get-Process -ComputerName SEC504STUDENT

```

Get-CimInstance Process Data:Get-Process doesn't capture some useful process details

``` powershell

    Get-CimInstance -Class Win32_Process | Select-Object ProcessId,
ProcessName, CommandLin

```


Get the parent process details:


``` powershell


    PS C:\Users\Sec504> Get-Process 'lsass' | Select-Object -Property Id
    644
    PS C:\Users\Sec504> Get-CimInstance -Class Win32_Process |
    Where-Object -Property ParentProcessId -EQ 644
    ProcessId Name HandleCount WorkingSetSize VirtualSize
    --------- ---- ----------- -------------- -----------
    2608 cmd.exe 49 2908160 2203370045440

```

<code>Get-Process</code> uses Id but <code>Get-CimInstance</code> uses <code>ProcessId</code> to refer to the same information.

## Identifying Suspicious Processes

CyberChef is a web-based tool where you create recipes (series of data transformation operations) through a drag-
and-drop interface. For example, you can base64 encode and decode data, encode and decode URLs, extract IP
address, extract URLs, and much more.
You can access an online version of CyberChef at https://gchq.github.io/CyberChef/. If you would prefer to
download your own copy, you can do so from the CyberChef GitHub repository:
https://github.com/gchq/CyberChef


## Examining Network Usage

``` powershell

    Get-NetTCPConnection

```


``` powershell

    Get-NetTCPConnection -State Listen | Select-Object -Property
LocalAddress,LocalPort,OwningProcess
    
```

``` powershell

    Get-NetTCPConnection -RemoteAddress 10.10.75.1 | Select-Object
        CreationTime, LocalAddress, LocalPort, RemoteAddress,RemotePort,OwningProcess, State
    
```

## Identifying Suspicious Network Activity

## Examining Services

``` powershell

    Get-Service
    
```

``` powershell
    Get-Service fROBkOyR
    
```

``` powershell

    Get-CimInstance -ClassName Win32_Service | Format-List Name,Caption,Description,PathName
    
```


## Registry Interrogation

``` powershell

    Get-ChildItem 'HKLM:\SOFTWARE\Wow6432Node\Microsoft\Windows
\CurrentVersion\Uninstall\' | Select-Object PSChildName
    
```

``` powershell

    Get-ItemProperty 'HKLM:Software\Microsoft\Windows\CurrentVersion\Run'
    
```


## Unusual Accounts
Look for new, unexpected accounts in the administrators group

``` powershell

    Get-LocalUser
    
```

``` powershell

    Get-LocalUser | Where-Object { $_.Enabled -eq $True }
    
```

``` powershell

    Get-LocalGroup
    
```

``` powershell

    Get-LocalGroupMember Administrators
    
```

## Unusual Scheduled Tasks


``` powershell

    Get-ScheduledTask *Avast* | Select-Object -Property TaskName
    
```

``` powershell

    Export-ScheduledTask -TaskName 'AvastUpdatre'
    
```

``` powershell

    Get-ScheduledTaskInfo -TaskName 'AvastUpdatre' | Select-Object
LastRunTime
    
```

## Unusual Log Entries