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
- **[ipsec-interconnect-operator](https://github.com/mdalgitsis/ipsec-interconnect-operator)** — A
  Kubernetes operator configuring IPsec tunnels between operator platforms through a vendor-neutral
  API with pluggable southbound drivers (strongSwan, VyOS). The tunnel is infrastructure with its own
  lifecycle, so it deliberately knows nothing about whatever consumes it.
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

**Platform and infrastructure**

- **[rke2-kubernetes-cluster](https://github.com/mdalgitsis/rke2-kubernetes-cluster)** — Ansible for
  HA RKE2: embedded-etcd control plane, air-gapped installs, and runbooks for upgrade, backup,
  restore and rotation. Passes `ansible-lint` at the production profile.
- **[kubevirt-gpu-passthrough](https://github.com/mdalgitsis/kubevirt-gpu-passthrough)** — Running
  VMs with a physically passed-through GPU on Kubernetes, including a Windows guest over RDP. Every
  link in the host-to-guest chain fails silently, so each one is asserted rather than assumed.

### Publications

First author:

- "6G-Core-in-the-Loop: Enabling Service and Network Orchestration in a Cloud-Native Ecosystem,"
  **IEEE Communications Standards Magazine**, vol. 10, pp. 72–79, 2026.
  [doi:10.1109/MCOMSTD.2026.3657234](https://doi.org/10.1109/MCOMSTD.2026.3657234)

- "Cloud-Native Orchestration Framework for Network Slice Federation Across Administrative Domains in 5G/6G
  Mobile Networks," **IEEE Transactions on Vehicular Technology**, vol. 73, pp. 9306–9319, 2024.
  [doi:10.1109/TVT.2024.3362583](https://doi.org/10.1109/TVT.2024.3362583)

- "NSFaaS: Network Slice Federation as a Service in Cloud-Native 5G and Beyond Mobile Networks,"
  **IEEE NFV-SDN 2023**, pp. 59–64.
  [doi:10.1109/NFV-SDN59219.2023.10329748](https://doi.org/10.1109/NFV-SDN59219.2023.10329748)

Co-author:

- T. Fernández De Barrena, J. L. Ferrando Chacón, A. García, M. Dalgitsis, "5G and MEC Based Data Streaming
  Architecture for Industrial AI," **Communications in Computer and Information Science**, pp. 32–52, 2023.
  [doi:10.1007/978-3-031-49339-3_3](https://doi.org/10.1007/978-3-031-49339-3_3)

- R. Nikbakht, M. Dalgitsis, S. Barrachina-Muñoz, S. Kahvazadeh, "Mobile Edge Vertical Applications Using ETSI
  MEC APIs and Sandbox," **IEEE CSCN 2022** (demo).
  [arXiv:2211.13995](https://arxiv.org/abs/2211.13995)

### Recognition

🥈 **2nd Prize — [ETSI / Linux Foundation MEC Hackathon 2022](https://mecwiki.etsi.org/index.php?title=Hack2022_2nd_Prize)**

Team **Pedraforca** (CTTC and Vicomtech), for *"Virtualized mobile and edge infrastructures with OpenAPI
integrations"* — mapping a commercial Amarisoft RAN's proprietary WebSocket interface onto the ETSI MEC012 RNIS
API, with a decision engine scaling edge applications through a Kubernetes OpenAPI I built.

### What I work with

**Platform** · `Kubernetes` `kubebuilder` `Helm` `kustomize` `Ansible` `Terraform` `KubeVirt` `Docker`

**Languages** · `Go` `Python` `FastAPI`

**Mobile networks** · `Open5GS` `free5GC` `UERANSIM` `Amarisoft` `3GPP 5G SA` `O-RAN`

**Standards and orchestration** · `ETSI MEC` `ETSI OSM` `ETSI OpenOP` `CAPIF` `CAMARA` `OpenAPI`

**Observability** · `Prometheus` `Grafana` `Thanos`

### Elsewhere

[LinkedIn](https://www.linkedin.com/in/michaildalgitsis/) · [ORCID](https://orcid.org/0000-0001-8660-0813)
