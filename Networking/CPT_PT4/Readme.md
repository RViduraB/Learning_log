# 📚 Inter VLAN Routing

## 📝Brief introduction
In this practical i established a netwrok that works with inter VLan connection with one Router, one Switch and two PCs

## 💡 What I Larned
✅: Inter Vlan Routing concept  
✅: Sub Interfaces with Ip Addresses
✅: How to configure Routers   
✅: Identify and add Gateway adresses to PCs  

## 💻 Tools and Technolgies
▶️: Cisco PAcket Tracer  
▶️: Routers 2811  
▶️: PC-PT computers  
▶️: Copper straight through  
▶️: 2960 Switch  

## 📊 Network Toology
![Basic network topology](basic.png)

## 🌐Configuration and Code Snippts

🖥️ PC-1 IPVV4 : 172.17.10.10 : 172.17.10.1  
🖥️ PC-2 IPVV4 : 172.17.20.10 : 172.17.20.1

🛢️ R0 interface -fa0/1-  
▶️ sub interface fa0/1.10 : 172.17.10.1  
▶️ sub interface fa0/1.20 : 172.17.20.1  

#### 🛢️R-0 Configuration

*----fa0/1.10----*
```
enable
configure teminal
hostname R0
exit
interface fa0/1.10
encapsulation dot1q 10
ip address 172.17.10.1 255.255.255.0
no shutdown
exit
```  
*----fe0/1.20----*
``` 
interface fa0/1.20
encapsulation dot1q 20
ip address 172.17.20.1 255.255.255.0
no shutdown
exit
```
*----fa0/1----*
``` 
interface fa0/1
no shutdown
exit
```
#### 🔲S-0 Configuration
``` 
enable
configure terminal
vlan 10
name VL10
exit
vlan 20
name VL20
no shutdown
exit
```

*----fa0/1----*

```
en
conf t
interface fa0/1
switchport mode access
switchport access vlan 10
exit
```
*----fa0/2----*

```
en
conf t
interface fa0/2
switchport mode access
switchport access vlan 20
exit
```
*----fa0/3----*

```
en
conf t
interface fa0/3
switchport mode trunk
switchport trunk native vlan 1
switchport trunk allowed vlan 10
switchport trunk allowed vlan 20
exit
```


## ☑️ Verfication and Testing

#### ☑️ PC1 to PC2 Ping test  
ping 172.17.20.10





#### ☑️ PC1 to PC2 Trace Route
tracert 172.17.20.10
