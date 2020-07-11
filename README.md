# Personal updates to dbatools

The files in this repository contain updated versions of commandlets from dbatools, that I need for demos and clients, but which are not (yet) part of an official release.  
Most of them are part of [open pull requests](https://github.com/sqlcollaborative/dbatools/pulls/andreasjordan), but some are just part of my personal development.

I run these commands to use the new versions:

    Import-Module -Name dbatools
    $updatedCommands = 'Install-DbaFirstResponderKit', 'New-DbaAgentJob', 'New-DbaAgentSchedule', 'Set-DbaSpConfigure'
    $uriBase = 'https://raw.githubusercontent.com/andreasjordan/dbatools_personal_updates/master'
    foreach ( $command in $updatedCommands ) { Invoke-Expression -Command (Invoke-WebRequest -Uri $uriBase/$command.ps1).Content }
