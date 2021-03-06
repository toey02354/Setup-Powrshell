# Setup-Powershell

## install scoop

```
iwr -useb get.scoop.sh | iex
scoop install sudo jq curl
scoop install nvim gcc
scoop install neovim gcc
```

## config commands

```
mkdir .config/powershell
nvim .config/powershell/user_profile.ps1
.................in user_profile.ps1...................
# Alias
Set-Alias vim nvim
Set-Alias ll ls
Set-Alias g git
Set-Alias grep finder
Set-Alias tig 'C:\Program Files\Git\usr\bin\tig.exe'
Set-Alias less 'C:\Program Files\Git\usr\bin\less.exe'
Set-Alias c clear
Set-Alias touch New-Item
.......................................................

vim $PROFILE.CurrentUserCurrentHost
........in $PROFILE.CurrentUserCurrentHost.............
. $env:USERPROFILE\.config\powershell\user_profile.ps1
.......................................................
```

** close and open terminal to update configs **

## install oh my posh

```
Install-Module posh-git -Scope CurrentUser -Force
Install-Module oh-my-posh -Scope CurrentUser -Force
vim .config/powershell/user_profile.ps1
............in user_profile.ps1 add these...............
# Prompt
Import-Module posh-git
Import-Module oh-my-posh
# Theme
Set-PoshPrompt paradox
........................................................
```

## install terminal icons

```
Install-Module -Name Terminal-Icons -Repository PSGallery
vim .config/powershell/user_profile.ps1
............in user_profile.ps1 add these...............
# Terminal Icons
Import-Module -Name Terminal-Icons
........................................................
```

## set theme

```
Get-PoshThemes
vim .config/powershell/user_profile.ps1
............in user_profile.ps1 add these...............
# Theme
Set-PoshPrompt Theme_you_like
........................................................
```

# set PSReadLine

```
Install-Module -Name PSReadLine -AllowPrerelease -Scope CurrentUser -Force -SkipPublisherCheck
Set-PSReadLineOption -PredictionSource History
vim .config/powershell/user_profile.ps1
............in user_profile.ps1 add these...............
# PSReadLine
Import-Module PSReadLine
Set-PSReadLineOption -PredictionSource History

# Utilities
function which ($command) {
 Get-Command -Name $command -ErrorAction SilentlyContinue |
 Select-Object -ExpandProperty Path -ErrorAction SilentlyContinue
}
........................................................
```
