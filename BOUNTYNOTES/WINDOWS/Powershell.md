**Verb-Noun Naming Convention**



**HELP**

Get-Help - Lists manual

Get-Help New-LocalUser -examples



Get-Alias -Definition Get-Content

Get-Alias type

Get-Alias - Lists aliases



**INVOKE**

Invoke-Command -ComputerName X -ScriptBlock { Get-Service }



**QUICK**

systeminfo - System information

Get-LocalUser - User information

Get-NetIPConfiguration - IPCONFIG information

Get-NetIPAddress - Every doorway your network has



**COMMANDS**
Get-Command - List commands

Get-Command -CommandType "Function" - List Function Commands

Get-Command -Name Remove\* - Find Remove Commands



**MONITORING**

Get-Process - List processes

Get-Service - List services

Get-NetTCPConnection - List TCP connections

Get-FileHash -Path .\\X.txt

Get-Item -Path "C:\\House\\house\_log.txt" -Stream \* - Get Active Data Stream



**INSTALL POWERSHELL MODULES**

Find-Module - Downloads modules

Find-Module -Name "PowerShell\*"



Install-Module - Downloads modules

Install-Module -Name "PowerShellGet"



**NAVIGATION**
Get-ChildItem -Path C:\\Users

tree C:\\Users

Select-String -Path ".\\captain-hat.txt" -Pattern "hat" 

Get-ChildItem | Where-Object -Property "Name" -like "ship\*"



**ADD ITEMS**

New-Item -Path ".\\captain-cabin\\captain-wardrobe" -ItemType "Directory"

New-Item -Path ".\\captain-cabin\\captain-wardrobe\\captain-boots.txt" -ItemType "File"



**REMOVE ITEMS**

Remove-Item -Path ".\\captain-cabin\\captain-wardrobe\\captain-boots.txt"

Remove-Item -Path ".\\captain-cabin\\captain-wardrobe"

&#x20;

**CAT**

Get-Content



**PIPING**

Get-ChildItem | Sort-Object Length

Get-ChildItem | Where-Object -Property "Extension" -eq ".txt" 

Get-ChildItem | Where-Object -Property "Name" -like "ship\*"

Get-ChildItem | Select-Object Name,Length 

Get-ChildItem | Sort-Object Length -Descending | Select-Object -First 1

Get-ChildItem | Where-Object -Property Length -gt 100



\-ne: "not equal". This operator can be used to exclude objects from the results based on specified criteria.

\-gt: "greater than". This operator will filter only objects which exceed a specified value. It is important to note that this is a strict comparison, meaning that objects that are equal to the specified value will be excluded from the results.

\-ge: "greater than or equal to". This is the non-strict version of the previous operator. A combination of -gt and -eq.

\-lt: "less than". Like its counterpart, "greater than", this is a strict operator. It will include only objects which are strictly below a certain value.

\-le: "less than or equal to". Just like its counterpart -ge, this is the non-strict version of the previous operator. A combination of -lt and -eq.

