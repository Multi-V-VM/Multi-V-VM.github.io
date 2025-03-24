---
title: Multi-V-VM: Migration based on WebAssembly
hide:
  - navigation
  - toc
---

*Any problem in computer science can be solved with another level of indirection.  -Butler Lampson*

Modern AI agents have evolved from simple text generators into fully interactive agents capable of producing, executing, and code generation, consist of both LLM and controlling software. This shift enables richer, more exploratory workflows—such as forking execution paths, rolling back to previous states, and dynamically adjusting resource allocations—yet makes deployment and management challenging. Our proposed AI agent-based container framework unifies cloud and edge resources into a single, adaptive environment for stateful LLM workloads. Instead of statically choosing between local or remote infrastructures, the system dynamically configures the best combination of models, hardware, and execution strategies. This approach optimizes for latency, cost, privacy, and performance simultaneously. Key innovations include seamless state management, allowing LLM applications to fork new tasks at predefined checkpoints, roll back to earlier reasoning stages, and quickly adapt to evolving constraints. Users can start a conversation or code analysis locally for privacy and then offload to a cloud accelerator for more complex computations—automatically, without service interruption. Evaluations on use cases like software development guidance, podcast generation, and survey paper drafting show our framework reduces latency tenfold, improves cost efficiency by 1.39x, and preserves privacy. Ultimately, our solution makes LLM deployments more flexible, context-aware, and resource-efficient.

<img width="683" alt="image" src="https://github.com/user-attachments/assets/ff94f01d-c1f0-4f7e-88ab-46dfdf35e31f" />

Despite their immense potential, current LLM agents face significant hurdles in deployment due to rigid hardware and infrastructure constraints shown in Figure 2. To address these limitations, our approach prioritizes three core requirements:

1. Cascade Attention (Forking): By supporting dynamic branching of attention mechanisms, we enable flexible scaling and forking of inference pathways to tackle diverse application needs.
2. Context Parallelism (Scheduling): Through partitioning computations into smaller contexts, workloads can be efficiently distributed across heterogeneous hosts—both within and across data centers—without compromising performance.
3. Cyber Foraging (Edge-Cloud Collaboration): Intelligent offloading and provisioning empower agents to exploit available resources on edge devices or cloud servers, thereby reducing latency and cost.

A key insight underlying this framework is the complete decoupling of the system state and accelerator state from the application logic, akin to “prefill decoding” techniques. Conventional application-level checkpointing and scheduling provide only partial solutions, as they lack transparency and cannot seamlessly migrate workloads to heterogeneous environments—including mobile devices. By preserving all necessary states within a self-contained environment, our containerization strategy fosters substantial innovation in areas like scheduling, resource allocation, and external function invocation.

<img width="711" alt="image" src="https://github.com/user-attachments/assets/81a664cd-b1e5-4e5c-9f56-bbcc061c8c78" />


Moreover, our performance evaluations emphasize the handling of external function calls—a crucial feature in many AI-agent applications. By embedding tools such as code editors (e.g., Cursor, Sonnet 3.7 + Clangd) within each container, we can transparently manage both function call overhead and resource footprints. This comprehensive approach, which we refer to as “Jump your AI agent everywhere,” significantly simplifies the deployment and scaling of LLM-based applications to any computing environment.
