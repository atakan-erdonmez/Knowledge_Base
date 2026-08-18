---
link:
  - "[[00_KnowledgeBase/1- MOCs/AWS]]"
tag:
  - "[[00_KnowledgeBase/2- Tags/Networking|Networking]]"
  - "[[00_KnowledgeBase/2- Tags/Security|Security]]"
---
To connect Site-to-Site VPN, you need:
1. Virtual Private Gateway (VGW) ^df075d
	- VPN concentrator on the AWS side
	- VGW is created and attached to the VPC 
	- Only one VGW can be attached to a single VPC

2. Customer Gateway (CGW)
	- Software application or physical device on datacenter side

> Important step: You should enable **Route Propagation** 


### VPN CloudHub
For multiple VPN connections. Low-cost hub-and-spoke model.

## AWS Managed Site-to-Site VPN Overview

By default, Amazon VPC instances cannot communicate with an on-premises network. To bridge this gap, you can establish an **AWS-managed Site-to-Site VPN**, which utilizes industry-standard **Internet Protocol Security (IPsec)** tunnels to securely connect your cloud infrastructure to your remote network.
![[AWS S2S VPN Overview.png]]
### Architecture Components

To deploy a single VPN connection, you must provision and configure the following components across both environments:

| **Component**                       | **Location** | **Description**                                                                                                                                                        |
| ----------------------------------- | ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Virtual Private Gateway (VGW)**   | AWS Side     | The VPN concentrator attached to your VPC that acts as the cloud anchor for the VPN tunnels.                                                                           |
| **Customer Gateway (CGW) Resource** | AWS Side     | A logical resource created within AWS that defines your on-premises gateway configuration to the cloud.                                                                |
| **Customer Gateway Device**         | On-Premises  | The physical appliance or software application on your remote network. It requires a static, internet-routable public IP address configured on its external interface. |

### Deployment Prerequisites & Workflow

To successfully route traffic between your VPC and your on-premises network, complete the following implementation steps:

- **Provision Hardware:** Define the Customer Gateway (CGW) resource in AWS using your on-premises public IP address.
    
- **Attach Gateway:** Create and attach a Virtual Private Gateway (VGW) to the target VPC.
    
- **Establish Tunnels:** Initiate the AWS-managed VPN connection to link the VGW and CGW.
    
- **Update Routing:** Configure a custom VPC route table with a route entry pointing your on-premises CIDR block destination to the VGW as the target.
    
- **Adjust Firewall Rules:** Update VPC Security Groups and Network Access Control Lists (NACLs) to permit inbound and outbound traffic from the remote network's IP range.
    
- **Configure Local Appliance:** Download the AWS configuration file and apply the IPsec tunnel settings to your physical on-premises gateway device.
