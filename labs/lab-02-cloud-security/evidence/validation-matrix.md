# Lab 02 validation matrix

**Author:** [mari-2215](https://github.com/mari-2215)

| ID | Source | Destination / command | Expected | Result | Evidence |
|---|---|---|---|---|---|
| VAL-01 | MATRIZ | `http://198.51.100.2` | Published WEB1 page loads | Pass | [`public-web-nat.png`](public-web-nat.png) |
| VAL-02 | BASTION | SSH to `172.16.20.1` | Authenticated R-CLOUD session | Pass | Edited video |
| VAL-03 | R-CLOUD | `show ip interface brief` | WAN and required subinterfaces up/up | Pass | Edited video |
| VAL-04 | R-CLOUD | `show ip route` | Local networks and headquarters route present | Pass | [`acl-nat-validation.png`](acl-nat-validation.png) |
| VAL-05 | R-CLOUD | `show access-lists` | ACL definitions and database/management counters visible | Pass with documented WAN correction | [`acl-nat-validation.png`](acl-nat-validation.png) |
| VAL-06 | R-CLOUD | `show ip nat translations` | `198.51.100.2:80` maps to `172.16.10.11:80` | Pass | [`acl-nat-validation.png`](acl-nat-validation.png) |
| VAL-07 | MATRIZ | `ping 10.20.0.1` | Headquarters gateway reachable | Pass, 4/4 | [`connectivity-policy.png`](connectivity-policy.png) |
| VAL-08 | MATRIZ | `ping 198.51.100.2` | R-CLOUD WAN reachable | Pass, 3/4 after initial resolution | [`connectivity-policy.png`](connectivity-policy.png) |
| VAL-09 | MATRIZ | `ping 172.16.30.10` | Direct database reachability denied | Pass, blocked | [`connectivity-policy.png`](connectivity-policy.png) |
| VAL-10 | SW-CLOUD | `show interfaces trunk` | G0/1 carries VLANs 10,20,30,99 | Pass | [`vlan-trunk-validation.png`](vlan-trunk-validation.png) |
| VAL-11 | SW-CLOUD | `show interfaces status` | Endpoint access ports are connected in intended VLANs | Pass | [`vlan-trunk-validation.png`](vlan-trunk-validation.png) |

Negative tests are marked as passing when the security policy correctly blocks the attempted flow.
