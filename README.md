# ITI-MCSA-Project


## Overview

This project demonstrates the implementation of a **Windows Server enterprise environment** including Active Directory, DHCP, Group Policy, file sharing permissions, VPN configuration, and storage management.

The goal of this project is to simulate a **real organizational infrastructure** using Windows Server administration tools and services.

---

## Domain Configuration

* Installed **Windows Server**
* Configured the server as **Primary Domain Controller (PDC)**
* Created a new forest domain:

```
ITISYSADMIN.com
```

---

## Organizational Units, Users, and Groups

Three departments were created in the domain:

* **IT Department**
* **HR Department**
* **Sales Department**

Each department includes **5 employees**:

Example:

IT Department
IT1, IT2, IT3, IT4, IT5

HR Department
HR1, HR2, HR3, HR4, HR5

Sales Department
Sales1, Sales2, Sales3, Sales4, Sales5

Each department has:

* A dedicated **Organizational Unit (OU)**
* A **Department Manager**

Managers were delegated permissions to:

* Reset passwords
* Create users
* Manage users inside their department OU

---

## DHCP Configuration

DHCP was configured to distribute IP addresses to clients.

Network:

```
10.0.0.0 /24
```

Settings:

* Excluded Address:
  `10.0.0.1`

* Reservation Range:
  `10.0.0.100` (Reserved for specific MAC addresses)

* MAC Address Filtering:

  * Allowed only known MAC addresses
  * Unknown devices are blocked

DHCP configuration was **backed up** for recovery purposes.

---

## Logon Restrictions

User access was restricted based on:

### Logon Hours

Users are allowed to log in only during work hours:

```
Saturday – Thursday
9:00 AM – 4:00 PM
```

### Logon Workstations

Each user is allowed to log in **only from their assigned computer**.

---

## Shared Folder and Permissions

A shared folder was created on:

```
E:\Data
```

Permissions were configured as follows:

| Department | Permission   |
| ---------- | ------------ |
| HR         | Read         |
| Sales      | Change       |
| IT         | Full Control |

---

## Disk Quota

Storage limits were applied to specific users:

| User   | Storage Limit |
| ------ | ------------- |
| IT2    | 200 MB        |
| Sales2 | 200 MB        |

Quota limits prevent users from exceeding the defined storage capacity.

---

## Group Policy (GPO)

Several **Group Policy Objects** were configured to manage the environment.

Policies implemented:

* Prevent users from opening **My Computer drives**
* Set a **default wallpaper** for all users
* Run a **logon script** that opens **Calculator**
* Backup the configured **GPO policies**

---

## Child Domain Controller

A **Child Domain Controller** was created under the main domain.

Child domain name:

```
NEWGRC.ITISYSADMIN.com
```

User creation and replication were tested by creating a user **(test)** from the PDC and verifying it on the child domain.

---

## VPN and RRAS Configuration

The server was configured as:

* **VPN Server**
* **Routing and Remote Access Server (RRAS)**

This allows remote clients to securely connect to the network.

---

## Storage Configuration

Three types of disk volumes were created:

| Volume Type           | Purpose                            |
| --------------------- | ---------------------------------- |
| Spanned Volume        | Read storage across multiple disks |
| Striped Volume        | High performance write operations  |
| Fault Tolerant Volume | Data protection                    |

---

## Client Testing

Client machines were joined to the domain:

```
ITISYSADMIN.com
```

The following tests were performed:

* User authentication
* DHCP IP assignment
* Group Policy application
* Folder access permissions
* Logon restrictions
* VPN connectivity

---

## Technologies Used

* Windows Server
* Active Directory Domain Services (AD DS)
* DHCP Server
* Group Policy Management
* RRAS
* VPN
* Disk Management
* File Server Permissions

---

## Project Files

This repository contains the configuration documentation and related files for the Windows Server administration project.

---

## Author

**Mai Wael**
System Administrator Trainee at ITI

