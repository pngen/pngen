# Paul Ngen

Principal Systems Engineer, Founder and Chief Architect of Summon Software Labs, building open-source accelerated-computing infrastructure, runtime systems, AI systems architecture, and runtime governance.

My work focuses on decomposing complex accelerated infrastructure into explicit, vendor-neutral runtime boundaries with deterministic ownership, authority, lifecycle, recovery, provenance, and evidence.

Each runtime owns one explicit systems boundary. Memory does not silently own scheduling. Scheduling does not silently own authority. Completion does not imply commit. Discovery does not imply capability. A cache hit does not imply reuse eligibility. A process exit does not imply authoritative output. A replica does not imply currency. A hardware fact does not imply freshness.

Authority is explicit: a decision remains valid only while the conditions that justified it remain current, and stale authority is fenced rather than silently inherited.

The architecture separates these concerns so that every transition can be governed, tested, fenced, replayed, recovered, and explained independently.

## Portfolio

### Open Source Data Center Model (OSDCM)

The [Open Source Data Center Model](https://github.com/summonlabs) is a 286-repository, vendor-neutral model of modern AI data-center infrastructure published by Summon Software Labs.

It is organized into three cumulative infrastructure layers:

- **Accelerated Systems Infrastructure (ASI) — 112 repositories**  
  Accelerator memory, reusable state, execution, scheduling, inference serving, communication, storage, compilation, virtualization, persistent execution, autonomous systems, federation, coherence, fault containment, cross-cluster state, runtime evolution, and hardware capability truth.

- **Distributed Fabric Infrastructure (DFI) — 102 repositories**  
  Fabric identity, topology, routing, traffic engineering, congestion, collectives, AI-aware communication, failure and recovery, lifecycle control, observability, NIC/SmartNIC/DPU offload, physical and optical infrastructure, rack and site composition, inter-site authority, and federation.

- **Data Center Control Plane (DCCP) — 72 repositories**  
  Rack and facility state, capacity, placement, electrical infrastructure, thermal and cooling control, hardware lifecycle, tenancy, policy, storage/control integration, failure recovery, observability, economics, regional brokering, federation, and multi-site operation.

**Browse the public corpus:**  
https://github.com/summonlabs

### Engineering Model

The repositories are implemented as inspectable runtime and control boundaries rather than one monolithic framework.

Validation is evidence-driven:

- independent OS processes for multiprocess claims
- real sockets for transport claims
- real CUDA allocation, data movement, integrity, and cleanup for applicable hardware claims
- real close/reopen and process restart for persistence claims
- deterministic race and concurrency coverage
- stale-authority and stale-generation fencing
- corruption and restart testing
- exact resource and accounting closure
- warning-clean builds and release validation
- install/export and independent downstream-consumer verification
- fresh-clone and remote Git release closure

Applicable accelerator paths have been validated on real NVIDIA RTX 5090 / CUDA hardware, with REAL, SYNTHETIC, and UNSUPPORTED evidence explicitly separated.

### Runtime Execution Governance

[Runtime Execution Governance](execution-governance.md) covers AIGOS, the open-source AI Governance Operating System foundation beneath AGIOS, and the AIGOS supervisor daemon `aigosd`.

AIGOS provides deterministic, policy-bounded, auditable runtime control over intelligence execution, including authority, jurisdiction, cost attribution, formal assurance, lifecycle, and liability.

[AGIOS — Artificial General Intelligence Operating System](https://summonsoftware.net) is the proprietary higher-order runtime mesh extending AIGOS.

## Summon Software Labs

The public infrastructure portfolio, including OSDCM repositories and related runtime systems, is maintained under the Summon Software Labs GitHub organization:

**https://github.com/summonlabs**
