# Lab 06 — Secure Management and IAM

**Author:** [mari-2215](https://github.com/mari-2215)

**Status:** Validated with a documented Packet Tracer limitation

## Executive summary

This lab builds a dedicated management plane for a Cisco Packet Tracer environment. Administrative access is restricted to the management network, remote administration uses SSH instead of Telnet, and AAA is designed around a RADIUS service with a controlled local fallback account.

The evidence intentionally separates what was configured from what was successfully validated. RADIUS reachability and service configuration are demonstrated, but Packet Tracer did not provide repeatable RADIUS authentication. The successful SSH session therefore proves the local fallback path, not a RADIUS login.

## Business scenario

An organization needs to prevent ordinary user devices from administering network infrastructure. Administrators require a dedicated path, centralized identity is preferred, and an emergency local account must remain available when the identity service is unavailable.

## Topology and addressing

| Component | Role | Address or network |
|---|---|---|
| `R1-MGMT` | Managed router and SSH target | `10.60.99.1/24` |
| `ADMIN-PC` | Authorized management workstation | `10.60.99.10/24` |
| `RADIUS` | AAA service | `10.60.99.30/24` |
| Management zone | Administrative traffic | `10.60.99.0/24` |
| User zone | Ordinary endpoint traffic | `10.60.10.0/24` |

The switch separates management and user access ports. Router interfaces provide the gateway paths for the two security zones.

## Security controls

- Dedicated management and user networks reduce administrative exposure.
- VTY lines accept SSH and reject Telnet.
- A standard ACL limits VTY access to `10.60.99.0/24`.
- AAA is enabled with a RADIUS-first design and local fallback.
- The `breakglass` account provides controlled recovery access.
- A five-minute VTY idle timeout reduces abandoned administrative sessions.
- Configuration evidence and positive and negative tests are captured in the edited video.

## Validation evidence

| Test | Expected result | Evidence status |
|---|---|---|
| Management workstation reaches `R1-MGMT` | Success | Validated |
| Router reaches the RADIUS server | Success | Validated (`5/5` ICMP replies) |
| SSH using the local fallback account | Success | Validated |
| Telnet to the router | Connection closed | Validated |
| VTY source restriction | Management subnet permitted by ACL 10 | Configuration and match evidence captured |
| RADIUS-backed SSH authentication | Centralized login succeeds | Not claimed; simulator behavior was not repeatable |

## Artifacts

- [Packet Tracer topology](packet-tracer/Lab_06_Secure_Management_IAM.pkt)
- [Edited validation video](video/Lab_06_Secure_Management_IAM_Final.mp4)

The video is silent by design so that operating-system notifications and unrelated audio are excluded. Chapter labels make each control and test understandable without narration.

## Troubleshooting findings

- Packet Tracer accepts different RADIUS command syntaxes depending on the simulated IOS image.
- ICMP reachability proves network connectivity but does not prove AAA authentication.
- A local SSH success must not be presented as centralized RADIUS success.
- Management ACLs, interface addressing, service secrets, AAA method lists, and the RADIUS client definition must all agree.

## Cloud security mapping

| Lab concept | AWS analogy | Microsoft Azure analogy |
|---|---|---|
| Central administrative identity | IAM Identity Center / IAM | Microsoft Entra ID |
| Restricted management path | Systems Manager Session Manager or controlled bastion access | Azure Bastion |
| Source-based access restriction | Security groups and network ACLs | Network security groups |
| Emergency local identity | Controlled break-glass access | Emergency access account |
| Administrative audit trail | AWS CloudTrail | Azure Activity Log |

These mappings are conceptual. Cisco IOS AAA and ACL behavior is not identical to cloud-native identity and network controls.

## Portfolio takeaway

The lab demonstrates management-plane segmentation, least-privilege remote access, SSH hardening, AAA design, negative testing, fallback planning, and honest documentation of simulator limitations.

## Author

**mari-2215**

[github.com/mari-2215](https://github.com/mari-2215)
