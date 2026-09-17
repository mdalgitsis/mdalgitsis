## Michail Dalgitsis

Telco and edge-cloud engineer working where mobile networks meet cloud-native infrastructure — 5G cores and
RAN, Kubernetes orchestration, MEC, and the APIs that let one drive the other. Currently at
[Nearby Computing](https://www.nearbycomputing.com/) in Barcelona; previously at
[Vicomtech](https://www.vicomtech.org/) in San Sebastián.

Most of my work is the unglamorous middle layer: packaging network functions so they actually deploy, making
infrastructure observable down to the radio, and designing the interfaces that let an orchestrator act on what
it sees. A recurring theme is failures that are **silent** — a CAPIF that disables itself and answers
normally, a load balancer that announces from no node and logs nothing, a GPU that never reaches the guest.
Most of what I build asserts rather than assumes.

On the research side I publish on network slice federation and cloud-native service orchestration for 5G and
6G, and I am writing a PhD thesis in the same area.

### Work

Grouped by what the problem is, rather than by language.

**Orchestration and federation** — making independently-run platforms cooperate

- **[sliceweaver](https://github.com/mdalgitsis/sliceweaver)** — Per-slice agents that negotiate
  bandwidth through Kubernetes Custom Resources. Two Go operators, a per-slice agent and a 5G
  simulator, with the CRs as the only interface: every decision is an object you can read, diff and
  replay, and any Kubernetes-aware orchestrator can drive it.
- **[closed-loop-k8s-scaling](https://github.com/mdalgitsis/closed-loop-k8s-scaling)** — Where that
  idea started: read a workload's CPU out of Thanos, decide, and write desired state into a
  Kubernetes object an orchestrator watches. Early work, and the README says what it got wrong —
  a Secret has no schema and no status to read back, so the loop never quite closes. `sliceweaver`
  is the same loop done properly.
- **[ipsec-interconnect-operator](https://github.com/mdalgitsis/ipsec-interconnect-operator)** — A
  Kubernetes operator configuring IPsec tunnels between operator platforms through a vendor-neutral
  API with pluggable southbound drivers (strongSwan, VyOS). The tunnel is infrastructure with its own
  lifecycle, so it deliberately knows nothing about whatever consumes it.
- **[edge-cloud-dns-testbed](https://github.com/mdalgitsis/edge-cloud-dns-testbed)** — Three
  Kubernetes sites, each claiming its own address and publishing its own DNS, so a service can
  migrate between edge and cloud and the name follows it. The infrastructure behind an
  [IEEE ICNP 2025 paper](https://doi.org/10.1109/ICNP65844.2025.11192408); Ansible, at the
  `ansible-lint` production profile.
- **[openop-federation-lab](https://github.com/mdalgitsis/openop-federation-lab)** — Standing up two
  independent operator platforms and federating them: cross-domain OAuth2, two Keycloak realms, and
  the investigation notes from making it actually work.
- **[BIND5G](https://github.com/mdalgitsis/BIND5G)** — Network as a Service API specification,
  cross-site Prometheus federation with Thanos, and the WireGuard VPN that federation runs over.

**5G core, RAN and network exposure**

- **[open5gs-k8s](https://github.com/mdalgitsis/open5gs-k8s)** — A complete Open5GS 5G Standalone
  core on Kubernetes with a **relocatable UPF**: one flag moves the user plane to edge nodes while
  the control plane stays central, which is the topology that makes edge offload measurable.
- **[nef-capif-testbed](https://github.com/mdalgitsis/nef-capif-testbed)** — A 3GPP NEF against a
  simulated core with ETSI OpenCAPIF doing real API authorisation, including why a half-configured
  CAPIF is indistinguishable from a working open one.
- **[mec-edge-site](https://github.com/mdalgitsis/mec-edge-site)** — A MEC site whose observability
  reaches past containers into the radio: per-UE throughput, MCS and SNR from a live Amarisoft RAN
  landing in the same Prometheus as pod metrics.

**Agents and LLM systems**

- **[agent-lab](https://github.com/mdalgitsis/agent-lab)** — Learning LLM agent development in Go,
  one concept at a time. Five self-contained stages from a single agent to agent-to-agent
  communication with a registry, memory and MCP tools. Kept as written, including the stage where
  four services collapse back into one because the distribution was not paying for itself.

**Platform and infrastructure**

- **[rke2-kubernetes-cluster](https://github.com/mdalgitsis/rke2-kubernetes-cluster)** — Ansible for
  HA RKE2: embedded-etcd control plane, air-gapped installs, and runbooks for upgrade, backup,
  restore and rotation. Passes `ansible-lint` at the production profile.
- **[kubevirt-gpu-passthrough](https://github.com/mdalgitsis/kubevirt-gpu-passthrough)** — Running
  VMs with a physically passed-through GPU on Kubernetes, including a Windows guest over RDP. Every
  link in the host-to-guest chain fails silently, so each one is asserted rather than assumed.

### Publications

**16 peer-reviewed publications, 8 as first author** — network slicing, slice federation, cloud-native
orchestration and edge-cloud service migration for 5G and 6G. The complete list with DOIs is in
**[PUBLICATIONS.md](PUBLICATIONS.md)**. A selection:

- "6G-Core-in-the-Loop: Enabling Service and Network Orchestration in a Cloud-Native Ecosystem,"
  **IEEE Communications Standards Magazine**, vol. 10, pp. 72–79, 2026.
  [doi](https://doi.org/10.1109/MCOMSTD.2026.3657234)

- "Cloud-Native Orchestration Framework for Network Slice Federation Across Administrative Domains in
  5G/6G Mobile Networks," **IEEE Transactions on Vehicular Technology**, vol. 73, pp. 9306–9319, 2024.
  [doi](https://doi.org/10.1109/TVT.2024.3362583)

- "Coupling Orchestration and DNS for Seamless Service Migration in the Edge–Cloud Continuum,"
  **IEEE ICNP 2025**. [doi](https://doi.org/10.1109/ICNP65844.2025.11192408)

- "Exploiting 6G RAN and Core Network Information for Intelligent Edge-Cloud Service Orchestration,"
  **EuCNC/6G Summit 2025**, pp. 369–374.
  [doi](https://doi.org/10.1109/EuCNC/6GSummit63408.2025.11037032)

- "NSFaaS: Network Slice Federation as a Service in Cloud-Native 5G and Beyond Mobile Networks,"
  **IEEE NFV-SDN 2023**, pp. 59–64. [doi](https://doi.org/10.1109/NFV-SDN59219.2023.10329748)

- "SDN-Based Resource Management for Optical-Wireless Fronthaul," in **Enabling 6G Mobile Networks**,
  Springer, pp. 467–500, 2021. [doi](https://doi.org/10.1007/978-3-030-74648-3_14)

### Recognition

🥈 **2nd Prize — [ETSI / Linux Foundation MEC Hackathon 2022](https://mecwiki.etsi.org/index.php?title=Hack2022_2nd_Prize)**

Team **Pedraforca** (CTTC and Vicomtech), for *"Virtualized mobile and edge infrastructures with OpenAPI
integrations"* — mapping a commercial Amarisoft RAN's proprietary WebSocket interface onto the ETSI MEC012 RNIS
API, with a decision engine scaling edge applications through a Kubernetes OpenAPI I built.

### What I work with

**Platform** · `Kubernetes` `kubebuilder` `Helm` `kustomize` `Ansible` `Terraform` `KubeVirt` `Docker`

**Languages** · `Go` `Python` `FastAPI`

**Agents** · `Google ADK` `MCP` `A2A` `LLM tool-calling`

**Mobile networks** · `Open5GS` `free5GC` `UERANSIM` `Amarisoft` `3GPP 5G SA` `O-RAN`

**Standards and orchestration** · `ETSI MEC` `ETSI OSM` `ETSI OpenOP` `CAPIF` `CAMARA` `OpenAPI`

**Observability** · `Prometheus` `Grafana` `Thanos`

### Elsewhere

[LinkedIn](https://www.linkedin.com/in/michaildalgitsis/) · [ORCID](https://orcid.org/0000-0001-8660-0813)
