# Personal updates to dbatools

The files in this repository contain updated versions of commandlets from dbatools, that I need for demos and clients, but which are not (yet) part of an official release.  
Most of them are part of [open pull requests](https://github.com/sqlcollaborative/dbatools/pulls/andreasjordan), but some are just part of my personal development.

I run these commands to use the new versions:

    $updatedCommands = 'Install-DbaFirstResponderKit', 'New-DbaAgentJob', 'New-DbaAgentSchedule', 'Set-DbaSpConfigure'
    $uriBase = 'https://raw.githubusercontent.com/andreasjordan/dbatools_personal_updates/master'
    $pathBase = Get-Module -Name dbatools -ListAvailable | Sort-Object -Property Version -Descending | Select-Object -First 1 -ExpandProperty ModuleBase
    foreach ( $command in $updatedCommands ) { Set-Content -Path $pathBase\functions\$command.ps1 -Value (Invoke-WebRequest -Uri $uriBase/$command.ps1 -UseBasicParsing).Content }
    $null = New-Item -ItemType Directory -Path $pathBase\.git -ErrorAction SilentlyContinue
    Import-Module -Name dbatools
