# Enterprise P1 War Room Simulator

An interactive, Senior-to-Principal level Major Incident Bridge simulator for practicing high-pressure network, firewall, and cloud outage troubleshooting.

## Overview

In large enterprise environments, resolving a Severity-1 (P1) outage rarely comes down to memorizing a single vendor's CLI syntax. It requires isolating layer boundaries across multi-vendor stacks, proving packet flow on the wire, navigating siloed engineering teams, and enforcing strict emergency change governance before touching production.

This prompt turns an AI session into a live P1 conference call with:
- **Multi-Vendor Enterprise Topologies:** Fortinet (FortiGate), Cisco Secure Firewall (FTD/FMC), Cisco routing/switching, F5 BIG-IP, and Microsoft Azure (ExpressRoute, vWAN, VNets, BGP).
- **Zero Hand-Holding:** No hints, highlighted log lines, or suggested next steps—diagnose strictly through raw packet captures, connection state flags, routing tables, and audit logs.
- **Realistic Bridge Dynamics:** Competing team silos (Cloud vs. Data Center/Firewall), a Major Incident Manager tracking time and change control, and an executive post-incident evaluation.

## How to Use

1. Open [`p1-incident-bridge-simulator.md`](./p1-incident-bridge-simulator.md) and copy the entire prompt.
2. Start a new chat session in your preferred LLM interface.
3. Paste the prompt (optionally specifying a focus area at the bottom, such as `FortiGate + Azure BGP` or `Cisco FTD asymmetric routing`).
4. Step onto the bridge as the external Principal Infrastructure Consultant and drive the investigation to resolution.

## Core Simulation Phases

1. **Triage & Isolation:** Clarify traffic flows (NAT vs. routing, ingress/egress paths) and request targeted wire captures to eliminate silo finger-pointing.
2. **State & Control-Plane Analysis:** Inspect connection tables, drop counters, route lookups, and policy-based routing behavior.
3. **Audit & Governance:** Verify configuration history, check deployment queues for uncommitted changes, notify stakeholders, and document the emergency change before deploying a rollback or fix.
4. **Post-Incident Review:** Hand off internal follow-ups cleanly, review the executive impact summary, and analyze diagnostic efficiency.
