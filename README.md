<h2> 🧭 Overview </h2>
<br>
This project documents a lab environment set up for exploring Apache CloudStack with VMware ESXi as the hypervisor. This project focused on configuring bare-metal servers, configuring a ubiquiti dream machine, configuring nodes, Apache CloudStack installation, Vcenter installation and configuration, CentOS, and VirtualBox.
<br>
<br>
<h2> 💻 Part 1 - VMware ESXi Installation </h2>
<br>
This screenshot shows the installation process of VMware ESXi on our physical server. At this stage, we were setting up the hypervisor that would later allow us to host and manage virtual machines in our cloud environment. This was done using a bootable USB with the ESXi installer:
<br>
<img src="images/Screenshot 2025-06-05 180150.png" alt="hostname" height="550">
<br>
After completing the installation of VMware ESXi, we reached the post-installation summary screen which displayed the assigned IPv4 address for the ESXi host. This address was statically configured to allow remote access via the web interface. This IP would be used to access the ESXi management portal from a browser. 

<img src="images/Screenshot 2025-06-05 182227.png" alt="hostname" height="550">
<br>
Note that the IP addresses are different between the screenshots because we kept changing them due to configuration issues. This screenshot shows successful access to the VMware ESXi web management interface through a browser. Using the previously configured static IP address, we verified that the hypervisor was up and network-reachable. This interface would be used to create and manage virtual machines in future phases of the lab.
<img src="images/Screenshot 2025-06-05 182345.png" alt="hostname" height="550">
<br>
Here, the ESXi configuration summary screen provides key details about the host, such as its CPU, memory, storage, and network configuration. Reviewing this information helped us ensure that the host was correctly recognized and ready to support virtual infrastructure provisioning.
<img src="images/Screenshot 2025-06-05 182444.png" alt="hostname" height="550">
<br>
<h2> 💻 Part 2 - VMware VCenter Installation </h2>
<br>
VMware vCenter Server is a centralized management platform that lets you manage multiple ESXi hypervisors, virtual machines, and associated resources from a single web interface. It's easier to manage multiple ESXi hosts through Vcenter rather than managing each one through its web interface (https://<host-ip>)
<br>
In this step, we specified the deployment target for the vCenter Server — the ESXi host where the vCenter VM would be installed. We entered the ESXi host’s IP address (192.168.4.241), HTTPS port (443), and administrative credentials (root). This began Stage 1 of the vCenter installer workflow. ✍️ Note: During the lab, the ESXi host was initially assigned a static IP in the `192.168.0.57`, '192.168.1.241', and '192.168.1.245'. Before deploying vCenter, we reconfigured the ESXi host with a new static IP address: `192.168.4.241`, to align with our management subnet used for centralized orchestration:

<img src="images/a part of part 2.png" alt="hostname" height="550">
<br>

This screenshot shows the step where we defined the vCenter virtual machine’s name, root password, and other configuration parameters needed to deploy the appliance on the ESXi host. This creates the actual VM instance that will become the vCenter server: 
<img src="images/Screenshot 2025-06-05 185438.png" alt="hostname" height="550">
<br>
In this stage, we configured networking for the vCenter appliance, including the static IP address, subnet, default gateway, and DNS settings. A static address ensures the vCenter remains reachable within the management network:
<img src="images/Screenshot 2025-06-05 185610.png" alt="hostname" height="550">
<br>
Here successfully installed vCenter:
<img src="images/Screenshot 2025-06-05 185914.png" alt="hostname" height="550">
<br>
<img src="images/Screenshot 2025-06-05 190027.png" alt="hostname" height="550">
<br>
After deployment, we accessed the vCenter Server web UI using a browser and the configured IP address. Reaching this page confirmed successful deployment and network accessibility.
<img src="images/Screenshot 2025-06-05 190158.png" alt="hostname" height="550">
<br>
<img src="images/Screenshot 2025-06-05 190342.png" alt="hostname" height="550">
<br>
The first post-deployment step was to create a datacenter within vCenter. This logical container allows grouping and management of multiple ESXi hosts under one centralized structure:
<img src="images/Screenshot 2025-06-05 190509.png" alt="hostname" height="550">
<br>
Finally, we added our ESXi hosts to the vCenter datacenter. This allows centralized management, VM migration, monitoring, and clustering features:
<img src="images/Screenshot 2025-06-05 190721.png" alt="hostname" height="550">
<br>
<img src="images/Screenshot 2025-06-05 191639.png" alt="hostname" height="550">
<br>
<img src="images/Screenshot 2025-06-05 190826.png" alt="hostname" height="550">





