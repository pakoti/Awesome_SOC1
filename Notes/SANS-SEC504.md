# SANS SEC 504
Incident Response and Cyber Investigations

## Powershell Commands 


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