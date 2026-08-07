# Packet Tracer Cybersecurity Portfolio

Hands-on network security labs designed, built, tested, and documented by **[mari-2215](https://github.com/mari-2215)**.

This repository turns Cisco Packet Tracer exercises into evidence-based security projects. Each lab is organized around a business scenario, a threat model, explicit security controls, positive and negative tests, troubleshooting notes, and a conceptual mapping to AWS and Microsoft Azure.

> Packet Tracer is used here to demonstrate networking and security fundamentals. Cloud mappings are conceptual; they do not claim that Cisco IOS ACLs and cloud-native controls behave identically.

## Featured project

### Lab 01 — Segmented Enterprise Network

A small enterprise network segmented into user, finance, server, IT, guest, management, and black-hole VLANs. The design uses 802.1Q trunks, router-on-a-stick, DHCP, NAT configuration, extended ACLs, and restricted SSH administration.

[Open the complete Lab 01 documentation](labs/lab-01-zero-trust-enterprise/README.md)

[Watch or download the final demonstration video](labs/lab-01-zero-trust-enterprise/video/Lab_01_portfolio_FINAL.mp4)

![Lab 01 validation](docs/assets/lab-01-cover.png)

## Portfolio roadmap

| Project | Security focus | Status |
|---|---|---|
| [Lab 01 — Segmented Enterprise Network](labs/lab-01-zero-trust-enterprise/README.md) | VLAN segmentation, ACLs, SSH, DHCP and troubleshooting | Documented |
| [Lab 02 — Cloud Security Architecture](labs/lab-02-cloud-security/README.md) | DMZ, private tiers, NAT and cloud control mapping | Planned |
| [Lab 03 — Incident Detection and Containment](labs/lab-03-incident-response/README.md) | Logging, indicators, ACL containment and recovery | Planned |
| [Lab 04 — Healthcare Network Segmentation](labs/lab-04-healthcare-segmentation/README.md) | Clinical, IoMT, administrative and guest isolation | Planned |
| [Lab 05 — Resilient Branch Routing](labs/lab-05-ospf-resilience/README.md) | OSPF, path preference, failure and convergence | Planned |
| [Lab 06 — Secure Administration](labs/lab-06-secure-administration/README.md) | SSH, AAA, RADIUS, RBAC and management-plane isolation | Planned |
| [Packets from Hell](labs/packets-from-hell/README.md) | OSPF, TTL, routing loops, STP and themed packet journeys | Planned |

## Repository structure

```text
.
├── docs/
│   ├── assets/                 # Portfolio-ready evidence images
│   ├── cloud-control-mapping.md
│   ├── learning-roadmap.md
│   └── references.md
├── labs/
│   ├── lab-01-zero-trust-enterprise/
│   │   ├── configs/            # Reference target configurations
│   │   ├── evidence/           # Validation notes and screenshots
│   │   ├── packet-tracer/      # Location for the .pkt artifact
│   │   └── video/              # Edited demonstration
│   └── ...                     # Future labs follow the same structure
└── templates/
    ├── lab-readme-template.md
    └── validation-matrix-template.md
```

## Documentation standard

Every completed lab should contain:

1. An executive summary and business scenario.
2. A diagram and addressing plan.
3. A short threat model.
4. The security controls and their rationale.
5. Reproducible configuration references.
6. Positive and negative validation cases.
7. Evidence such as screenshots, command output, and video.
8. Troubleshooting notes and known limitations.
9. A conceptual AWS and Azure mapping.
10. Links to primary vendor documentation.

## Portfolio principles

- **Evidence over claims:** a control is marked as validated only when the repository contains supporting output.
- **Negative testing matters:** security demonstrations include expected failures, not only successful pings.
- **Troubleshooting is part of the work:** cabling, VLAN membership, addressing, and policy-order mistakes are documented rather than hidden.
- **Least privilege:** administrative access and inter-zone traffic should be limited to required sources and destinations.
- **No production secrets:** all passwords, addresses, and names are lab-only examples.

## Technology represented

- Cisco Packet Tracer
- Cisco IOS-style switching and routing
- IEEE 802.1Q VLAN trunks
- Inter-VLAN routing with subinterfaces
- IPv4, DHCP, DNS and NAT concepts
- Standard and extended access control lists
- SSH management-plane access
- AWS VPC and Azure Virtual Network control mapping

## Responsible-use notice

These labs are defensive educational environments. They are not production architectures, penetration-testing authorizations, or substitutes for vendor-specific design review. Only test systems that you own or are explicitly authorized to assess.

## Author

**mari-2215**  
GitHub: [github.com/mari-2215](https://github.com/mari-2215)

