Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose

PS C:\\Users\\phillip> Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose -- Reset Password On Next Login

