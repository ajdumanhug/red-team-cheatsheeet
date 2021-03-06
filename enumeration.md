## Domain Enumeration
```
- Get-NetDomain
This command will give us information about the current domain like the domain name.

- Get-NetDomain -domain “Domain Name”
If you want to get the same results for another domain, use the above command.

- Get-DomainSID 
Use this command to get the domain SID (Security IDentifier is a unique ID number that a computer or domain controller uses to identify you).

- (Get-DomainPolicy).”system access” 
Use this command to get the policy of the current domain.

- Get-NetDomainController
Use this command to get information about the current domain controller (DC).

- Get-NetUser
Use this command to list all the users in the current domain with information about each  user.

- Get-UserProperty –Properties pwdlastset
Use this command to see the last password set of each user in the current domain.

- Get-NetComputer
Use this command to list all the computers in the current domain.

- Get-NetComputer –OperatingSystem "Windows 7 Ultimate"
Use this command to list all the operating systems “Windows 7 Ultimate”.

- Get-NetComputer -Ping
Use this command to get all the pingable computers (live hosts) in the current domain.

- Get-NetGroup
Use this command to get all the groups in the current domain.

- Get-NetGroup *admin*
Use this command to get all the groups that contain the word “admin” in the group name.

- Get-NetGroupMember -GroupName "Domain Admins"
Use this command to get the members of the group “Domain Admin”.

- Get-NetGroup –UserName "aj"
Use this command to get the group membership of the user “aj”.

- Get-NetLocalGroup –ComputerName Client-02
Use this command to get all the local administrators on a machine. (Note that it needs administrative rights).

- Get-NetLoggedon –ComputerName “Client-02”
Use this command to get actively logged users on a computer (Note that it needs administrative rights)

- Get-LastLoggedOn –ComputerName Client-02
Use this command to get the last logged user on a computer (Note that it needs administrative rights)

- Invoke-ShareFinder
Use this command to find shares on the hosts in the current domain.
```

## Group Policy (GPO) Enumeration
```
- Get-NetGPO -ComputerName client-02.fanzy.com
Use this command to get a list of the GPO in the computer (Client-02).

- Find-GPOComputerAdmin –Computername client-02.fanzy.com
Use this command to find users who have local admin rights over the machine Client-02 through GPO

- Find-GPOLocation -UserName Aj
Use this command to find all computers that ”Aj” has local administrator rights in the current domain through the applied GPO.

- Get-NetOU
Use this command to get all the OUs (Organization Units) in the current domain.
```

## Forest & Trust Enumeration
```
- Get-NetDomainTrust
Use this command to get a list of all domain trusts for the current domain to map the domain trust.

- Get-NetForest
Use this command to get details about the current forest.

- Get-NetForest -Forest dampy.com
Use this command to get details about another forest.

- Get-NetForestDomain
Use this command to get all the domains in the current forest.

- Get-NetForestCatalog
Use this command to get all global catalogs for the current forest.

- Get-NetForestTrust
Use this command to map the trusts of a forest.
```


## User Hunting
```
- Find-LocalAdminAccess
Use this command to find all machines on the current domain where the current user has local admin access.

- Invoke-EnumerateLocalAdmin
Use this command to find local admins on all machines of the domain (needs administrator privs on non-dc machines).

- Invoke-UserHunter
Use this command to find computers where a domain has logged in.

- Invoke-UserHunter -UserName “Aziz"
Use this command to find computers where a specific user has sessions.

- Invoke-UserHunter -CheckAccess
Use this command to find computers where a domain admin is logged in and current user has access.
```

## Access Control Lists (ACL) Enumeration
```
- Get-ObjectAcl -SamAccountName "users" -ResolveGUIDs
Use this command to enumerate the ACLs for the users group.

- Get-NetGPO | %{Get-ObjectAcl -ResolveGUIDs -Name $_.Name}
Use this command to see if there is any user has a modification rights to a GPO.

- Get-ObjectAcl -SamAccountName labuser -ResolveGUIDs -RightsFilter "ResetPassword"
Use this command to check if the user “Sarah” has the permission (Reset Password).
```
