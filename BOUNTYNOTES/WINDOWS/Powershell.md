**Verb-Noun Naming Convention**


**HELP**

Get-Help - Lists manual

Get-Help New-LocalUser -examples



Get-Alias -Definition Type

Get-Alias - Lists aliases



**GET COMMANDS**
Get-Command - List commands

Get-Command -CommandType "Function" - List Function Commands

Get-Command -Name Remove\* - Find Remove Commands



**INSTALL POWERSHELL MODULES**

Find-Module - Downloads modules

Find-Module -Name "PowerShell\*"



Install-Module - Downloads modules

Install-Module -Name "PowerShellGet"



**ADD ITEMS**

New-Item -Path ".\\captain-cabin\\captain-wardrobe" -ItemType "Directory"

New-Item -Path ".\\captain-cabin\\captain-wardrobe\\captain-boots.txt" -ItemType "File"



**REMOVE ITEMS**

Remove-Item -Path ".\\captain-cabin\\captain-wardrobe\\captain-boots.txt"

Remove-Item -Path ".\\captain-cabin\\captain-wardrobe" 

&#x20;       

**CAT**

Get-Content

