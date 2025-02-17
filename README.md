# nmap掃描_使用Kali linux

你可以參考筆者提供的bat, 寫一個屬於自己的腳本，使用多種掃描方式進行資訊蒐集

### 一、主要流程
Assume: 我們不知道要掃描之主機的IP(屬於內網), 自己的IP。

#### 1. 先查看Kali host的IP
```
ip addr
```
![image](https://github.com/user-attachments/assets/a76d5889-a684-4259-9fc6-bff3fb9877a3)

得知Kali IP: 192.168.88.129
#### 2. 欲掃描之主機IP, 因假設內網，所以用 `arp -a`即可
```
arp -a
```
![image](https://github.com/user-attachments/assets/50001a1f-a130-4879-abd7-b766c5d31110)

得知Host IP: 192.168.88.130

#### 3. 掃描，使用`nmap` or `nmap -Pn`

```
nmap 192.168.88.130
```

![image](https://github.com/user-attachments/assets/4c5f9179-493b-4380-8a62-e9ec7155c8ed)


#### 4. 依照分析結果觀察並分析Port開啟及使用狀況

因為掃描虛擬機所以開啟的Port很少，而正常情況下的主機不會那麼少，但此處不一一演示，
詳細掃描結果請自行查詢。




#### // 額外情況
此處若是有防火牆之設定，請將其關閉，否則會如圖一樣，掃描不到Port的狀況。
![image](https://github.com/user-attachments/assets/a5dfa42d-75bc-4de4-a1af-58ee5f825fea)


----
### 二、其他命令
因為命令不少，筆者就不一一解釋 or 放圖

1. `nmap -sS`  //目標Host 所有開放之Port, TCP半開
2. `nmap -sS -T3`  //繞過防火牆
3. `nmap -sT`  //目標Host 所有開放之Port, TCP全開
4. `nmap -sP`  //目標Host 網段下所有存在的主機
5. `nmap -sV`  //目標Host 所有開啟的Port對應之Service和版本
6. `nmap -O`   //目標Host OS
7. `nmap -sn`  //快速找到內網所有設備, IP自己對應
8. `nmap -p 1-65535` //掃描開放埠

操作法:
nmap ip -p port -sS -sV
nmap ip -p port -sS -O
nmap ip -p port -sS -A
nmap -iR number -p port -sS -A


...etc

----
# Eng
Nmap Scan using Kali Linux
### I. Main Process
Assume: We don't know the target host's IP (it is within a private network) or our own IP.

#### 1. Check Kali Host IP
`ip addr`
This will display the network interfaces and their assigned IP addresses.

Example output (Kali IP: 192.168.88.129):

![image](https://github.com/user-attachments/assets/a76d5889-a684-4259-9fc6-bff3fb9877a3)


#### 2. Find the Target Host IP (since it is in the internal network, we use ARP)
`arp -a`
This will list all detected IP addresses in the same network.

Example output (Target Host IP: 192.168.88.130):

![image](https://github.com/user-attachments/assets/50001a1f-a130-4879-abd7-b766c5d31110)


#### 3. Scan the Target Host using nmap or nmap -Pn
nmap 192.168.88.130
Example output:

![image](https://github.com/user-attachments/assets/4c5f9179-493b-4380-8a62-e9ec7155c8ed)

#### 4. Analyze Open Ports and Service Status
Since this is a scan of a virtual machine, only a few ports are open. In a real-world scenario, there would be many more open ports, depending on the services running.

#### // Additional Considerations
If there is a firewall enabled, the scan may return no results (as shown in the image below). To get accurate results, disable or adjust the firewall settings accordingly.


![image](https://github.com/user-attachments/assets/a5dfa42d-75bc-4de4-a1af-58ee5f825fea)

### II. Other Useful Nmap Commands
Here are some additional nmap commands commonly used for scanning.

Command	Description
```
nmap -sS	Scan all open ports using TCP SYN scan (half-open scan).
nmap -sS -T3	Bypass firewalls with TCP SYN scan and medium timing.
nmap -sT	Scan all open ports using a full TCP connection.
nmap -sP	Detect all hosts in the network range without scanning ports.
nmap -sV	Identify services and versions running on open ports.
nmap -O	Detect the operating system of the target host.
nmap -sn	Quickly find all devices in the internal network.
nmap -p 1-65535	Scan all possible open ports.
```
