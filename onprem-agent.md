# OnPre Agent

These steps helps you to setup an On-Prem Deployment / Build Agent in your Dynamics 365 Business Central container.

## Get your Azure DevOps PAT

The PAT (Personal Access Token) is used by the build / deployment agent to access Azure DevOps wit your rights.

Please follow theses steps to get your PAT: **[Create a PAT](https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=Windows#create-a-pat)**

## Install Build Agent in BC-Docker Container

The following script download and install a [Self Hosted Agent](https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/v2-windows?view=azure-devops) as Service inside of a NAV-/BC-Docker Container with PowerShell:

```PowerShell
$agentURL       = "https://vstsagentpackage.azureedge.net/agent/2.204.0/vsts-agent-win-x64-2.204.0.zip"
Add-LocalGroupMember -Group Administrators -Member "Network Service" -ErrorAction SilentlyContinue

Write-Host "Setup VSTS-Agent $agentName for pool $poolName" -f Cyan
$agentFile = "C:/run/my/agent.zip"
Set-Location "C:/run/my"

$ProgressPreference="SilentlyContinue"
Write-Host "Download VSTS-Agent"
[Net.ServicePointManager]::SecurityProtocol = [Net.ServicePointManager]::SecurityProtocol -bor [Net.SecurityProtocolType]::Tls12
Invoke-WebRequest -Uri "$agentURL" -OutFile "$agentFile"

Write-Host "Extract VSTS-Agent"
Expand-Archive $agentFile "C:/agent"
$ProgressPreference="Continue"
```

Afterwards you need to setup the build / deployment agent *(For deployment agent, please start the configuration with parameter `--deploymentgroup`)*:

* Your Azure DevOps **Organization URL**
* Your PAT (*[Create a PAT](https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=Windows#create-a-pat)*)
* The name of the Agent Pool (e.g. `MyProject-Deployment`)

Please execute `C:\agent\config.cmd` and follow the instructions to configure your agent with your information:

```cmd
PS C:\run\my> C:\agent\config.cmd

  ___                      ______ _            _ _
 / _ \                     | ___ (_)          | (_)
/ /_\ \_____   _ _ __ ___  | |_/ /_ _ __   ___| |_ _ __   ___  ___ 
|  _  |_  / | | | '__/ _ \ |  __/| | '_ \ / _ \ | | '_ \ / _ \/ __|
| | | |/ /| |_| | | |  __/ | |   | | |_) |  __/ | | | | |  __/\__ \
\_| |_/___|\__,_|_|  \___| \_|   |_| .__/ \___|_|_|_| |_|\___||___/
                                   | |
        agent v2.204.0             |_|          (commit 166abe8)   


>> Connect:        

Enter server URL >                                        https://dev.azure.com/DoK-2022
Enter authentication type (press enter for PAT) >         [ENTER]
Enter personal access token >                             ****************************************************  (My PAT)
Connecting to server ...

>> Register Agent:

Enter agent pool (press enter for default) >              MyProject-Deployment
Enter agent name (press enter for E378CE4E961A) >         [ENTER]
Scanning for tool capabilities.
Connecting to the server.
Successfully added the agent
Testing agent connection.
Enter work folder (press enter for _work) >               [ENTER]
2022-06-10 09:35:46Z: Settings Saved.
Enter run agent as service? (Y/N) (press enter for N) >   y
Enter User account to use for the service (press enter for NT AUTHORITY\NETWORK SERVICE) >      [ENTER]
Granting file permissions to 'NT AUTHORITY\NETWORK SERVICE'.
Service vstsagent.DoK-2022.MyProject-Deployment.E378CE4E961A successfully installed
Service vstsagent.DoK-2022.MyProject-Deployment.E378CE4E961A successfully set recovery option
Service vstsagent.DoK-2022.MyProject-Deployment.E378CE4E961A successfully set to delayed auto start
Service vstsagent.DoK-2022.MyProject-Deployment.E378CE4E961A successfully configured
Enter whether to prevent service starting immediately after configuration is finished? (Y/N) (press enter for N) >    [ENTER]
Service vstsagent.DoK-2022.MyProject-Deployment.E378CE4E961A started successfully

```

## Power Shell Library

You can also use this Power Shell library / examples:

* [Azure-DevOps-Utils (PowerShell Library)](https://github.com/megel/Azure-DevOps-Utils)
* [Azure-DevOps-Agents-for-BC-Examples](https://github.com/megel/Azure-DevOps-Agents-for-BC-Examples)
