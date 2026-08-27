<div align="center">

# Danushka Stanley

### Senior DevOps Engineer building secure, observable cloud-native systems

**AWS · Kubernetes · Terraform · Platform Engineering · eBPF · Go · Rust**

<p>
  <a href="https://www.danushkastanley.com">
    <img src="https://img.shields.io/badge/Website-danushkastanley.com-0F172A?style=for-the-badge&logo=safari&logoColor=white" alt="Website" />
  </a>
  <a href="https://github.com/danushkastanley">
    <img src="https://img.shields.io/badge/GitHub-danushkastanley-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" />
  </a>
  <a href="https://github.com/danushkastanley/KubeMemLens">
    <img src="https://img.shields.io/badge/Open%20Source-KubeMemLens-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white" alt="KubeMemLens" />
  </a>
</p>

📍 Sri Lanka  
**MSc Cybersecurity & Forensics — Distinction**  
University of Westminster

</div>

---

## About me

I design and operate multi-region AWS platforms, build IaC-first delivery systems, and create practical tooling for Kubernetes reliability and runtime security.

Most of my work begins with an operational problem: reduce uncertainty, automate the repetitive parts, preserve useful evidence, and leave behind something safer and easier to operate.

My current focus is:

- 🔎 **Kubernetes diagnostics** — making workload memory behaviour understandable with KubeMemLens
- 🛡️ **Runtime security** — continuing my eBPF-based Kubernetes RASP research through KyNox
- 🧠 **MLOps and MLSecOps** — applying platform reliability, supply-chain security and observability practices to model delivery
- ✍️ **Technical writing** — sharing practical lessons from Kubernetes, DevSecOps, eBPF and production engineering

---

## Featured project: [KubeMemLens](https://github.com/danushkastanley/KubeMemLens)

> **See why your Kubernetes Pod memory is high.**

<a href="https://github.com/danushkastanley/KubeMemLens">
  <img
    src="https://raw.githubusercontent.com/danushkastanley/KubeMemLens/main/docs/images/kube-memlens-tui-2.0.jpg"
    alt="KubeMemLens terminal interface showing Kubernetes workload memory evidence"
    width="100%"
  />
</a>

<p>
  <a href="https://github.com/danushkastanley/KubeMemLens/releases">
    <img src="https://img.shields.io/github/v/release/danushkastanley/KubeMemLens?include_prereleases&sort=semver&style=flat-square&label=release" alt="Latest release" />
  </a>
  <a href="https://github.com/danushkastanley/KubeMemLens/stargazers">
    <img src="https://img.shields.io/github/stars/danushkastanley/KubeMemLens?style=flat-square&logo=github" alt="GitHub stars" />
  </a>
  <a href="https://github.com/danushkastanley/KubeMemLens/commits/main">
    <img src="https://img.shields.io/github/last-commit/danushkastanley/KubeMemLens?style=flat-square" alt="Last commit" />
  </a>
  <a href="https://github.com/danushkastanley/KubeMemLens/issues">
    <img src="https://img.shields.io/github/issues/danushkastanley/KubeMemLens?style=flat-square" alt="Open issues" />
  </a>
</p>

KubeMemLens is a terminal-first Kubernetes memory inspector built after a real production investigation where the Pod memory number was high, but the application heap did not explain it.

Instead of presenting one aggregate number, it separates observed cgroup memory into **anonymous memory, filesystem-backed cache, shmem/tmpfs and residual memory**, then adds pressure, OOM, writeback and workload context.

Its current workflow includes:

- An incident-focused TUI with node, namespace, workload, Pod and container navigation
- Memory composition, limits, headroom, trends, pressure and OOM evidence
- Historical investigation, safe incident capture, replay and before/after comparison
- Read-only recommendations with rationale and guard conditions
- Structured JSON, YAML and CSV output for automation
- Authenticated access through the Kubernetes aggregation layer
- Published lifecycle and scale-qualification evidence, including a 5,000-container local RC run

> [!IMPORTANT]
> KubeMemLens is currently in alpha and is intended for evaluation on disposable or explicitly authorised clusters. It does not yet carry a production stability or support guarantee.

