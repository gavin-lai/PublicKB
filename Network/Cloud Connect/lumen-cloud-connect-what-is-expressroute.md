{{{
  "title": "Lumen Cloud Connect - What is ExpressRoute",
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

Users plan to order [Lumen Cloud Connect](../../Network/Cloud Connect/lumen-cloud-connect-introduction.md) to connect to their Azure environment.

### Prerequistes

None

### What is ExpressRoute
[Microsoft Azure ExpressRoute](//azure.microsoft.com/en-us/documentation/articles/expressroute-introduction/) lets you create private connections between Microsoft datacenters and the infrastructure that’s in a co-location environment. ExpressRoute connections offer higher security, more reliability, faster speeds and predictable latencies than typical connections over the Internet. In some cases, using ExpressRoute connections to transfer data between your on-premises network and Azure can also yield significant cost benefits.
Azure offers circuit bandwidths from 50 Mbps to 10 Gbps (50Mbps, 100Mbps, 200 Mbps, 500 Mbps, 1 Gbps, 2 Gbps, 5Gbps, and 10 Gbps).
Azure compute services, namely virtual machines (IaaS) and virtual networks (VNETs) deployed within a virtual network can be connected through the Azure Private Peering domain. 
PaaS Services such as Azure Storage, SQL databases and Web Apps are offered on public IP addresses. You can privately connect to services hosted on public IP addresses, including VIPs of your cloud services, through the Microsoft Peering routing domain. You can connect the Microsoft Peering domain to your extranet and connect to all Azure services on their public IP addresses from your WAN without having to connect through the Internet


![microsoft-expressroute](../../images/network/MicrosoftExpressRoute.png)
![microsoft-expressroute-peering](../../images/network/microsoftexpressroute-peering.png)

### Lumen Cloud Connect for Microsoft ExpressRoute

![cloudconnect-azure-mpls](../../images/network/cloudconnect-azure-mpls.png)

**Cloud Provider**|**Microsoft® Azure**
-------------|-------------
**Connection Type**|**ExpressRoute**
Wavelength (Layer 1)|
Ethernet (Layer 2)|:heavy_check_mark:
IP VPN (Layer 3)|:heavy_check_mark:
Dynamic Connections|:heavy_check_mark:

For On-Ramps location, please refer to the [maps](//assets.lumen.com/is/content/Lumen/maps-cloud-connect-on-ramps?Creativeid=c3d38810-e03e-4fb5-bb94-fd6551ff7388).

To learn more on how Lumen Cloud Connect can connect your company to Microsoft Azure, please visit the [Product page](//www.lumen.com/en-us/hybrid-it-cloud/cloud-connect.html) or consult with your account team.  

### Support

* For issues related to Lumen Cloud Connect Services, please open a Lumen Support ticket by visiting [customer support](//www.lumen.com/en-us/contact-us-support.html) or [through the Lumen Support website](//www.lumen.com/help/en-us/home.html).
