<h1>HOW TO FORWARD WSL PORT TO HOST PORT</h1>

<h2>Active powershell script</h2>
<code>Get-ExecutionPolicy</code>

<h2>Forward port</h2>
<p>See WSL IP (ifconfig in wsl distri) or :</p><br/>
<code>wsl hostname -i</code><br/>
<p>Run:</p>
<br/>
<code>netsh interface portproxy add v4tov4 listenport=[PORT] listenaddress=0.0.0.0 connectport=[PORT] connectaddress=[WSL_IP]</code><br/>
<p>Sample:</p>
<p>[RUN] netsh interface portproxy add v4tov4 listenport=80 listenaddress=0.0.0.0 connectport=80 connectaddress=172.27.123.178</p>

<h2>Autorize port in firewall</h2>
<code>New-NetFirewallRule -DisplayName "WSL2 Port Bridge" -Direction Inbound -Action Allow -Protocol TCP -LocalPort [port list]</code><br/>
<p>Sample:</p>
<p>[RUN] New-NetFirewallRule -DisplayName "WSL2 Port Bridge" -Direction Inbound -Action Allow -Protocol TCP -LocalPort 80,8080,443</p>
