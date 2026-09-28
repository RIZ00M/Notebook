# Active Directory — PowerShell

## Reset a User's Password

```powershell
Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose
```

Resets the password for the AD user `sophie`, prompting securely for the new password.

## Force Password Reset On Next Login

```powershell
PS C:\Users\phillip> Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose
```

Flags the AD user `sophie` so they must change their password the next time they log in.
