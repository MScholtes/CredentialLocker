# CredentialLocker
CredentialLocker is a powershell module that provides commandlets to manage credentials in the password vault.
It is a secure password safe for your application (as secure as your login environment). Usernames and passwords stored using the Credential Locker are encrypted and saved locally and can only be accessed by the user who saved them.

With this module you can manage stored credentials of Internet Explorer and Edge too.

Requires Windows 8 / Server 2012 or up.

* Get-VaultCredential and Show-VaultCredentials to display credentials 
* Add-VaultCredential and Remove-VaultCredential to manage credentials 
* ConvertTo-VaultCredential and ConvertFrom-VaultCredential to convert between PSCredential and CredentialLocker credential 

By Markus Scholtes, 2019
## Installation

```powershell
PS C:\> Install-Module CredentialLocker
```
or download from here: https://www.powershellgallery.com/packages/CredentialLocker/.

Also look for the script based version here [Powershell Module CredentialLocker](https://gallery.technet.microsoft.com/scriptcenter/Powershell-Module-f0f91920).
## List Of Commands
### Get-VaultCredential [-Resource &lt;Resource&gt;] [-UserName &lt;UserName&gt;]
Retrieves credentials stored in the password vault searched by resource and/or user name.
### Show-VaultCredentials
List all credentials stored in the password vault.
### Add-VaultCredential -Resource &lt;Resource> -UserName &lt;UserName&gt; -Password &lt;Password&gt; [-IE] [-Edge] [-Hide]
### Add-VaultCredential -Credential &lt;VaultCredential&gt; [-IE] [-Edge] [-Hide]
Adds a credential to the password vault. Parameter -IE or -Edge generates a credential for a web page. Parameter -Hide hides the credential in control panel.
### Remove-VaultCredential -Resource &lt;Resource&gt; -UserName &lt;UserName&gt;
### Remove-VaultCredential -Credential &lt;VaultCredential&gt;
Removes credentials from the password vault.
### ConvertTo-VaultCredential -Credential &lt;PSCredential&gt;
Converts Powershell credential to password vault credential.
### ConvertFrom-VaultCredential -Credential &lt;VaultCredential&gt;
Converts password vault credential to Powershell credential.
## Examples
```powershell
Get-VaultCredential "https://github.com/" 
 
(Get-VaultCredential -resource "https://github.com/").Password 
 
Add-VaultCredential "https://login.live.com/" "test@test.com" "P@ssw0rd" -Edge -Hide 
 
Get-Credential | ConvertTo-VaultCredential -Resource "MyApp" | Add-VaultCredential -Application "MyApp" 
 
Remove-VaultCredential -Resource "https://github.com/" 
 
Get-VaultCredential -Resource "https://github.com/" -UserName "logonname" | Remove-VaultCredential 
```
## Versions
### 1.0.0, 2019-09-10
First stable release (hope so)
