# Paul Ngen

Chief AI Architect and Founder of Summon Software Labs, building open-source AI accelerator infrastructure and runtime systems.

My work focuses on converting expensive private AI infrastructure into explicit, vendor-neutral runtime boundaries across memory, reusable state, execution, inference, compilation, caching, movement, recovery, authority, resource governance, and observability.

## Open Source AI Accelerator Infrastructure

Summon Software Labs develops an expanding open-source accelerator infrastructure portfolio for heterogeneous AI systems.

The portfolio spans memory, reusable computational state, inference serving, execution placement, compilation, kernel and graph reuse, resource governance, distributed authority, recovery, communication, and observability.

The architecture is intentionally decomposed.

Each runtime owns a specific systems boundary rather than collapsing memory, state, execution, movement, recovery, scheduling, caching, and policy into one monolithic framework.

Current public infrastructure:

| Runtime | Systems boundary | Core question |
| --- | --- | --- |
| [FlashTier](https://github.com/pngen/FlashTier) | Heterogeneous accelerator-memory residency across device memory, pinned host memory, and NVMe. | Where do the bytes live? |
| [Context Fabric](https://github.com/pngen/Context-Fabric) | Identity, ownership, generations, replicas, persistence, migration, lineage, and placement for reusable computational state. | Where does accumulated reusable computation live? |
| [Compute Fabric](https://github.com/pngen/Compute-Fabric) | Distributed execution placement across heterogeneous compute nodes. | Where should the next computation run? |
| [Reclaim Fabric](https://github.com/pngen/Reclaim-Fabric) | Economic reclamation of reusable machine state. | What state is still worth keeping? |
| [Checkpoint Fabric](https://github.com/pngen/Checkpoint-Fabric) | Coherent checkpointing, persistence, restore, migration, rollback, lineage, fencing, and crash recovery. | What execution state must survive? |
| [KV Fabric](https://github.com/pngen/KV-Fabric) | Distributed reusable KV and prefix inference state. | Where should reusable inference state live, when should it move, who may use it, and when is reuse cheaper than recomputation? |
| [Tensor Cache](https://github.com/pngen/Tensor-Cache) | Reusable tensor-shaped computational state across accelerator, host, storage, process, and execution boundaries. | Where should reusable tensor state live, when should it move, when should it be reused, and when is reconstruction cheaper than retention or transfer? |
| [Unified Buffer](https://github.com/pngen/Unified-Buffer) | Buffer allocation, identity, ownership, residency, pooling, reuse, sharing, and movement across heterogeneous memory domains. | What should a buffer mean when memory is no longer one place? |
| [Transfer Fabric](https://github.com/pngen/Transfer-Fabric) | Planning, routing, staging, scheduling, overlapping, verifying, and governing data movement. | How should bytes move? |
| [Topology Fabric](https://github.com/pngen/Topology-Fabric) | Hardware and interconnect discovery, topology, locality, path cost, and candidate ranking. | What hardware topology exists, what connects it, and what does that imply about locality and path cost? |
| [Memory Pressure](https://github.com/pngen/Memory-Pressure) | Memory scarcity detection, modeling, pressure state, budgets, thresholds, and governed response. | When memory becomes scarce, how should the system know and respond before scarcity becomes failure? |
| [Prefix Fabric](https://github.com/pngen/Prefix-Fabric) | Reusable token-prefix identity, indexing, matching, lineage, segmentation, and reuse discovery. | What reusable prefix structure already exists, which requests overlap with it, and what exact relationship justifies reuse? |
| [Model Cache](https://github.com/pngen/Model-Cache) | Caching, validation, versioning, persistence, integrity, deduplication, dependencies, and reuse of model artifacts. | What reusable model artifact already exists for this exact requirement, is it valid, and should we reuse it instead of rebuilding or reacquiring it? |
| [Allocator Lab](https://github.com/pngen/Allocator-Lab) | Designing, benchmarking, stress-testing, replaying, and comparing memory allocators. | How should memory allocation strategies be measured, compared, stressed, and understood before one of them is trusted inside serious AI infrastructure? |
| [Memory Observatory](https://github.com/pngen/Memory-Observatory) | Measurement, correlation, explanation, replay, provenance, and diagnostics for heterogeneous memory behavior. | What is memory doing across the system, why is it behaving that way, and what evidence explains how that behavior changed over time? |
| [Inference Scheduler](https://github.com/pngen/Inference-Scheduler) | Admission, queueing, batching, fairness, deadlines, phase coordination, backpressure, retries, cancellation, and accelerator-aware dispatch. | What inference work should run next, where should it run, and under what latency, fairness, capacity, batching, and execution constraints? |
| [Batch Fabric](https://github.com/pngen/Batch-Fabric) | Dynamic inference batching, compatibility-aware grouping, latency-bounded formation, splitting, merging, fairness, and cancellation. | Which inference requests should execute together, when should a batch seal, and when is waiting for a larger batch no longer worth the latency cost? |
| [Prefill Fabric](https://github.com/pngen/Prefill-Fabric) | Scheduling, packing, partitioning, executing, and governing prompt-prefill work. | How should prompt-prefill work be formed, scheduled, partitioned, executed, and governed so large and heterogeneous prompts make progress without destroying latency, fairness, memory headroom, or downstream serving capacity? |
| [Decode Fabric](https://github.com/pngen/Decode-Fabric) | Continuous scheduling, regrouping, execution, and governance of iterative token decoding. | How should active generation work be scheduled, regrouped, executed, and governed token by token so many concurrent sequences make progress without sacrificing latency, fairness, memory headroom, cancellation responsiveness, or throughput? |
| [Speculation Fabric](https://github.com/pngen/Speculation-Fabric) | Speculative proposal, verification, partial acceptance, rollback, branching, retry, and distributed authority. | How should speculative generation be proposed, verified, accepted, rejected, rolled back, and accounted for so work can run ahead of authority without sacrificing correctness, fairness, memory discipline, or deterministic recovery? |
| [Kernel Cache](https://github.com/pngen/Kernel-Cache) | Caching, validating, persisting, reusing, invalidating, rebuilding, and evicting compiled AI kernel artifacts. | Which compiled kernel artifact may be reused, under what compatibility constraints, where should it reside, and when must it be invalidated, rebuilt, or evicted? |
| [Graph Cache](https://github.com/pngen/Graph-Cache) | Caching, validating, persisting, reusing, invalidating, and recapturing AI execution graphs. | Which captured execution graph may be safely replayed for this workload, under what compatibility and generation constraints, and when has that graph become stale? |
| [Compilation Fabric](https://github.com/pngen/Compilation-Fabric) | AI compilation specialization, code generation, validation, reuse, invalidation, reproducibility, and accelerator-targeted deployment. | How should executable AI artifacts be derived, specialized, validated, reproduced, invalidated, and deployed across heterogeneous accelerators? |
| [Placement Observatory](https://github.com/pngen/Placement-Observatory) | Reconstructing, explaining, replaying, and comparing AI workload placement decisions across compute, memory, topology, queue, capacity, and locality constraints. | Why did this work land here, what alternatives existed, which constraints and costs drove the decision, and can that decision be reconstructed later from evidence rather than guessed from outcome? |
| [Latency Governor](https://github.com/pngen/Latency-Governor) | Enforcing explicit latency SLOs across admission, waiting, batching, placement, movement, execution, speculation, retry, and recovery. | How should resource and execution decisions be governed against explicit latency obligations before the deadline is lost? |
| [Admission Fabric](https://github.com/pngen/Admission-Fabric) | Multidimensional admission control across accelerator memory, host memory, pinned memory, KV growth, tensor state, transfer demand, compute occupancy, quotas, token budgets, capability requirements, and latency SLOs. | Given current capacity, quotas, predicted resource demand, token budget, expected duration, and latency obligations, can this work be admitted safely now, should it be deferred, or must it be rejected? |
| [Quota Fabric](https://github.com/pngen/Quota-Fabric) | Multidimensional quota governance across accelerator memory, host memory, KV/tensor state, compute time, transfer bandwidth, persistent cache, model residency, and concurrent serving capacity, with guarantees, burst, borrowing, recall, hierarchy, and continuous enforcement. | Who may consume scarce accelerator infrastructure, how much are they entitled to, what may they borrow or burst into, and what must they return when stronger obligations arrive? |
| [Bandwidth Governor](https://github.com/pngen/Bandwidth-Governor) | Governing scarce PCIe, NVLink-class, host-memory, storage, and inter-node bandwidth across competing AI workloads with explicit fairness, priority, latency, reservations, throttling, path-aware arbitration, and authority fencing. | How should competing data flows share scarce bandwidth without violating latency, fairness, priority, reservation, and throughput requirements? |
| [Replica Fabric](https://github.com/pngen/Replica-Fabric) | Governing replicated AI runtime state across identity, generation, health, readiness, placement, promotion, draining, failover, recovery, and serving authority. | Which live replica is current, healthy, ready, authoritative, and allowed to serve? |
| [Warmth Fabric](https://github.com/pngen/Warmth-Fabric) | Operational readiness across model state, adapters, tokenizer/runtime state, CUDA context, kernels, execution graphs, allocators, reusable prefix/KV state, engine readiness, and local dependencies, with explicit warmth state, decay, invalidation, budgets, and rewarming. | How ready is this workload to execute now, what state is already warm, what remains cold, what will warming cost, and when has prepared state become stale or invalid? |
| [Adapter Fabric](https://github.com/pngen/Adapter-Fabric) | Governing adapter identity, compatibility, composition, residency, activation, migration, invalidation, persistence, recovery, and execution authority across heterogeneous AI serving infrastructure. | Which adapter state is valid, compatible, resident, composed, and authorized to affect execution right now? |
| [Serving Observatory](https://github.com/pngen/Serving-Observatory) | Reconstructing, explaining, replaying, and attributing per-request AI serving behavior across queueing, batching, dispatch, prefill, decode, KV reuse, residency, kernel/graph reuse, transfers, retries, failures, recovery, resource use, and tail latency. | What happened to this request while it was being served, where did its time and resources go, which runtime decisions shaped the outcome, and can that behavior be reconstructed later from evidence rather than guessed from aggregate metrics? |
| [Inference Ledger](https://github.com/pngen/Inference-Ledger) | Exact, replayable accounting of inference-resource consumption, useful work, waste, reuse, shared costs, attributed cost, and authority across requests, attempts, batches, residency, transfers, retries, and failures. | What resources did this inference request actually consume, what useful work did those resources produce, what was reused or wasted, and what exact cost should be attributed to the request? |
| [Failure Fabric](https://github.com/pngen/Failure-Fabric) | Governing failure semantics, ambiguity, idempotency, rollback, compensation, recovery ownership, retryability, side effects, terminality, persistence, and stale-authority rejection across distributed AI infrastructure. | When distributed AI work fails, what happened, what may still be true, who owns recovery, what may safely retry or roll back, and what is still allowed to become authoritative? | 
| [Chaos Lab](https://github.com/pngen/Chaos-Lab) | Deterministic adversarial validation across failure injection, process death, transport disruption, persistence corruption, stale authority, restart behavior, resource pressure, race conditions, and recovery in distributed AI infrastructure. | Can this system survive the failure we think it can survive under deterministic, reproducible evidence rather than assumption? |
| [Compatibility Registry](https://github.com/pngen/Compatibility-Registry) | Canonical compatibility identities, deterministic rule evaluation, provenance, generations, dependencies, invalidation, historical replay, and explicit compatibility outcomes across models, tokenizers, tensors, KV formats, kernels, graphs, adapters, runtimes, protocols, policies, and accelerator capabilities. | What exactly must agree before reuse, movement, loading, replay, activation, binding, or execution is allowed? | 
| [State Provenance](https://github.com/pngen/State-Provenance) | Governing origin, derivation, lineage, compatibility, authority, dependencies, invalidation, historical replay, and reuse eligibility across machine-produced AI state. | Where did this reusable state come from, what exact computation and inputs produced it, what depends on it, what authority made it current, and is it still valid to reuse now? | 
| [Artifact Fabric](https://github.com/pngen/Artifact-Fabric) | Governing machine-produced AI artifacts across identity, compatibility, provenance, persistence, dependency, lifecycle, authority, reuse, invalidation, supersession, quarantine, and deployment. | What artifact exists, where did it come from, what is it compatible with, which dependencies and generations make it valid, and when is it safe to reuse, invalidate, supersede, or retire? | 
| [GPU Fleet Agent](https://github.com/pngen/GPU-Fleet-Agent) | Governing GPU fleet state, identity, capability, health, readiness, freshness, authority, recovery, and execution eligibility across accelerator infrastructure. | What accelerator resources exist right now, which ones are healthy, compatible, trustworthy, and ready for work, and which fleet state is authoritative enough to drive execution decisions? |
| [Accelerator Health](https://github.com/pngen/Accelerator-Health) | Governing accelerator health, readiness, recovery, degradation, evidence freshness, fault history, quarantine, revalidation, and execution eligibility across heterogeneous AI infrastructure. | Is this accelerator actually healthy enough to execute work now, what evidence supports that judgment, what is degraded or failing, and what must happen before it can safely return to service? |
| [Power Governor](https://github.com/pngen/Power-Governor) | Governing accelerator power, energy, thermal headroom, workload policy, reservations, execution limits, freshness, authority, and recovery across heterogeneous AI infrastructure. | How much power and energy may this accelerator consume now, what constraints bind execution, and what work should be allowed, limited, deferred, or rejected? |
| [Energy Observatory](https://github.com/pngen/Energy-Observatory) | Measuring, attributing, explaining, replaying, and reconstructing accelerator energy consumption across workloads, devices, execution phases, retries, failures, recovery, and distributed AI infrastructure. | How much energy did accelerator work actually consume, where did that energy go, what useful work did it produce, what evidence supports the attribution, and can that conclusion be reconstructed later? |
| [NUMA Fabric](https://github.com/pngen/NUMA-Fabric) | NUMA-aware CPU, memory, accelerator, and I/O locality across heterogeneous AI infrastructure. | Where should work and memory live relative to the hardware using them? |
| [PCIe Fabric](https://github.com/pngen/PCIe-Fabric) | PCIe topology, locality, path capability, measured transfer behavior, contention, and accelerator/I/O placement across heterogeneous AI infrastructure. | What path connects this work to the hardware it depends on, and what can that path actually deliver? |
| [Collective Fabric](https://github.com/pngen/Collective-Fabric) | Collective communication planning, topology, membership, execution authority, failure, recovery, and commit across distributed accelerator infrastructure. | Which collective should run, over what topology, under whose authority, and which result may become real? |
| [RDMA Buffer](https://github.com/pngen/RDMA-Buffer) | Governed remote-access memory across registration, protection domains, access rights, leases, key generations, revocation, reuse, invalidation, and stale-authority fencing. | Which buffer is valid, who owns it, and is this remote operation still authorized to touch the memory? |
| [Storage Fabric](https://github.com/pngen/Storage-Fabric) | AI-specific storage across object identity, tier placement, replicas, durability, integrity, movement, restore, eviction, capacity, and authority. | Where should AI state live, which copy is authoritative, and what must survive failure or restart? |
| [Checkpoint Store](https://github.com/pngen/Checkpoint-Store) | Checkpoint storage, chunking, deduplication, integrity, retention, garbage collection, replica authority, restore, and recovery. | Which checkpoint bytes exist, which chunks are shared, what may be reclaimed, and what can safely be restored? |

The portfolio is designed as a cumulative accelerated-computing substrate.

Each runtime exposes infrastructure that serious AI operators would otherwise need to design, integrate, harden, validate, and maintain independently.

## Runtime Governance

[AIGOS](https://github.com/pngen/aigos) is the open-source AI Governance Operating System foundation beneath AGIOS.

It provides deterministic, policy-bounded, auditable runtime control over intelligence execution.

AIGOS makes core governance questions explicit:

- what executed
- what was authorized
- which policy applied
- which jurisdiction governed execution
- what execution cost
- who held authority
- who held liability
- what can be replayed
- what can be formally verified

The AIGOS supervisor daemon:

**[aigosd](https://github.com/pngen/aigosd)**

Core systems:

- [DIO — Deterministic Intelligence Orchestrator](https://github.com/pngen/dio)
- [ZT-AAS — Zero-Trust Autonomous Agent Sandbox](https://github.com/pngen/zt-aas)
- [ICAE — Inference Cost Attribution Engine](https://github.com/pngen/icae)
- [POC — Policy-to-Outcome Compiler](https://github.com/pngen/poc)
- [FAK — Formal Assurance Kernel](https://github.com/pngen/fak)
- [ARE — Authority Realization Engine](https://github.com/pngen/are)
- [JIB — Jurisdictional Intelligence Boundary](https://github.com/pngen/jib)
- [ICL — Intelligence Capital Ledger](https://github.com/pngen/icl)
- [GSAS — Governance Substrate for Autonomous Systems](https://github.com/pngen/gsas)
- [ABLE — Authority-Bound Liability Engine](https://github.com/pngen/able)

AGIOS extends that foundation into broader runtime governance for general intelligence and institutional deployment.

## Accelerated Systems Engineering

Primary areas of work include:

- heterogeneous accelerator memory
- reusable computational state
- distributed AI state
- inference scheduling and serving
- CUDA and accelerator integration
- compilation and executable artifacts
- kernel and execution-graph reuse
- execution placement and dispatch
- data movement and transfer
- topology and locality
- memory pressure and resource governance
- admission and quota control
- latency and bandwidth governance
- persistence and crash recovery
- replica lifecycle and failover
- distributed authority and fencing
- deterministic lifecycle and shutdown
- integrity and resource accounting
- multi-process and framed-network runtimes
- replayable observability
- policy-bounded execution
- formal assurance
