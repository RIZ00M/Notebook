# PowerShell

> Commands follow a **Verb-Noun** naming convention.

## Help

| Command | Purpose |
|---|---|
| `Get-Help` | Lists manual |
| `Get-Help New-LocalUser -examples` | Shows usage examples for a specific command |
| `Get-Alias -Definition Get-Content` | Finds the alias(es) for a given command |
| `Get-Alias type` | Shows what `type` is an alias for |
| `Get-Alias` | Lists all aliases |

## Invoke

```powershell
Invoke-Command -ComputerName X -ScriptBlock { Get-Service }
```

Runs `Get-Service` on remote computer `X`.

## Quick Reference

| Command | Purpose |
|---|---|
| `systeminfo` | System information |
| `Get-LocalUser` | User information |
| `Get-NetIPConfiguration` | IPCONFIG-equivalent information |
| `Get-NetIPAddress` | Every "doorway" your network has |

## Commands

| Command | Purpose |
|---|---|
| `Get-Command` | List commands |
| `Get-Command -CommandType "Function"` | List function commands |
| `Get-Command -Name Remove*` | Find commands starting with "Remove" |

## Monitoring

| Command | Purpose |
|---|---|
| `Get-Process` | List processes |
| `Get-Service` | List services |
| `Get-NetTCPConnection` | List TCP connections |
| `Get-FileHash -Path .\X.txt` | Get the hash of a file |
| `Get-Item -Path "C:\House\house_log.txt" -Stream *` | Get active data stream |

## Installing PowerShell Modules

| Command | Purpose |
|---|---|
| `Find-Module` | Downloads modules |
| `Find-Module -Name "PowerShell*"` | Find modules matching a name pattern |
| `Install-Module` | Installs modules |
| `Install-Module -Name "PowerShellGet"` | Installs a specific module |

## Navigation

```powershell
Get-ChildItem -Path C:\Users
tree C:\Users
Select-String -Path ".\captain-hat.txt" -Pattern "hat"
Get-ChildItem | Where-Object -Property "Name" -like "ship*"
```

## Add Items

```powershell
New-Item -Path ".\captain-cabin\captain-wardrobe" -ItemType "Directory"
New-Item -Path ".\captain-cabin\captain-wardrobe\captain-boots.txt" -ItemType "File"
```

## Remove Items

```powershell
Remove-Item -Path ".\captain-cabin\captain-wardrobe\captain-boots.txt"
Remove-Item -Path ".\captain-cabin\captain-wardrobe"
```

## Cat Equivalent

```powershell
Get-Content
```

## Piping

```powershell
Get-ChildItem | Sort-Object Length
Get-ChildItem | Where-Object -Property "Extension" -eq ".txt"
Get-ChildItem | Where-Object -Property "Name" -like "ship*"
Get-ChildItem | Select-Object Name,Length
Get-ChildItem | Sort-Object Length -Descending | Select-Object -First 1
Get-ChildItem | Where-Object -Property Length -gt 100
```

### Comparison Operators

| Operator | Meaning |
|---|---|
| `-ne` | "Not equal". Excludes objects from the results based on specified criteria. |
| `-gt` | "Greater than". Filters only objects which exceed a specified value (strict — equal values are excluded). |
| `-ge` | "Greater than or equal to". Non-strict version of `-gt` (combination of `-gt` and `-eq`). |
| `-lt` | "Less than". Strict operator — includes only objects strictly below a certain value. |
| `-le` | "Less than or equal to". Non-strict version of `-lt` (combination of `-lt` and `-eq`). |
