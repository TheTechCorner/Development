# Setup a WSL2 Environment

[Microsoft: Setup WSL](https://learn.microsoft.com/en-us/windows/wsl/setup/environment?source=recommendations)

## Install Windows Terminal app

```Powershell
winget search 'Windows Terminal'
```

```output
Name                     Id                                Version      Source
--------------------------------------------------------------------------------
Windows Terminal         9N0DX20HK701                      Unknown      msstore
Windows Terminal Preview 9N8G5RFZ9XK3                      Unknown      msstore
Windows Terminal         Microsoft.WindowsTerminal         1.22.11751.0 winget
Windows Terminal Preview Microsoft.WindowsTerminal.Preview 1.23.11752.0 winget
```

```PowerShell
winget install Microsoft.WindowsTerminal
```

## Update PowerShell 7.x.x

[Microsoft Update Windows Powershell](https://learn.microsoft.com/en-us/shows/it-ops-talk/how-to-install-powershell-7)

```Powershell
winget search Microsoft.PowerShell
```

```output
Name               Id                           Version Source
---------------------------------------------------------------
PowerShell         Microsoft.PowerShell         7.5.2.0 winget
PowerShell Preview Microsoft.PowerShell.Preview 7.6.0.4 winget
```

```PowerShell
winget install 'Microsoft.Powershell'
```

## Install Microsoft Visual Studio Code

```powershell
winget search 'Microsoft.VisualStudioCode'
```

```output
Name                                      Id                                      Version Source
-------------------------------------------------------------------------------------------------
Microsoft Visual Studio Code              Microsoft.VisualStudioCode              1.106.3 winget
Microsoft Visual Studio Code CLI          Microsoft.VisualStudioCode.CLI          1.106.3 winget
Microsoft Visual Studio Code Insiders     Microsoft.VisualStudioCode.Insiders     1.107.0 winget
Microsoft Visual Studio Code Insiders CLI Microsoft.VisualStudioCode.Insiders.CLI 1.107.0 winget
```

```PowerShell
winget install Microsoft.VisualStudioCode
```

## Install Docker Desktop

```PowerShell
winget search 'Docker Desktop'
```

```output
Name                Id                       Version     Source
-----------------------------------------------------------------
Docker Desktop      XP8CBJ40XLBWKX           Unknown     msstore
Docker Desktop      Docker.DockerDesktop     4.63.0      winget
Docker Desktop Edge Docker.DockerDesktopEdge 2.5.4.50534 winget
```
