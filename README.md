# Enterprise P1 War Room Simulator

An interactive, Senior-to-Principal level Major Incident Bridge simulator for practicing high-pressure network, firewall, and cloud outage troubleshooting.

## Overview

In large enterprise environments, resolving a Severity-1 (P1) outage rarely comes down to memorizing a single vendor's CLI syntax. It requires isolating layer boundaries across multi-vendor stacks, proving packet flow on the wire, navigating siloed engineering teams, and enforcing strict emergency change governance before touching production.

This prompt turns an AI session into a live P1 conference call with:
- **Multi-Vendor Enterprise Topologies:** Fortinet (FortiGate), Cisco Secure Firewall (FTD/FMC), Cisco routing/switching, F5 BIG-IP, and Microsoft Azure (ExpressRoute, vWAN, VNets, BGP).
- **Zero Hand-Holding:** No hints, highlighted log lines, or suggested next steps—diagnose strictly through raw packet captures, connection state flags, routing tables, and audit logs.
- **Realistic Bridge Dynamics:** Competing team silos (Cloud vs. Data Center/Firewall), a Major Incident Manager tracking time and change control, and an executive post-incident evaluation.
- **5-Skill Principal Scorecard:** An objective 1–10 evaluation at the end of every session across key incident-command dimensions.

## How to Use

1. Open [`p1-incident-bridge-simulator.md`](./p1-incident-bridge-simulator.md) and copy the entire prompt.
2. Start a new chat session in your preferred LLM interface.
3. Paste the prompt (optionally specifying a focus area at the bottom).
4. Step onto the bridge as the external Principal Infrastructure Consultant and drive the investigation to resolution.

## Customizing for Your Specialization

You can tailor the simulator to match your specific role, tech stack, or target difficulty by adjusting two sections of the prompt before pasting:

### 1. Swap the Tech Stack (Rule 1)
Replace the default vendor list in **Rule 1 (`My Role & Tech Stack`)** with your environment:
- **Cloud & Hybrid Networking:** `AWS (Transit Gateway, Direct Connect, Network Firewall), Azure vWAN, Terraform, BGP/EVPN`
- **Security & Zero Trust:** `Palo Alto Networks (PAN-OS/Panorama), Zscaler ZIA/ZPA, FortiGate, Okta/SAML`
- **Data Center & Load Balancing:** `Cisco Nexus (NX-OS/ACI), Arista EOS, F5 BIG-IP (LTM/GTM), VMware NSX`
- **Enterprise Wireless & Campus:** `Cisco Catalyst Center / WLC 9800, Aruba ClearPass, RADIUS/802.1X, DHCP/DNS`

### 2. Set a Scenario Focus (`How to Start`)
Append a specific constraint to the final line of the prompt to target a particular failure mode:
- **Asymmetric Routing / Stateful Drops:** *"Focus: Asymmetric routing across dual-homed ExpressRoute circuits hitting a stateful firewall."*
- **Control-Plane / BGP Instability:** *"Focus: BGP route leak or community misconfiguration between on-prem core routers and cloud edge."*
- **TLS / Application Delivery:** *"Focus: Intermittent HTTPS timeouts between an F5 load balancer and backend microservices."*
- **High-Chaos Mode:** *"Include a red herring metric from one of the teams and an executive asking for ETAs every few turns."*

### 3. Dial Up the Realism ("Pain Mode" Modifiers)
If the default simulation feels too smooth, append any of these modifiers to **Rule 2** or **Rule 3** of the prompt to simulate real-world 2:00 AM bridge friction:

- **Tooling & Access Friction:** *"Occasionally make an engineer take an extra turn to get CLI access, run a capture on the wrong interface/VRF first, or ask for clarification on pre-NAT vs. post-NAT IPs before returning the right output."*
- **Noisy Logs & Red Herrings:** *"Bury the relevant flow inside realistic background noise (health-check probes, unrelated drops, or a red herring metric from one of the teams) so I have to filter out false leads."*
- **Executive DR Pressure:** *"Have a VP or Application Owner join mid-call pushing for a premature DR failover that would worsen the outage unless I talk them down with concrete technical evidence."*

## Core Simulation Phases

1. **Triage & Isolation:** Clarify traffic flows (NAT vs. routing, ingress/egress paths) and request targeted wire captures to eliminate silo finger-pointing.
2. **State & Control-Plane Analysis:** Inspect connection tables, drop counters, route lookups, and policy-based routing behavior.
3. **Audit & Governance:** Verify configuration history, check deployment queues for uncommitted changes, notify stakeholders, and document the emergency change before deploying a rollback or fix.
4. **Post-Incident Review & Scorecard:** Hand off internal follow-ups cleanly, review the executive impact summary, and receive a **1–10 Principal Architect rating** across:
   - **Diagnostic Precision & Isolation**
   - **Wire & State-Level Rigor**
   - **Bridge Leadership & Silo Diplomacy**
   - **Change Governance & Risk Control**
   - **Role Boundaries & Handoff Hygiene**

## Limitations & Transparency

To get the most out of this simulator, keep the following boundaries in mind:

* **Simulated Telemetry, Not a Lab Emulator:** Because this runs purely via an LLM rather than a stateful packet emulator (such as EVE-NG, GNS3, or Containerlab), CLI commands, packet captures, and state-table flags are **synthetically generated**. While the logic reflects real-world networking behavior, occasional vendor syntax inaccuracies or minor output inconsistencies ("hallucinations") can occur. Use this to practice **diagnostic methodology, bridge communication, and change governance**—not as a vendor CLI reference.
* **Model Quality Matters:** Maintaining complex topology state and enforcing strict "zero hand-holding" rules across a multi-turn outage requires strong reasoning capabilities. Frontier models produce significantly more realistic, consistent P1 simulations than lightweight or fast-tier models.
* **Organization-Specific Governance:** The change-control workflows modeled here (audit verification, deployment-diff checks, stakeholder notifications, and emergency change records) represent general enterprise best practices and should be adapted to your organization's actual Incident Management policies.
