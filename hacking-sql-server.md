Tool Needed: PowerUpSQL
https://github.com/netspi/PowerUpSQL

## SQL Instance Enumeration
```
- Get-SQLServerInfo -Instance <instance_name>
Use this command to get more information about the SQL Server.

-  Get-SQLDatabase -Verbose
Use this to get database list.
```

| Attacker Perspective | PowerUpSQL Function |
| --- | --- |
| Unauthenticated | Get-SQLInstanceFile |
| Unauthenticated | Get-SQLInstanceUDPScan |
| Local User | Get-SQLInstanceLocal |
| Domain User | Get-SQLInstanceDomain |

## Testing Login Access

| Attacker Perspective | Attack | PowerUpSQL Function Example |
| --- | --- | --- |
| Unauthenticated | Dictionary Attacks | `Invoke-SQLAuditWeakLoginPw –Instance “Server1\Instance1” -UserFile c:\temp\users.txt –PassFile C:\temp\Passwords.txt` |
| Unauthenticated | Default Vendor Passwords | `Get-SQLInstanceFile C:\temp\Computers.txt \| Select Computername \| Get-SQLInstanceScanUDPThreaded –Verbose \| Get-SQLServerLoginDefaultPw -Verbose` |
| Local User | Excessive Login Priv | `Get-SQLInstance \| Get-SQLConnectionTest -Verbose` |
| Domain User | Excessive Login Pri | `Get-SQLInstanceDomain \| Get-SQLConnectionTestThreaded -Verbose` |
