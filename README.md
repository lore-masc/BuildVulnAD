# Buil Vulnerable Active Directory

## Introduction
This script provides instructions for adding assets to a scenario designed for creating a vulnerable path among assets in a Windows Active Directory environment. The configurations of assets are set randomly to ensure a unique scenario every time for practicing purposes. The script is designed to be modularly extended and aimed at improving RedTeam and BlueTeam techniques.
Please follow the steps carefully to ensure that the assets are added correctly.

The script provides automatic joining procedure for the choosed assets in json configuration. The script have to be run on Domain Controller asset: if there is not any yet, you can run on a Windows Server and it will be promoted to DC automatically.
This script includes the following vulnerabilities or misconfigurations:

- Default password, not changed by users
- Password in user description
- Bad ACLs
- Kerberoastable users
- REP-roastable users
- DCSync privileges
- Service abuse
- User credentials in LSASS
- Constrained Delegations for Users and Computers
- Unconstrained Delegations for Computers
- MSSQL instance command executions (under testing)
- Windows Defender exception
- Parent domain traversal (under development)

## Dependencies
Put in the same directory:

- MSSQL server setup: [SQL2022-SSEI-Dev.exe](https://go.microsoft.com/fwlink/p/?linkid=2215158&clcid=0x410&culture=it-it&country=it)
- AD_network.json
- [subinacl.exe](https://social.technet.microsoft.com/wiki/contents/articles/51625.subinacl-a-complete-solution-to-configure-security-permission.aspx)

## Prerequisites
Before adding assets to the scenario, please ensure that the following prerequisites are met:

- Machine discovery in domain and guest is ON
- Machines have only a single network interface
- PowerShell is opened in administrator mode on machines
- The following commands have been executed on the machines:

```
winrm quickconfig -q
winrm set winrm/config/client @{TrustedHosts="*"}
```

## Warnings
Please note the following warnings before adding assets to the scenario:

- Ensure that new hostnames are different from old ones
- Use only the built-in "Administrator" local user to allow domain joining (especially for client OS versions). Ensure it is activated on clients and log on with it almost the first time.

## Suggestions
- Install VM with Windows Server Core (a 'GUI-less' version of Windows) to save disk space.
- Clone VMs and run the following commands to speed up:
```
Sysprep /generalize
```
Sysprep generates a new SID for asset allowing successful joining.

## Conclusion
By following the above steps and warnings, you should be able to add assets to the scenario successfully. If you encounter any issues, please refer to the troubleshooting guide or contact the support team for assistance.

## Acknowledgements
Some parts of the code used in this script were adapted from the repository [WazeHell/vulnerable-AD](https://github.com/WazeHell/vulnerable-AD).




