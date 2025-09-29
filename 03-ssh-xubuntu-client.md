# **3 - SSH with Xubuntu Client**

## **3.1 Introduction**

This part demonstrates the integration of a virtual client into the network. In this case, a Xubuntu PC is added to the topology, configured with an IP address, and connected to Router R1. The goal is to show secure remote access by establishing an SSH session from the Xubuntu client to the router.

![TOPOLOGY-map-3](images/Pasted%20image%2020250929021208.png)


## **3.2 Topology**

| Device         | Interface    | Connected to -> | Peer Interface | IP Address   | Subnet Mask   | Gateway     |
| -------------- | ------------ | --------------- | -------------- | ------------ | ------------- | ----------- |
| Router R1      | Gi0/0        | Switch SW1      | Gi0/0          | 192.168.1.1  | 255.255.255.0 | -           |
| Switch SW1     | Gi0/0        | Router R1       | Gi0/0          | -            | -             | -           |
| Switch SW1     | Gi0/1        | PC1 (VPCS1)     | Eth0           | -            | -             | -           |
| Switch SW1     | Gi0/2        | PC2 (VPCS2)     | Eth0           | -            | -             | -           |
| Switch SW1     | Gi0/3        | Xubuntu-client  | Gi0/0          | -            | -             | -           |
| PC1 (VPCS1)    | e0           | Switch SW1      | Gi0/1          | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| PC2 (VPCS2)    | e0           | Switch SW1      | Gi0/2          | 192.168.1.11 | 255.255.255.0 | 192.168.1.1 |
| Xubuntu-client | Gi0/0 (ens3) | Switch SW1      | Gi0/3          | 192.168.1.20 | 255.255.255.0 | 192.168.1.1 |

**Default credentials (Xubuntu client):**  

- Username: lab-01  
- Password: 12345


## **3.3 Steps**

1. Add a Xubuntu client to the topology and connect it to SW1.
    
2. Configure SSH on Router R1:
       - Define domain name.
       - Generate RSA keys.
       - Create a local admin user.
       - Enable SSH version 2.
       - Configure VTY lines for SSH login.
    
3. Configure IP address and default gateway on the Xubuntu client.
    
    
4. Test SSH connection from Xubuntu client to Router R1.

## **3.4 Configuration**

**Router R1:**

```plaintext
enable
configure terminal
ip domain-name lab1.local
crypto key generate rsa
1024
username admin secret admin123
ip ssh version 2
line vty 0 4
login local
transport input ssh
exec-timeout 10
end
write memory
```
![SSH-R1](images/Pasted%20image%2020250928225120.png)

**Xubuntu Client:**

```plaintext
sudo ip addr add 192.168.1.20/24 dev ens3
sudo ip route add default via 192.168.1.1
```
![Xubuntu-client](images/Pasted%20image%2020250929012344.png)

>**note.:** Identify the correct network interface on Xubuntu using `ip a` (e.g. ens3).


**SSH from Xubuntu-client to R1:**

```
ssh admin@192.168.1.1
```
![SSH](images/Pasted%20image%2020250929012614.png)

## **3.5 Diagnostics**

1. Verify connectivity by running pings from **Xubuntu-client** to PCs and Router R1.
    

```text
ping 192.168.1.10
ping 192.168.1.11
ping 192.168.1.1
```
![xubuntu-clien-ping-test](images/Pasted%20image%2020250929012924.png)

2. On Router R1, run `show ip ssh` to confirm SSH is enabled.
    

```text
show ip ssh
```
![SSH-test](images/Pasted%20image%2020250929013118.png)


## **3.6 Conclusion**

This lab demonstrates the integration of a virtual Xubuntu PC into the network and secure remote access to Router R1 via SSH. By configuring IP connectivity and SSH, the Xubuntu client successfully establishes an encrypted session with the router. This validates the use of a virtual client in the lab environment for secure device management.

---

**Back to project overview:** README