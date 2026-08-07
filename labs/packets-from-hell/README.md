# Packets from Hell

**Author:** [mari-2215](https://github.com/mari-2215)  
**Status:** Planned  
**Tone:** Technically serious, visually ridiculous

## Concept

Five routers form a pentagram-shaped routed topology. Packets travel through named nodes while the lab demonstrates OSPF path selection, TTL behavior, controlled routing loops, failure recovery, and spanning-tree convergence.

The theme is humorous; the networking evidence must remain reproducible.

## Planned nodes

- `LUCIFER`
- `LEVIATHAN`
- `BEELZEBUB`
- `BELIAL`
- `MAMMON`
- `INFERNO` service host
- `CULTIST-PC` traffic source
- `HOLY-SERVER` protected destination

## Planned tests

| ID | Scenario | Expected evidence |
|---|---|---|
| HF-01 | Source reaches INFERNO through OSPF | Preferred path and route entries |
| HF-02 | One red link fails | Alternate route appears |
| HF-03 | Controlled static routing loop | TTL expires; loop identified |
| HF-04 | Incorrect routes removed | Normal failure behavior restored |
| HF-05 | Redundant Layer 2 ring | STP blocks one path |
| HF-06 | Active STP link fails | Alternate port transitions to forwarding |
| HF-07 | Guest-demon reaches for HOLY-SERVER | `EXORCISM` ACL blocks the flow |

## Safety boundary

All traffic remains inside Packet Tracer. The routing loop is created only for an unused demonstration network and is removed immediately after observing TTL behavior.

