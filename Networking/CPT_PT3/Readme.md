# 📚 Static Routing Connection

## 📝Brief introduction
In this practical work i studied how to perform the **static routing** with Cisco Packet Tracer with two PCs and Two Routers

## 💡 What I Larned
✅: Static Routing  
✅: How to configure Routers for Static Routing   
✅: Identify and add Gateway adresses to PCs  

## 💻 Tools and Technolgies
▶️: Cisco PAcket Tracer  
▶️: Routers 2811  
▶️: PC-PT computers  
▶️: Copper straight through  
▶️: Copper cross  
▶️: HWIC2T Serial Ports  

## 📊 Network Toology
![Basic network topology](basic.png)

## 🌐Configuration and Code Snippts

🖥️ PC-1 IPVV4 : 192.168.0.2  
🖥️ PC-2 IPVV4 : 192.168.2.2  

🛢️ R1 : 192.168.0.1 -fa0/1-        192.168.1.1 -se0/0/0-  
🛢️ R2 : 192.168.2.1 -fa0/1-        192.168.1.2 -se0/0/0-  

#### 🛢️R-1 Configuration

*----fa0/1----*
```
enable
configure teminal
hostname R0
exit
interface fa0/1
ip address 192.168.0.1 255.255.255.0
no shutdown
exit
```  
*----se0/0/0----*
``` 
interface se0/0/0
ip address 192.168.1.1 255.255.255.0
clock rate 6400
no shutdown
exit
```
#### 🛢️R-2 Configuration

```
enable
configure teminal
hostname R2
exit
```
*----fa0/1----*
```
enable 
configure terminal
interface fa0/1
ip address 192.168.2.1
no shutdown
exit
```
*----se0/0/0----*
```
interface se0/0/0
ip address 192.168.1.2 255.255.255.0
no shutdown
exit
```

## ☑️ Verfication and Testing

#### ☑️ PC1 to PC2 Ping test  
ping 192.168.2.2

#### ☑️ PC1 to PC2 Trace Route
tracert 192.168.2.2
