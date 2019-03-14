# powershell-public

Set permissions that applies to folder, subfolder and files without iCacls
==========================================================================
https://techstronghold.com/blogs/scripting/powershell-tip-how-to-set-permissions-that-applies-to-folder-subfolder-and-files-without-icacls

$path = 'C:\Temp'

New-Item -Path $path -ItemType directory
$acl = Get-Acl -Path $path
$permission = 'Everyone', 'FullControl', 'ContainerInherit, ObjectInherit', 'None', 'Allow'
$rule = New-Object -TypeName System.Security.AccessControl.FileSystemAccessRule -ArgumentList $permission
$acl.SetAccessRule($rule)
$acl | Set-Acl -Path $path