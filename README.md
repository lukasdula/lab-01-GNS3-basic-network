
# **Lab Basic Network**


## Introduction and Objectives

This first lab in GNS3 demonstrates the basic configuration of a small network.  

The objectives are:

- Connect router, switch, and end devices (PC1, PC2, Xubuntu client).  
- Configure IP addressing.  
- Set up secure access with local passwords.  
- Verify remote management via SSH.  

This lab builds on previous experience from Packet Tracer but introduces the possibilities of GNS3. During the process, I added a virtual Xubuntu client, configured it, and connected it to the network. It was interesting to see the differences between simulation and virtualization and to explore the new tools in GNS3.

![TOPOLOGY-map](images/Pasted%20image%2020250929022418.png)




## Lab Structure

[1. Basic setup](basic-setup.md)
    
[2. Secure access](secure-access.md)
    
[3. SSH – Xubuntu client](ssh-xubuntu-client.md)



## Credentials

- **Local admin account (console/VTY, SSH):**  
  username: `admin`  
  password: `admin123`  

- **Privileged mode (enable secret):**  
  password: `cisco123`  



## How to run the labs

1. Open the project file in GNS3 from the corresponding folder:

   - `01-basic-setup/01-basic-setup.gns3`  
   - `02-secure-access/02-secure-access.gns3`  
   - `03-ssh-xubuntu-client/03-ssh-xubuntu-client.gns3`  

2. Start all devices in the selected lab (R1, SW1, PCs, Xubuntu client).

3. Follow the configuration steps described in the lab notes.

4. Use the provided credentials if needed (admin / admin123).



## Key Features

- Hostname & IP setup
    
- Securing access (local admin, enable secret, banner)
    
- SSH remote access from Xubuntu QEMU client


## Author's Note

This lab is my first in GNS3. I enjoyed installing the Xubuntu client, connecting it to the network, and logging in via SSH. It feels like a new level compared to Packet Tracer, but my previous experience helped me a lot. It is exciting to explore GNS3 and see the network behave realistically.  

I am looking forward to the next lab, where I will deploy an Apache server on Xubuntu and demonstrate client access to a web service. 
I also plan to add a DHCP server to make the network more realistic.


---

© 2025 – Lukas Dula | Home Network Lab & Portfolio
