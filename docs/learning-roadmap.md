# Learning Roadmap

**Portfolio owner:** [mari-2215](https://github.com/mari-2215)

The projects are ordered to build from packet flow and segmentation toward cloud defense, incident response, resilience, and secure administration.

| Stage | Project | Main outcome |
|---:|---|---|
| 1 | Lab 01 — Segmented Enterprise Network | Explain VLANs, trunks, gateways, ACL direction, DHCP and SSH evidence |
| 2 | Lab 02 — Cloud Security Architecture | Design public, application and database tiers with explicit trust boundaries |
| 3 | Lab 03 — Incident Detection and Containment | Capture a baseline, identify suspicious traffic, contain it and prove recovery |
| 4 | Lab 04 — Healthcare Segmentation | Apply risk-based isolation to clinical, IoMT, administrative and guest zones |
| 5 | Lab 05 — OSPF Resilience | Demonstrate normal path, failure event, convergence and restored service |
| 6 | Lab 06 — Secure Administration | Add AAA/RADIUS, management-plane isolation, RBAC concepts and fallback testing |
| 7 | Packets from Hell | Combine routing, TTL, OSPF and STP in a memorable troubleshooting challenge |

## Evidence progression

Each new lab should improve the previous one by capturing:

1. A clean initial state.
2. The exact test command or action.
3. The observed result.
4. The enforcing control and its counters/logs.
5. A recovery or rollback path.
6. A final state with no unresolved topology indicators.

## Cloud-defense progression

- Map segmentation to AWS VPC subnets and Azure VNet subnets.
- Compare stateful and stateless policy controls.
- Add flow-log analysis and control-plane audit trails.
- Replace persistent local administration with centralized identity patterns.
- Practice least privilege, change review, incident containment, and evidence preservation.

