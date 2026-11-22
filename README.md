# AIOps Agents on Kubernetes

Read-only AI agents for operations work (Kubernetes debugging first, then CD platforms, GitHub and other systems), isolated in gVisor or microVM sandboxes, on one central platform built with [kagent](https://kagent.dev) and Agent Substrate.

## Documents

Read them in this order:

| # | Document | What it covers |
| --- | --- | --- |
| 1 | [Lab Results](01-lab-results.md) | The lab setup, 21 tests, findings, risks and conclusions |
| 2 | [Production Deployment Plan](02-production-plan.md) | Architecture, security baseline, connecting systems, cluster scope, rollout |
| 3 | [Installation Guide](03-installation-guide.md) | Step-by-step install on bare-metal Kubernetes or AKS, with in-cluster Kubernetes access and GitHub |
| 4 | [Creating Your First Agent](04-creating-your-first-agent.md) | Build one agent and bind its runtime, tools, skills, egress and access policies |
| 5 | [Lab Evidence](05-lab-evidence.md) | Raw command outputs behind the lab results |

## Key decisions

- **In-cluster only for now.** Agents debug the cluster that runs the platform, on bare metal or AKS. Other clusters come later.
- **Read-only is enforced by RBAC** on each tool server, not by tool lists or prompts.
- **gVisor by default.** A microVM worker pool is optional where KVM is available.
- **No credentials in the sandbox.** The egress gateway adds them in transit.
- **Writes come later**, behind human approval.

## Status

The lab was run on 22 Nov 2026 (kagent 1.0, Agent Substrate 1.0, Kubernetes 1.37). The production plan and guides have not been tested end to end yet. Check the "Points to confirm" section of the Installation Guide before you use them.
