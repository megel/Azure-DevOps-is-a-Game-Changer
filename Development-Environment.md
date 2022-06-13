# Development Environment

The best development environment is nothing without tools! Here are some PowerShell Scripts to install my preferred selection. *Admin Rights may be needed to execute these Scripts.*

## Chocolatey & Tools

Install from **PowerShell**:

* Chocolatey [https://chocolatey.org](https://chocolatey.org)
* [Git](https://chocolatey.org/packages/git)
* [UPack (Universal Package)](https://chocolatey.org/packages/upack)
* [Azure-CLI](https://chocolatey.org/packages/azure-cli) + [Azure-CLI Extension for Azure DevOps](https://marketplace.visualstudio.com/items?itemName=ms-vsts.cli)
* [Google Chrome](https://chocolatey.org/packages/GoogleChrome)
* [Microsoft Edge](https://chocolatey.org/packages/microsoft-edge)

```powershell
# Install Choco
[Net.ServicePointManager]::SecurityProtocol = [Net.ServicePointManager]::SecurityProtocol -bor [Net.SecurityProtocolType]::Tls12
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
# Install Git
choco install -y git
choco upgrade -y git
# Install UPack
choco install -y upack
choco upgrade -y upack
# Install Azure CLI
choco install -y azure-cli 
choco upgrade -y azure-cli
# Install Google Chrome
choco install -y googlechrome
choco upgrade -y googlechrome
# Install Microsoft Edge
choco install -y microsoft-edge
choco upgrade -y microsoft-edge
# Reload the PATH variable
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine")
# Install Azure CLI Extension for Azure-DevOps
az extension add --name azure-devops
```

## Chocolatey & VSCode & VSCode Extensions for AL

```powershell
# Install Choco
[Net.ServicePointManager]::SecurityProtocol = [Net.ServicePointManager]::SecurityProtocol -bor [Net.SecurityProtocolType]::Tls12
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
# Install VSCode
choco install -y vscode
choco upgrade -y vscode
# Reload the PATH variable
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine")
# Install VS-Code Extensions for AL
try { code --install-extension cosmoconsult.cosmo-azure-devops | Out-Null } catch {}
try { code --install-extension ms-dynamics-smb.al | Out-Null } catch {}
try { code --install-extension file-icons.file-icons | Out-Null } catch {}
try { code --install-extension andrzejzwierzchowski.al-code-outline | Out-Null } catch {}
try { code --install-extension rasmus.al-formatter | Out-Null } catch {}
try { code --install-extension martonsagi.al-object-designer | Out-Null } catch {}
try { code --install-extension davidanson.vscode-markdownlint | Out-Null } catch {}
try { code --install-extension hnw.vscode-auto-open-markdown-preview | Out-Null } catch {}
try { code --install-extension eriklynd.json-tools | Out-Null } catch {}
try { code --install-extension waldo.crs-al-language-extension | Out-Null } catch {}
try { code --install-extension donjayamanne.githistory | Out-Null } catch {}
try { code --install-extension eamodio.gitlens | Out-Null } catch {}
try { code --install-extension heaths.vscode-guid | Out-Null } catch {}
try { code --install-extension streetsidesoftware.code-spell-checker | Out-Null } catch {}  
```

## Full Tooling

Use this to install everything on a new virtual machine to get started...

```Powershell
# Install Choco
[Net.ServicePointManager]::SecurityProtocol = [Net.ServicePointManager]::SecurityProtocol -bor [Net.SecurityProtocolType]::Tls12
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
# Install Git
choco install -y git
choco upgrade -y git
# Install UPack
choco install -y upack
choco upgrade -y upack
# Install Azure CLI
choco install -y azure-cli 
choco upgrade -y azure-cli
# Install Google Chrome
choco install -y googlechrome
choco upgrade -y googlechrome
# Install Microsoft Edge
choco install -y microsoft-edge
choco upgrade -y microsoft-edge
# Reload the PATH variable
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine")
# Install Azure CLI Extension for Azure-DevOps
az extension add --name azure-devops

# Install VSCode
choco install -y vscode
choco upgrade -y vscode
# Reload the PATH variable
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine")
# Install VS-Code Extensions for AL
try { code --install-extension cosmoconsult.cosmo-azure-devops | Out-Null } catch {}
try { code --install-extension ms-dynamics-smb.al | Out-Null } catch {}
try { code --install-extension file-icons.file-icons | Out-Null } catch {}
try { code --install-extension andrzejzwierzchowski.al-code-outline | Out-Null } catch {}
try { code --install-extension rasmus.al-formatter | Out-Null } catch {}
try { code --install-extension martonsagi.al-object-designer | Out-Null } catch {}
try { code --install-extension davidanson.vscode-markdownlint | Out-Null } catch {}
try { code --install-extension hnw.vscode-auto-open-markdown-preview | Out-Null } catch {}
try { code --install-extension eriklynd.json-tools | Out-Null } catch {}
try { code --install-extension waldo.crs-al-language-extension | Out-Null } catch {}
try { code --install-extension donjayamanne.githistory | Out-Null } catch {}
try { code --install-extension eamodio.gitlens | Out-Null } catch {}
try { code --install-extension heaths.vscode-guid | Out-Null } catch {}
try { code --install-extension streetsidesoftware.code-spell-checker | Out-Null } catch {}
```
