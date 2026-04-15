# GNS3 Intro Project Report

## Project Name

**GNS3-Intro-12313596**

## Student Details

* **Name:** [Your Name]
* **Student ID:** 12313596
* **Date:** 18 March 2026
* **Unit:** [Your Unit Code]
* **Campus:** [Your Campus]

---

## 📌 Objective

The objective of this project is to create a basic GNS3 network with a single Linux host, configure a static IP address, and verify the configuration using the console.

---

## 🖥️ Network Setup

* One **Linux Host** node was added to the workspace.
* Project title and student details were displayed using text annotations.
* The selected IP address for the host:

  ```
  10.10.1.1
  ```

---

## ⚙️ Configuration Steps

### 1. Static IP Configuration

The following configuration was added to the `/etc/network/interfaces` file **before starting the node**:

```
auto eth0
iface eth0 inet static
    address 10.10.1.1
    netmask 255.255.255.0
```

---

### 2. Start Node

* The Linux host was started successfully from GNS3.

---

### 3. Open Console

* A web console was opened in a new tab.

---

### 4. Verify IP Address

Command used:

```
ip addr
```

Output confirmed:

* Interface `eth0` assigned IP address **10.10.1.1**

---

## 📸 Screenshots

### 🔹 Network Topology

![Network Screenshot](images/GNS-Intro-12313596-network.png)

---

### 🔹 IP Address Verification

![IP Address Screenshot](images/GNS-Intro-12313596-ipaddress.png)

---

## 🧠 Learnings

* Learned how to create and name a project in GNS3
* Understood how to add and configure a Linux host
* Learned how to assign a static IP using `/etc/network/interfaces`
* Gained experience using the console to verify network configuration
* Understood the importance of configuring network settings **before booting the node**

---

## 🛠️ Commands Used

* Edit network config:

  ```
  nano /etc/network/interfaces
  ```
* Restart networking:

  ```
  /etc/init.d/networking restart
  ```
* Check IP address:

  ```
  ip addr
  ```

---

## ✅ Conclusion

The project was successfully completed. The Linux host was configured with a static IP address and verified through the console. All required outputs, including screenshots and configuration steps, were completed.

---
