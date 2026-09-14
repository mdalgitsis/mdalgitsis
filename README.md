## Michail Dalgitsis

Telco and edge-cloud engineer working where mobile networks meet cloud-native infrastructure — 5G cores and
RAN, Kubernetes orchestration, MEC, and the APIs that let one drive the other. Currently at
[Nearby Computing](https://www.nearbycomputing.com/) in Barcelona; previously at
[Vicomtech](https://www.vicomtech.org/) in San Sebastián.

Most of my work is the unglamorous middle layer: packaging network functions so they actually deploy, making
infrastructure observable down to the radio, and designing the interfaces that let an orchestrator act on what
it sees. On the research side I publish on network slice federation and cloud-native service orchestration for
5G and 6G.

### Selected work

**[open5gs-k8s](https://github.com/mdalgitsis/open5gs-k8s)** — A complete Open5GS 5G Standalone core on
Kubernetes, built for edge research. The UPF is relocatable: one flag moves the user plane to edge nodes while
the control plane stays central, which is the topology that makes edge offload measurable. Network slicing via
S-NSSAI, Prometheus metrics, a UERANSIM gNB/UE simulator, and the Dockerfiles for every image it needs.

**[mec-edge-site](https://github.com/mdalgitsis/mec-edge-site)** — A Multi-access Edge Computing site: a
kubeadm cluster, ETSI OSM integration for orchestrating network functions, and an observability stack that
reaches past containers into the mobile network — per-UE throughput, MCS and SNR from a live Amarisoft RAN
landing in the same Prometheus as your pod metrics. Includes the Edge-API, a REST interface for driving cluster
workloads and scaling remotely.

**[BIND5G](https://github.com/mdalgitsis/BIND5G)** — My contributions to the Basque Industry 5G project: the
Network as a Service API specification, cross-site Prometheus federation with Thanos, and the WireGuard
site-to-site VPN that federation runs over.

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

`Kubernetes` · `Helm` · `Ansible` · `Terraform` · `Docker` · `Go` · `Python`
`Open5GS` · `UERANSIM` · `Amarisoft` · `ETSI OSM` · `ETSI MEC` · `O-RAN`
`Prometheus` · `Grafana` · `Thanos` · `OpenAPI` · `3GPP 5G SA`

### Elsewhere

[LinkedIn](https://www.linkedin.com/in/michaildalgitsis/) · [ORCID](https://orcid.org/0000-0001-8660-0813)
