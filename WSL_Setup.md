# Set Up a WSL2 Environment

[Microsoft: Set Up WSL](https://learn.microsoft.com/en-us/windows/wsl/setup/environment?source=recommendations)

## Install the Windows Terminal app

```powershell
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

```powershell
winget install Microsoft.WindowsTerminal
```

## Update PowerShell 7.x.x

[Microsoft: Update Windows PowerShell](https://learn.microsoft.com/en-us/shows/it-ops-talk/how-to-install-powershell-7)

```powershell
winget search Microsoft.PowerShell
```

```output
Name               Id                           Version Source
---------------------------------------------------------------
PowerShell         Microsoft.PowerShell         7.5.2.0 winget
PowerShell Preview Microsoft.PowerShell.Preview 7.6.0.4 winget
```

```powershell
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

```powershell
winget install Microsoft.VisualStudioCode
```

## Install Docker Desktop

```powershell
winget search 'Docker Desktop'
```

```output
Name                Id                       Version     Source
-----------------------------------------------------------------
Docker Desktop      XP8CBJ40XLBWKX           Unknown     msstore
Docker Desktop      Docker.DockerDesktop     4.63.0      winget
Docker Desktop Edge Docker.DockerDesktopEdge 2.5.4.50534 winget
```

## Choose a WSL Distribution

### List Available Distributions
```powershell
wsl -l -o
```

```output
The following is a list of valid distributions that can be installed.
Install using 'wsl.exe --install <Distro>'.

NAME                            FRIENDLY NAME
Ubuntu                          Ubuntu
Ubuntu-24.04                    Ubuntu 24.04 LTS
openSUSE-Tumbleweed             openSUSE Tumbleweed
openSUSE-Leap-16.0              openSUSE Leap 16.0
SUSE-Linux-Enterprise-15-SP7    SUSE Linux Enterprise 15 SP7
SUSE-Linux-Enterprise-16.0      SUSE Linux Enterprise 16.0
kali-linux                      Kali Linux Rolling
Debian                          Debian GNU/Linux
AlmaLinux-8                     AlmaLinux OS 8
AlmaLinux-9                     AlmaLinux OS 9
AlmaLinux-Kitten-10             AlmaLinux OS Kitten 10
AlmaLinux-10                    AlmaLinux OS 10
archlinux                       Arch Linux
FedoraLinux-43                  Fedora Linux 43
FedoraLinux-42                  Fedora Linux 42
eLxr                            eLxr 12.12.0.0 GNU/Linux
Ubuntu-20.04                    Ubuntu 20.04 LTS
Ubuntu-22.04                    Ubuntu 22.04 LTS
OracleLinux_7_9                 Oracle Linux 7.9
OracleLinux_8_10                Oracle Linux 8.10
OracleLinux_9_5                 Oracle Linux 9.5
openSUSE-Leap-15.6              openSUSE Leap 15.6
SUSE-Linux-Enterprise-15-SP6    SUSE Linux Enterprise 15 SP6
```

## Install a WSL Distribution
```powershell
wsl --install -d Debian
```

## Configure systemd

```bash
sudo nano /etc/wsl.conf
```

Add the following to `/etc/wsl.conf`:

```ini
[boot]
systemd=true
```

Save the file. Save any work in other WSL distributions, then run the following command in PowerShell to shut down all running WSL distributions:

```powershell
wsl --shutdown
```

Reopen Debian, then verify that systemd is running:

```bash
systemctl status
```

## Set Up Standard XDG User Directories
```bash
sudo apt update

sudo apt install xdg-user-dirs -y

xdg-user-dirs-update
```

## Install essentials
```bash
sudo apt update

sudo apt install -y git g++ gdb make ninja-build rsync zip cmake build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm gpg libcurl4-openssl-dev libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```

## Install SSH
```bash
sudo apt update

sudo apt install openssh-server -y
```

## Configure sshd_config

- `Port 2222`: Change the port from 22 to 2222. Windows often uses port 22 natively for its own OpenSSH service, causing conflicts.
- `ListenAddress 0.0.0.0`: Forces SSH to listen on all IPv4 addresses.
- `PasswordAuthentication yes`: Allows password login (switch to public key authentication later if desired).

## Start and Enable the SSH Service
```bash
sudo systemctl start ssh

sudo systemctl enable ssh

sudo systemctl status ssh
```

## Install Google Chrome

```bash
cd /tmp

sudo wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

sudo apt install ./google-chrome-stable_current_amd64.deb
```

### To launch, enter:
```bash
google-chrome 2>/dev/null &
```

## Install Remmina

```bash
sudo apt update

sudo apt install -y remmina remmina-plugin-rdp remmina-plugin-vnc remmina-plugin-secret
```

### To launch, enter:
```bash
remmina 2>/dev/null &
```

## Install FileZilla
```bash
sudo apt update

sudo apt install -y filezilla
```

### To launch, enter:
```bash
filezilla 2>/dev/null &
```

## Back Up a WSL Distribution
```powershell
wsl --export Debian "D:\Backup\debian_temp.tar"
```

## Install Microsoft Edge

[Download Microsoft Edge](https://www.microsoft.com/en-us/edge/download?form=MA13FJ)

Download the Debian/Ubuntu `.deb` package. Before running the installation command, replace `<actual-filename>` with the downloaded file's name, excluding the `.deb` extension. Run the commands from the directory containing the downloaded file.

```bash
sudo apt update

sudo apt install ./<actual-filename>.deb
```

### To launch, enter:

```bash
microsoft-edge 2>/dev/null &
```
