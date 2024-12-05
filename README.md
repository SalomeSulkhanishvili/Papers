# Memory-Aware Denial-of-Service Attacks on Shared Cache in Multicore Real-Time Systems

## Citation
- **Author(s):** [Michael Bechtel](https://orcid.org/0000-0002-1452-3289), [Heechul Yun](https://orcid.org/0000-0002-8515-2622)  
- **Published In:** [IEEE Transactions on Computers, 2021](https://ieeexplore.ieee.org/document/9523780)  
- **DOI:** [10.1109/TC.2021.3108044]

---

## Area
**Attacks on Shared Cache in Multicore Real-Time Systems**

## Overview
This document summarizes the exploration and analysis of multicore platforms, memory performance, and considerations for real-time systems. It evaluates the suitability of various processors for safety-critical applications, discusses DRAM bank mapping, and examines how out-of-order processors can be adapted for real-time use.


## Problem
In multicore systems, tasks running on different cores share resources. A malicious program might exploit this shared cache to harm the performance of another program by causing significant delays. 


## Solution
To identify systems benchmarks, this paper proposes a new method **"Memory-Aware Denial-of-Service Attacks"** which can more efficiently slow down memory performance. 

## Key Idea
to exploit the memory system's DRAM bank structure. By carefully controlling memory access patterns, the attacker can generate a large number of requests that target the same DRAM bank. This results in **bank conflicts**, significantly slowing down memory access and overall system performance.

## Key Insights
- **Attack Mechanism:**  
  The attacker generates linked lists with all entries allocated in the same memory bank. When an out-of-order core accesses these linked lists, all memory requests target the same DRAM bank, leading to longer cache blocking.  
  - *Concurrent memory requests mapped to the same DRAM bank cannot be processed in parallel.*
- **Experimental Validation:**  
  Using both synthetic and real-world benchmarks, demonstrating enhanced attacks on two popular embedded out-of-order multicore platforms:
  - Odroid-XU4  
  - Raspberry Pi 4 Model B  
- **Results:**  
  Memory-aware cache DoS attacks are significantly more effective than prior cache DoS attacks in reducing memory performance.
- **Assumptions:**
  1. **HugePage Support:** The runtime system (OS) supports HugePages, and the attacker can allocate memory in its private address space using this feature.  
  2. **Knowledge of DRAM Bank Mapping:** The attacker knows the system's physical address to DRAM bank address mapping
- **Limitations:**
  1. **Inefficiency on In-Order Processors:**  
   Unlike out-of-order cores, in-order cores cannot traverse multiple linked lists concurrently, which limits their ability to generate concurrent cache misses and induce cache blocking. *(Future Work)*  
  2. **Dependence on Non-Public Memory Mappings:**  
   Hardware platforms do not publicly disclose detailed memory mapping information, making attacks more challenging.  
  3. **Impact of Page Size:**  
   Smaller page sizes reduce the attacker's ability to control memory allocation and target specific DRAM banks, mitigating the attack's effectiveness.

## Key Questions


## My Analysis
- **Potential Issues:**


## Platforms Used for Validation

### 1. **Raspberry Pi 4**
- **Processor**: Cortex-A72  
  - High-performance, low-power processor for general-purpose applications.
- **Limitations**:
  - Not designed for hard real-time applications.
  - Unsuitable for safety-critical environments.

### 2. **Odroid XU4**
- **Processor**: Lacks a Real-Time Kernel.
- **Limitations**:
  - Does not provide deterministic guarantees required for safety-critical applications.

#### **Conclusion**:
These platforms are more suitable for general-purpose applications rather than real-time or safety-critical environments. For such systems, processors like **Cortex-R series** are preferred due to their real-time guarantees and safety-critical features.

---

## DRAM Bank Mapping

- The proposed validation method highlights a valuable framework for analyzing **low-level cache attacks**.
- **Challenge**:
  - The assumption of known DRAM bank mapping is unrealistic in practice.
  - Modern systems implement security measures to protect memory integrity, which complicates direct bank mapping analysis.

---

### Applicability of Attacks to Out-of-Order Processors

### **In Real-Time Systems**
- Typically, **in-order processors** are preferred due to:
  - Easier Worst-Case Execution Time (WCET) guarantees.
  - Predictable behavior required for safety-critical applications.

### **Adapting Out-of-Order Processors**
- **Article Reference**: [IEEExplore: Virtual Traces](https://ieeexplore.ieee.org/document/5467051)
  - Virtual traces demonstrate substantial WCET reductions for out-of-order processors.
  - Key techniques include:
    - Improved locality and execution predictability.
    - Enhanced instruction-level parallelism using predicated instruction sets.
  
- **Benefits of Virtual Traces**:
  - Reduce cache pressure from victim tasks through efficient execution.
  - Improve the ability to tolerate cache contention via predictable execution paths.

---

#### Conclusion

- **Out-of-order processors** can be adapted for real-time systems by implementing mechanisms such as virtual traces.
- These mechanisms:
  - Improve task execution predictability.
  - Mitigate the impact of memory-aware DoS attacks.
- However, in traditional safety-critical applications, **in-order processors** and **Cortex-R series** are generally more suitable.






