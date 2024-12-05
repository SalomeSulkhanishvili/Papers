# Paper topic:  AVP Real-Time Cache Partitioning for Multicore Processors

## Time-Predictable Out-of-Order Execution for Hard Real-Time Systems
https://ieeexplore.ieee.org/document/5467051

## 1.Inter-task cache interference aware partitioned real-time scheduling
https://dl.acm.org/doi/10.1145/3341105.3374014

With the increasing number of cores in processors, shared resources like caches are interfering task execution behaviours more heavily and often render global scheduling approaches infeasible in practice. While partitioned scheduling alleviates such interference, in most existing partitioned approaches, constant WCET, which potentially includes all possible interference, must be statically pre-determined prior to the partitioning processes. In this paper, we show that by taking inter-task interference into consideration when making scheduling decisions, resource efficiency can be significantly improved in both temporal and spatial domains for multi/many-core real-time systems. In particular, we propose the inter-task interference matrix (ITIM) to model the inter-task cache/memory interference in a pair-wise manner. Focusing on the problem of interference-aware partitioned scheduling with ITIM, we formalize it as a mixed integer linear program (MILP), which can be solved to achieve optimal solution at the cost of high computational complexity. Meanwhile, we also provide several polynomial-time algorithms to solve the problem approximately. We extensively profile a set of WCET benchmark programs on x86-based multiprocessor server to collect ITIM. The algorithms are evaluated comprehensively, and the evaluation results demonstrate the superior performance of the proposed approaches under various settings.


## 2. Cache Interference-aware Task Partitioning for Non-preemptive Real-time Multi-core Systems
https://dl.acm.org/doi/10.1145/3487581

Shared caches in multi-core processors introduce serious difficulties in providing guarantees on the real-time properties of embedded software due to the interaction and the resulting contention in the shared caches. Prior work has studied the schedulability analysis of global scheduling for real-time multi-core systems with shared caches. This article considers another common scheduling paradigm: partitioned scheduling in the presence of shared cache interference. To achieve this, we propose CITTA, a cache interference-aware task partitioning algorithm. We first analyze the shared cache interference between two programs for set-associative instruction and data caches. Then, an integer programming formulation is constructed to calculate the upper bound on cache interference exhibited by a task, which is required by CITTA. We conduct schedulability analysis of CITTA and formally prove its correctness. A set of experiments is performed to evaluate the schedulability performance of CITTA against global EDF scheduling and other greedy partition approaches such as First-fit and Worst-fit over randomly generated tasksets and realistic workloads in embedded systems. Our empirical evaluations show that CITTA outperforms global EDF scheduling and greedy partition approaches in terms of task sets deemed schedulable.

## 3. Dynamic Cache-Partition Schedulability Analysis
https://ieeexplore.ieee.org/document/9162466
Recent integration of the cache-partition model has ushered in new paradigms of research in the predictability and schedulability analysis for real-time systems. However, simplicity in the analysis framework has prompted existing contributions to be biased towards a static cache-partitioning scheme. The dynamic scheme has largely been untackled despite its proficiency in schedulability, flexibility, and energy-efficiency. In this letter, we address the latter problem and make initial contributions to a dynamic cache-partition schedulability analysis for multicore partitioned scheduling of real-time fixed-priority sporadic tasks. We devise a sufficient schedulability test and then refine the upper-bound by proposing techniques to reduce the pessimism in the interference caused by cache-contention.



## 4. Flexible Cache Partitioning for Multi-Mode Real-Time Systems
https://ieeexplore.ieee.org/document/9474240
Cache partitioning is a well-studied technique that mitigates the inter-processor cache interference in multiprocessor systems. The resulting optimization problem involves allocating portions of the cache to individual processors. In multi-mode applications (e.g., flight control system that runs in take-off, cruise, or landing mode), the cache memory requirement can change over time, making runtime cache repartitioning necessary. This paper presents a cache partition allocation framework enabling flexible cache partitioning for multi-mode real-time systems. The main objective is to guarantee timing predictability in the steady states and during mode changes. We evaluate the effectiveness of our approach for multiple embedded benchmarks with different ranges of cache size sensitivity. The results show increased schedulability compared to static partitioning approaches.


