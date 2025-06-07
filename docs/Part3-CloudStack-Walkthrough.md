<h2> 🖼️ 1. Setting Up the CloudStack Repository </h2> 
In this step, we created a custom YUM repository configuration file at /etc/yum.repos.d/cloudstack.repo, pointing to the official Apache CloudStack repo for version 4.19. This allows the yum package manager to locate and install CloudStack components:
<br>
<br>
<img src="images/Screenshot 2025-06-06 144449.png" alt="CloudStack" width="460">
<h2> 🖼️ 2. Installing CloudStack Management Server </h2>
Here, we executed sudo yum install cloudstack-management, which installed the CloudStack management server along with required dependencies like Python 3, ipmitool, Java, and MySQL. This is the core backend that provides the web UI and orchestrates cloud infrastructure.
<br>
<br>
<img src="images/Screenshot 2025-06-06 144607.png" alt="CloudStack" width="460">
<h2> 🖼️ 3. Verifying Java Versions and Setting Defaults </h2>
Apache CloudStack requires Java, and here we verified the installed versions and used alternatives --config java to switch to the correct one (openjdk-11). This ensures compatibility when running CloudStack services.
<br>
<br>
<img src="images/Screenshot 2025-06-06 144648.png" alt="CloudStack" width="460">
<h2> 🖼️ 4. Installing and Configuring MySQL/MariaDB</h2>
MySQL (specifically MariaDB or MySQL Community Server) is used as CloudStack’s backend database. This screenshot shows the installation and configuration of MySQL on CentOS, replacing the default MariaDB version with MySQL 8.
<br>
<br>
<img src="images/Screenshot 2025-06-06 144706.png" alt="CloudStack" width="600">
<h2> 🖼️ 5. Starting MySQL and Running the Secure Setup </h2>
After configuring the database, we started the MySQL service and ran mysql_secure_installation to set the root password, remove anonymous users, and secure the installation. This step is essential before initializing the CloudStack database schema. Apologies for the blurry photo. 
<br>
<br>
<img src="images/Screenshot 2025-06-06 144822.png" alt="CloudStack">
<h2> 🖼️ 6. MySQL Secure Installation Finalization </h2>
This screenshot shows the final stage of the mysql_secure_installation command, where insecure defaults are removed (anonymous users, test database), and root login is restricted. This hardens the MySQL setup before being used as CloudStack's backend.
<br>
<br>
<img src="images/Screenshot 2025-06-06 144923.png" alt="CloudStack">
<h2> 🖼️ 7. Editing SELinux Config to Permissive </h2>
Apache CloudStack doesn’t work well with SELinux in enforcing mode by default. This screenshot shows editing /etc/selinux/config and switching SELinux to permissive mode, ensuring CloudStack services won’t be blocked by SELinux policies.
<br>
<br>
<img src="images/Screenshot 2025-06-06 144943.png" alt="CloudStack">
<h2> 🖼️ 8.  Initializing the CloudStack Database </h2>
This screenshot captures a successful run of cloudstack-setup-databases, which initializes the CloudStack schema and creates all necessary tables. It confirms MySQL is working and that CloudStack can communicate with it.
<br>
<br>
<img src="images/Screenshot 2025-06-06 145121.png" alt="CloudStack" width="700">
<h2> 🖼️ 9. Configuring and Starting the CloudStack Management Server </h2>
Here, the cloudstack-setup-management command is used to configure the CloudStack management server. A message confirms setup is complete and notes which ports (8080, 8250, 8443, 9090) must be open for web access.
<br>
<img src="images/Screenshot 2025-06-06 145003.png" alt="CloudStack" width="600">
<h2> 🖼️ 10. NFS Storage Directories and Export Setup </h2>
CloudStack requires shared storage, and in this screenshot, I created /export/primary and /export/secondary directories and configured them for NFS export. I then used exportfs -a to activate the exports.
<img src="images/Screenshot 2025-06-06 145141.png" alt="CloudStack" width="600">
<br>
<img src="images/Screenshot 2025-06-06 145213.png" alt="CloudStack" width="600">
<h2> 🖼️ 11. Firewall Rules Configured with iptables </h2>
This screenshot shows /etc/sysconfig/iptables where custom firewall rules were added to allow essential CloudStack ports (e.g., 8080, 8250, 8443, 9090, NFS ports, etc.). These rules ensure that the management server and services are reachable through the network.
<br>
<br>
<img src="images/Screenshot 2025-06-06 145327.png" alt="CloudStack" width="600">
<h2> 🖼️ 12. Apache CloudStack Web UI – Dashboard Access</h2>
This screenshot confirms that the Apache CloudStack web dashboard is accessible at 192.168.4.150:8080, indicating that the management server is working and reachable via browser. From here, you can manage zones, storage, hypervisors, and more.
<img src="images/Screenshot 2025-06-06 145440.png" alt="CloudStack" width="600">
<h2> 🖼️ 13. Creating a VM via vSphere for CloudStack Use </h2>
This shows a new virtual machine being created in VMware ESXi (via vSphere). This VM could later be used as a CloudStack-managed guest, secondary controller, or additional system infrastructure, bridging your ESXi and CloudStack setups.
<img src="images/Screenshot 2025-06-06 145425.png" alt="CloudStack" width="600">
<br>
This is the furthest we got in this lab due to time constraints. Thank you for taking the time to view my work. 














