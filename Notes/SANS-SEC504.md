# SANS SEC 504
Incident Response and Cyber Investigations

## Powershell Commands 
a Powerful tool for data access, analysis, and automation

<ul>
<li>Examining Processes</li>
<li>Identifying Suspicious Processes</li>
<li>Examining Network Usage</li>
<li>Identifying Suspicious Network Activity</li>
<li>Examining Services</li>
<li>Registry Interrogation</li>
<li>Unusual Accounts</li>
<li>Unusual Scheduled Tasks</li>
<li>Unusual Log Entries</li>
</ul>


| Functionality | Powershell | Legacy Command|
| --- | --- | --- |
|List processes|Get-Process|wmic.exe process|
|Network connections |Get-NetTNetworkconnection |netstat.exe -nao|
|List services |Get-Service|sc.exe query|
|Registry access |Get-ChildItem|reg.exe|
|List users |Get-LocalUser|net.exe user|
|List groups  |Get-LocalGroup|net.exe localgroup|
|List scheduled tasks |Get-ScheduledTask|schtasks.exe|
|Access Event Logs |Get-WinEvent|wevtutil.exe|
|Identify differences  |Compare-Object|fc.exe|





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

<ul>
<li>Abnormal for the associated process</li>
<li>Abnormal for the environment</li>
<li>Lateral movement implies connections to other internal hosts</li>
<li>Known malicious hosts/addresses</li>
</ul>


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

<ul>
<li>Look for unusual scheduled tasks: Get-ScheduledTask</li>
<li>Export scheduled task for command details: Export-ScheduledTask</li>
<li>Examine last run status: Get-ScheduledTaskInfo</li>
</ul>

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

Get events for a specific date range

``` powershell

    PS C:\> $start = Get-Date 3/1/2022;
    PS C:\> $end = Get-Date 3/31/2022;
    PS C:\> Get-WinEvent -FilterHashtable @{LogName='Security';
    StartTime=$start; EndTime=$end;}

```


Identify event log messages for new service installation.

``` powershell

    PS C:\WINDOWS\system32> Get-WinEvent -LogName System |
    Where-Object -Property Id -EQ 7045 |
    Format-List -Property TimeCreated,Message

```
# Network Investigations

## Useful tcpdump Options

Capture traffic for an interface. Can also use any

``` bash


    tcpdump -i interface


```


Capture traffic for an interface and write to a file.

``` bash


    tcpdump -i interface -w file


```



Read packets from a file and don't resolve hosts and ports.

``` bash


    tcpdump -r file -n


```




Read packets from a file, don't resolve, show as ASCII

``` bash


    tcpdump -r file -n -A 


```




capture packets from the vmnet42 interface and save them to the file called output.pcap

``` bash


    tcpdump -i vmnet42 -w output.pcap


```




read packets from a file called packets.pcap
``` bash


    tcpdump -nnr packets.pcap


```







## Berkeley Packet Filters BPF Examples 




Traffic going to or from host 8.8.8.8

``` bash


    tcpdump -r file 'host 8.8.8.8'


```





Traffic coming from host 8.8.8.8

``` bash


    tcpdump -r file 'src host 8.8.8.8'


```



Traffic where the src is not 8.8.8.8

``` bash


    tcpdump -r file 'not src host 8.8.8.8'

```






Only ICMP from 8.8.8.8

``` bash


    tcpdump -r file 'icmp and (src host 8.8.8.8)'


```

# Memory Investigations

## Volatility

Listing Processes

``` bash


    vol -q -f win10.0.22000.556.raw windows.pslist.PsList


```


Parent and Child Processes

``` bash


    vol -q -f win10.0.22000.556.raw windows.pstree.PsTree


```



Scanning for Network Connections 


``` bash


    vol -q -f win10.0.22000.556.raw windows.netscan.NetScan


```





Process Command Line


``` bash 


    vol -q -f win10.0.22000.556.raw windows.cmdline.CmdLine


```




| Volatility3 Module | capability | 
| --- | --- |
|windows.dlllist.DllList|List DLLs for processes|.
|windows.driverscan.DriverScan|List kernel modules|
|windows.envars.Envars|List environment variables|
|windows.filescan.FileScan|Scan for files|
|windows.dumpfiles.DumpFiles|Carve out files|
|windows.info.Info|Examine Windows version information|
|windows.hashdump.Hashdump|Retrieve password hashes|
|windows.privileges.Privs|List privileges by process|
|windows.registry.hivelist.HiveList|List registry hive offsets|
|windows.registry.printkey.PrintKey|Access keys with --offset|
|windows.registry.userassist.UserAssist|Enumerate programs run from the Start menu|
|windows.registry.certificates.Certificates|List trusted certificates in Windows cert. store|
|windows.svcscan.SvcScan|List service name, display name, and PID|


# Malware Investigations

## Basic Attributes


Calculate the SHA256 hash of a file on Windows

``` powershell 


    Get-FileHash file

```

View ASCII and 16-bit little endian Unicode strings in PS C:\tools\sysinternals> 

``` powershell 


    strings file


```




View the ASCII strings on Linux

``` bash 


    strings file


```




View 16-bit little endian Unicode strings on Linux

``` bash 


    strings -e l file


```



# DNS Interrogation


## DNS Zone Transfer in Windows



``` bash  

    C:\Users\Sec504> nslookup
    > server 81.4.108.41
    > set type=AXFR
    > ls -d zonetransfer.me

``` 

To run a zone transfer using dig

``` bash  

    dig @81.4.108.41 AXFR zonetransfer.me

``` 


## DNS Automated Interrogation


``` bash  

    $ dig AXFR holidayhackchallenge.com
    ; Transfer failed.
    $ sudo nmap --script dns-brute --script-args dns-
    brute.domain=holidayhackchallenge.com,dns-brute.threads=6,dns-
    brute.hostlist=./namelist.txt -sS -p 53

``` 



## DNS Reconnaissance Defenses



<ul>
<li>Do not allow zone transfers from just any system</li>
<li>Use split DNS</li>
<li>Inspect DNS server logs for signs of attack</li>


</ul>


## How to make money on malicious code:

<ul>
<li> Cryptocurrency miners</li>
<li> Spam and web-based advertising</li>
<li> Phishing: Email, phone, and targeted (spear) phishing</li>
<li> Denial-of-Service extortion</li>
<li> Keystroke loggers stealing financial information</li>
<li> Rent out armies of infected systems for all the above</li>
<li> RAM scrapers pulling CC numbers from POS terminals</li>
</ul>




## Website Reconnaissance 

<ul>
<li>search target website </li>
<li>search engine recon</li>
<li>wordlist generation</li>
<li>search related website</li>
<li>file meatdata</li>
<li>website Recon defense</li>
</ul>


## Dns Interrogation

dns is a wealth of valuable target information publicly available.

<ul>
<li>reveals target information </li>
<li>defenses(Disallow zone transfers,split pub and priv DNS)</li>
<li>interrogation techniques(Manual,auto interrogation,zone transfer)</li>
</ul>







