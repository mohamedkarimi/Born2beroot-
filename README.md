*This project has been created as part of the 42 curriculum by mokarimi.*

# Born2beroot

## Description

Born2beroot is a system administration project whose goal is to introduce students to the fundamentals of virtualization, Linux system installation, and security hardening.  
The project consists of creating and configuring a secure virtual machine while following strict rules related to users, permissions, services, firewall, SSH, password policies, sudo configuration, and disk partitioning.

Through this project, I gained practical experience with:
- Virtual machines and hypervisors
- Linux system administration
- Security best practices
- User and group management
- Logical Volume Management (LVM)
- System monitoring and automation

---

## Instructions

### Choice of Operating System

The chosen operating system for this project is **Debian GNU/Linux**.

#### Why Debian
Debian was selected because it is known for its **stability, reliability, and strong community support**, making it suitable for server environments and long-term usage. It provides a simple and efficient package management system through **APT** and integrates **AppArmor** for security by default.

---

### Disk Partitioning

- The disk is partitioned using **LVM (Logical Volume Manager)** inside an **encrypted container**.
- Separate logical volumes are created for:
  - `/`
  - `/home`
  - `/var`
  - `/var/log`
  - `/srv`
  - `/tmp`
  - `swap`
- This design improves **security, flexibility, and system stability**, preventing critical directories from filling the root filesystem.

---

### Security Policies

- A strong **password policy** is enforced using **PAM and pwquality**:
  - Minimum password length
  - Uppercase, lowercase, and numeric characters required
  - Password history enforcement
  - Policy applied to the root user
- **Sudo** is configured with strict rules:
  - Limited authentication attempts
  - Custom error messages
  - Full input and output logging
- **Root login via SSH is disabled** to reduce security risks.

---

### User Management

- A non-root user is created for daily operations.
- Users are assigned to specific groups (`sudo`, `user42`) following the principle of **least privilege**.
- Administrative actions require explicit use of `sudo`.

---

### Services Installed

- **SSH** for secure remote access (configured on port 4242)
- **UFW** to manage firewall rules and restrict network access
- **Cron** to automate a monitoring script executed every 10 minutes
- **Wall** to broadcast system information to all logged-in users

---

## Comparisons

### Debian vs Rocky Linux

**Debian:**  
Debian is a community-driven Linux distribution known for its stability and reliability. It uses the APT package manager and `.deb` packages. Debian is widely used on servers and is well suited for long-term and general-purpose system administration.

**Rocky Linux:**  
Rocky Linux is an enterprise-oriented distribution based on Red Hat Enterprise Linux (RHEL). It uses the DNF package manager and `.rpm` packages. Rocky Linux is designed for production environments requiring enterprise compatibility and long-term support.

---

### AppArmor vs SELinux

**AppArmor:**  
AppArmor is a Linux security module that uses path-based access control. It is easier to configure and understand, making it suitable for simpler security setups. AppArmor is enabled by default on Debian.

**SELinux:**  
SELinux is a Linux security module that uses label-based access control. It provides very fine-grained security policies but is more complex to configure. SELinux is enabled by default on Rocky Linux.

---

### UFW vs firewalld

**UFW:**  
UFW (Uncomplicated Firewall) is a simple firewall management tool that provides an easy way to define static firewall rules. It is beginner-friendly and commonly used on Debian systems.

**firewalld:**  
firewalld is a more advanced firewall management service that uses zones and dynamic rule updates. It is designed for enterprise environments and is the default firewall on Rocky Linux.

---

### VirtualBox vs UTM

**VirtualBox:**  
VirtualBox is a cross-platform virtualization software widely used in the 42 curriculum. It is well documented and suitable for creating and managing virtual machines on multiple operating systems.

**UTM:**  
UTM is a virtualization tool mainly used on macOS, especially on Apple Silicon devices. It relies on native macOS virtualization technologies and is used when VirtualBox is not available.
