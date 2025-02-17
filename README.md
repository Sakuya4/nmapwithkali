# nmap掃描_使用Kali linux

### 一、檢查必要資訊
Assume: 我們不知道要掃描之主機的IP(屬於內網), 自己的IP。

1. 先查看Kali host的IP
```
ip addr
```
![image](https://github.com/user-attachments/assets/74a51ae1-f5c8-490f-be40-0c9595c6291d)


2. 欲掃描之主機IP, 因假設內網，所以用 `arp -a`即可
```
arp -a
```
![image](https://github.com/user-attachments/assets/50001a1f-a130-4879-abd7-b766c5d31110)

3. 
