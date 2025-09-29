
# **1 - Basic setup**

## **1.1 Introduction**  

This lab introduces the basic configuration of a simple network in GNS3.  
The goal is to connect a router, a switch, and two PCs, assign IP addresses, and verify connectivity within the same subnet.  
The exercise demonstrates how devices are connected and how basic communication between them is established.

![TOPOLOGY-map-1](images/Pasted%20image%2020250929022139.png)


## **1.2 Topology**


| Device | Hostname | Interface | IP Address   | Subnet Mask   | Gateway     |
| ------ | -------- | --------- | ------------ | ------------- | ----------- |
| Router | R1       | Gi0/0     | 192.168.1.1  | 255.255.255.0 | –           |
| Switch | SW1      | Gi0/0     | –            | –             | –           |
| PC1    | PC1      | eth0      | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| PC2    | PC2      | eth0      | 192.168.1.11 | 255.255.255.0 | 192.168.1.1 |


---

## **1.3 Steps**

1. **Set hostname and IP address on the router**
    
    - Assign hostname R1.
        
    - Configure IP address on Gi0/0 interface.
        
    - Enable the interface
         
    * Set ip address and mask (192.168.1.1 255.255.255.0)   
        
        
2. **Set hostname on the switch**
    
    - Assign hostname SW1.
        
    - No IP address or VLAN configuration is needed for this lab.
        
3. **Configure PCs (VPCS1 and VPCS2)**
    
    - Set IP addresses and default gateway.
        
    - Gateway is the router’s IP (192.168.1.1).
        
    * Testing ping PCs -> R1

---

## **1.4 Configuration in CLI**

**Router (R1)**

```plaintext
enable
configure terminal
hostname R1
interface Gi0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
end
write memory
```
![R1-IP](images/Pasted%20image%2020250928021458.png)

Switch (SW1)

```
enable
configure terminal
hostname SW1
exit
write memory
```
![SW1-hostname](images/Pasted%20image%2020250928021709.png)

**PC1 (VPCS1)**

```plaintext
ip 192.168.1.10 255.255.255.0 192.168.1.1
save
```
![PC1-IP-PING](images/Pasted%20image%2020250928021817.png)


**PC2 (VPCS2)**

```plaintext
ip 192.168.1.11 255.255.255.0 192.168.1.1
save
```
![PC2-IP-PING](images/Pasted%20image%2020250928021950.png)

---


## 1.5 **Diagnostics on Router (R1)**



1. Verify interface status with `show ip interface brief`.
    
    - Check assigned IP address on Gi0/0.
        
    - Confirm that the interface is **up/up**.
        
2. Test connectivity to PCs.
    
    - `ping 192.168.1.10` / `192.168.1.11`
        
    - Verify 100% success rate.
        


```
R1#show ip interface brief
R1#ping 192.168.1.10
R1#ping 192.168.1.11
```
![R1-DIAGNOSTIC](images/Pasted%20image%2020250928022124.png)

## **1.6 Conclusion**

This lab successfully demonstrated the configuration of a basic network in GNS3.  
A single router, switch, and two PCs were connected, configured, and tested.  

The router was assigned an IP address, the switch received a hostname, and both PCs were configured with IP addresses and a default gateway.

Connectivity was verified using the `ping` command, confirming that all devices are able to communicate within the same subnet.  

This basic setup provides a solid foundation for more advanced labs, where additional features such as secure access, SSH, and the integration of a QEMU Xubuntu client will be introduced.


---


**Next part:** [Secure access](02-secure-access.md)
