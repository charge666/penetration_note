# penetration_note

## AD

### 外網打到內網
1. nmap 掃對外開放機器的 port
nmap -A IP
有防火牆 : nmap -A -Pn IP

### 列出資訊
1. 列出 Domain 中所有 User
net user /domain

2. 列出 Domain 中的 DC
net group "domain controllers" /domain
dsquery server

3. 列出當前登入域中的電腦上的身分以及資訊
net config workstation

4. 列出電腦上 patch 
wmic qfe

### 橫向移動
1. wmic
2. net use &IPC
3. rdp
4. psexec

目前攻擊步驟
掃對外開放機器的 port -> 開有沒有已知漏洞未修補可以打進去 -> 沒有，重複
                                                   -> 有 -> ipconfig 查看內網網段 -> nmap 掃出內網機器 -> 試著找出 DC 和 domain admin -> 有 domain admin dump all hash 出來
Zerologon
有 MDE 就算建立起 reverse shell 也會被停止
