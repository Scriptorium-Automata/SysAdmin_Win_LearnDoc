## Architecture Overview: AD DS Learning Lab

## Purpose
This document provides the high-level design for the Identity-as-Code lab based on the Microsoft AD DS training path.

## Forest and Domain Design
The lab will utilise a single-forest, single-domain model to reduce resource consumuption on the local hypervisor while allowing for full GPO and FSMO role testing.
- **Forest Name:** `lab.local`
- **Functional Level:** Windows Server 2025 (latest technical preview/releas)
- **Top-Level Domain (TLD):** `.local`

## Network Topoligy
The environment resides on a private Hyper-V virtual switch to isolate lab traffic from the host.
network.mermaid
graph TD
subgraph Identity_Layer
DC01
end
subgraph Client_Layer
CL01
end 
CL01 -->|DNS/LDAP| DC01

```
## Rationale
We have chosen a `.local` TLD for this lab to avoid conflicts with external DNS zones, ensuring the lab environment remains entrirely self-contained.
```