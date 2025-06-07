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
<h2> 🖼️ 6. Starting MySQL and Running the Secure Setup </h2>
After configuring the database, we started the MySQL service and ran mysql_secure_installation to set the root password, remove anonymous users, and secure the installation. This step is essential before initializing the CloudStack database schema. Apologies for the blurry photo. 
<br>
<br>
<img src="images/Screenshot 2025-06-06 144822.png" alt="CloudStack" width="460">

















