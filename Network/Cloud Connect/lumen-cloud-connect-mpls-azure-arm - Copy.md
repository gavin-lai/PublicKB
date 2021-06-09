{{{
  "title": "Lumen Cloud Connect MPLS/IPVPN to Microsoft Azurevia Azure portal Azure Resource Manager",
  "date": "06-06-2021",
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
* [Procedure to Configure Lumen Cloud Connect](#procedure-to-configure-lumen-cloud-connect)
* [Support](#support)

### Overview
The purpose of this document is to provide an end-to-end walk through for a customer setting up ExpressRoute for the first time via Lumen’s Cloud Connect. Information contained is provided to serve as a supplement to Microsoft documentation linked throughout this document. Users should check the provided links to obtain the most up-to-date information and for more details pertaining to Microsoft processes.


### Audience

Users has ordered [Lumen Cloud Connect](../../Network/Cloud Connect/lumen-cloud-connect-introduction.md) to connect to their Azure environment.

### Prerequistes

Lumen Cloud Connect is ordered and access to Azure Portal with the right permission

### What is ExpressRoute
[Microsoft Azure ExpressRoute](//azure.microsoft.com/en-us/documentation/articles/expressroute-introduction/) lets you create private connections between Microsoft datacenters and the infrastructure that’s in a co-location environment. ExpressRoute connections offer higher security, more reliability, faster speeds and predictable latencies than typical connections over the Internet. In some cases, using ExpressRoute connections to transfer data between your on-premises network and Azure can also yield significant cost benefits.
Azure offers circuit bandwidths from 50 Mbps to 10 Gbps (50Mbps, 100Mbps, 200 Mbps, 500 Mbps, 1 Gbps, 2 Gbps, 5Gbps, and 10 Gbps).
Azure compute services, namely virtual machines (IaaS) and virtual networks (VNETs) deployed within a virtual network can be connected through the Azure Private Peering domain. 
PaaS Services such as Azure Storage, SQL databases and Web Apps are offered on public IP addresses. You can privately connect to services hosted on public IP addresses, including VIPs of your cloud services, through the Microsoft Peering routing domain. You can connect the Microsoft Peering domain to your extranet and connect to all Azure services on their public IP addresses from your WAN without having to connect through the Internet


![microsoft-expressroute](../../images/network/MicrosoftExpressRoute.png)
![microsoft-expressroute-peering](../../images/network/microsoftexpressroute-peering.png)

### Lumen Cloud Connect for Microsoft ExpressRoute

![cloudconnect-azure-mpls](../../images/network/cloudconnect-azure-mpls.png)

* Customer is responsible for express route costs and configuration
* Firewall / NAT services will be provided by Lumen when accessing Microsoft Peering for PaaS/SaaS Services

### Lumen Cloud Connect Roles and Responsibilities
**Steps required to set up Azure ExpressRoute connectivity**|**End Customer**|**Lumen**|**Microsoft Azure (Automated via portal)**
-------------|-------------|-------------|-------------
**Set up physical connectivity to Azure ExpressRoute location**| | |
Decide on the type of BGP peering required (Azure Private Peering-IaaS or Microsoft Peering-PaaS/SaaS)|X| |
Order Layer 3 (MPLS) Cloud Connect service to Azure ExpressRoute location from Lumen Account Team|X| | 
Order MSFT Azure ExpressRoute connection via MSFT Azure Portal, using “Level 3 Communications – IPVPN” as the Service Provider name, with the appropriate bandwidth and location.  *see your Cloud Connect Solutions Architect for more details or direction. More options can be available by contacting your Lumen sales representative.|X| |
Provision Layer 3 (MPLS) Service device with BGP, connecting to MSFT Azure ExpressRoute| |X|
Provision ExpressRoute circuit and provide the ExpressRoute Service Key to Lumen| | |X
**Set up BGP peering between Lumen provided customer edge and Azure edge device**| | |
Configure BGP Peering on Lumen PE Routers| |X|
Configure BGP Peering on Azure side| |X|
Configure BGP Route Filtering (:warning: required for Microsoft Peering PaaS/SaaS)|X| |
**Link services on Azure to the dedicated circuit**| | |
Link virtual Network(s) to the dedicated circuit*|X| |


Placeholder for overview pages for each of the cloud providers
* AWS
* Azure
* GCP
* Oracle
* IBM

### Procedure to Configure Lumen Cloud Connect

For new Lumen Cloud Connect users, please refer to [product readiness page](//www.lumen.com/help/en-us/readiness/products.html)
Examples include:
* [EVPL to Microsoft Azure](//www.lumen.com/content/dam/lumen/help/readiness/evpl-to-microsoft-azure.pdf)
* [MPLS/IPVPN to AWS with Dedicated Cross Connect](//www.lumen.com/content/dam/lumen/help/readiness/mpls-ipvpn-to-aws-with-dedicated-cross-connect.pdf)

### Support

* For issues related to Lumen Cloud Connect Services, please open a Lumen Support ticket by visiting [customer support](//www.lumen.com/en-us/contact-us-support.html) or [through the Lumen Support website](//www.lumen.com/help/en-us/home.html).
