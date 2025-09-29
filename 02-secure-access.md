# 2 - Secure access

## **2.1 Introduction**  

This lab extends the basic setup by adding **secure access configuration**. The goal is to secure privileged access, configure a local admin account, encrypt stored passwords, and set up basic access restrictions for console and VTY lines.


![TOPOLOGY-map-2](images/Pasted%20image%2020250929021657.png)


---

## **2.2 Steps**

1. Create a local admin user with a secret password.
2. Secure privileged EXEC mode with an enable secret.
3. Enable local login for console access.
4. Enable local login for VTY access.
5. Encrypt all stored passwords.
6. Add a login banner for unauthorized access warning.
7. Save the configuration.

---

## **2.3 Configuration**

**Router (R1):**

```plaintext
configure terminal
username admin secret admin123
enable secret cisco123
service password-encryption
banner motd # Unauthorized access is prohibited #
line console 0
login local
line vty 0 4
login local
end
write memory
```
![RI-password](images/Pasted%20image%2020250928202727.png)

**Switch (SW1):**

```plaintext
configure terminal
username admin secret admin123
enable secret cisco123
service password-encryption
banner motd # Unauthorized access is prohibited #
line console 0
login local
line vty 0 4
login local
end
write memory
```
![SW1-password](images/Pasted%20image%2020250928202957.png)

---

## **2.4 Diagnostics**

1. Verify that MOTD banner is displayed and login with username `admin` and password `admin123` works on console/VTY.  

```text
Login: admin
Password: admin123
```
![diagnostics-1](images/Pasted%20image%2020250928203317.png)

2. Enter privileged EXEC mode using the enable secret.  

```
enable
Password: cisco123
```
![Diagnostics-2](images/Pasted%20image%2020250928203345.png)

3. Use `show running-config` to verify encrypted passwords.  

```text
show running-config
```
![Diagnostics-3](images/Pasted%20image%2020250928203437.png)

![Diagnostics-4](images/Pasted%20image%2020250928203527.png)


---

### **2.5 Conclusion**  

This lab provides a **secured baseline configuration** for network devices.  
- Console and VTY access require the **local admin account** (`admin/admin123`).  
- Privileged EXEC mode is protected with an encrypted **enable secret**.  
- All passwords are encrypted in the configuration.  
- Unauthorized users are warned via a login banner.


---


**Next part:** SSH - Xubuntu client