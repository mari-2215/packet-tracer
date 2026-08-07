# Cloud Control Mapping

**Author:** [mari-2215](https://github.com/mari-2215)

This document explains how the reasoning practiced in the Packet Tracer labs can transfer to AWS and Microsoft Azure. It is a conceptual map, not a claim of feature parity.

## Why the mapping is not one-to-one

Cisco IOS ACLs, AWS security groups, AWS network ACLs, Azure Network Security Groups, and managed cloud firewalls differ in scope, state tracking, evaluation order, defaults, logging, identity integration, and operational ownership.

For example:

- AWS security groups are stateful and attached to resources/network interfaces; they contain allow rules.
- AWS network ACLs operate at subnet scope, support allow and deny entries, and are stateless.
- Azure NSGs filter inbound and outbound traffic at subnet or network-interface scope and evaluate numbered priorities.
- Cisco IOS ACLs are ordered interface policies applied in a specified direction and end in an implicit deny.

These differences matter during migration and incident analysis.

## Control comparison

| Lab concept | AWS | Azure | Transferable skill |
|---|---|---|---|
| VLAN trust zone | VPC subnet | VNet subnet | Segment resources by role and trust level |
| Router subinterface gateway | VPC router and route table behavior | VNet system routes and route tables | Understand next hops and routing boundaries |
| Inbound IOS ACL | Security group or network ACL, depending on intended scope | NSG or Azure Firewall policy | Express source, destination, protocol, port, direction and priority |
| Black-hole/unused segment | Isolated subnet, restrictive route table and policy | Isolated subnet, NSG and route control | Reduce unintended attachment and reachability |
| NAT overload | NAT Gateway or NAT instance pattern | Azure NAT Gateway | Separate private addressing from controlled egress |
| Restricted SSH from IT | Scoped security group, private access, Systems Manager or bastion pattern | Scoped NSG and Azure Bastion | Keep management access off broad public paths |
| IOS command evidence | VPC Flow Logs, CloudTrail and CloudWatch | Flow logs, activity logs and Azure Monitor | Validate policy with telemetry rather than configuration alone |
| Local IOS account | IAM-controlled operations and federated administration | Microsoft Entra ID and Azure RBAC | Prefer centralized identity, short-lived access and auditable authorization |

## AWS-oriented redesign of Lab 01

A cloud implementation could use:

1. One VPC with separate subnets for users/workloads, services, management, and controlled ingress/egress.
2. Route tables that expose only the required paths.
3. Security groups as the primary resource-level control.
4. Network ACLs only where stateless subnet-level defense-in-depth is justified.
5. A NAT Gateway for private-subnet egress rather than IOS PAT on a lab router.
6. Systems Manager Session Manager or a tightly controlled bastion pattern instead of broadly exposed SSH.
7. VPC Flow Logs and CloudTrail to validate network behavior and control-plane changes.

## Azure-oriented redesign of Lab 01

An Azure implementation could use:

1. A VNet with role-based subnets.
2. NSGs associated with subnets and, where justified, NICs.
3. User-defined routes when traffic must traverse an inspection point.
4. Azure NAT Gateway or another approved outbound architecture.
5. Azure Bastion for management without assigning public IP addresses to target VMs.
6. Azure Monitor and network-flow telemetry for validation and investigation.
7. Microsoft Entra ID and Azure RBAC for administrative authorization.

## Defender-oriented questions

When translating a packet-level lab to the cloud, ask:

- What is the actual enforcement scope: resource, NIC, subnet, VPC/VNet, managed firewall, or identity layer?
- Is the control stateful or stateless?
- What implicit and default rules exist?
- Which route makes the traffic reach the policy-enforcement point?
- How are changes authorized and audited?
- Which telemetry proves the allow or deny decision?
- Can the same objective be achieved without exposing SSH or RDP?
- What happens when a new workload is created without the intended policy attachment?

## Primary references

- [AWS — Control traffic using security groups](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-groups.html)
- [AWS — Control subnet traffic with network ACLs](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html)
- [AWS — Infrastructure security in Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/infrastructure-security.html)
- [Microsoft — Azure network security groups overview](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview)
- [Microsoft — Virtual networks and virtual machines](https://learn.microsoft.com/en-us/azure/virtual-network/network-overview)
- [Microsoft — Configure NSG rules for Azure Bastion](https://learn.microsoft.com/en-us/azure/bastion/bastion-nsg)

