<h1>HOW TO FORWARD WSL PORT TO HOST PORT</h1>

<h2>Active powershell script</h2>
[RUN] Get-ExecutionPolicy

<h2>Forward port</h2>
See WSL IP (ifconfig in wsl distri) or :
[COMMAND] wsl hostname -i

[COMMAND] netsh interface portproxy add v4tov4 listenport=[PORT] listenaddress=0.0.0.0 connectport=[PORT] connectaddress=[WSL_IP]
Sample:
[RUN] netsh interface portproxy add v4tov4 listenport=80 listenaddress=0.0.0.0 connectport=80 connectaddress=172.27.123.178

<h2>Autorize port in firewall</h2>
[COMMAND] New-NetFirewallRule -DisplayName "WSL2 Port Bridge" -Direction Inbound -Action Allow -Protocol TCP -LocalPort [port list]
Sample:
[RUN] New-NetFirewallRule -DisplayName "WSL2 Port Bridge" -Direction Inbound -Action Allow -Protocol TCP -LocalPort 80,8080,443