[**Repository**](https://github.com/danushkastanley/KubeMemLens) ·
[**Documentation**](https://github.com/danushkastanley/KubeMemLens/tree/main/docs) ·
[**Releases**](https://github.com/danushkastanley/KubeMemLens/releases) ·
[**Report an issue**](https://github.com/danushkastanley/KubeMemLens/issues)

---

## Runtime security research: KyNox

**KyNox** is the open-source continuation of my MSc dissertation research into eBPF-based Runtime Application Self-Protection for Kubernetes.

It combines a privileged **Rust and libbpf-rs node agent** with a **Go control plane**, using gRPC and mutual TLS to transport security-relevant workload telemetry.

```mermaid
flowchart LR
    Kernel["Linux kernel"] -->|"eBPF events"| Agent["Rust node agent"]
    Agent -->|"gRPC + mTLS"| Controller["Go controller"]
    Controller --> Detection["Detection and classification"]
    Controller --> Alerts["Slack and webhooks"]
```

The research explores:

- Process execution and parent-child activity
- Filesystem access and permission changes
- Network connections and socket operations
- Privilege, capability and `ptrace` activity
- Kubernetes workload-context enrichment
- Event classification, rate limiting and alert aggregation

<p>
  <a href="https://github.com/danushkastanley/kynox-pod-agent">
    <img src="https://img.shields.io/badge/Node%20Agent-Rust%20%2B%20eBPF-DEA584?style=for-the-badge&logo=rust&logoColor=white" alt="KyNox node agent" />
  </a>
  <a href="https://github.com/danushkastanley/kynox-pod-controller">
    <img src="https://img.shields.io/badge/Controller-Go-00ADD8?style=for-the-badge&logo=go&logoColor=white" alt="KyNox controller" />
  </a>
</p>

> [!NOTE]
> KyNox is a pre-1.0 research prototype for controlled, non-production evaluation. It provides telemetry and detection signals rather than replacing Kubernetes hardening, admission control or incident response.

---

## Selected engineering impact

| Focus | Outcome |
|---|---|
| **Reliability and observability** | Improved MTTA from hours to approximately **1 minute** and MTTR from approximately **4–5 hours to under 1 hour** through a Datadog observability migration |
| **Delivery automation** | Reduced post-deployment validation from approximately **60 minutes to 10 minutes** using Playwright and evidence-backed notifications |
| **Platform engineering** | Built a reusable library of **30+ Terraform modules** for standardised multi-region AWS environments |
| **Kubernetes adoption** | Migrated production workloads from **Elastic Beanstalk to Amazon EKS** using IaC-first change control |
| **Secure software delivery** | Rolled out SonarQube quality gates across **300+ repositories** and introduced automated OWASP ZAP validation |
| **Incident response** | Built actionable monitoring and operational workflows across Datadog, CloudWatch and PagerDuty |

---

## Toolbox

<p align="center">
  <img
    src="https://skillicons.dev/icons?i=aws,kubernetes,docker,terraform,githubactions,jenkins,go,rust,python,bash,linux,prometheus,grafana&perline=13"
    alt="Core engineering technologies"
  />
</p>

<p align="center">
  <code>Amazon EKS</code>
  <code>Helm</code>
  <code>Argo CD</code>
  <code>Buildkite</code>
  <code>Datadog</code>
  <code>CloudWatch</code>
  <code>PagerDuty</code>
  <code>Playwright</code>
  <code>GitHub Actions</code>
</p>

---

## Engineering principles

> **Fewer features, stronger guarantees.** Automate to reduce cognitive load, make failures explainable, and treat security as part of the platform rather than something bolted on afterwards.

---

## Writing and collaboration

I write about **Kubernetes, eBPF, cloud security, platform reliability, DevSecOps and applied AI** at [danushkastanley.com](https://www.danushkastanley.com).

Contributions, non-production test reports and well-scoped issues are welcome on [KubeMemLens](https://github.com/danushkastanley/KubeMemLens).

<div align="center">

### Build reliable systems. Make failure explainable. Keep security practical.

[Website](https://www.danushkastanley.com) ·
[GitHub](https://github.com/danushkastanley) ·
[KubeMemLens](https://github.com/danushkastanley/KubeMemLens)

</div>
