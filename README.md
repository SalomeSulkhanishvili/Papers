# Memory-Aware Denial-of-Service Attacks on Shared Cache in Multicore Real-Time Systems

## Citation
- **Author(s):** [Michael Bechtel](https://orcid.org/0000-0002-1452-3289), [Heechul Yun](https://orcid.org/0000-0002-8515-2622)  
- **Published In:** [IEEE Transactions on Computers, 2021](https://ieeexplore.ieee.org/document/9523780)  
- **DOI:** [10.1109/TC.2021.3108044]

---

## Area
**Attacks on Shared Cache in Multicore Real-Time Systems**

## Problem
In multicore systems, tasks running on different cores share resources. A malicious program might exploit this shared cache to harm the performance of other programs by causing significant delays.


## Solution
The paper proposes a novel method, **Memory-Aware Denial-of-Service Attacks**, which more efficiently slows down memory performance by targeting specific vulnerabilities in the shared cache architecture.

## Key Idea
The attack exploits the DRAM bank structure of the memory system. By carefully controlling memory access patterns, the attacker can generate a large number of requests targeting the same DRAM bank. This induces **bank conflicts**, significantly slowing down memory access and degrading overall system performance.

## Key Insights
- **Attack Mechanism:**  
  The attack generates linked lists with all entries allocated in the same memory bank. When an out-of-order core accesses these linked lists, all memory requests target the same DRAM bank, leading to prolonged cache blocking.  
  - *Concurrent memory requests mapped to the same DRAM bank cannot be processed in parallel.*
- **Experimental Validation:**  
  using both synthetic and real-world benchmarks demonstratting enhanced attacks on two popular embedded out-of-order multicore platforms:  
  - Odroid-XU4  
  - Raspberry Pi 4 Model B  
- **Results:**  
  Memory-aware cache DoS attacks are significantly more effective than prior cache DoS attacks in reducing memory performance.
- **Assumptions:**
  1. **HugePage Support:** The runtime system (OS) supports HugePages, and the attacker can allocate memory in its private address space using this feature.  
  2. **Knowledge of DRAM Bank Mapping:** The attacker has knowledge of the system's physical address to DRAM bank address mapping
- **Limitations:**
  1. **Inefficiency on In-Order Processors:**  
   Unlike out-of-order cores, in-order cores cannot traverse multiple linked lists concurrently, which limits their ability to generate concurrent cache misses and induce cache blocking. *(Future Work)*  
  2. **Dependence on Non-Public Memory Mappings:**  
   Hardware platforms do not publicly disclose detailed memory mapping information, making attacks more challenging.  
  3. **Impact of Page Size:**  
   Smaller page sizes reduce the attacker's ability to control memory allocation and target specific DRAM banks, mitigating the attack's effectiveness.

## Key Questions


## My Analysis
- **Connection to Review Topic:**  
  
- **Potential Questions for Seminar:**  


## References





