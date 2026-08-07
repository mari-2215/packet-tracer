# Lab 01 Validation Matrix

**Tester:** mari-2215  
**Environment:** Cisco Packet Tracer  
**Evidence video:** [`../video/Lab_01_portfolio_FINAL.mp4`](../video/Lab_01_portfolio_FINAL.mp4)

| ID | Source | Action | Expected result | Observed result | Status |
|---|---|---|---|---|---|
| VAL-01 | VLAN 40 host `10.10.40.21` | `ping 10.10.40.1` | Router reachable | Four replies, no loss | PASS |
| VAL-02 | VLAN 40 host | `ssh -l admin 10.10.40.1` | Login permitted | R1-ZT prompt obtained | PASS |
| VAL-03 | SSH session | `show users` | Admin visible on VTY | `admin` displayed on VTY 0 | PASS |
| VAL-04 | SSH session | `show ip interface brief` | Required routed interfaces up/up | Subinterfaces displayed up/up | PASS |
| VAL-05 | VLAN 50 host `10.10.50.21` | `ping 10.10.30.10` | Internal access unsuccessful | Destination unreachable / 100% loss | PASS as negative reachability test |
| VAL-06 | VLAN 50 host | `ping 198.51.100.10` | External access succeeds | Recording inconclusive | NOT VALIDATED |
| VAL-07 | R1-ZT | `show access-lists GUEST-IN` after test | Deny counter increases | Counter not captured | NOT VALIDATED |
| VAL-08 | R1-ZT | `show ip nat translations` after egress | Translation displayed | Not captured | NOT VALIDATED |

## Evidence-quality note

VAL-05 proves that the attempted internal communication was unsuccessful. Because ACL counters were not captured in the same evidence chain, the repository does not claim that the video alone identifies the exact dropping rule.

## Recommended re-test

```text
R1-ZT# clear access-list counters

PC-GUEST> ping 10.10.30.10

R1-ZT# show access-lists GUEST-IN
```

Capture the ACL before the test, the negative test, and the increased deny counter without changing configuration between steps.

