{{{
  "title": "Lumen Cloud Connect Services Introduction",
  "date": "05-18-2021",
  "author": "Gavin Lai",
  "attachments": [
  {
    "file_name": "Sample CloudFormation template to create VPC with VPN connectivity",
    "url": "../attachments/vpn-vpc-cloudforamtion.zip",
    "type": "application/zip"
  }
  ],
  "contentIsHTML": false,
  "sticky": true
}}}

### In this article:

* [Overview](#overview)
* [Audience](#audience)
* [Prerequistes](#prerequistes)
* [Lumen Cloud Connect Capabilities and Flexibility](#lumen-cloudconnect-capabilities-flexibility)
* [Cloud Providers supported by Lumen Cloud Connect](#cloud-providers-supported-by-lumne-cloud-cloudconnect)
* [Lumen Cloud Connect Connectivity Options](#lumen-cloud-connect-connectivity-options)
* [VPN setup with an existing VPC](#vpn-setup-with-an-existing-vpc)
* [VPN Configuration on CLC](#vpn-configuration-on-clc)
  * [Phase 1](#phase-1)
  * [Phase 2](#phase-2)
* [Verify AWS Route Tables ](#verify-aws-route-tables)
* [Custom Configurations](#custom-configurations)
* [Support](#support)

### Overview
Lumen Cloud Connect Solutions delivers secure, high-performance and virtualized networking functionality to leading public and private clouds. Our global reach and extensive Wavelength, Carrier Ethernet and IP VPN connectivity options meet today’s hybrid cloud business requirements. And available, dynamic SDN-based controls can provide you with a network experience that matches your cloud experience.

### Audience

All users intertest in connecting to any public cloud platform

### Prerequistes

None

### CloudConnect Capabilities and Flexibility
* Capabilities
  * Global Reach - Cloud connections in the North American, European, Latin American and Asia-Pacific regions
  * Connectivity - Extensive connectivity options including Wavelengths, Ethernet Services and IP VPN, globally for most major CSPs
  * Visibility - Available portals, mobile applications and APIs for accessibility to data, metrics and SDN network controls
  * Data Center Connectivity - 360+ Lumen data centers, 2,200 third-party data centers
* Flexibility
  * Dynamic SDN-based capabilities are layered onto network services to provide greater visibility, flexibility and control of application traffic traversing your metro or wide-area network

![lumen-cloud-coneect](../../images/cloudconnect/cloud-connect.png)

### Cloud Providers supported by Lumen Cloud Connect

* Amazon Web Services® Direct Connect
* Microsoft® ExpressRouteTM
* Google® Cloud Partner Interconnect
* Google® Cloud Carrier Peering
* IBM® Resiliency Services
* IBM® Cloud Managed Services
* IBM® Cloud Direct Link
* Oracle® Cloud Infrastructure FastConnect

For providers not listed above, please contact your Lumen sales representative with your destinations.

### Lumen Cloud Connect Connectivity Options
**Cloud Provider/Connection Type**|**AWS**|**Azure**|**GCP**|**Oracle**|IBM Cloud**|**IBM Resiliency Services and Cloud Managed Services**
-------------|-------------|-------------|-------------|-------------|-------------|-------------
Layer 1 (WaveLength)|X|X|X|X|X|
Layer 2 (Ethernet)|X|X|X|X| |X
Layer 3 (MPLS/IP VPN)|X|X| | |X|X

### VPN setup with an existing VPC

1. Under VPC, Virtual Private Gateways, create a VPG for the VPC if one does not exist

   ![aws-vpg](../../images/awsvpn/aws-vpg.png)

2. Once it is created, create a VPN connection under VPC on AWS portal

   ![aws-vpn](../../images/awsvpn/aws-vpn.png)  

3. Provide  
  *	Name Tag  
  *	Virtual Private Gateway that the VPN is connecting  
  *	Customer Gateway (New for Lumen Cloud)  
  *	IP can be found in Create VPN page on Lumen Cloud (1 per data center)  
  *	BGP ASN (leave as default)  
  *	Routing option: Static  
  *	Enter Lumen Cloud Network(s) that needs to communicate with AWS environment  
  *	Tunnel Options: default  
4. Using the AWS VPN configuration file, with the information from the file, complete the VPN setup in Lumen Cloud Site to Site VPN setup

### VPN Configuration on CLC
1. From Lumen Cloud portal under Network -> Site to Site VPN.  Detail is for the Lumen Cloud Site to Site VPN setup is available here. Pick the VPN endpoint that is configured as part of the AWS VPN configuration and add the Lumen Cloud VLAN(s) as part of the VPN setup for **VPN Peer IPv4 Address**.
   ![aws-vpn](../../images/awsvpn/clc-vpn-endpoint.png)

2. Enter **Site Name** (this can be the AWS VPN Connection ID) and **Device Name** (can be anything or using the AWS VPN ID).  

   **VPN Peer IPv4 Address** is the Remote Gateway from the configuration file.  

3. **Tunnel Encrypted Subnets** : Click **Add network block**. This is the private subnet from the AWS VPC.

4. Click **next: phase 1**   

Using the VPN configuration file downloaded to complete the next two step

#### Phase 1

* **Protocol Mode** - Main
* **Encryption Algorithm** - AES-128 (can be AES-128, AES-192, AES-256 or 3DES)
* **Hashing Algorithm** - SHA1(96) (can be SHA1, SHA2 or MD5)
* **Pre-Shared Key** - Shared Key from the AWS VPN configuration
* **Diffie-Hellman Group** - Group 2
* **Lifetime Value** - 8 hours
* **DPD State** - ON
* NAT-T State - OFF

#### Phase 2  
* **IPEC Protocol** ESP  
* **Encryption Algorithm**: AES-128   
* **Hashing Algorithm**: SHA1  
* **PFS Enabled**: ON, Group 2  
* **Lifetime Value**: 1 hour  

Click **Finish**.  
Once the Lumen VPN is created, check on the AWS portal and click on **VPN connections**. The tunnel should now be **UP**.  


### Verify AWS Route Tables
1. Once VPN setup is completed, verify the VPC Route Tables is correct, either the default route or the Lumen subnets should be routed through the Virtual Private Network
   ![aws-routing](../../images/awsvpn/aws-routing.png)
2. Ensure Network ACL and Security Group are configured to allow traffic from the CLC network  
   ![acl](../../images/awsvpn/acl.png)  
   ![aws-securitygroup](../../images/awsvpn/aws-securitygroup.png)  
3. Initiate “ping” or SSH from a CLC server to a server in the AWS network to validate the connectivity

### Custom configurations
Customers who require custom configuration can leverage our [service task](//www.ctl.io/service-tasks/#vpn-tunnels-deployment). Examples include:
* Redundant VPN Tunnels
* AES256 IPSEC Encryption

### Support

* For issues related to cloud infrastructure (VM's, network, etc), or if you experience a problem deploying any Blueprint or Script Package, please open a Lumen Cloud Support ticket by emailing [help@ctl.io](mailto:help@ctl.io) or [through the Lumen Cloud Support website](//t3n.zendesk.com/tickets/new).
